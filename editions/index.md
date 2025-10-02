---
title: The Daily Anomaly
layout: default
---

# Today’s Edition

{% assign editions = site.pages
  | where: "layout", "edition"
  | sort: "path" | reverse %}

{% if editions.size > 0 %}
- [Read the latest edition]({{ editions.first.url | relative_url }})

{% if editions.size > 1 %}
## Previous Editions
{% for ed in editions offset: 1 %}
- [{{ ed.title }}]({{ ed.url | relative_url }})
{% endfor %}
{% endif %}
{% else %}
*No editions yet. Check back soon.*
{% endif %}
