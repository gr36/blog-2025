---
layout: post
title: "How To Exclude A Category From Main WordPress RSS Feed, But Not All Feeds"
microblog: false
guid: http://greg-morris.micro.blog/2019/05/20/how-to-exclude.html
post_id: 3987795
date: 2019-05-20T18:00:53-0000
lastmod: 2024-12-03T08:48:42-0000
type: post
categories:
- "Essay"
- "Guide"
url: /2019/05/20/how-to-exclude.html
---
<p><!--kg-card-begin: html--></p>
<p><!--kg-card-begin: html--></p>
<p>In my journey back to WordPress, there are lots of little modifications I need to make the website my own. One of which is the addition of micro and link posts.</p>
<p>I do not like all posts showing in the main RSS feed nor on the main index page of my blog. Many options and guides tell you to install plugins or add in code to your functions to exclude categories to all feeds. If you can avoid a plugin, then I would advise it, to prevent any unnecessary loading of your blog.</p>
<p>I did stumble on a solution to my requirements on <a href="https://stackoverflow.com/questions/12918765/exclude-category-from-main-rss-feed-but-not-all-feeds">Stack Overflow</a> (where else), and this is detailed below.</p>
<pre>add_action(‘pre_get_posts’, ‘exclude_category’ ); function exclude_category( &amp;$wp_query ) // Exclude from loop, archive and feed but not from category page/feed { if( is_home() || ( is_feed() &amp;&amp; !is_category() ) || ( is_archive() &amp;&amp; !is_category() )) { // Exclude from home, feed, but not from category page/feed set_query_var(‘category__not_in’, array(120)); // Exclude category with ID 120 } }</pre>
<pre>Add this to your themes functions.php file and remember to change the (‘category__not_in’, array(120)</pre>
<p>to your desired category ID , if you need help finding that, check out <a href="https://www.wpwhitesecurity.com/find-wordpress-category-id/">this guide</a>.</p>
<p><!--kg-card-end: html--></p>
