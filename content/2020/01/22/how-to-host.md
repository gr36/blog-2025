---
layout: post
title: "How To Host Your Own Ghost Blog On Digital Ocean"
microblog: false
guid: http://greg-morris.micro.blog/2020/01/22/how-to-host.html
post_id: 3987686
date: 2020-01-22T08:30:00-0000
lastmod: 2024-12-03T08:48:53-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/9cb8be9542.jpg
- https://greg-morris.micro.blog/uploads/2024/91ebd54149.jpg
- https://greg-morris.micro.blog/uploads/2024/884cf8140a.jpg
- https://greg-morris.micro.blog/uploads/2024/28616a5c60.jpg
- https://greg-morris.micro.blog/uploads/2024/54a20989c1.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/9cb8be9542.jpg
- https://greg-morris.micro.blog/uploads/2024/91ebd54149.jpg
- https://greg-morris.micro.blog/uploads/2024/884cf8140a.jpg
- https://greg-morris.micro.blog/uploads/2024/28616a5c60.jpg
- https://greg-morris.micro.blog/uploads/2024/54a20989c1.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/9cb8be9542.jpg
  width: 1000
  height: 771
- url: https://greg-morris.micro.blog/uploads/2024/91ebd54149.jpg
  width: 1000
  height: 771
- url: https://greg-morris.micro.blog/uploads/2024/884cf8140a.jpg
  width: 1000
  height: 384
- url: https://greg-morris.micro.blog/uploads/2024/28616a5c60.jpg
  width: 599
  height: 247
- url: https://greg-morris.micro.blog/uploads/2024/54a20989c1.jpg
  width: 598
  height: 149
url: /2020/01/22/how-to-host.html
---
<p><!--kg-card-begin: html--></p>
<p>I still blame <a href="https://birchtree.me/blog/the-biggest-change-to-birchtree-in-5-years/">Matt Birchler</a> for putting the idea in my head, I was quite happy on WordPress (not completely but pretty happy) and then he comes in and introduces <a href="https://ghost.org/">Ghost to me</a>, and I moved within a few days. On first look it seems like a ridiculously expensive option, and more suited to larger companies, but if you don’t want to splash out the $29/per month there are other options.</p>
<p>If you want to get a Ghost blog set up, its pretty easy to host it ‘yourself’,  here is a short guide on doing it on a Digital Ocean droplet.</p>
<p><img style="margin-left: auto; margin-right: auto;" title="Screenshot-2020-01-21-at-10.05.43-1.png" src="https://greg-morris.micro.blog/uploads/2024/9cb8be9542.jpg" alt="Screenshot 2020 01 21 at 10 05 43 1" width="1000" height="771" border="0" /></p>
<h2>Create A Droplet</h2>
<p>Signing up for a Digital Ocean account and creating a droplet is really straight forward. Most blogs will only need a $5 a month droplet unless you are getting serious traffic.</p>
<p>Click on Market place under ‘Choose an image’, this does allow you to choose loads of different options – but if you’re reading this guide you’ll find Ghost under ‘blogs and forums’. Once selected you will see a guide underneath detailing your requirements after your droplet is set up. On this page you will also find all information about the version being installed.</p>
<p><img style="margin-left: auto; margin-right: auto;" title="Screenshot-2020-01-21-at-10.06.10-1.png" src="https://greg-morris.micro.blog/uploads/2024/91ebd54149.jpg" alt="Screenshot 2020 01 21 at 10 06 10 1" width="1000" height="771" border="0" />It won’t matter too much where your data centre is, so choose your preference – if things like GDPR and also government monitoring are important to you, then choose wisely. Give your droplet and name and then let it do its thing.</p>
<h2>After Creation</h2>
<p>Once completed, you will receive an email from Digital Ocean with your Droplet IP address and SSH password. Keep this information extremely safe and do not share with anyone.</p>
<h3>Point Your Domain</h3>
<p>On your Digital Ocean Project page, add your domain. This will populate the NS records and give you your name severs. This is more than likely going to be <code>ns1.digitalocean.com.</code>, <code>ns2.digitalocean.com.</code> and <code>ns3.digitalocean.com.</code> – add these to your domain settings.</p>
<p><img style="margin-left: auto; margin-right: auto;" title="Screenshot-2020-01-21-at-10.28.45-copy-1.png" src="https://greg-morris.micro.blog/uploads/2024/884cf8140a.jpg" alt="Screenshot 2020 01 21 at 10 28 45 copy 1" width="1000" height="384" border="0" />Also add in an A record in Digital Ocean, with a host name of <code>@</code> and direct it to your IP address of the droplet. It is vitally important you wait for all changes to propagate before continuing otherwise you may have issues with setting up Ghost. I would advise you to wait 24 hours.</p>
<p>Once you are happy the domain information has properly propagated, continue to setting up the blog.<br /><img style="margin-left: auto; margin-right: auto;" title="pasted-image-0-1.png" src="https://greg-morris.micro.blog/uploads/2024/28616a5c60.jpg" alt="Pasted image 0 1" width="599" height="247" border="0" /></p>
<h3>SSH Into Your Droplet</h3>
<p>Nothing will be live until you SSH into your droplet and set up Ghost. You should see a page telling you as mush if your domain has propagated correctly. Open your terminal and type in:<br /><code>ssh root@your-ip-address</code></p>
<p>The sever will ask for your password, copy and paste this in, and then immediately make you change it. You will need to put your current one in again, and then choose a new one – Keep this safe!</p>
<p>Once this is done Ghost will download updates and set itself up. Press Enter.</p>
<p><img style="margin-left: auto; margin-right: auto;" title="pasted-image-0-2-1.png" src="https://greg-morris.micro.blog/uploads/2024/54a20989c1.jpg" alt="Pasted image 0 2 1" width="598" height="149" border="0" /><br />You won’t need to put in any details about SQL databases or directories, you <em>will</em> have to put in your blog URL. Do this with the <code>https://</code> on and Ghost will set up your Let Encrypt certificate for you. This is where the installation will fall down if your domain is not properly propagated.</p>
<p>Ghost will be installed and set up at <code>/var/www/ghost</code></p>
<p>If everything goes ok, you will be given a url of <em>https://your-url/ghost</em>. Head to this address and set up your profile and blog title. If you want to migrate from WordPress, here’s some <a href="https://gr36.com/migrating-from-wordpress-to-ghost/">points to consider</a>.</p>
<p><!--kg-card-end: html--></p>
