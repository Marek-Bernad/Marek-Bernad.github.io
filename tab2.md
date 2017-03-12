---
layout: page
title: "Sports"
---

<hr>
{% for sport in site.sports %}

<div class="sports" style="margin-bottom: 40px;">

<span style="float:left;  width: 80px; height: 80px;  margin-right: 10px; ">
<img src="{{ sport.image_path }}" alt="{{ sport.title }}" /></span>
 <h3>{{ sport.title }}</h3>
</div>

<div style="margin-bottom: 40px;">
{{ sport.content  }}
</div>
<hr>
{% endfor %}