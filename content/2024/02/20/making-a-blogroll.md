---
layout: post
title: "Making a Blogroll"
microblog: false
guid: http://greg-morris.micro.blog/2024/02/20/making-a-blogroll.html
post_id: 3987751
date: 2024-02-20T11:15:00-0000
lastmod: 2024-04-12T09:49:51-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/5028cac5d7.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/5028cac5d7.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/5028cac5d7.jpg
  width: 0
  height: 0
url: /2024/02/20/making-a-blogroll.html
---
One of the great things about making your own website is that you can build new things. One of the worst things about making your own website is that you keep building new things. After web mentions and a way to publish easily, the next thing on my list was a blogroll. Not just a page people can go to, but a way to surface the things I like to everyone who happens to visit my website.

Thankfully, this was easy, and I took inspiration from Chris Hannah's [blogroll on GitHub](https://github.com/chrishannah/blogroll.js). Starting with creating two JSON files with information on the blogs I enjoy reading, and the products I like and would recommend to people.

![My blogroll design, it's just two squares with a random blog I like in one, and a product I like in another](https://greg-morris.micro.blog/uploads/2024/5028cac5d7.jpg)

After creating the files, I added an Eleventy filter to generate a random number in order to pick a blog and product at random for each place this would appear. It was important to me that it cycle through as many as possible, but it was not browser-intensive, and my blog continued to serve static pages.

```js
eleventyConfig.addFilter("randomItem", (arr) => {
    arr.sort(() => {
      return 0.5 - Math.random();
    });
    return arr.slice(0, 1);
  });
    return {
      dir: {
        input: "src",
        output: "public",
      },
    };
```

Then I can show them wherever I wish using `{% raw %}{% for blog in blogroll | randomItem %}{% endraw %}`. The best place for this is a partial, and at the moment it lies at the end of each blog post. However, I have plans to improve the design and be able to place it in more spaces.

I have a few things in the JSON files at the moment, but I have a feeling this will grow quickly
