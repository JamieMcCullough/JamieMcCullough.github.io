---
layout: page
show_meta: false
title: "Articles"
header:
   image_fullwidth: "header_unsplash_5.jpg"
permalink: "/articles/"
---
<ul>
    {% for post in site.categories.design %}
    <li><a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>
