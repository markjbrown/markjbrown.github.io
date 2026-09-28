---
layout: page
title: About
permalink: /about/
eyebrow: About me
heading: "A product leader with an engineer's perspective."
description: "Mark Brown's approach to product and team leadership, shaped by engineering, cloud architecture, developer marketing, and community."
image: /assets/img/mark-head.jpg
---

<div class="about-intro">
  <div class="prose">
    <p class="lead">I'm Mark Brown, a Principal PM Manager on Microsoft's Azure Cosmos DB team. I bring product and team leadership together with hands-on engineering and a career spent working with developers.</p>
    <p>I've worked across product management, software engineering, cloud architecture, developer marketing, and community. That breadth shapes how I lead: connect customer needs to product direction, help people do their best work, and bring contributors together across organizational boundaries.</p>
    <p>Technical depth is part of that leadership, not a separate story. Building samples, reviewing contributions, and explaining difficult architecture choices help me understand where a product works well—and where we need to make it better.</p>
  </div>
  <figure class="about-portrait">
    <img src="{{ '/assets/img/mark-head.jpg' | relative_url }}" alt="Mark Brown smiling outdoors" width="2000" height="1571">
    <figcaption>Curiosity has been the through line.</figcaption>
  </figure>
</div>

<section class="about-section" aria-labelledby="today-title">
  <div class="section-label"><p class="eyebrow">Today</p><h2 id="today-title">Making complex platforms useful.</h2></div>
  <div class="prose">
    <p>On Cosmos DB, my work centers on helping developers and architects build with distributed data: data modeling and partitioning, resilient applications, vector search, and AI agents. I'm particularly interested in the connections between operational data, analytics, and the developer experience.</p>
    <p>I work through both people and practical deliverables. I've launched an open-source migration tool and guide its contributors, initiated a multi-agent workshop with cross-organizational participation, and authored samples alongside other contributors. These are tangible examples of how I connect product priorities with tools people can learn from and use.</p>
    <p>I also speak and teach about distributed systems and cloud development. Developer education and advocacy remain an important part of how I listen, communicate, and lead.</p>
    <p><a class="text-link" href="{{ '/projects/' | relative_url }}">Explore the work and my role in it <span aria-hidden="true">↗</span></a></p>
  </div>
</section>

<section class="about-section" aria-labelledby="career-title">
  <div class="section-label"><p class="eyebrow">The path here</p><h2 id="career-title">Built across disciplines.</h2></div>
  <div class="career-list">
    <div class="career-entry">
      <p class="eyebrow">2016–present · Microsoft</p>
      <h3>Product management &amp; team leadership</h3>
      <p>I returned to Microsoft in early 2016, worked on Azure Networking, and then joined Cosmos DB. Today, as a Principal PM Manager, I bring that platform experience to the work of leading people and building for developers.</p>
    </div>
    <div class="career-entry">
      <p class="eyebrow">2014–2016 · Solliance</p>
      <h3>Cloud architecture, close to customers</h3>
      <p>As a Cloud Architect at Solliance, I built Azure solutions for customers and returned to hands-on engineering full time. During this period, I was recognized as an Azure MVP.</p>
    </div>
    <div class="career-entry">
      <p class="eyebrow">2000–2014 · Microsoft</p>
      <h3>Platforms, developer marketing &amp; community</h3>
      <p>My first Microsoft chapter spanned early mobile and tablet platforms, Virtual Earth and Bing Maps, and the Web Platform team behind IIS, ASP.NET, and WebMatrix. I worked in developer community and evangelism, including as Community Manager for Azure MVPs and Insiders, and in product marketing for Azure Websites and Cache during Azure's early growth.</p>
    </div>
    <div class="career-entry">
      <p class="eyebrow">Since 1992 · Engineering foundations</p>
      <h3>Learning by solving real problems</h3>
      <p>I'm a self-taught developer. My first application automated work in a resort's accounting department using a beta of Microsoft Access 1.0. That led to business-process integration, web development, and message-based e-commerce systems—and a lasting interest in how software makes someone's work better.</p>
    </div>
  </div>
</section>

<section class="about-section" aria-labelledby="principles-title">
  <div class="section-label"><p class="eyebrow">Leadership principles</p><h2 id="principles-title">What I come back to.</h2></div>
  <div class="principles-list">
    <div><h3>Make the problem clear.</h3><p>I want teams to understand the customer need, the choices in front of us, and why the work matters—not just the next deliverable.</p></div>
    <div><h3>Create room for others.</h3><p>I value clear direction and shared ownership. Guiding contributors means helping people bring their expertise to the work, not making every decision myself.</p></div>
    <div><h3>Keep the feedback loop short.</h3><p>I stay close to code, customers, and community. A working example or an honest conversation often reveals what a presentation cannot.</p></div>
  </div>
</section>

<section class="connect-note" aria-labelledby="connect-title">
  <h2 id="connect-title">Continue the conversation.</h2>
  <p>Find my professional background, public work, and speaking topics.</p>
  <ul class="inline-links">
    {% for link in site.profile_links %}<li><a href="{{ link.url }}">{{ link.title | escape }} <span aria-hidden="true">↗</span></a></li>{% endfor %}
  </ul>
</section>
