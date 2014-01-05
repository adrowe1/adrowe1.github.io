---
layout: jumbotron
title: Blog posts by subject
heading1: Blog posts here. <a class="btn btn-lg btn-primary pull-right" href="blog.html" role="button">To all blog posts</a>
---

##Blog post tag categories

<!-- https://github.com/edrex/edrex.github.io/blob/master/pages/tags.html -->

{% for tag in site.tags %}
<h2 class="tag"><a class="label label-default" data-toggle="collapse" data-parent="#accordion" href="#tag-{{tag[0]}}">{{tag[0]}}</a></h2>
<ul id="tag-{{tag[0]}}" class="collapse">
{% for p in tag[1] %}
  <li><a href="{{ p.url }}">{{ p.title }}</a></li>
{% endfor %}
</ul>
{% endfor %}

##Other pages on site

<h2><a class="label label-default" data-toggle="collapse" data-parent="#accordion" href="#orphans"><i class="icon-frown icon-large"></i>All other pages</a></h2>
<ul id="orphans" class="collapse">
    {% for post in site.pages %}{% unless post.tags contains "main" %}{% if post.url != '/' and post.title != null %}
      <li>
        <a href="{{ post.url }}" title="{{ post.description | strip_html }}">
          {% if post.icon %}<i class="icon-{{ post.icon }}"></i>{% endif %} {{ post.title }}
        </a>
      </li>
    {% endif %}{% endunless %}{% endfor %}
</ul>