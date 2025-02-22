---
layout: post
title: "My Blog Webmention Counts"
microblog: false
guid: http://greg-morris.micro.blog/2024/02/18/my-blog-webmention.html
post_id: 3988353
date: 2024-02-18T08:22:00-0000
lastmod: 2024-04-12T10:07:06-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/6c7d3fa5a0.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/6c7d3fa5a0.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/6c7d3fa5a0.jpg
  width: 0
  height: 0
url: /2024/02/18/my-blog-webmention.html
---
---
This week I have been building parts of my blog, to learn and to get it to a point that I am happy with. A large part of this was webmentions, and thanks to a few [excellent](https://mxb.dev/blog/using-webmentions-on-static-sites/) [guides](https://equk.co.uk/2023/07/18/adding-webmentions-in-eleventy/) I got 90% of the the way their. With only a few design things to think through I read [more](https://campegg.com/2024/02/11/over-the-last.html) [posts](https://rknight.me/blog/webmentions-redux/) on webmentions and realised the way I was doing it was the best solution for privacy and so here we are with a reduced version. 

I need to preface this with the fact I am a noob, and this might be a) wrong or b) a stupid way of doing it. This is just the way I did it, and if you’ve got some advice I am all ears.

## Webmentions

I had already implemented a script to pull these from webmention.io and cache these into a local file. 

```
  // Import required modules
  const fetch = require('node-fetch');
  const fs = require('fs');
  const path = require('path');
  require('dotenv').config();

  // Constants
  const CACHE_DIR = './_cache';
  const API_ORIGIN = 'https://webmention.io/api/mentions.jf2';
  const TOKEN = process.env.WEBMENTION_IO_TOKEN;

  // Ensure cache directory exists
  if (!fs.existsSync(CACHE_DIR)) {
      fs.mkdirSync(CACHE_DIR);
  }

  // Function to fetch data from the API
  async function fetchData() {
      try {
          const response = await fetch(`${API_ORIGIN}?token=${TOKEN}`);
          if (!response.ok) {
              throw new Error(`Failed to fetch data: ${response.status} ${response.statusText}`);
          }
          const data = await response.json();
          return data;
      } catch (error) {
          console.error('Error fetching data:', error.message);
          throw error;
      }
  }

  // Function to save data to JSON file
  function saveDataToFile(data) {
      try {
          const filePath = path.join(CACHE_DIR, 'webmentions.json');
          fs.writeFileSync(filePath, JSON.stringify(data, null, 2));
          console.log('Data saved to:', filePath);
      } catch (error) {
          console.error('Error saving data to file:', error.message);
          throw error;
      }
  }

  // Main function to fetch data and save it to file
  async function main() {
      try {
          const data = await fetchData();
          saveDataToFile(data);
      } catch (error) {
          console.error('An error occurred:', error.message);
          process.exit(1);
      }
  }

  // Run main function
  main();
```

Instead of loading all of the information from this as most guides do, I decided instead to simply count the important details. I think this could be cleaner but its working as thats all I am working on at the moment.

```
{% raw %}
const filteredWebmentions = data.children.filter(entry => {
      return entry['like-of'] === url || entry['in-reply-to'] === url || entry['repost-of'] === url;
    });

    // Initialize counts for each type
    let likeCount = 0;
    let replyCount = 0;
    let repostCount = 0;

    // Loop through each entry in the filtered webmentions
    filteredWebmentions.forEach(entry => {
      // Check if the entry matches the given URL for like, reply, or repost
      if (entry['like-of'] === url) {
        likeCount++;
      }
      if (entry['in-reply-to'] === url) {
        replyCount++;
      }
      if (entry['repost-of'] === url) {
        repostCount++;
      }
    });

    // Return an object containing the counts
    return {
      likeCount,
      replyCount,
      repostCount
    };
{% endraw %}
```

This is then displayed on my post using:

```
{% raw %}
{% set urlnohtml = page.url | url | absoluteUrl(metadata.url) | replace('.html', '') %}
{% set urlhtml = page.url | url | absoluteUrl(metadata.url) %}
{% set countnohtml = webmentionsFilePath | countWebmentions(urlnohtml) %}
{% set counthtml = webmentionsFilePath | countWebmentions(urlhtml) %}
{% set totallikes = countnohtml.likeCount + counthtml.likeCount %}
{% set totalreplies = countnohtml.replyCount + counthtml.replyCount %}
{% set totalrepost = countnohtml.repostCount + counthtml.repostCount %}
{% endraw %}
```

This is not very effect as I ran into an issue where i had shared some links with `.html` on the end and some without, so got an MVP working late last night.

![](https://greg-morris.micro.blog/uploads/2024/6c7d3fa5a0.jpg)

## Mastodon Information

I could then link people to the resulting Mastodon post but decided I wanted to go further and display the information from the toot.

The easy way would have been to rely on the embed code and link to the toot, but I decided instead to make as many things static as possible. Deciding instead to pull the rss feed from my account and filter it by the page url. 

```
{% raw %}
const axios = require('axios');
const Parser = require('rss-parser');
const fs = require('fs');

const rssFeedUrl = 'https://social.lol/@gr36.rss';
const jsonFilePath = './_cache/mastodon.json';

// Function to read the previously saved entries from the JSON file
const readSavedEntries = () => {
  try {
    const jsonData = fs.readFileSync(jsonFilePath, 'utf8');
    return JSON.parse(jsonData).map(entry => entry.link);
  } catch (error) {
    // If the file doesn't exist or is empty, return an empty array
    return [];
  }
};

axios.get(rssFeedUrl)
  .then(response => {
    const parser = new Parser();
    return parser.parseString(response.data);
  })
  .then(feed => {
    const savedEntryUrls = readSavedEntries();
    const newEntries = feed.items.filter(item => !savedEntryUrls.includes(item.link));

    if (newEntries.length === 0) {
      console.log('No new entries found.');
      return;
    }

    const items = newEntries.map(item => ({
      link: item.link,
      pubDate: item.pubDate,
      content: item.content
    }));

    const jsonData = JSON.stringify([...items, ...readSavedEntries()], null, 2);

    fs.writeFile(jsonFilePath, jsonData, err => {
      if (err) {
        console.error('Error writing JSON file:', err);
        return;
      }
      console.log(`${newEntries.length} new entries saved to ${jsonFilePath}`);
    });
  })
  .catch(error => {
    console.error('Error fetching or parsing RSS feed:', error);
  });
{% endraw %}
```

  This is then parsed into json (I just think it looks better) and stored in a cache file.

  I can then query this for specific page urls using

```
{% raw %}
eleventyConfig.addFilter('searchContentForUrl', (mastodonData, currentPageUrl) => {
  // Load the JSON data
  const jsonData = JSON.parse(fs.readFileSync('./_cache/mastodon.json', 'utf8'));
  
  // Iterate over entries and search for the current URL in content property
  for (const entry of jsonData) {
    if (entry.content.includes(currentPageUrl)) {
      return entry;
    }
  }
  
  return null; // Return null if URL is not found in any content property
});
{% endraw %}
```

  And display thing on the post page using `{% raw %}{% set mastoContent = mastodon | searchContentForUrl(urlnohtml) %}{% endraw %}`

  I then show this with:

```
{% raw %}
<a href="{{ mastoContent.link}}"><i class="fa-brands fa-mastodon"></i> Join the conversation on Mastodon
<div>{{ mastoContent.content | safe }}</div></a>
{% endraw %}
```

## Future Plans

Like I said right at the start, I am a complete noob with front end and I am currently studying to improve things. I’d like to pull all the information once using the mastodon API, so I have access to replies_count, reblogs_count and favourites_count but that can wait for now.

This only shows on a few posts due to a change in URL but I am planning to pull in old data and show this too. All in all, I’m fairly happy with it for now considering it was cobbled together fairly quickly when I changed my mind on what I wanted to display. Any helpful recommendation will be happily received.
