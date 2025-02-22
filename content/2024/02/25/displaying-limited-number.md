---
layout: post
title: "Displaying Limited Number Of Posts In 11ty"
microblog: false
guid: http://greg-morris.micro.blog/2024/02/25/displaying-limited-number.html
post_id: 3987755
date: 2024-02-25T08:38:00-0000
lastmod: 2024-04-12T09:49:54-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/fe58829c7a.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/fe58829c7a.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/fe58829c7a.jpg
  width: 0
  height: 0
url: /2024/02/25/displaying-limited-number.html
---
Another day, another tweak I'm making to my blog. Today's task, alongside [sorting out the navigation](https://social.lol/@gr36/111988050307279780)  to display better, was adding some content to my [Posts page](/tags/posts/). On my old blog, this page listed all the tags I have and a few examples of the posts found in them, so I set about doing exactly that.

![Screenshot of my blog displaying the first 5 posts in my reviews collection](https://greg-morris.micro.blog/uploads/2024/fe58829c7a.jpg)

## Add A Filter
After attempting to write my own code to pull out the latest five posts from a specific tag, I stumbled across [Max Böck](https://mxb.dev/) Github repo with an example of [how to display webmentions](https://github.com/maxboeck/eleventy-webmentions). This filter allowed passing a collection to it and also customizing the number of posts to display. The filter is as follows:

```
// Get the first n elements of a collection.
  eleventyConfig.addFilter('head', (array, n) => {
    if (n < 0) {
      return array.slice(n)
    }

    return array.slice(0, n)
  })
```

## Displaying On Page
This made my job much easier, and the filter could potentially be reusable in other situations. For the time being, I chose to display the three most-used tags until I can clean up my imported posts from my old blog and integrate others than using for. As an example, to show the first 5 posts in my Reviews Collection, I use `{% raw %}{% for post in collections.Review | head(-5) %}{% endraw %}`.

I use `head(-5)` in the filter to get the latest 5 posts, whereas `head(5)` would get the first 5 from the collection, i.e., the oldest posts. Once I have cleaned up my posts, I plan to display all collections here and make the code cleaner rather than repeating it three times. But as a stopgap while I do this, I am pretty happy with how it turned out.
