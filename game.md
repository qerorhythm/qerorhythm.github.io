---
layout: archive
title: "ゲーム図鑑"
permalink: /games/
author_profile: true
---

<div class="game-grid">
  {% for post in site.posts %}
    {% comment %} カテゴリに「ゲーム」が含まれているか判定 {% endcomment %}
    {% if post.categories contains "ゲーム" %}
      <a href="{{ post.url | relative_url }}" class="game-card">
        <div class="game-card__image">
          {% comment %} 画像パスを取得（teaser優先、なければimage） {% endcomment %}
          {% assign thumb = post.header.teaser | default: post.header.image %}

          {% if thumb %}
            <img src="{{ thumb | relative_url }}" alt="{{ post.title }}">
          {% else %}
            <!-- 画像がない場合のフォールバック（鴨の羽色） -->
            <div class="game-card__no-image" style="width:100%; height:100%; background-color:#006e7a; display:flex; align-items:center; justify-content:center; color:white; font-size: 0.9em; font-weight: bold;">
              No Image
            </div>
          {% endif %}
        </div>

        <div class="game-card__content">
          <h2 class="game-card__title">{{ post.title }}</h2>
          {% if post.excerpt %}
            <p class="game-card__excerpt">{{ post.excerpt | strip_html | truncate: 80 }}</p>
          {% endif %}
        </div>
      </a>
    {% endif %}

{% endfor %}

</div>
