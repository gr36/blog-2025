---
layout: post
title: "Agenda App URL Scheme"
microblog: false
guid: http://greg-morris.micro.blog/2018/10/31/agenda-app-url.html
post_id: 3987841
date: 2018-10-31T10:57:00-0000
lastmod: 2018-10-31T10:57:00-0000
type: post
categories:
- "Essay"
url: /2018/10/31/agenda-app-url.html
---
<!--kg-card-begin: html--><p><!--kg-card-begin: html--></p>
<p>The opinions on Agenda app range from excitement to confusion but it has caused quite a stir in iOS productivity circles. The developers are constantly improving the app and there are now a bunch of automation options available for Agenda via x-callback URL.</p>
<p>You can use these in Shortcuts or a whole range of automation apps and here is a breakdown of what you can do.</p>
<h2>Open</h2>
<p>On-the-agenda view<br />
<code>agenda://x-callback-url/on-the-agenda<br />
</code></p>
<p>Open the Today overview<br />
<code>agenda://x-callback-url/today<br />
</code></p>
<p>Open a project<br />
<code>agenda://x-callback-url/open-project?title=[project title]<br />
</code></p>
<p>Open a note<br />
<code>agenda://x-callback-url/open-note?title=[title text]<br />
</code></p>
<h2>Create</h2>
<p>Create a new note<br />
<code>agenda://x-callback-url/create-note?project-title=[project name]&amp;title=[title text]&amp;text=[body text]<br />
</code></p>
<p>Append to existing note<br />
<code>agenda://x-callback-url/append-to-note?title=[title text]&amp;text=[body text]<br />
</code></p>
<h2>Optional extras</h2>
<p>Add in extras to the end of the url if you need some more control. These are not mandatory.</p>
<p>On the agenda<br />
<code>&amp;on-the-agenda=[true or false]<br />
</code></p>
<p>Specific date<br />
<code>&amp;date=[year]-[month]-[day]<br />
</code></p>
<p>Start and/or end dates<br />
<code>&amp;start-date=yesterday&amp;end-date=tomorrow<br />
</code></p>
<h3>Example 1</h3>
<p><code>agenda://x-callback-url/create-note?project-title=My%20Project&amp;title=New%20Note&amp;text=Hello%20World&amp;on-the-agenda=true&amp;date=2018-03-12<br />
</code></p>
<h3>Example 2</h3>
<p><code>agenda://x-callback-url/create-note?project-title=Blogposts&amp;title=New%20Post29&amp;text=Hello%20World&amp;on-the-agenda=false&amp;start-date=yesterday&amp;end-date=tomorrow</code></p>
<p><!--kg-card-end: html--></p>
<!--kg-card-end: html-->
