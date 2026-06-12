---
layout: page
title: Projects
permalink: /projects/
---

## Pinned repositories

A curated set of my most notable public projects. See [my full GitHub profile](https://github.com/markjbrown) for everything.

<div id="pinned-repos" style="margin-top:1rem;display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:0.75rem;">
</div>

## All public repositories

<div id="repos" style="margin-top:1rem;">Loading repositories…</div>

<script>
(function () {
  var PINNED = [
    'cosmos-global-distribution-demos',
    'VectorSearchAiAssistant',
    'design-patterns',
    'cosmos-chatgpt',
    'ClaimsProcessing',
    'RealTimeTransactions'
  ];

  function escapeHtml(s) {
    return String(s)
      .replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;').replace(/'/g, '&#39;');
  }

  function repoCard(r, pinned) {
    var desc = r.description ? escapeHtml(r.description) : '<em>No description.</em>';
    var lang = r.language ? '<span style="opacity:0.7;">' + escapeHtml(r.language) + '</span>' : '';
    var border = pinned ? '2px solid #6e8cff' : '1px solid #444';
    return '' +
      '<div style="border:' + border + ';border-radius:8px;padding:1rem;">' +
        '<div style="display:flex;justify-content:space-between;gap:0.75rem;align-items:baseline;flex-wrap:wrap;">' +
          '<a href="' + r.html_url + '" style="font-weight:600;font-size:1.05rem;">' + escapeHtml(r.name) + '</a>' +
          '<span style="white-space:nowrap;font-size:0.9rem;opacity:0.8;">★ ' + r.stargazers_count + (lang ? '&nbsp; ' + lang : '') + '</span>' +
        '</div>' +
        '<p style="margin:0.5rem 0 0;font-size:0.95rem;">' + desc + '</p>' +
      '</div>';
  }

  var pinnedContainer = document.getElementById('pinned-repos');
  var allContainer    = document.getElementById('repos');

  fetch('https://api.github.com/users/markjbrown/repos?per_page=100&sort=updated')
    .then(function (r) { return r.json(); })
    .then(function (repos) {
      if (!Array.isArray(repos)) {
        pinnedContainer.innerHTML = '<p>Could not load repositories right now.</p>';
        allContainer.innerHTML = '';
        return;
      }

      var byName = {};
      repos.forEach(function (r) { byName[r.name] = r; });

      // Pinned section — show featured repos in declared order
      var pinnedHtml = PINNED
        .filter(function (name) { return byName[name]; })
        .map(function (name) { return repoCard(byName[name], true); })
        .join('');
      pinnedContainer.innerHTML = pinnedHtml || '<p>Could not load pinned repositories.</p>';

      // All-repos section — non-fork, non-archived, sorted by stars, excluding pinned
      var pinnedSet = new Set(PINNED);
      var rest = repos
        .filter(function (r) { return !r.fork && !r.archived && !pinnedSet.has(r.name); })
        .sort(function (a, b) { return b.stargazers_count - a.stargazers_count; });

      if (rest.length === 0) {
        allContainer.innerHTML = '<p>No additional public repositories found.</p>';
        return;
      }
      allContainer.innerHTML = rest.map(function (r) { return repoCard(r, false); }).join('');
    })
    .catch(function () {
      pinnedContainer.innerHTML = '<p>Could not load repositories right now.</p>';
      allContainer.innerHTML = '';
    });
})();
</script>
