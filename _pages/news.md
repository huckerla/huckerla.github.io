---
title: "News"
layout: single
permalink: /news/
author_profile: true
---

{% assign news_items = site.news | sort: "date" | reverse %}

<div class="news-container">
  {% for item in news_items %}
    <div class="news-row">
      <div class="news-date-box">
        {{ item.date | date: "%m/%Y" }}
      </div>

      <div class="news-text">
        {{ item.content | markdownify | remove: "<p>" | remove: "</p>" }}
      </div>
    </div>
  {% endfor %}
</div>