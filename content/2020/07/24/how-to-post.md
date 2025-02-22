---
layout: post
title: "How To Post Films Watched To Micropub"
microblog: false
guid: http://greg-morris.micro.blog/2020/07/24/how-to-post.html
post_id: 3987741
date: 2020-07-24T10:48:00-0000
lastmod: 2024-12-03T08:49:04-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/23cd288f5c.jpg
- https://greg-morris.micro.blog/uploads/2024/249f233fa1.jpg
- https://greg-morris.micro.blog/uploads/2024/7a61b825bb.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/23cd288f5c.jpg
- https://greg-morris.micro.blog/uploads/2024/249f233fa1.jpg
- https://greg-morris.micro.blog/uploads/2024/7a61b825bb.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/23cd288f5c.jpg
  width: 599
  height: 551
- url: https://greg-morris.micro.blog/uploads/2024/249f233fa1.jpg
  width: 1000
  height: 962
- url: https://greg-morris.micro.blog/uploads/2024/7a61b825bb.jpg
  width: 1000
  height: 919
url: /2020/07/24/how-to-post.html
---
<p><!--kg-card-begin: html--></p>
<p>I am currently experimenting with moving all of my social things to micro.blog. I know I have tried <a href="https://gr36.com/youre-not-cool-enough-for-micro-blog/">this before</a> (twice) but this time I don’t want it to be my blog I just want a place to hang out and post everything to. This will mainly be an Instagram replacement, posting checkins as most importantly books and films I have watched.</p>
<p>I can’t quite work out Goodreads yet, but by using <a href="https://letterboxd.com/">Letterboxed</a> I can post watched film easily using <a href="https://help.micro.blog/2017/api-posting/">Micropub</a>. You can of course use this with micro.blog but also with any service that support Micropub, so also applies to WordPress and other more mainstream services.</p>
<h2>Choose your way</h2>
<p>There are two relatively easy ways to do this, one free and one paid, both with pros and cons. They both rely on singing up to Letterboxed, and using your profile RSS feed to post updates. So, whichever you choose, you will need to sign up and then copy your feed address from your profile page. Once logged in, on the menu bar furthest to the right you will notice an RSS icon. Right click and copy this first.</p>
<h2>IFTTT</h2>
<p>This method is completely free so is a win straight off the bat, but as a caveat is a little more complex to set up and I found a little limited to work with. This is personal preference, of course, but IFTTT is still very straight forward to set up.</p>
<p>Click on Create and chose RSS as your IF (the trigger), choose new item in feed and paste in your RSS feed from Letterboxed. The Then (action) part is a Webhook to allow you to post to micropub services. For this example, I am going to run through a micro.blog, but they will all be pretty much the same.</p>
<p><img style="margin-left: auto; margin-right: auto;" title="Screenshot-2020-07-24-at-09.27.01-1.png" src="https://greg-morris.micro.blog/uploads/2024/23cd288f5c.jpg" alt="Screenshot 2020 07 24 at 09 27 01 1" width="599" height="551" border="0" />Make a web request, and then put in the URL of your service, in this case it is <code>https://micro.blog/micropub</code>. Method is POST and content type is usually application/x-form-url-encoded. In the body you need two bits of information, an access code and what you want the post to display. This will be dependent on your device but in my micro.blog case I use the following.</p>
<p><code>access_token=ABCDEF&amp;content={{EntryContent}}&amp;name={{ItemTitle}}</code></p>
<p>With the access token generated in my setting of my micro.blog.</p>
<p>You can customise the body content to whatever you want to display in the post. If you leave this as is, then it will display the raw content of the RSS feed.</p>
<h2>Zapier</h2>
<p>This is a much more rounded service that makes it much easier to customise the post content, but at a cost of £20 per month. For this cost, you get the ability to automate many more things, so it <em>might</em> be worth considering but please bear this in mind.</p>
<p><img style="margin-left: auto; margin-right: auto;" title="Screenshot-2020-07-24-at-09.11.31-1.png" src="https://greg-morris.micro.blog/uploads/2024/249f233fa1.jpg" alt="Screenshot 2020 07 24 at 09 11 31 1" width="1000" height="962" border="0" />Start by creating a new Zap, the trigger is RSS and the event is a new item in the feed, Past in the Letterboxed RSS feed you have saved and that is all you need to do on this step as you don’t need any information to access this feed. On the next step Zapier will find the data — so make sure you’ve at least recorded one watched film, and then pull everything into Zapier.</p>
<p>The action is Webhooks, and the action event needs to be POST to tell micropub to post information. By customising the request you can go as deep as you like, this is where Zapier makes it so easy to post images, ratings and everything the feed contains effortlessly and understandably. To do this put the Micropub url into the first box, in my case this is <code>https://micro.blog/micropub</code> and leave the Payload type and Form.</p>
<p>Click the plus sign under Data, and type <code>content</code> into the first box, and then you can customise the post until your heart is content. Click the plus button again and type <code>access_token</code> into the first box and in the second one copy in an access code from micro.blog. Your service may not require this, but will usually require some kind of authentication.</p>
<p><img style="margin-left: auto; margin-right: auto;" title="Screenshot-2020-07-24-at-09.12.01-1.png" src="https://greg-morris.micro.blog/uploads/2024/7a61b825bb.jpg" alt="Screenshot 2020 07 24 at 09 12 01 1" width="1000" height="919" border="0" />All the other topics can remain as they are by default, by clicking continue you are given the option to test the post. Do this and check that everything appears correctly — you can always go back and change things before re-testing. This is another option that makes Zapier a great service to work with. Once you’re happy, finish everything off and now every time you review a film it will post to Micropub.</p>
<p><!--kg-card-end: html--></p>
