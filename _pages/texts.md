---
layout: page
title: Archive
description: Experiments in machine learning.
---

<section class="posts" style="padding-left:0;">
<ul style="padding-left:0;">
{% for post in site.posts %}
<li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%m-%d-%Y" }}</time></li>
{% endfor %}
</ul>
</section>
