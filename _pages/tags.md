---
layout: default
title: Tags
---

<section class="posts tag-cloud">
	<h1>{{ page.title }}</h1>
{% assign tags = site.tags | sort %}

{% for tag in tags %}
 <a href="/tag/{{ tag | first | slugify }}/">{{ tag[0] | replace:'-', ' ' }} ({{ tag | last | size }}){% unless forloop.last %}, {% endunless %}</a>
{% endfor %}

</section>
