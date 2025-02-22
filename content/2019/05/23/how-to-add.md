---
layout: post
title: "How To Add Twitter Cards To Wordpress"
microblog: false
guid: http://greg-morris.micro.blog/2019/05/23/how-to-add.html
post_id: 3987794
date: 2019-05-23T14:31:30-0000
lastmod: 2024-12-03T08:48:23-0000
type: post
categories:
- "Essay"
- "Guide"
url: /2019/05/23/how-to-add.html
---
<p><!--kg-card-begin: html--></p>
<p>Sharing previews are yet another thing missing from WordPress which should really be included by now. It’s dead easy to <a href="https://en-gb.wordpress.org/plugins/wordpress-seo/">install a plugin</a> and have it all done for you, but why bother with slowing down your site with needless plugins when you can add a tiny bit of code to your functions file.</p>
<pre><code>//Add Twitter Cards Meta Info
function add_twitter_card_info() {
 global $post;
 if ( !is_singular())
 return;
 echo ‘’;
 echo ‘’;
 echo ‘’;
 echo ‘’;
 echo ‘’; //optional: username of website
 echo ‘’; //optional: username of content creator
 if(!has_post_thumbnail( $post-&gt;ID )) { //use a default image if no featured image set
 $default_image=“http://example.com/image.jpg”; //replace this with a default image
 echo ‘’;
 }
 else{
 $thumbnail_src = wp_get_attachment_image_src( get_post_thumbnail_id( $post-&gt;ID ), ‘medium’ );
 echo ‘’;
 }
 echo “n”;
}
add_action( ‘wp_head’, ‘add_twitter_card_info’);
</code></pre>
<p>Simply paste in the above code to the functions.php file in your WordPress theme and validate all has gone correctly using the <a href="https://cards-dev.twitter.com/validator">Card Validator</a>.</p>
<p><!--kg-card-end: html--></p>
