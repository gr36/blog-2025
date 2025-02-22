---
layout: post
title: "Migrating From Wordpress To Ghost"
microblog: false
guid: http://greg-morris.micro.blog/2020/01/21/migrating-from-wordpress.html
post_id: 3987684
date: 2020-01-21T08:31:22-0000
lastmod: 2024-04-12T09:48:20-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/3ad9506b40.jpg
- https://greg-morris.micro.blog/uploads/2024/40f2b21bb6.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/3ad9506b40.jpg
- https://greg-morris.micro.blog/uploads/2024/40f2b21bb6.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/3ad9506b40.jpg
  width: 0
  height: 0
- url: https://greg-morris.micro.blog/uploads/2024/40f2b21bb6.jpg
  width: 0
  height: 0
url: /2020/01/21/migrating-from-wordpress.html
---
<p>I’m going to be completely honest, this wasn’t easy for me – it was supposed to be straight forward, but everything that could have gone wrong did. I took the inspiration from <a href="https://birchtree.me/blog/the-biggest-change-to-birchtree-in-5-years/">Matt Birchler</a> to post about my migration and the issues I faced in the hope someone else won’t run into the same.</p>
<h2 id="exporting-from-wordpress"><strong>Exporting From WordPress</strong></h2>
<p>The easiest way to do this is through the <a href="https://wordpress.org/plugins/ghost/">Ghost export plugin</a>. The plugin promises to download all of your posts, pages, and information into an easy to import ZIP file. Unfortunately, I haven’t met anyone yet that this has worked correctly.</p>
<p>In preparation, you will need to think about the categories you have on your blog. Ghost works on tags and not categories, so this information needs to be transferred before you export. Use the <a href="https://wordpress.org/plugins/wpcat2tag-importer/">Categories to Tags converter</a> plugin and run this once before export.</p>
<p>Also if you are a lone blogger, make sure your user account has the same email address as the one used on WordPress. If they are different the import will set up another User account that is locked. Deleting this user also deletes all of the posts, and short of transferring each post over individually, you are a bit stuck.</p>
<p>I had to switch to using the JSON option as the exporter kept timing out, even when I increased the memory available and also the time limit to infinite. This JSON file will only give you post and page content, not images to go along with it.</p>
<figure class="kg-card kg-image-card"><img class="kg-image" title="imports-and-exports-in-Ghost-1.png" src="https://greg-morris.micro.blog/uploads/2024/3ad9506b40.jpg" alt="Imports and exports in Ghost 1" /></figure>
<h2 id="importing-to-ghost"><strong>Importing To Ghost</strong></h2>
<p>Once you’ve set up your blog on Ghost, log into the dashboard, go to Labs &gt; Import content &gt; Choose your file. The process is swift, and at the end, all of your posts and pages will be live on your site. If you’ve managed to export a zip file, you have nothing more to do other than check through your posts and make sure you are happy with them.</p>
<p>Due to my issues, I had the job of downloading all of my images from 7 years of posts and combing through each post to put them in. I tried to import all of my images into the recommended <code>content/images</code> folder; however, I used this opportunity to tidy up the folder.</p>
<p>There is no reason a bulk import of images wouldn’t work providing you keep the same structure as your WordPress blog. However, bear in mind that WordPress stores multiple versions of the same image at different sizes so your images folder is going to be overinflated – if storage space is an issue for you then consider doing some work to tidy up beforehand.</p>
<p>Now all I had to work about is a theme, and setting up my <a href="https://gr36.com/how-to-set-up-ghost-link-posts-using-canonical-url/">link posts</a>!</p>
<figure class="kg-card kg-image-card"><img class="kg-image" title="Blog-screenshot-1.png" src="https://greg-morris.micro.blog/uploads/2024/40f2b21bb6.jpg" alt="Blog screenshot 1" /></figure>
<h2 id="improvements"><strong>Improvements</strong></h2>
<p>If I did this again, I would work a little more on editing the JSON to my liking and making everything run a little smoother. More information on doing your import can be found on the <a href="https://ghost.org/docs/api/v3/migration/">Ghost site.</a>  My move was time sensitive as my hosting was coming to an end, but given more time, I would work on a testing domain with Ghost and spend more time on the import and set up.</p>
<p>Exporting and importing from hosting platforms needs to become more uniform. Manton Reece, the creator of micro.blog, has called for an <a href="https://www.manton.org/2017/11/24/blog-archive-format.html">implemented standard</a> to make things much more comfortable to move around. It is times like this when you wish something existed. Many applications spend time working on importing from other options, so perhaps it’s time this becomes a consideration to those that run blogging platforms.</p>
