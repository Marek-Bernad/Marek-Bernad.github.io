---
layout: page
title: "Sports"
---

{% for sport in site.sports %}

<div class="sports" style="margin-bottom: 40px;">

<span style="float:left;  width: 80px; height: 80px;  margin-right: 10px; ">
<img src="{{ sport.image_path }}" alt="{{ sport.title }}" /></span>
 <h2>{{ sport.title }}</h2>
</div>

<div style="margin-bottom: 40px;">
{{ sport.content  }}
</div>

{% endfor %}