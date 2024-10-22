---
layout: page
show_meta: false
title: "Articles"
permalink: "/articles/"

header:
    title: header with text
    background-color: "#EFC94C;"
    image_fullwidth: "dark-universe-lss-large.jpg"
    caption: "Credit: Ralf Kaehler, Carter Emmart, Tom Abel, Oliver Hahn"
    caption_url: https://www.slac.stanford.edu/~kaehler/homepage/visualizations/images/
---
<ul>
    {% for post in site.categories.articles %}
    <li><a href="{{ site.url }}{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
</ul>
