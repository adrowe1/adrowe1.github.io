---
layout: jumbotron
title: Blog posts
heading1: Blog posts here.
heading2: <a class="btn btn-lg btn-primary" href="bysubject.html" role="button">By subject</a>
---



<div class="posts">
  {% for post in site.posts %}
  <div class="post">
    <h1>
      <a href="{{ post.url }}">
        {{ post.title }}
      </a>
    </h1>

    <span class="post-date">{{ post.date | date_to_string }}</span>

    {{ post.content }}
  </div>
  {% endfor %}
</div>



