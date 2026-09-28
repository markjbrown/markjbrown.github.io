---
layout: page
title: Portfolio
permalink: /projects/
eyebrow: Selected work
heading: "Product direction. Practical proof."
intro: "I lead, build, and contribute. These public projects show different parts of that work—from guiding open-source contributors to making complex platforms easier to use."
description: "A curated portfolio of Mark Brown's open-source leadership, workshops, samples, and architecture contributions, with the scope of his role in each."
---

<section class="portfolio-section" aria-labelledby="featured-projects-title">
  <div class="section-heading">
    <h2 id="featured-projects-title">Featured projects</h2>
    <p class="section-aside">Shared work. Specific contributions.</p>
  </div>
  {% assign featured_projects = site.data.projects | where: 'featured', true %}
  {% for project in featured_projects %}
    {% include project.html project=project %}
  {% endfor %}
</section>

<section class="section-block" aria-labelledby="supporting-projects-title">
  <div class="section-heading">
    <div>
      <p class="eyebrow">More from the workbench</p>
      <h2 id="supporting-projects-title">Architecture &amp; deployment</h2>
    </div>
  </div>
  <p class="section-intro">Focused examples that make infrastructure choices and distributed-systems trade-offs easier to explore.</p>
  <div class="supporting-projects">
    {% assign supporting_projects = site.data.projects | where: 'featured', false %}
    {% for project in supporting_projects %}
      {% include project.html project=project compact=true %}
    {% endfor %}
  </div>
</section>

<div class="portfolio-end">
  <p>These projects include work by many people. I've described my own role rather than claiming the whole effort.</p>
  <a class="text-link" href="https://github.com/markjbrown">More on GitHub <span aria-hidden="true">↗</span></a>
</div>
