---
layout: post
title: "Statuslog Micro.blog Plugin"
microblog: false
guid: http://greg-morris.micro.blog/2024/04/17/statuslog-microblog-plugin.html
post_id: 3997787
date: 2024-04-17T06:46:49-0000
lastmod: 2024-06-22T16:19:14-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/nowpage.png
- https://greg-morris.micro.blog/uploads/2024/config.png
photos:
photos_with_metadata:
url: /2024/04/17/statuslog-microblog-plugin.html
---
Display your omg.lol Statuslog on a micro.blog page.

![](https://greg-morris.micro.blog/uploads/2024/nowpage.png)

## Set Up
Install the plugin from the [official plugin page](https://micro.blog/account/plugins/view/124), or from Github by clicking design, edit theme, and then add new plugin. This will be available as an official plugin, but the submit page is currently broken.

Call the plugin anything you wish, copy in the [URL from the Github page](https://github.com/gr36/status-log), and click Add Plugin.

### Add Shortcode
Add the shortcode to the page you wish this to show on, for example, I have placed this on my home page but you could do this wherever you like.

Simply add the statuslog shortcode to your page wherever you want the updates to appear. I cannot put the shortcode here, even in a code block because micro.blog renders this! For a copy and past option, head to [Github](https://github.com/gr36/status-log). 

### Configuration
You *must* change the account name in the plugin configuration to your own, otherwise Adams statues, as great as they are, will appear on your page! Whilst you are there you can choose how many statuses you want to appear on the page.

![](https://greg-morris.micro.blog/uploads/2024/config.png)

## Styling
There is absolutely no styling applied to the div elements placed on the page. This is to give you the most choice possible for how it looks. In my example screenshot above I have some very simple flexbox styling as shown below.

	#omg_statuslog {
	    display: flex;
	    flex-direction: column;
	    gap: 20px;
	    font-size: 80%;
	}
	
	#omg_statuslog > div:nth-child(1) {
	    background: blue;
	    border-radius: 11px;
	    color: white; 
	}
	
	#omg_statuslog > div {
	        display: flex;
	        justify-content: space-between;
	        padding: 10px;
	        flex-direction: row;
	        flex-wrap: nowrap;
	        gap: 20px
	}
	
	#omg_statuslog .status_emoji {
	    font-size: 50px;
	}
	
	#omg_statuslog .status_content {
	    flex: 80%;
	}

## Considerations
This plugin uses on page javascript so there are a few things to bear in mind.

- it takes a few seconds to fetch the data from the API and display this on the page
- if a browser is setup to blog javascript then nothing will appear on the page.

## Credits
Thanks to Adam for creating such a great service in omg.lol. The statuslog is just a small part of the service, check it out [here](https://home.omg.lol).

