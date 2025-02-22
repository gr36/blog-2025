---
layout: post
title: "Ghost Members Sign Up Form Not Working? Three Things To Check"
microblog: false
guid: http://greg-morris.micro.blog/2021/01/31/ghost-members-sign.html
post_id: 3988141
date: 2021-01-31T13:45:37-0000
lastmod: 2024-04-12T10:01:26-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/6fac857dfa.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/6fac857dfa.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/6fac857dfa.jpg
  width: 0
  height: 0
url: /2021/01/31/ghost-members-sign.html
---
<p>Sending email newsletters from Ghost can be a daunting experience, especially if you have not done anything like this before. A big issue I have come across is the signup form not working for people trying to get set up. It either does nothing, or just spins and doesn’t set up a subscriber.</p>
<p>This is more than likely due to the email service and nothing you have done wrong. Emails are actually split into two types on Ghost so you might be able to send out a newsletter to thousands of people, but none of them are able to log in. The two types of emails sent by your Ghost install are:</p>
<ul>
<li>Bulk – Your actual newsletter. So you can send test emails and posts out to all of your subscribers.</li>
<li>Transactional – These are everything else. Sign up emails, log in emails and everything else to do with memberships.</li>
</ul>
<p>If you’re having issues these areas are where to check.</p>
<h2 id="set-up-mailgun-api">Set Up Mailgun API</h2>
<p>Chances are you’ve already done this, most guides walk you through this part. Head into your Labs section, turn on Members and at the bottom under Email Newsletter settings paste in your Mailgun API and the domain you are using.</p>
<figure class="kg-card kg-image-card"><img class="kg-image" src="https://greg-morris.micro.blog/uploads/2024/6fac857dfa.jpg" alt="" /></figure>
<p>If in doubt click on the links under the boxes to head straight to the area you need in Mailgun. Don’t forget to change your region to EU if you have an EU flag next to your domain.</p>
<p>This will enable you to send all your ‘bulk’ emails.</p>
<h2 id="set-up-smtp">Set Up SMTP</h2>
<p>Depending on where you host your Ghost blog, this part may not be needed, however if your on <a href="https://gregmorris.co.uk/how-to-host-your-own-ghost-blog-on-digital-ocean/">Digital Ocean like me</a>, you’ll need to send your transactional emails by SMTP and not direct from your server.</p>
<p>SSH into your droplet and</p>
<pre><code>nano /var/www/ghost/config.production.json
</code></pre>
<p>Then copy in this code to replace the mail JSON item that is there already. Changing the “user” and “pass” to your own Mailgun details.</p>
<p>If you have a droplet in the EU change the “host” to your version.</p>
<pre><code class="language-json">“mail”: {
“from”: “Your name ”,
“transport”: “SMTP”,
“options”: {
“service”: “Mailgun”,
“host”: “smtp.mailgun.org”,
“port”: 465,
“secureConnection”: true,
“auth”: {
“user”: “your_user_name”,
“pass”: “your_password”
}
}
},
</code></pre>
<p>Also set the email you want these transaction emails to appear from as this is different from your newsletter ones. An email address that is in use anyway is advisable to avoid spam filters.</p>
<p>This should allow you to send all of your transactional emails.</p>
<h2 id="check-domain-and-ssl">Check Domain And SSL</h2>
<p>This is the part that drove me crazy. I have set everything up and still my Ghost members subscribe from did not work. This was due to a miss match in the domain set up in my production.json. So head back into there:</p>
<pre><code>nano /var/www/ghost/config.production.json
</code></pre>
<p>And check right at the top where it says “URL” that this is https:// and not http:// if you are using SSL – which you will be.</p>
<pre><code>“url”: “https://YOURDOMAIN”,
</code></pre>
<p>Your sign up form should now be working correctly and you can start gaining subscribers!</p>
