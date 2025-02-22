---
layout: post
title: "New Plugin: Search Partial"
microblog: false
guid: http://greg-morris.micro.blog/2024/04/15/new-plugin-search.html
post_id: 3990509
date: 2024-04-15T07:11:24-0000
lastmod: 2024-06-22T16:19:14-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/search-bar.png
- https://greg-morris.micro.blog/uploads/2024/search-results.png
- https://greg-morris.micro.blog/uploads/2024/search-options.png
photos:
photos_with_metadata:
url: /2024/04/15/new-plugin-search.html
---
In my work to recreate my 11ty blog on micro.blog I wanted a better search experience for readers, and also myself when searching for posts to link to. Manton did a great job with his [search page plugin](https://github.com/microdotblog/plugin-search-page), so I adapted this to be able to appear on any page.

![](https://greg-morris.micro.blog/uploads/2024/search-bar.png)

This plugin for micro.blog will allow you to add a search bar to any page you wish.

## Set Up
This plugin is available from the [micro.blog plugin page](https://micro.blog/account/plugins/view/122), or feel free to install it from Github by clicking design, edit theme, and then add new plugin.

Call the plugin anything you wish, copy in the URL from the [Github page](https://github.com/gr36/search-partial), and click Add Plugin.

### Add Partial
Add the partial to the page you wish this to show on, for example, I have placed this on my home page but you could do this wherever you like.

Simply add ```{{ partial “search.html” . }}``` to your page and the search bar will show as 100% width of the element it is placed in.

When searching, an HTML element will appear and show the results, linking to pages that contain the searched for words.

![](https://greg-morris.micro.blog/uploads/2024/search-results.png)

### Customise Search
You can customise the number of results shown on your page by heading into plugin options and changing the default from 5. 

![](https://greg-morris.micro.blog/uploads/2024/search-options.png)

## Styling
The styling of the search bar will be depend on your theme, I have added in some basic styling as follows.

	.field {
	        width: 100%;
	        height: 34px;
	        border: 2px solid #eee;
	        padding-left: 10px;
	        margin-top: 20px;
	        margin-bottom: 20px;
	        border-radius: 11px;
	    }
	    
	    #list_results {
	        padding: 2rem;
	        border-radius: 11px;
	        box-shadow: rgba(60, 64, 67, 0.3) 0px 1px 2px 0px, rgba(60, 64, 67, 0.15) 0px 1px 3px 1px;
	    
	    }

`.field` is the search box itself.

`#list_results` is the results box that only shows when search results are found.

## Credits
The basis of this plugin came from Manton [search page plugin](https://github.com/microdotblog/plugin-search-page). 
