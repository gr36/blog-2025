---
layout: post
title: "How To Start Hacking Roam Research"
microblog: false
guid: http://greg-morris.micro.blog/2020/08/21/how-to-start.html
post_id: 3987620
date: 2020-08-21T11:16:00-0000
lastmod: 2024-12-03T08:49:33-0000
type: post
categories:
- "Essay"
- "Guide"
url: /2020/08/21/how-to-start.html
---
<p><!--kg-card-begin: html--></p>
<p>As with everything I get invested in I like to go in deep and see what it can really do. One of the easiest ways to start to mould <a href="https://gr36.com/tag/roam-research/">Roam Research</a> to your will and make it unique for your use case is to add in CSS or JS. These are two official supported ways that are easy to implement and can also be removes at your will.</p>
<h2>Roam/css</h2>
<p>You can easily change the look and feel of Roam by tweaking the CSS of the pages. This can go from a little light modding, to in-depth changes on how the layout looks.</p>
<p>To start create a page called <code>roam/css</code> and simply add in a code block that specifies css. There are a huge range of options available already created and shared on the <a href="https://roamresearch.com/#/app/help/page/fJRcVITNY">help pages</a>. I am currently using ‘<a href="https://roamresearch.com/#/app/help/page/nkj1JWWS4">Better Roam Research</a>’ to add in dark mode.</p>
<p>Don’t forget to change the code block to specify css, it defaults to Clojure.</p>
<p><!--kg-card-end: html--></p>
<h2>Roam/js</h2>
<p>If you want to go further into Roam and really start building things that customise it to your usage then roam/js is the place to be. There are a huge number of <a href="https://www.reddit.com/r/RoamResearch/comments/hj08fl/any_good_roamjs_files/">scripts available</a> that do everything from add more buttons, to change the way Roam works in the browser.</p>
<p>To add in this capability create a page call <code>roam/js</code> or just a block with this as its only contents. Nested under this write the following. <code>{{[[roam/js]]}}</code>, this will give you the following warning.</p>
<p>It is worth paying attention to this, and only run scripts you are familiar with as there are security and safety issues to bear in mind with javascript. If you are completely sure, click “Yes, I know what I am doing” once you have nested the script you wish to use underneath. You can stop the js from running at any point by clicking “stop this”.<!--kg-card-end: html--></p>
<p>This particular script I am running allows me to clear out empty Daily Notes pages and can be found <a href="https://paste.ee/p/syUGk">here</a>.</p>
<p><!--kg-card-end: html--></p>
