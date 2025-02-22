---
layout: post
title: "Moving My Mastodon Account To Micro.blog"
microblog: false
guid: http://greg-morris.micro.blog/2022/12/02/moving-my-mastodon.html
post_id: 3987588
date: 2022-12-02T14:11:27-0000
lastmod: 2024-04-12T09:45:10-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/9cb404633a.jpg
- https://greg-morris.micro.blog/uploads/2024/024480d6ca.jpg
- https://greg-morris.micro.blog/uploads/2024/eb021f290d.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/9cb404633a.jpg
- https://greg-morris.micro.blog/uploads/2024/024480d6ca.jpg
- https://greg-morris.micro.blog/uploads/2024/eb021f290d.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/9cb404633a.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/024480d6ca.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/eb021f290d.jpg
  width: 0
  height: 0
url: /2022/12/02/moving-my-mastodon.html
---
Well, first things first. I am not really moving my Mastodon account to micro.blog in the technical sense but rather forwarding everything, but if you’re reading this you want to do the same. Thankfully, the process is pretty easy, and you won’t need much knowledge to do it.

The reason I wanted to do this, is that I can follow Mastodon accounts (or any other ActivityPub service) from inside micro.blog and didn’t see the point using two apps to do the same things. I went [backwards and forwards](/2022/11/30/shortcut-find-mastodon.html) on which way I was going to do this, and [decided that a quieter timeline](/2022/12/01/snacking-on-the.html) on micro.blog was the way I wanted to go. My only concern was leaving my other Mastodon account on [social.lol](https://social.lol/) empty and losing the people that I follow. 

I first created an [iOS Shortcut](/2022/11/30/shortcut-find-mastodon.html) to find the accounts that I wanted to follow on micro.blog. For more information about following ActivityPub accounts on micro.blog check out the help docs [here](https://help.micro.blog/t/activitypub/95). I gave this a day or so to see if this was the way I wanted to go, and then went all in.

## Micro.blog Alias
On micro.blog head to Account \> ActivityPub and click set Mastodon compatible username. The default for this is your micro.blog username, so mine would be `@gr36@micro.blog` I changed this to one using my custom url and to keep things nice and simple I chose `@greg@gr36.com`. Once you have done this, your username will appear in a box at the top of the page, next to this click Aliases. 

![](https://greg-morris.micro.blog/uploads/2024/9cb404633a.jpg)

Here, you add in your ‘old’ Mastodon account that you want to transfer followers from and forward all traffic. You can add multiple aliases here if you need to.

## Mastodon Move
On your Mastodon instance, head to Settings \> Account and towards the bottom you will see Move to a different account. Here you need to add in your new micro.blog Mastodon compatible username, and then put in your password. 

![](https://greg-morris.micro.blog/uploads/2024/024480d6ca.jpg)

I would like to point out that you can only migrate once every 30 days, and that the process may take a while to complete. All of your followers will be moved across to the micro.blog account and if anyone replies to your ‘old’ account this will also show up in micro.blog. 

![](https://greg-morris.micro.blog/uploads/2024/eb021f290d.jpg)

Although you *can* unlink these if you want to open your account back up again, I have not tested this. I have no idea if your followers or content come back again, so consider this destructive, unless you find out otherwise and please let me know.
