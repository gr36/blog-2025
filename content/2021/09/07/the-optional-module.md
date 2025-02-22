---
layout: post
title: "The optional module, imagick, is not installed, or has been disabled - Digital Ocean"
microblog: false
guid: http://greg-morris.micro.blog/2021/09/07/the-optional-module.html
post_id: 3988180
date: 2021-09-07T11:44:49-0000
lastmod: 2024-04-12T10:02:51-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/1bd9e4533d.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/1bd9e4533d.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/1bd9e4533d.jpg
  width: 0
  height: 0
url: /2021/09/07/the-optional-module.html
---
<p>Before I start, the full disclosure is I don’t think this error message makes much difference. After resolving this I have not noticed any improvements with image handling, but some-people (me included) just like clearing warning messages! So, if you’re like me and just want to get rid of the bits of red on your WordPress health check then here’s some help.</p><figure class="kg-card kg-image-card"><img src="uploads/2024/1bd9e4533d.jpg" class="kg-image" alt loading="lazy" /></figure><h2 id="the-error-">The Error:</h2><p>When running a WordPress health check you will get the following error</p><blockquote><em>The WordPress Hosting Team maintains a list of those modules, both recommended and required, in the team handbook (opens in a new tab).</em><br /><br /><em>Warning The optional module, imagick, is not installed, or has been disabled.</em></blockquote><h2 id="what-does-imagick-do">What does Imagick do?</h2><p>To use their own words “Imagick is a native php extension to create and modify images using the ImageMagick API”. it will enable you to edit your images much easier with the ability to add in loads of different effects and customisations natively in the WordPress media gallery.</p><p>It is also used to optimise the image you upload to WordPress and create different version fo images for different situations. Imagick also works with a larger range of image types and is thought to produce <a href="https://support.pagely.com/hc/en-us/articles/115000052451-Imagick-vs-GD-in-WordPress">higher quality images overall</a>. With that said, WordPress functions perfectly fine without it so installing is at your own risk and completely up to you.</p><h2 id="the-fix-for-digital-ocean-hosting-">The Fix For Digital Ocean Hosting:</h2><p>On Debian/Ubuntu SSH into your server using terminal and do the following:</p><pre><code class="language-ruby">$ sudo apt install php-imagick
$ sudo systemctl reload apache2</code></pre><p>If you run the PHP-FPM service, you also need to restart PHP-FPM service for Apache.</p><p>If you are hosting on anything else, or don’t have access to your server please consult with your host to solve this issue. Also note that the module is optional and not required, to reinforced what I have said previously I have noticed zero difference and merely did it to get rid of the warning – do so at your own risk.</p>
