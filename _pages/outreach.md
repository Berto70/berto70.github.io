---
layout: single
title: "Outreach Project"
permalink: /outreach/
author_profile: true
classes: wide
#header:
#  image: /assets/images/vioz.jpeg
#  image_description: "Monte Vioz (Italy)"
#  caption: "Photo credit: Giacomo Mantovan, Iphone SE"
---

<p> Since 2017, I'm an editor and admin of one of the largest Italian space-releated outreach pages, <b>Link2Universe</b>.</p>
<p> You can follow our work on <a href="www.instagram.com/link2universe">Instagram</a>, <a href="www.facebook.com/Link2Universe">Facebook</a> and <a href="https://t.me/L2U_official">Telegram</a>!</p>


<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Link2Universe Instagram Feed</title>
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
</head>
<body>

<div id="random-instagram-post"></div>

<script>
$(document).ready(function(){
    // Your Instagram account username
    var username = "link2universe";
    
    // Fetch recent posts from the Instagram account
    $.ajax({
        url: "https://www.instagram.com/"+ username +"/?__a=1",
        type: "GET",
        success: function(response){
            var posts = response.graphql.user.edge_owner_to_timeline_media.edges;
            
            // Select a random post
            var randomIndex = Math.floor(Math.random() * posts.length);
            var randomPost = posts[randomIndex].node;
            
            // Generate embed code
            var embedCode = '<blockquote class="instagram-media" data-instgrm-permalink="https://www.instagram.com/p/'+ randomPost.shortcode +'/"></blockquote>';
            
            // Inject embed code into the HTML
            $('#random-instagram-post').html(embedCode);
            
            // Load Instagram embed script
            $.getScript("//www.instagram.com/embed.js");
        },
        error: function(xhr, status, error){
            console.log("Error fetching Instagram data: " + error);
        }
    });
});
</script>

</body>
</html>

