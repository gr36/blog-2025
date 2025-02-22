---
layout: post
title: "Exporting Highlights From A Kobo E-Reader"
microblog: false
guid: http://greg-morris.micro.blog/2024/05/08/exporting-highlights-from.html
post_id: 4057001
date: 2024-05-08T08:25:24-0000
lastmod: 2024-06-22T16:19:25-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.24.01.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.23.57.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.29.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.38.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.48.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.54.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.16.49.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.17.02.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.18.33.png
- https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.20.33.png
photos:
photos_with_metadata:
url: /2024/05/08/exporting-highlights-from.html
---
After [loosing my Kindle Paperwhite in London](https://gregmorris.co.uk/2024/04/25/i-managed-to.html) a couple of weeks ago I have been a bit lost. I did order another one, but when [posts started](https://thedent.net/post/the-kobo-libra-colour) [popping up](https://maique.eu/2024/05/01/the-kobo-review.html) about a [colour Kobo Libra](https://amzn.to/4abDTh0) I decided to return it and try something new. Granted I have only had it since Friday, but I am already in love with it.

I will no doubt write a longer post about it later, but there are not many downsides to this new device. It has a nice screen with colour, has a separately available stylus for note taking and highlighting which I love. However reporting those highlights is not a simple as with Kindle, but I found some ways to make use of them. The below works with the Kobo Libra Colour, Kobo Libra 2 and Kobo Clara Colour - so I don’t see any reason it shouldn’t work with others.

## In A Text File
1. Connect kobo to your device
2. Open a file browser and mount the device once connected
3. Allow your file browser to see hidden files ( CMD + Shift + . On Mac)
4. Go to the hidden folder `.kobo/Kobo`
5. In a text editor open `eReader.conf`
6. In the text file find (or if not present add `[FeatureSettings]` 
7. Add a new line `ExportHighlights=true`
8. Save the file and unmount your device from the computer

To export the notes from a book, long press on the book and tap `Export Annotations`.

When you reconnect your Kobo there will be a new file called Exported Annotations with text files for the exported books. Bear in mind this does not update with new ones, so consider doing this only when they need to be exported.

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.24.01.png)![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.23.57.png)

There are some reports of truncated highlights where not all the content is exported in the text file. This has not happened to me, but please take this into consideration.

## Using A Calibre Plugin
When it comes to self management and conversion of e-books, [Calibre](https://calibre-ebook.com?from=gregmorris.co.uk) is king. I have been using it for a while to (cough) manage (cough) my Kindle e-books but it is even more invaluable when using a Kobo device. There is a wide range of plugins available and for this method we will add a new one - namely [Annotations](https://www.mobileread.com/forums/showthread.php?from=gregmorris.co.uk) by David Forrester.

Head to the preferences panel and click Plugins.

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.29.png)

Click Get new plugins and search for `Annotations`.

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.38.png)

This will give you a couple of popups, one is a warning that plugins can contain malware - they are programmes after all. And once installed you will need to restart Calibre. 

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.48.png)
![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.15.54.png)

Once restarted, customise the plugin by clicking the big yellow highlighter in the top bar, and select Customise plugin. 

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.16.49.png)

In the next window click the wand icon next to the Comments dropdown and add in the Annotations option. Once done click ok.

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.17.02.png)

Now connect your Kobo device, and once Calibre recognises it, click the highlighter again and select Fetch annotations from connected device. The popup window will allow you to select which books have them available.

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.18.33.png)

These will show in the book details window for ease of viewing, or you can copy and paste them for use elsewhere.

![](https://greg-morris.micro.blog/uploads/2024/cleanshot-2024-05-06-at-17.20.33.png)

## Use Readwise
If you use Readwise, or want a seamless way to sync your highlights, these can be directly added using the [standard options](https://help.kobo.com/hc/en-us/articles/10789206247703-Use-Readwise-to-view-and-manage-your-annotations). They will sync to the Readwise service and also be accessible from any of your set up export options such as Notion or Obsidian.

However, this will only work for highlights made to Kobo purchased books. This **will not work** for manually added ePub books or PDFs. There is a solution for this pointed out by Readwise themselves, called [October](https://utf9k.net/projects/october/), that grabs these from a connected device - however I have not tested this out myself so cant speak for its usage.
