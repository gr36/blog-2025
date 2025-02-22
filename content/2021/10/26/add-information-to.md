---
layout: post
title: "Add Information To Notion With Shortcuts"
microblog: false
guid: http://greg-morris.micro.blog/2021/10/26/add-information-to.html
post_id: 3988063
date: 2021-10-26T19:00:00-0000
lastmod: 2024-04-12T09:58:00-0000
type: post
categories:
- "Essay"
images:
- https://greg-morris.micro.blog/uploads/2024/a19ce8904e.jpg
- https://greg-morris.micro.blog/uploads/2024/5ed5c14b64.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/a19ce8904e.jpg
- https://greg-morris.micro.blog/uploads/2024/5ed5c14b64.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/a19ce8904e.jpg
  width: 827
  height: 418
- url: https://greg-morris.micro.blog/uploads/2024/5ed5c14b64.jpg
  width: 1536
  height: 596
url: /2021/10/26/add-information-to.html
---
<p>Without getting too much into the tools I use (yet again) I have been enjoying using <a href="https://notion.so/">Notion</a> lately for all of my productivity needs. It’s not perfect but the power and flexibility it offers me for free is pretty crazy. One of the downsides is using it on the go as the iOS apps leave a little to be desired, but seeing as my usage on mobile is limited now I built a shortcut to help out.</p><h2 id="the-set-up">The Set Up</h2><p>The Notion API has been around a little while but it’s very under utilised in my opinion. Given the fact Notion appeals to a wide rage of businesses and individuals alike it comes as no surprised that the API allows for quite a lot to be achieved without even opening the app. In order to get access to this you will need to visit their integrations page and set up you own access token.</p><p>1 – Whilst signed in to Notion, head to the <a href="https://www.notion.com/my-integrations">main page for setting up automation</a> and add a new integration with a name of your choice. Once set up you will need the API Key, so copy this somewhere safe. This allows limitless access to your Notion data (with a few bits of extra information needed) so please keep it safe!</p><p>2 -Second you will need the ID of the database you want to add information into, you can find this in the URL when the database is open as a page. This does not work with Linked Databases so make sure you have the original one open and copy the URL.</p><pre><code class="language-jsx">https://www.notion.so/{workspace_name}/{database_id}?v={view_id}
</code></pre><p>If you have only one Workspace you wont have the Workspace name in your URL, so just copy everything after the Notion URL and before the question mark.</p><figure class="kg-card kg-image-card"><img src="uploads/2024/a19ce8904e.jpg" class="kg-image" alt loading="lazy" width="827" height="418" /></figure><p>While you have this page open share this database with your integration by clicking <strong><strong>‘Share’</strong></strong> then <strong><strong>‘Add people, emails, groups or integrations’</strong></strong> and selecting the integration you just set up. This gives the API full access to this database only. In my example below this is my ‘Inbox’ where everything goes first for me to sort out later on at my desk.</p><figure class="kg-card kg-image-card kg-width-wide"><img src="uploads/2024/5ed5c14b64.jpg" class="kg-image" alt loading="lazy" width="1536" height="596" /></figure><h2 id="the-shortcut">The Shortcut</h2><p>Download the Shortcut found <a href="https://www.icloud.com/shortcuts/a6cd20ece2324bdc9981eb266e8345d8">here</a>. Paste in the API Key when requested and secondly add in the Database ID. You can change these afterwards by editing the commented text boxes with the relevant data.</p><p>Once run, this simple set upasks you for a title and some content for the quick database entry you are making. This then puts the information into the below JSON format using the supplied variables. The real power of using the Notion API is the possibilities are huge. The API contains the ability to set up any number of blocks inside this page, rich text styling, adding images and loads more. You can find out more information in their <a href="https://developers.notion.com/docs/getting-started">extensive API documents</a>.</p><pre><code class="language-html">{
    "parent": { "database_id": "{database ID￼}" },
    "properties": {
        "title": {
      "title": [{ "type": "text", "text": { "content": "{page title}" } }]
        }
    },
    "children": [
    {
      "object": "block",
      "type": "paragraph",
      "paragraph": {
        "text": [{ "type": "text", "text": { "content": "{block content}" } }]
      }
    }
  ]
}
</code></pre><p>I have set up a few of these to be able to add in items for my Todo list, blog post ideas and also clip web information for me to look at later on. I may look at creating something much bigger in future as my usage of Notion increases, it may never <a href="https://gr36.com/2021/05/15/my-obsidian-set/">pull me away from Obsidian</a> fully but it’s an amazing service none the less. If you create something I would love to see where you go with the Notion API and Shortcuts.</p>
