---
layout: page
title: Search
---

<style>
	#search-container {
	    max-width: 100%;
			margin-top: 1em;
	}

	input[type=text] {
		font-size: 1em;
    outline: none;
    padding: 1rem;
		background: rgb(236, 237, 238);
		color: #ff00ff;
    width: 100%;
		height: 50px;
		font-family: inherit;
    font-weight: 500;
		border: none;
		border-radius: 0;
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;
	}

	input[type=submit] {
	  width: 100%;
		height: 50px;
		background-color: #fff;
		color: #000;
		font-size: 1em;
	  padding: 14px 20px;
	  margin: 8px 0;
	  border: 2px solid #000;
		border-radius: 0;
	  cursor: pointer;
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;		
	}

	input[type=submit]:hover,
	input[type=submit]:focus {
	  background-color: #ff00ff;
		color: #000;
	}

	#search-results {
		margin: 2rem 0;
		padding-left: 0;
	}

	#search-results li {
		list-style: none;
	}
	a {
		transition: all 0.25s;
	}
	.hidden {
		display: none;
	}
</style>

<!-- Html Elements for Search -->
<div id="search-container">
<form action="/search.html" method="get">
  <label for="search-box" class="hidden">Search</label>
  <input type="text" id="search-box" name="query">
  <input type="submit" value="Search">
</form>

<ul id="search-results"></ul>

</div>

<script>
  window.store = {
    {% for post in site.posts %}
      "{{ post.url | slugify }}": {
        "title": "{{ post.title | xml_escape }}",
        "author": "{{ post.author | xml_escape }}",
        "category": "{{ post.category | xml_escape }}",
        "content": {{ post.content | strip_html | strip_newlines | jsonify }},
        "url": "{{ post.url | xml_escape }}"
      }
      {% unless forloop.last %},{% endunless %}
    {% endfor %}
  };
</script>
<script src="/assets/js/lunr.min.js" type="text/javascript"></script>
<script src="/assets/js/search.js" type="text/javascript"></script>
