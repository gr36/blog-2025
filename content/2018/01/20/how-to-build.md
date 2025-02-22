---
layout: post
title: "How To Build A Micro Blog On Jekyll"
microblog: false
guid: http://greg-morris.micro.blog/2018/01/20/how-to-build.html
post_id: 3987862
date: 2018-01-20T16:14:00-0000
lastmod: 2024-12-03T08:48:28-0000
type: post
categories:
- "Essay"
- "Guide"
url: /2018/01/20/how-to-build.html
---
<p><!--kg-card-begin: html--></p>
<p>After exploring other options to sharing on social media and <a href="https://gr36.com/2018-01-20-using-microblog/">using Micro.blog</a> I’m stuck. There doesn’t seem to be the perfect option out there to fulfil all of my needs so for now I still to my own blog.</p>
<p>Now comes the issues with posting lots of updates and where they need to go. Ultimately there are a few things I want to achieve.</p>
<ul>
<li>Keeping content mine as much as possible</li>
<li>post to other social media platforms</li>
<li>not clog up longer blog post streams or RSS</li>
</ul>
<p>Since my blog is already built on Jekyll and hosted on Github I set to work to hit as many of these goals as possible.</p>
<h2><strong>Keep content mine</strong></h2>
<p>The main feature of my <a href="/">micro.blog usage was for Daring Fireball style link posts</a>. Short quotes from other peoples articles (linking back to them) and a few words (sub 150) from my self as a comment. I built a Workflow to do this easily on micro.blog so sharing these shouldn’t be a major issue.</p>
<h3><strong>Micro Blog Collection</strong></h3>
<p>Inside your _config.yml set up a collection with a name of your choice. Seeing as this will be aimed at micro blog I went for something easy.</p>
<pre><code>Collections:
micro:
 output: true
 permalink: /micro/:title
</code></pre>
<p>This will mean that posts in this collection will not be posted to the main index page and also not in the main RSS feed. Create a folder called _micro for all the micro posts to go into.</p>
<h3><strong>Micro Blog Index</strong></h3>
<p>In the main repo create a file called micro.html and set the YAML with a permalink as /micro/index.html. Example below:</p>
<pre><code>—
permalink: permalink: /link/index.html</code></pre>
<h2 id="title:linkposts">title: Link Posts</h2>
<p>Then it’s time to get all of your posts listed, this is pretty easy to do and will ultimately be dictated by what info you will want to see on an index page, the below is the contents of mine. This page will then be found at /micro/.</p>
<pre><code>{ % for item in site.micro reversed % }</code></pre>
<article class="post-preview">  { % if item.link % }
 <a>
  </a>
<h2> </h2>
<a>
  </a>   { % else %}   
<h2> </h2>
{ % endif % }   
<p> </p>
</article>
<pre><code>
{ % endfor % }
</code></pre>
<p>I have chosen to only show the title and then all of the content as these will only be small posts. The If item.link is unique to my use case and means that if I set a link in my YMAL front matter the title will link to this URL in a similar vein to Daring Fireball.</p>
<p>The</p>
<article>tag is set in my CSS and simply adds in the same formatting as my blog and separates the posts neatly.
<p>If in doubt copy the content from your index.html and add in <code>{ % for item in site.micro reversed % }</code>.</p>
<h3><strong>Micro Blog RSS Feed</strong></h3>
<p>This might come as a shock but if you’ve got a regular blog people won’t want to read a barrage of micro updates. So a collection and separate RSS feed is a must. This is the easiest part of the set up. Simply create a file called micro.xml and add the following:</p>
<pre><code>—</code></pre>
</article>
<p>  Hello Friends https://gr36.com</p>
<pre><code>{ % for post in site.micro reversed % }

    &lt;title&gt;&lt;/title&gt;




    https://gr36.com
    https://gr36.com

{ % endfor % }
</code></pre>
<p>  </p>
<p>All of your posts in the Micro collection will now be delivered through this separate RSS feed. So you can set this to post to social media through IFTTT or many other places as you desire however there are limitations.</p>
<h2><strong>Cross Posting</strong></h2>
<p>This is where I fall down. I haven’t found a way to share full posts that are below 280 characters straight to twitter and longer ones as links. I am pretty sure this is achievable however I stopped short when realising almost every one of my posts was way past this limit.</p>
<p>I believe there may be a way to do this with a limited RSS of 280 characters. However in practice this hasn’t worked for me to auto post through IFTTT. If this is a major issue for you then micro.blog is the place for you!</p>
<p>Hopefully this helps with improving your Jekyll site and can be modified to your use cases for collections. I am currently adapting this to add in a few collections so the possibilities are endless.</p>
<p><!--kg-card-end: html--></p>
