---
title: Editions Archive
layout: default
permalink: /editions/
---

# Editions Archive

Browse every issue of *The Daily Anomaly*. Select a date to read its reported anomalies and edge-science highlights.

<ul class="edition-list">
  {% assign edition_pages = site.pages | where_exp: 'p', 'p.path contains "editions/"' %}
  {% assign edition_pages = edition_pages | where_exp: 'p', 'p.name != "index.md"' %}
  {% assign edition_pages = edition_pages | sort: 'path' | reverse %}
  {% for edition in edition_pages %}
    {% assign edition_slug = edition.name | split: '.' | first %}
    {% assign edition_date_formatted = edition_slug | date: "%B %-d, %Y" %}
    <li>
      <span class="edition-list__date">{{ edition_date_formatted }}</span>
      <a href="{{ site.baseurl }}{{ edition.url }}">Read the edition</a>
    </li>
  {% endfor %}
</ul>
