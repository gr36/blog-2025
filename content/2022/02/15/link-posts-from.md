---
layout: post
title: "Link Posts From Obsidian"
microblog: false
guid: http://greg-morris.micro.blog/2022/02/15/link-posts-from.html
post_id: 3987545
date: 2022-02-15T13:38:30-0000
lastmod: 2024-04-12T09:43:01-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/86dfde2825.jpg
- https://greg-morris.micro.blog/uploads/2024/3c1d689e3c.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/86dfde2825.jpg
- https://greg-morris.micro.blog/uploads/2024/3c1d689e3c.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/86dfde2825.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/3c1d689e3c.jpg
  width: 0
  height: 0
url: /2022/02/15/link-posts-from.html
---
<p>This started off life as a link post to an interesting video on <a href="https://birchtree.me">Matt Birchlers</a> writing set up. However, it quickly spiralled out of control into me writing regular expressions, editing javascript and spending two days making this set up my own. If you’re into doing anything like this, then the best place to start is his excellent video below.</p>
<figure class="kg-card kg-embed-card">[embed]https://youtube.com/watch?v=GqTyyQBi3hA&amp;feature=oembed[/embed]</figure>
<p>I’ve been <a href="https://gregmorris.co.uk/blog/my-obsidian-set/">using Obsidian for a while</a> and created quite a robust set-up for tasks, notes, and everything else. This lasted a while but started to fall away the longer it went on because I still had to use other apps to get things done, <a href="https://gregmorris.co.uk/blog/looking-for-my/">such as Ulysses</a>. The thing I have found about being consistent is to remove as much resistance as possible. Cutting down on the chance that the idea will slip away, or the task just won’t be completed. So transferring fascinating links in Obsidian and then then into a writing app or Ghost was untenable.</p>
<p>So, thanks to Matt, and a few tweaks I have found something that really works and in the process I have even moved reading apps!</p>
<h2 id="matter">Matter</h2>
<p>Despite being in the beta testers since really early on, <a href="https://hq.getmatter.app">Matter</a> never really stuck with me. I was a hardcore <a href="https://www.getupnext.com">Upnext</a> user and nothing could tear me away. That was until the team kept updating and improving things to a point I had to go back. Matter allows me to read all the articles I want, highlight them, make notes on them and then push them straight into Obsidian (and Notion too is thats your thing).</p>
<p>By installing the <a href="https://github.com/getmatterapp/obsidian-matter">Obsidian plugin</a>, all of my notes and highlights are pulled in and displayed for later reference. I use this to refer to things, link notes together, and research some topics that come up whilst digesting my reading list. To make this my own, I had to edit the javascript to display things exactly as I wanted. My biggest desire was for the highlighted quotes to appear as markdown quotes and a title at the top. Matt walks you though how he did his, my changes are made in the same place as follows.</p>
<pre><code class="language-css"># ${feedEntry.content.title}
${this._renderMetadata(feedEntry)}</code></pre>
<h2 id="notes">Notes</h2>
<pre><code class="language-css"></code></pre>
<p>${annotations.map(this._renderAnnotation).join(“n”)}
<code>.trim();
  }
  _renderMetadata(feedEntry) {
    if (feedEntry.content.publication_date) {
      const publicationDate = new Date(feedEntry.content.publication_date);
      const publicationDateStr = publicationDate.toISOString().slice(0, 10);
      metadata +=</code> Published Date: ${publicationDateStr}<code>;
    }
    if (feedEntry.content.author) {
      metadata +=</code> Author: ${feedEntry.content.author.any_name}<code>;
    }
    metadata += "n";
    return metadata;
  }
  _renderAnnotation(annotation) {
    return</code> &gt; ${annotation.text}${annotation.note ? <code>
  * **Note**: ${annotation.note}</code> : “n”} `.trim(); } };</p>
<pre><code class="language-css"></code></pre>
<h2 id="shortcuts">Shortcuts</h2>
<p>If I decide that the quote, and my thoughts are interesting enough for a link post on my blog, then the second step is to get that into Ulysses. To achieve this, I use the <a href="https://www.macstories.net/stories/obsidian-shortcut-launcher/">MacStories Shortcut Launcher Obsidian Plugin</a> and link this to my Link Post Apple Shortcut.</p>
<figure class="kg-card kg-image-card kg-width-wide"><img class="kg-image" src="https://greg-morris.micro.blog/uploads/2024/86dfde2825.jpg" alt="" /></figure>
<p>With thanks to Matt once agin for s<a href="https://twitter.com/mattbirchler/status/1493282183628402695?s=20&amp;t=ghaffL4AEjFm_JVu0DvTiw">haring his Shortcut with me</a>, he got me quite far down the road. Due to me messing around with the way I wanted the information to be displayed in Obsidian, his regular expressions didn’t work, so I had to customise this quite a bit.</p>
<figure class="kg-card kg-bookmark-card">
<div class="kg-bookmark-content">
<div class="kg-bookmark-title">Shortcuts</div>
<div class="kg-bookmark-description"> </div>
<div class="kg-bookmark-metadata"><img class="kg-bookmark-icon" src="https://greg-morris.micro.blog/uploads/2024/3c1d689e3c.jpg" alt="" /></div>
</div>
</figure>
<p>This Shortcut looks for the title, URL, and Author. There’s also some customisation with the option to select the quote you wish to use and then the facility to add a different title to your post. It works on Mac and iOS; however text input is a bit finicky on macOS (as all Shortcuts seem to be). Regular expressions are the key here, so the shortcut is pretty messy and probably could be better, but the elements are as follows.</p>
<p><code>(?&lt;=Author:)(.?)(?=n)</code> does the same but with author.</p>
<p><code>^(#)s?(.+)n{1,2}</code> finds anything in the document that is H1, i.e. a title with a #.</p>
<p><code>&gt;(.*?)(?=n)</code> finds all markdown quotes in the document.</p>
<p>It is unusual for me to show more than one quote in a post as I try and pick something that sums up the whole point. Or sometimes pick up smaller sections that hit me personally but don’t necessarily reflect the whole post. If you wish to pull out all quotes then deleting the ‘select from list’ section will transfer all into Ulysses.</p>
<p>All of this is rearranged into my set-up I publish link posts in and then opened in a new Ulysses sheet. I promise not to spam everyone with loads of link posts. In fact I don’t post many of them, but this set up has already meant that I have referred back to what I have been reading a lot more. Obviously, your millage may vary.</p>
