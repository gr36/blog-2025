---
layout: post
title: "How I Use OMG.lol Statuses"
microblog: false
guid: http://greg-morris.micro.blog/2022/10/17/how-i-use.html
post_id: 3987453
date: 2022-10-17T09:59:06-0000
lastmod: 2024-12-03T08:48:01-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/e6a68339d4.jpg
- https://greg-morris.micro.blog/uploads/2024/298c6757ab.jpg
- https://greg-morris.micro.blog/uploads/2024/7bbfda8759.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/e6a68339d4.jpg
- https://greg-morris.micro.blog/uploads/2024/298c6757ab.jpg
- https://greg-morris.micro.blog/uploads/2024/7bbfda8759.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/e6a68339d4.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/298c6757ab.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/7bbfda8759.jpg
  width: 0
  height: 0
url: /2022/10/17/how-i-use.html
---
<p>The fun little service <a href="https://home.omg.lol">omg.lol</a> is the new hotness on micro.blog and seems to be seeping out into the wider internet. Not only is it ridiculously cheap for what you get, the developer Adam seems to be making constant updates and offering more and more value for money. For just £5 per year you get access to a landing page for your social media, mastodon instance, email forwarding and my favourite service — statuslog.</p>
<p>Statuslog allows you to post small updates containing whatever you wish, along with an emoji. Exactly the type of thing that allows you to share what you are up to without having to interact with a service. As with everything omg.lol creates, it’s brilliantly designed and easy to customise for your use.</p>
<h2 id="statusonmyblog">Status On My Blog</h2>
<p>I have embraced the set-up of micro.blog. It promotes using your blog for shorter posts as well as longer ones to keep hold of your content. There are just some posts that I don’t care about, and are what Twitter was really made for. Short, to the point life updates, that have no value — think “drinking coffee” and not tweet storms of information.</p>
<figure><img src="uploads/2024/e6a68339d4.jpg" alt="" /></figure>
<p>I put the status card right at the top of my blog home page, so should anyone land on it, they can see what I am currently up to. The level of usefulness is debatable, but I like it! For a full walk through of getting this set up see the help page <a href="https://home.omg.lol/info/statuslog">here</a>, but in short I put in the following code.</p>
<pre><code>&lt;script src="https://status.lol/[your-address].js?time&amp;link&amp;fluent&amp;pretty"&gt;&lt;/script&gt;
</code></pre>
<h3 id="styling">Styling</h3>
<p>Thankfully, the styling of the status card looks great out the box, so it’s rare you will have to do anything. I wanted it to look more like part of my blog, so I styled a few elements. This took me a bit of trial and error to get this correct. When I first implemented by own changes, I used the <code>&amp;pretty</code> on the end of the script and simply styled the areas I wanted. However, this now uses some <code>!important</code> styling and as such breaks any custom styling you want to override.</p>
<p>To style the status card, you will need to remove <code>&amp;pretty</code> from the script above and style <em>everything</em> in CSS. The default CSS used at the time of writing is below, however this could change at any time.</p>
<pre><code>.statuslol_container {

},

.statuslol {
display: flex; 
flex-wrap: wrap; 
gap: 1em; 
background: #e7ebf3; 
color: #111; 
border-radius: .5em; 
padding: 1em;
}

.statuslol_emoji_container {
    flex: 0 0 1em; 
    font-size: 3em;
    padding-right: 0;
}

.statuslol_content {
    flex-grow: 1; 
  flex-shrink: 1; 
  flex-basis: 0; 
  margin: -.5em 0 0 0; 
  text-align: left; 
  overflow-wrap: break-word; 
  overflow-wrap: anywhere; 
  color: #111 !important;
}

.statuslol_time {
    opacity: .5; color: #111 !important;
}
</code></pre>
<p>You can then go for your life, change anything and everything you want to, and make it look to your taste. I love the stock gradient of the card, but implemented my own darker version I found on <a href="https://uigradients.com/#Quepal">UI Gradients</a>.</p>
<h2 id="postingstatuses">Posting Statuses</h2>
<p>For a long time, I have wanted to be able to post tweets without actually opening the app. This used to be straightforward with Shortcuts (née Workflow) but the best you can do now is transfer text into the app to tweet from it. This is where the excellent statuslog service comes in. I use it to post a short update, which is posted to micro.blog, Twitter and Mastodon.</p>
<p>If you are a Drafts user, you can use a <a href="https://actions.getdrafts.com/a/2DT">really nice action</a> to update your status easily. However, I am not, so after some inspiration from micro.blog user and omg.lol unofficial ambassador <a href="https://micro.blog/maique/13513088">Maique </a> I created a Shortcut to do this. You can grab the shortcut from <a href="https://www.icloud.com/shortcuts/2be68317c569484781cea2ca32c8b03c">here</a>.</p>
<figure><img src="uploads/2024/298c6757ab.jpg" alt="" /></figure>
<p>To use this Shortcut, you will need an API key for your OMG.LOL account, that can be found <a href="https://home.omg.lol/account#api-key">here</a>, and also put your account username in the other box as outlined on importing the Shortcut. As you can see, I have added this to my Home Screen for easy access and made an icon, which is below.</p>
<figure><img src="uploads/2024/7bbfda8759.jpg" alt="" /></figure>
<p>Icon available <a href="https://greg-morris.micro.blog/uploads/2024/7bbfda8759.jpg">here</a></p>
<p>If you then wish to then import the status into micro.blog the RSS feed you will need is <code>http://[your-address].status.lol/feed</code> replace your address with yours. If you do not use micro.blog there are automation services such as <a href="https://ifttt.com">IFTTT</a> that can Tweet whenever an RSS feed is updated.</p>
