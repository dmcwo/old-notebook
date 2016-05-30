# notebook building notes

#### style pagination

#### figure out if I want to hide cv from navigation

#### think about integrating things as submodules
https://github.com/blog/2104-working-with-submodules

#### host font awesome locally?

#### text program

#### improve social icons

#### fix about page



#### reduce file size of bg img
cropped and compressed to 164KB (from 2MB)

#### pagination and next/prev post

in ```_config.yml```

```
# gems
gems: [jekyll-paginate]
```

in ```index.html``` the following does a few things:

* write out links to posts, the date, and the content up to the first ```<!--break-->``` (found this here: https://gist.github.com/mikeygee/2626538)
* then it will make a paginator.

```
<!-- This loops through the paginated posts -->
{% for post in paginator.posts %}
  <h1><a href="{{ post.url | prepend: site.baseurl }}">{{ post.title }}</a></h1>
  <p class="author">
    <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>
  </p>
  <!--<div class="content">-->
    {{ post.content | split:'<!--break-->' | first }} <!-- ty: https://gist.github.com/mikeygee/2626538 -->
   	{% if post.content contains '<!--break-->' %}
      <a href="{{ post.url | prepend: site.baseurl }}">read more</a>
   	{% endif %}
  <!--</div>-->
{% endfor %}

<!-- Pagination links -->
<div class="pagination">
  {% if paginator.previous_page %}
    <a href="{{ paginator.previous_page_path | prepend: site.baseurl}}" class="previous">Previous</a>
  {% else %}
    <span class="previous">Previous</span>
  {% endif %}
  <span class="page_number ">Page: {{ paginator.page }} of {{ paginator.total_pages }}</span>
  {% if paginator.next_page %}
    <a href="{{ paginator.next_page_path | prepend: site.baseurl}}" class="next">Next</a>
  {% else %}
    <span class="next ">Next</span>
  {% endif %}
</div>
```

##### next/prev post
in ```_layouts/post.html```

```
<!-- ty: http://david.elbe.me/jekyll/2015/06/20/how-to-link-to-next-and-previous-post-with-jekyll.html -->

<div class="PageNavigation">
  {% if page.previous.url %}
    <a class="prev" href="{{page.previous.url | prepend: site.baseurl}}">&laquo; {{page.previous.title}}</a>
  {% endif %}
  {% if page.next.url %}
    <a class="next" href="{{page.next.url | prepend: site.baseurl}}">{{page.next.title}} &raquo;</a>
  {% endif %}
</div>

```