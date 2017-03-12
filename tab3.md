---
layout: page
title: Hobbies
---

{% for hobby in site.hobbies %}

<div class="hobbies" style="margin-bottom: 40px;">
<h2><a href="{{ hobby.url }}">{{hobby.title}}</a></h2>
</div>

{% endfor %}