---
layout: page
title: Hobbies
---

<hr>

{% for hobby in site.hobbies %}

<div class="hobbies" style="margin-bottom: 40px;">
<h4><a href="{{ hobby.url }}">{{hobby.title}}</a></h4>
</div>

<hr>

{% endfor %}