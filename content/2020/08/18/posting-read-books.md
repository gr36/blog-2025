---
layout: post
title: "Posting Read Books On Goodreads To Micropub"
microblog: false
guid: http://greg-morris.micro.blog/2020/08/18/posting-read-books.html
post_id: 3987609
date: 2020-08-18T13:23:00-0000
lastmod: 2020-08-18T13:23:00-0000
type: post
categories:
- "Essay"
url: /2020/08/18/posting-read-books.html
---
<!--kg-card-begin: html--><p>After spending some time setting up <a href="https://gr36.com/post-films-watched-micropub/">posting films to micropub</a>, I really wanted to get my reading sorted. There are great options out there like <a href="https://indiebookclub.biz/">indiebookclub</a> – but I wanted to automate it and make it possible every time I finish a book on my kindle.</p>
<p>With nothing fitting the bill I delved into the API (which is pretty good by the way) and came up with a solution. It relies on a developer key from Goodreads so I don’t promise how long this will work, they could pull this or remove your access to it at any point.</p>
<h2>Developer Key</h2>
<p>Goodreads will let anyone <a href="https://www.goodreads.com/api/keys">set up a developer key</a> for access to their API, all you need to add are a few details about yourself and agree to the developer terms. If you break these terms, they are well within their right to stop you using the service – so please read them.</p>
<p>Once agreed, you will need the top part labeled ‘key’ – keep this safe and don’t share it with anyone as it gives access to all of your information and you can read/write to your Goodreads account with it. A full list of API abilities are available <a href="https://www.goodreads.com/api">here</a>.</p>
<p>From here I researched what is available through the API and discovered you can pull books you have read from the following feed.</p>
<pre><code class="language-html">https://www.goodreads.com/review/list/[ID].xml?key=[key]&amp;shelf=read
</code></pre>
<p>I have focused on updating micro.pub whenever I finish a book, but you can find extra information about books in your shelf by chaining after the <code>&amp;</code> to be <code>currently-reading</code> or <code>to-read</code>.</p>
<h2>IFTTT</h2>
<p>Once you have this information it is pretty easy to set up a posting trigger in your service of choice. IFTTT is completely free so is a win straight off the bat, but as a caveat is a little more complex to set up and I found a little limited to work with. This is personal preference, of course, but IFTTT is still very straight forward to set up.</p>
<p>Click on Create and chose RSS as your IF (the trigger), choose new item in feed and paste in your RSS feed. The Then (action) part is a Webhook to allow you to post to micropub services. For this example, I am going to run through micro.blog, but they all will all be pretty much the same.</p>
<p>Make a web request, and then put in the URL of your service, in this case it is <code>https://micro.blog/micropub</code>. Method is POST and content type is usually application/x-form-url-encoded. In the body you need two bits of information, an access code and what you want the post to display. This will be dependent on your service but in my micro.blog case I use the following.</p>
<p><code>access_token=ABCDEF&amp;content={{EntryContent}}&amp;name={{ItemTitle}}</code></p>
<p>With the access token generated in the setting of my micro.blog.</p>
<p>You can customise the body content to whatever you want to display in the post. If you leave this as is, then it will display the raw content of the RSS feed.</p>
<h2>Zapier</h2>
<p>This is a much more rounded service that makes it much easier to customise the post content, but at a cost of £20 per month. For this cost, you get the ability to automate many more things, so it might be worth considering but please bear this in mind.</p>
<p>Start by creating a new Zap, the trigger is RSS and the event is a new item in the feed. Paste in the RSS feed you have saved and that is all you need to do on this step as you don’t need any information to access this feed. On the next step Zapier will find the data — so make sure you’ve at least read one book, and then pull everything into Zapier.</p>
<p>The action is Webhooks, and the action event needs to be POST to tell micropub to post information. By customising the request you can go as deep as you like, this is where Zapier makes it so easy to post images, ratings and everything the feed contains effortlessly and understandably. To do this put the Micropub url into the first box, in my case this is <code>https://micro.blog/micropub</code> and leave the Payload type as Form.</p>
<p>Click the plus sign under Data, and type <code>content</code> into the first box, and then you can customise the post until your heart is content. Click the plus button again and type <code>access_token</code> into the first box and in the second one copy in an access code from micro.blog. Your service may not require this, but will usually require some kind of authentication.</p>
<p>All the other topics can remain as they are by default, by clicking continue you are given the option to test the post. Do this and check that everything appears correctly — you can always go back and change things before re-testing. This is another option that makes Zapier a great service to work with. Once you’re happy, finish everything off and now every time you finish a book it will post to Micropub.</p>
<!--kg-card-end: html-->
