---
layout: post
title: "How To Use Tailwind With Your Ghost Blog"
microblog: false
guid: http://greg-morris.micro.blog/2021/12/06/how-to-use.html
post_id: 3988292
date: 2021-12-06T13:57:46-0000
lastmod: 2024-12-03T08:49:52-0000
type: post
categories:
- "Essay"
- "Guide"
images:
- https://greg-morris.micro.blog/uploads/2024/948bdc03a8.jpg
photos:
- https://greg-morris.micro.blog/uploads/2024/948bdc03a8.jpg
photos_with_metadata:
- url: https://greg-morris.micro.blog/uploads/2024/948bdc03a8.jpg
  width: 0
  height: 0
url: /2021/12/06/how-to-use.html
---
<p>Never one to be left behind, I am continually looking for a way to speed up my theme development. Call it desire to be cutting edge, or near of missing out, whatever it is I love to play around with it. One thing that gets loads of attention is Tailwind CSS, so naturally this was on my list to play around with.</p>
<p>They call it “A utility-first CSS framework” but what it actually means is you can style all of your classes right in the HTML. There are pros and cons with this, but here’s how to get it working on your Ghost Blog.</p>
<h2 id="before-you-start">Before You start</h2>
<p>Fair warning this requires a bit of command line work, and if you’re not comfortable with this back away now! You will need:</p>
<ul>
<li>A computer running a desktop OS (macOS, Linux, or Windows)</li>
<li>A supported version of <a href="https://nodejs.org/en/">Node.js</a> (at the time of writing this is 12.x, 14.x or 16.x)</li>
<li><a href="https://yarnpkg.com/en/docs/install#alternatives-tab">Yarn</a> and <a href="https://www.npmjs.com/get-npm">npm</a> installed</li>
<li>A folder to do all your work in</li>
</ul>
<h2 id="install-ghost-locally">Install Ghost Locally</h2>
<p>First, start with Ghost CIL. In the command line:</p>
<p><code>npm install ghost-cli@latest -g</code></p>
<p>Now CD into your empty directory and run:</p>
<p><code>ghost install local</code></p>
<p>This will get ghost up and running locally on your machine, most errors are communicated daily well, but for extras do <code>ghost help</code>.</p>
<p>If everything looks OK you’ll have a site at <code>http://localhost:2368/ghost</code>. For more information on what this means, check out the <a href="https://ghost.org/docs/install/local/">Ghost docs</a>.</p>
<h2 id="your-theme">Your Theme</h2>
<p>This next part is up to you, either install a theme you want to use Tailwind with, or start developing your own using the <a href="https://github.com/TryGhost/Starter">Ghost Starter</a>. You will need to put your theme files into your Ghost local install folder, <code>content/themes</code>. If you want to clone a theme from GitHub, or your theme is stored on GitHub (<a href="https://gregmorris.co.uk/blog/how-to-edit-your-ghost-theme-using-github/">you should be!</a>) CD into this folder and use:</p>
<p><code>git clone git@github.com:&lt;your-github-username/.git name-of-theme</code></p>
<figure class="kg-card kg-image-card"><img class="kg-image" src="https://greg-morris.micro.blog/uploads/2024/948bdc03a8.jpg" alt="" /></figure>
<h2 id="install-dependencies">Install Dependencies</h2>
<p>Your theme more than likely will use Yarn, the Ghost Starter linked above is the best example. Use Arm to install everything needed by Tailwind. In your theme folder, use <code>yarn add tailwindcss</code> and then add in the necessarily files <code>npx tailwindcss init</code>.</p>
<h3 id="gitignor-file">Gitignor File</h3>
<p>Unless you want more than 5,00 new files committing to your repo, you’ll need a robust gitignor file. Most themes have these set up already to no commit files such as DS_Store on Mac, so make sure you add in <code>node_modules</code> to your file.</p>
<h3 id="import-css">Import CSS</h3>
<p>In <code>/assets/css/screen.css</code> add in:</p>
<pre><code class="language-css">@tailwind base;
@tailwind components;
@tailwind utilities;
</code></pre>
<p>This imports the tailwind classes to your main CSS. This may partly replace some of your CSS to the Tailwind classes, so something such as typography may change on your theme.</p>
<h3 id="gulpfilejs">Gulpfile.js</h3>
<p>Add in the following to your <code>gulpfile.js</code>.</p>
<p>1 - Under <code>// gulp plugins and utils</code> put in <code>const tailwind = require(‘tailwindcss’)</code></p>
<p>Under <code>function css(done)</code> there will be a section for <code>postcss(</code> add in <code>tailwind(),</code> so it will look something like the following.</p>
<pre><code class="language-css">function css(done) {
 pump([
 src(‘assets/css/screen.css’, {sourcemaps: true}),
 postcss([
 easyimport,
 autoprefixer(),
 cssnano(),
 tailwind(),
 ]),
 dest(‘assets/built/’, {sourcemaps: ‘.’}),
 livereload()
 ], handleError(done));
}
</code></pre>
<h3 id="restart-all-the-things">Restart All The Things</h3>
<p>Now that everything is completed, restart Ghost with <code>ghost restart</code> to make sure everything is being cached correctly. You should be good to go now and can get cracking with adding in new styling. When doing this, you will need to CD into your theme folder and run <code>yarn dev</code> to build the correct CSS.</p>
<p>You can also try out some themes that already have Tailwind built into them such as <a href="https://github.com/tailwindtoolbox/Ghostwind">Ghostwind</a> or <a href="https://www.origintheme.co">Origin</a> but I am enjoying working new classes into my website. For more information on using Tailwind, see their <a href="https://tailwindcss.com/docs">documentation</a>.</p>
