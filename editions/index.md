---
title: The Daily Anomaly
layout: default
---

# Today’s Edition

{% assign eds = site.pages
  | where_exp: "p", "p.path contains '/editions/'"
  | sort: "path" | reverse %}
{% assign latest = eds | first %}

{% if latest %}
- 👉 [Read the full edition]({{ latest.url | relative_url }})
{% else %}
*No editions yet. Check back soon.*
{% endif %}
