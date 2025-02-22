---
layout: post
title: "Importing Apple Notes Into Bear"
microblog: false
guid: http://greg-morris.micro.blog/2020/01/21/importing-apple-notes.html
post_id: 3987683
date: 2020-01-21T14:00:00-0000
lastmod: 2020-01-21T14:00:00-0000
type: post
categories:
- "Essay"
url: /2020/01/21/importing-apple-notes.html
---
<p>I have been using <a href="https://gregmorris.co.uk/bear-the-serious/">Bear notes for years now</a>, it’s by far my favourite app for writing, and goes far beyond a simple notes app. The great thing is it keeps getting better and better without overly complicating things and becoming hard to use – not to mention it looks gorgeous.</p>
<p>The recent update to <a href="https://twitter.com/BearNotesApp/status/1219258627816665097">Version 1.7.8</a> brings in some improvements to tag icons but also an automated way to import your Apple Notes. This is something that has been lacking, not due to the developers, but to Apple’s locked down approach to notes, unlike importing from other apps which has existed for quite awhile.</p>
<p>This is a bit of a workaround, and unfortunately you can only do this process on Mac.</p>
<h2 id="mac-use-our-automator-workflow">Mac: use our Automator Workflow</h2>
<p><a href="https://sf-applications.s3.amazonaws.com/Bear/utils/NotesExporter.workflow.zip">Download our Automator Workflow</a>  Minimum system requirements: macOS 10.10 Yosemite<br />We built an Automator Workflow for macOS that can export all your Apple Notes as HTML files. This will include most note contents, but not all. See the breakdown below:</p>
<ul>
<li>Text, lists, and photos should be included</li>
<li>Note: only macOS 10.15 Catalina supports photo export. On earlier macOS versions, Apple Notes will not export photos</li>
<li>Task lists convert into bulleted lists</li>
<li>Rich media links will convert to plain text links</li>
<li>Non-photo attachments like PDFs or other files are not supported and will be excluded from export to HTML files. They will remain safely in Apple Notes</li>
</ul>
<h3 id="how-to-use-this-automator-workflow">How to use this Automator Workflow</h3>
<ul>
<li>Download our AppleScript</li>
<li>Double-click it to open Automator</li>
<li>Press the Play button</li>
<li>Choose or create a new folder to store your exported Apple Notes</li>
<li>In Bear, click File &gt; Import Notes</li>
<li>In the dialog that opens, find the folder containing your exported notes</li>
<li>Select one or notes</li>
<li>(Optional) Adjust any import features such as whether to keep the original creation date, and whether to use the first line or file name for note titles</li>
<li>Click Import Notes</li>
</ul>
<p>For more information, see the full guide in the <a href="https://bear.app/faq/Import%20&amp;%20export/Migrate%20from%20Apple%20Notes/#how-to-use-this-automator-workflow">Bear FAQ’s</a></p>
