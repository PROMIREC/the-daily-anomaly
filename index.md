---
title: The Daily Anomaly
layout: default
---

{% assign edition_pages = site.pages | where_exp: 'p', 'p.path contains "editions/"' %}
{% assign edition_pages = edition_pages | where_exp: 'p', 'p.name != "index.md"' %}
{% assign edition_pages = edition_pages | sort: 'path' | reverse %}
{% assign latest_edition = edition_pages | first %}
{% if latest_edition %}
  {% assign latest_slug = latest_edition.name | split: '.' | first %}
  {% assign latest_title = latest_edition.title | default: latest_slug %}
  {% assign latest_url = latest_edition.url %}
  {% assign latest_date = latest_slug | date: "%B %-d, %Y" %}
  <section class="home-intro">
    <p class="home-kicker">Edge Science &amp; High Strangeness</p>
    <h1 class="home-headline">Today’s Edition</h1>
    <p class="home-subhead">Evidence-graded anomalies, fringe tech, and curious signals gathered daily.</p>
    <p class="home-cta"><a class="badge" href="{{ site.baseurl }}{{ latest_url }}">Read the full edition →</a></p>
  </section>
{% else %}
  <p>No editions are available yet. Check back soon.</p>
{% endif %}

{% if edition_pages.size > 1 %}
  <section class="home-archive">
    <h2>Recent Editions</h2>
    <ul class="edition-list">
      {% for edition in edition_pages limit: 5 %}
        {% assign edition_slug = edition.name | split: '.' | first %}
        {% assign edition_date_formatted = edition_slug | date: "%B %-d, %Y" %}
        <li>
          <span class="edition-list__date">{{ edition_date_formatted }}</span>
          <a href="{{ site.baseurl }}{{ edition.url }}">Read the edition</a>
        </li>
      {% endfor %}
    </ul>
    <p class="home-archive__link"><a href="{{ site.baseurl }}/editions/">Browse the archive →</a></p>
  </section>
{% endif %}
