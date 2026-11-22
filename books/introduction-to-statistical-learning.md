---
layout: page
title: An Introduction to Statistical Learning
permalink: /books/introduction-to-statistical-learning/
---

<div class="book-header">
  <p class="book-authors"><strong>Authors:</strong> Gareth James, Daniela Witten, Trevor Hastie, Robert Tibshirani</p>
  <p class="book-desc">An accessible introduction to statistical learning and machine learning.</p>
  <div class="book-links">
    <a href="https://www.statlearning.com/" target="_blank" rel="noopener noreferrer">Official book website</a>
    <a href="https://hastie.su.domains/ISLR2/ISLRv2_corrected_June_2023.pdf.download.html" target="_blank" rel="noopener noreferrer">Read the PDF</a>
  </div>
</div>

<div class="chapter-list">
  {% for chapter in site.data.chapter_notes %}
    <article class="chapter-card{% unless chapter.image %} no-image{% endunless %}">
      <div class="chapter-text">
        <div class="chapter-meta">
          <span>{{ chapter.date }}</span>
          <span>{{ chapter.read_time }}</span>
        </div>
        <h3 class="chapter-title">
          {% if chapter.link %}
            <a href="{{ chapter.link | relative_url }}">{{ chapter.title }}</a>
          {% else %}
            {{ chapter.title }}
          {% endif %}
        </h3>
        <p class="chapter-subtitle">{{ chapter.subtitle }}</p>
      </div>
      {% if chapter.image %}
      <div class="chapter-image">
        <span class="chapter-image-art" role="img" aria-label="{{ chapter.title }} notes" style="background-image: url('{{ chapter.image | relative_url }}'); aspect-ratio: {{ chapter.aspect | default: '1 / 1' }};"></span>
      </div>
      {% endif %}
    </article>
  {% endfor %}
</div>

[Back to Books Read]({{ '/books-read/' | relative_url }})
