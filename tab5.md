---
layout: page
title: WPUB project
---

<div class="wrapper">
<div class="home">

  <h1 class="page-heading">Posts</h1>

      <hr>
  <ul class="post-list">
    {% for post in site.posts %}
      <li>
        <span class="post-meta">{{ post.date | date: "%b %-d, %Y" }}</span>

        <h2>
          <a class="post-link" href="{{ post.url | relative_url }}">{{ post.title | escape }}</a>
        </h2>
      </li>
            <hr>
    {% endfor %}
  </ul>


</div>
</div>
