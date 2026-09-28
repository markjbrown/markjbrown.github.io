---
layout: page
title: Blog
permalink: /blog/
eyebrow: Writing
heading: Notes from practice.
intro: "Ideas and lessons from working with cloud platforms, distributed data, and the people who build with them."
description: "Mark Brown's writing on cloud development, distributed data, AI, and developer experience."
---

<section aria-labelledby="all-writing-title">
  <div class="section-heading">
    <h2 id="all-writing-title">All writing</h2>
    <a class="text-link" href="{{ '/feed.xml' | relative_url }}">Subscribe via RSS</a>
  </div>
  {% include post-list.html posts=site.posts limit=site.posts.size %}
</section>
