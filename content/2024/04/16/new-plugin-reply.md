---
layout: post
title: "New Plugin: Reply Count"
microblog: false
guid: http://greg-morris.micro.blog/2024/04/16/new-plugin-reply.html
post_id: 3991573
date: 2024-04-16T06:30:10-0000
lastmod: 2024-06-22T16:19:14-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/replies.png
- https://greg-morris.micro.blog/uploads/2024/settings.png
photos:
photos_with_metadata:
url: /2024/04/16/new-plugin-reply.html
---
This plugin allows you to display how many replies your micro.blog posts have - it's a vanity metric, nothing more.

![](https://greg-morris.micro.blog/uploads/2024/replies.png)

## SetUp
You can install the plugin from [the plugins page](https://micro.blog/account/plugins/161059/find), or feel free to get it from Github by clicking design, edit theme, and then add new plugin.

Call the plugin anything you wish, copy in the URL from [the Github page](https://github.com/gr36/reply-count), and click Add Plugin.

### Add Partial
Add the partial to the place you wish this to show, for example this may go in the meta information for the post. This can be used in a single post, or in a loop of posts. Each reply count is place in a unique div element so feel free to experiment. 

Simply add ```{ partial "replycount.html" . }}``` to your page and the number of replies to that specific post will appear.

### Styling
You can style the block however you like using the class `replies`. The count number itself sits inside an inline-block class `reply_count`.

## Config
To aid styling you can add in your own emoji to appear before the number, as well as your own text to appear afterwards. If thats not your thing then either options can be toggled on/off in the plugin settings.

![](https://greg-morris.micro.blog/uploads/2024/settings.png)

## Credits
Thanks to [Manton](https://www.manton.org) for creating micro.blog and for making the API so well rounded and easy to interact with.


