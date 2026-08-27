---
title: "News Archive"
layout: single
permalink: /news-archive/
author_profile: true
---

{% assign news_items = site.news | sort: "date" | reverse %}
{% assign four_months_ago = 'now' | date: "%s" | minus: 10368000 | plus: 0 %}

<style>
  .news-row.has-image {
    position: relative;
    padding-right: 200px;
    min-height: 120px;
  }

  .news-row.has-image .news-image {
    position: absolute;
    top: 0;
    right: 0;
    width: 180px;
  }

  .news-row.has-image .news-image img {
    display: block;
    width: 100%;
    height: auto;
  }

  @media (max-width: 700px) {
    .news-row.has-image {
      padding-right: 0;
    }

    .news-row.has-image .news-image {
      position: static;
      width: 180px;
      margin-top: 10px;
      margin-left: auto;
    }
  }
</style>

<div class="news-container">
  {% for item in news_items %}
    {% assign item_timestamp = item.date | date: "%s" | plus: 0 %}

    {% if item_timestamp < four_months_ago %}
      <div class="news-row{% if item.image %} has-image{% endif %}">

        <div class="news-date-box">
          {{ item.date | date: "%m/%Y" }}
        </div>

        <div class="news-text">
          {{ item.content | markdownify | remove: "<p>" | remove: "</p>" }}
        </div>

        {% if item.image %}
          <div class="news-image">
            {% if item.image_link %}
              <a href="{{ item.image_link }}">
                <img src="{{ item.image | relative_url }}" alt="">
              </a>
            {% else %}
              <img src="{{ item.image | relative_url }}" alt="">
            {% endif %}
          </div>
        {% endif %}

      </div>
    {% endif %}
  {% endfor %}
</div>

<div class="news-row">
  <div class="news-date-box">
    <i class="fas fa-newspaper"></i>
  </div>

  <div class="news-text">
    <a href="{{ '/news/' | relative_url }}">Recent news</a>
  </div>
</div>