---
layout: post
title: "How To Open External Links In A New Tab By Default In Ghost"
microblog: false
guid: http://greg-morris.micro.blog/2020/04/27/how-to-open.html
post_id: 3987710
date: 2020-04-27T15:12:43-0000
lastmod: 2024-12-03T08:48:59-0000
type: post
categories:
- "Essay"
- "Guide"
url: /2020/04/27/how-to-open.html
---
<p><!--kg-card-begin: html--></p>
<p>Updated: Added in non-jQuery code snippet</p>
<p>This problem is a reasonably simple one if you know what you are doing with writing Javascript. Unfortunately, I am not, and this feels like an issue that shouldn’t need some script, but here we are.</p>
<p>After loads of Googling, looking at Github Gist, and trial and error, I finally found a solution to opening new links in a new tab thanks to <a href="https://www.insidersbyte.com/open-external-links-in-a-new-tab-by-default-ghost/">InsidersByte</a>.</p>
<p>As they point out you can do this with markdown or adding in <code>target=_blank</code> to the end of each Url, but who has time for that? So add this into the footer of your site.</p>
<p>With jQuery</p>
<pre><code class="language-jQuery">
var links = document.links;</code></pre>
<p>for (var i = 0, linksLength = links.length; i &lt; linksLength; i++) {
 if (links[i].hostname != window.location.hostname) {
 links[i].target = '_blank';
 }
}</p>
<p>non-jQuery</p>
<pre><code class="language-javascript">
 var links = document.querySelectorAll(‘a’);
 links.forEach((link) =&gt; {
 var a = new RegExp(‘/’ + window.location.host + ‘/’);
 if(!a.test(link.href)) {
 link.addEventListener(‘click’, (event) =&gt; {
 event.preventDefault();
 event.stopPropagation();
 window.open(link.href, ‘_blank’);
 });
 }
 });
</code></pre>
<p>You could do this in your theme template if you like, but the easiest way is to head to your dashboard, and then Settings &gt; Code Injection. Copy and paste in the code and remember to save!</p>
<p>Reload your site, and you should be sorted.</p>
<p><!--kg-card-end: html--></p>
