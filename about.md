---
layout: page
title: About
permalink: /about/
---

Mostly, I've been wanting a place to jot things down.

{% for post in site.posts %}
{% capture year %}{{ post.date | date: '%Y' }}{% endcapture %}
{% capture next_year %}{{ post.next.date | date: '%Y' }}{% endcapture %}
{% if year != next_year %}
<h3>{{ post.date | date: '%Y' }}</h3>
{% endif %}
&middot; {% assign m = post.date | date: "%B" %} {% case m %} {% when 'April' or 'May' or 'June' or 'July' %}{{ m }} {% when 'September' %}Sept. {% else %}{{ post.date | date: "%b" }}. {% endcase %} {{ post.date | date: "%-d" }} <a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a>
{% endfor %}

<i class="fa fa-camera-retro"></i>
