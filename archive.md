---
title: Archive
layout: default
permalink: /archive/
---

# Past Editions
<ul>
{% assign eds = site.pages
  | where: "layout", "edition"
  | sort: "path" | reverse %}
{% if eds.size > 0 %}
{% for ed in eds %}
  <li><a href="{{ ed.url | relative_url }}">{{ ed.title }}</a></li>
{% endfor %}
{% else %}
  <li>No editions yet. Check back soon.</li>
{% endif %}
</ul>
