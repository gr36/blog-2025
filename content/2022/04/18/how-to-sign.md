---
layout: post
title: "How To Sign Shortcuts Files"
microblog: false
guid: http://greg-morris.micro.blog/2022/04/18/how-to-sign.html
post_id: 3987537
date: 2022-04-18T14:41:58-0000
lastmod: 2024-12-03T08:49:25-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/714b9d8669.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/714b9d8669.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/714b9d8669.jpg
  width: 0
  height: 0
url: /2022/04/18/how-to-sign.html
---
<p>I woke to an email about an ancient <a href="https://github.com/gr36/Shortcuts">Shortcuts repo</a> I had stored old backup files in. They were available as a place to save Shortcut files I had written about because the iCloud link sharing can be a bit flaky. They were so old it contained loads of .wflow files and I had forgotten it even existed, but they now need to be signed to work with iOS15.</p>
<p>Of course, I felt no need to update these, but thought it should be pretty simple, so tried to get them updated anyway. Unfortunately, I was wrong and the lack of detail in how to do this is pretty poor, but with a bit of trial and error I got them signed without issue – I hope.</p>
<h2 id="tools">Tools</h2>
<p>You will need a Mac to do this. It is the only way I have found to reliably get everything signed using the command line. Some information online suggest that it can be done on iOS using SSH, but I couldn’t get <a href="https://www.reddit.com/r/shortcuts/comments/pich0y/shortcut_source_helper_helper_for_shortcut_plist/">this to work</a>, and it felt very fiddly.</p>
<figure class="kg-card kg-image-card"><img class="kg-image" src="https://greg-morris.micro.blog/uploads/2024/714b9d8669.jpg" alt="" /></figure>
<p>So to use <em>this</em> guide, you will need a Mac running macOS Monterey and be able to use the terminal app on your device.</p>
<h2 id="how-to-sign-the-shortcut">How To Sign The Shortcut</h2>
<p>Open terminal on your Mac, and cd into the folder containing the shortcut files. Use the following command to sign the shortcut file:</p>
<pre><code>shortcuts sign -i a.wflow -o b.wflow</code></pre>
<p>Where <code>a.wflow</code> is the name of the shortcuts file, and <code>b.wflow</code> is the name you want the signed Shortcuts file to be called. Due to the weirdness in names, I actually found it easier to rename my source file as ‘a’ and then rename ‘b’ to whatever I wanted it to become.</p>
<p>Who knows if Apple will change the requirement yet again, but for the time being, you will now be able to load the file into shortcuts on Mac or iOS without issue, as the new file is now signed.</p>
