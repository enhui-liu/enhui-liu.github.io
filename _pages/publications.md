---
layout: page
permalink: /publications/
title: Publications
description: Publications synchronized with the CV publications and Conference Presentations sections.
nav: true
nav_order: 2
_styles: |
  .publications.publications-cv {
    margin-top: 1.5rem;
  }

  .publications.publications-cv .list-group,
  .publications.publications-cv .list-group-flush {
    background-color: transparent;
  }

  .publication-section {
    margin-top: 2.75rem;
  }

  .publication-section:first-of-type {
    margin-top: 0;
  }

  .publication-section-heading {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    gap: 1rem;
    margin-bottom: 1rem;
    padding-bottom: 0.65rem;
    border-bottom: 1px solid var(--global-divider-color);
  }

  .publication-section-heading h3 {
    margin: 0;
    font-size: 1.35rem;
  }

  .publication-section-heading p {
    margin: 0;
    color: var(--global-text-color-light);
    font-size: 0.98rem;
  }

  .presentations-list {
    list-style: none;
    margin: 0;
    padding: 0;
    display: grid;
    gap: 1rem;
  }

  .presentations-list li {
    position: relative;
    padding: 1rem 1.25rem 1rem 3rem;
    border: 1px solid var(--global-divider-color);
    border-radius: 16px;
    background: color-mix(in srgb, var(--global-bg-color) 92%, var(--global-theme-color) 8%);
    box-shadow: 0 10px 24px rgba(0, 0, 0, 0.04);
  }

  .presentations-list li::before {
    content: '•';
    position: absolute;
    left: 1.2rem;
    top: 0.9rem;
    font-size: 1.8rem;
    line-height: 1;
    color: var(--global-theme-color);
  }

  .presentations-list p {
    margin: 0;
    line-height: 1.8;
  }

  .publications.publications-cv .list-group-item {
    background-color: transparent;
    color: var(--global-text-color);
    padding: 1.75rem 0;
    border-bottom: 1px solid var(--global-divider-color);
  }

  .publications.publications-cv .list-group-item:first-child {
    padding-top: 0.5rem;
  }

  .publications.publications-cv .title {
    font-size: 1.2rem;
    line-height: 1.55;
    margin-bottom: 0.6rem;
  }

  .publications.publications-cv h6 {
    margin-bottom: 0.5rem;
  }

  .publications.publications-cv p {
    font-size: 1rem;
    line-height: 1.85;
    margin-bottom: 0;
  }

  .publications.publications-cv .badge {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    min-width: 88px !important;
    font-size: 0.95rem;
    padding: 0.5rem 0.85rem;
    line-height: 1.1;
    white-space: nowrap;
  }

  .publications.publications-cv .badge.year-2024 {
    background-color: #f48fb1 !important;
    color: #ffffff !important;
  }

  @media (max-width: 767.98px) {
    .publication-section {
      margin-top: 2.25rem;
    }

    .publication-section-heading {
      flex-direction: column;
      align-items: flex-start;
      gap: 0.35rem;
    }

    .presentations-list li {
      padding: 0.95rem 1rem 0.95rem 2.75rem;
      border-radius: 14px;
    }

    .publications.publications-cv .list-group-item {
      padding: 1.25rem 0;
    }

    .publications.publications-cv .title {
      font-size: 1.08rem;
    }

    .publications.publications-cv p {
      line-height: 1.7;
    }
  }
---

<!-- _pages/publications.md -->

{% assign empty_array = '' | split: ',' %}
{% assign publications = site.data.cv.cv.sections.Publications | default: site.data.resume.publications | default: empty_array %}
{% assign presentations = site.data.cv.cv.sections['Conference Presentations'] | default: empty_array %}

<section class="publication-section">
  <div class="publications publications-cv">
    {% if publications.size > 0 %}
      {% assign entries = publications %}
      {% include cv/publications.liquid %}
    {% else %}
      <p>No publications available.</p>
    {% endif %}
  </div>
</section>

{% if presentations.size > 0 %}
  <section class="publication-section">
    <div class="publication-section-heading">
      <h3>Conference Presentations</h3>
    </div>
    <ul class="presentations-list">
      {% for presentation in presentations %}
        <li>
          <p>
            {{ presentation.bullet | markdownify | remove: '<p>' | remove: '</p>' }}
            {% if presentation.date %} ({{ presentation.date }}){% endif %}
          </p>
        </li>
      {% endfor %}
    </ul>
  </section>
{% endif %}
