---
layout: page
title: Blog
permalink: /blog/
---

<ul style="list-style:none;padding:0;">
{% for post in site.posts %}
  <li style="margin-bottom:1.5rem;">
    <a href="{{ post.url | relative_url }}" style="font-size:1.15rem;font-weight:600;">{{ post.title }}</a>
    <div style="opacity:0.7;font-size:0.9rem;margin-top:0.15rem;">
      {{ post.date | date: "%B %-d, %Y" }}
      {% if post.tags.size > 0 %} · {{ post.tags | join: ", " }}{% endif %}
    </div>
    {% if post.excerpt %}
      <div style="margin-top:0.4rem;">{{ post.excerpt | strip_html | truncate: 220 }}</div>
    {% endif %}
  </li>
{% else %}
  <li><em>No posts yet — check back soon.</em></li>
{% endfor %}
</ul>
