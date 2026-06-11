---
layout: post
title: "Starting over: this blog is now on GitHub Pages"
date: 2026-06-11 11:00:00 -0700
tags: [meta, jekyll, azure]
---

I just retired my old WordPress site and rebuilt
[markjbrown.com](https://markjbrown.com) as a static Jekyll site hosted on
GitHub Pages. The old site had been on Azure App Service for years and was
quietly costing me money to host content I wasn't even maintaining.

A few things I like about the new setup:

- **Free hosting.** GitHub Pages costs $0 for public repos.
- **No surface area to attack.** No WordPress admin, no PHP, no database, no
  plugins to patch.
- **Git is the CMS.** Writing a post is `git commit && git push`. Editing
  happens in any editor — and PRs give me a built-in review workflow.
- **The site IS the source.** No more "where did I write that?" — it's all
  Markdown in a public repo at
  [github.com/markjbrown/markjbrown.github.io](https://github.com/markjbrown/markjbrown.github.io).

I'm planning to start writing again here — mostly about the stuff I'm working
on day-to-day on the Azure Cosmos DB team: data modeling at scale, vector
search, multi-agent AI patterns, and the surprises that fall out of running
real workloads in distributed systems.

More soon.
