---
layout: post
title: "How To Edit Your Ghost Theme Using Github"
microblog: false
guid: http://greg-morris.micro.blog/2021/11/21/how-to-edit.html
post_id: 3988263
date: 2021-11-21T13:10:23-0000
lastmod: 2024-12-03T08:48:38-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/e0d0564529.jpg
- https://greg-morris.micro.blog/uploads/2024/bc80373cc6.jpg
- https://greg-morris.micro.blog/uploads/2024/87fe123509.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/e0d0564529.jpg
- https://greg-morris.micro.blog/uploads/2024/bc80373cc6.jpg
- https://greg-morris.micro.blog/uploads/2024/87fe123509.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/e0d0564529.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/bc80373cc6.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/87fe123509.jpg
  width: 2000
  height: 796
url: /2021/11/21/how-to-edit.html
---
<p>Since <a href="https://gregmorris.co.uk/blog/migrating-from-wordpress/">first trying Ghost</a>, one of the best things about editing my theme is the ability to host on Github. Through a simple integration I can easily edit my theme to make changes from almost anywhere. If you want to do this too, this guide should help you out.</p>
<h2 id="ghost-integration">Ghost Integration</h2>
<p>First set up the Github integration on your Ghost install, this provides you with an API Key that you will need when using Github. Head to the settings cog at the bottom of you control panel and click on Integrations.</p>
<figure class="kg-card kg-image-card"><img class="kg-image" src="https://greg-morris.micro.blog/uploads/2024/e0d0564529.jpg" alt="" /></figure>
<p>Create a new integration and give it a name. On the next screen make a note of the Admin API URL and the Admin API Key. Please keep these private as these allow access to your blog content.</p>
<figure class="kg-card kg-image-card"><img class="kg-image" src="https://greg-morris.micro.blog/uploads/2024/bc80373cc6.jpg" alt="" /></figure>
<h2 id="github-set-up">Github Set Up</h2>
<p>Secondly you will need to host all of your themes files on Github. Make a private repo, give it a name that represents your theme and head to settings &gt; secrets. Click ‘New repository secret’ and set up <code>GHOST_ADMIN_API_URL</code> and <code>GHOST_ADMIN_API_KEY</code> with the integration details you set up earlier.</p>
<figure class="kg-card kg-image-card"><img class="kg-image" src="https://greg-morris.micro.blog/uploads/2024/87fe123509.jpg" alt="" width="2000" height="796" /></figure>
<p>Once you have done this upload all of your theme files to the repo and commit them. The last step is to create a new file in your repo <code>.github/workflows/main.yml</code>. This file needs to contain the following.</p>
<pre><code class="language-html">name: Deploy Theme
on:
 push:
 branches:
 - master
 - main
jobs:
 deploy:
 runs-on: ubuntu–18.04
 steps:
 - uses: actions/checkout@master
 - uses: TryGhost/action-deploy-theme@v1.4.1
 with:
 api-key: ${{ secrets.GHOST_ADMIN_API_KEY }}
</code></pre>
<p>This theme will now show up in your design settings, however you will need to make a change to you theme to trigger this. Adding in some text to your readme file is the easiest way.</p>
<p>You can now make changes to your theme through whatever way is easiest for you. I use <a href="https://code.visualstudio.com">Visual Studio Code</a>, but on iPad I found the best app is <a href="https://workingcopyapp.com">Working Copy</a>. Every time you push a change GitHub will build your site and them push these to your live site, this usually takes less than a minute.</p>
