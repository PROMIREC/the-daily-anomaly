---
title: Archive
layout: default
permalink: /archive/
---

# Past Editions
<ul>
{% assign eds = site.pages
  | where_exp: "p", "p.path contains '/editions/'"
  | sort: "path" | reverse %}
{% for ed in eds %}
  <li><a href="{{ ed.url | relative_url }}">{{ ed.title }}</a></li>
{% endfor %}
</ul>
