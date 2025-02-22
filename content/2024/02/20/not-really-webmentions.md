---
layout: post
title: "Not Really Webmentions Part 2"
microblog: false
guid: http://greg-morris.micro.blog/2024/02/20/not-really-webmentions.html
post_id: 3988376
date: 2024-02-20T08:22:00-0000
lastmod: 2024-02-20T08:22:00-0000
type: post
categories:
- "Essay"
url: /2024/02/20/not-really-webmentions.html
---
In keeping with my ways, as soon as I published my rather long-winded [method of pulling in pseudo webmentions](/2024/02/18/my-blog-webmention-counts), I knew I wasn’t satisfied. Functioning is one thing, but seeing all the code on a page and having trouble following it myself gave me a headache. I began working on updates I had planned for a few weeks later.

I am now just using the Mastodon API to pull in all the information I want to display.

```
async function fetchAndUpdateUserPosts(instanceURL, accessToken, username) {
  try {
    const fetchedPosts = await fetchUserPosts(instanceURL, accessToken, username);
    const filePath = `./_cache/mastodon_posts.json`;

    // Check if the file exists
    if (fs.existsSync(filePath)) {
      // Read existing posts from file
      const existingPosts = JSON.parse(fs.readFileSync(filePath, 'utf-8'));

      // Update or add new posts
      fetchedPosts.forEach(newPost => {
        const index = existingPosts.findIndex(oldPost => oldPost.id === newPost.id);
        if (index !== -1) {
          // Update existing post
          existingPosts[index] = newPost;
        } else {
          // Add new post
          existingPosts.push(newPost);
        }
      });

      // Write updated posts back to the file
      fs.writeFileSync(filePath, JSON.stringify(existingPosts, null, 2));
      console.log(`Posts for user ${username} fetched and updated successfully.`);
    } else {
      // Write fetched posts to a new file
      fs.writeFileSync(filePath, JSON.stringify(fetchedPosts, null, 2));
      console.log(`Posts for user ${username} fetched and saved successfully.`);
    }
  } catch (error) {
    console.error('Error:', error);
  }
}
```

Full gist [here](https://gist.github.com/gr36/bbddf18a17ce903e8b2dc321d96e1801).

For this, you will need an access token for the API, which is available in your settings - more info here. You will also need a username, which isn’t your actual username but more of an ID. More information on how to get this is available here.

The full script checks for changes to the cached file and only updates changes, which is handy for adding new comments, likes, or when you edit your post.

## Displaying Information

This method makes displaying the information much easier, as the old way was a complete mess. It illustrates the learning process here!

Now I just need `{% raw %}{% set mastoContent = mastodon | searchContentForUrl(page.url | url | absoluteUrl(metadata.url)) %}{% endraw %}` so in my post I can then display the toot content, likes, boosts and a comment count. For instance my toot data is:
```
{% raw %}
<div><i class="fa-regular fa-star"></i> {{ mastoContent.favourites_count}}</div>
<div><i class="fa-regular fa-comment"></i> {{ mastoContent.replies_count}}</div>
<div><i class="fa-solid fa-rocket"></i> {{ mastoContent.reblogs_count}}</div>
{% endraw %}
```

## Future Plans
This new approach, although much cleaner, disregards webmentions from any source other than Mastodon. I am still pulling these in but displaying them on a private dashboard in my CMS. My plans are to filter out Mastodon-related ones and display these on the post page as well. This will take me a while to figure out the best way to show them, and at this point, I will pull in all old data from my old blog.
