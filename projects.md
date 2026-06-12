---
layout: page
title: Projects
permalink: /projects/
---

## Pinned repositories

My pinned projects — sourced from [my GitHub profile](https://github.com/markjbrown).

<div id="pinned-repos" style="margin-top:1rem;display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:0.75rem;">
  <p id="pinned-loading">Loading…</p>
</div>

## All public repositories

<div id="repos" style="margin-top:1rem;">Loading repositories…</div>

<script>
(function () {
  // Actual pinned repos from the GitHub profile (including cross-org repos)
  var PINNED = [
    'AzureCosmosDB/banking-multi-agent-workshop',
    'AzureCosmosDB/CosmicWorks',
    'documentdb/documentdb-kubernetes-operator',
    'AzureCosmosDB/travel-multi-agent-workshop',
    'AzureCosmosDB/gallery',
    'AzureCosmosDB/cosmos-fabric-samples'
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
    var displayName = pinned && r.full_name ? escapeHtml(r.full_name) : escapeHtml(r.name);
    return '' +
      '<div style="border:' + border + ';border-radius:8px;padding:1rem;">' +
        '<div style="display:flex;justify-content:space-between;gap:0.75rem;align-items:baseline;flex-wrap:wrap;">' +
          '<a href="' + r.html_url + '" style="font-weight:600;font-size:1rem;">' + displayName + '</a>' +
          '<span style="white-space:nowrap;font-size:0.9rem;opacity:0.8;">★ ' + r.stargazers_count + (lang ? '&nbsp; ' + lang : '') + '</span>' +
        '</div>' +
        '<p style="margin:0.5rem 0 0;font-size:0.95rem;">' + desc + '</p>' +
      '</div>';
  }

  var pinnedContainer = document.getElementById('pinned-repos');
  var allContainer    = document.getElementById('repos');

  // Fetch all pinned repos concurrently from their respective org/user API endpoints
  Promise.all(
    PINNED.map(function (fullName) {
      return fetch('https://api.github.com/repos/' + fullName)
        .then(function (r) { return r.ok ? r.json() : null; })
        .catch(function () { return null; });
    })
  ).then(function (results) {
    var cards = results
      .filter(function (r) { return r && r.html_url; })
      .map(function (r) { return repoCard(r, true); })
      .join('');
    pinnedContainer.innerHTML = cards || '<p>Could not load pinned repositories.</p>';
  });

  // Fetch markjbrown's own public repos for the "All" section
  fetch('https://api.github.com/users/markjbrown/repos?per_page=100&sort=updated')
    .then(function (r) { return r.json(); })
    .then(function (repos) {
      if (!Array.isArray(repos)) {
        allContainer.innerHTML = '<p>Could not load repositories right now.</p>';
        return;
      }
      var rest = repos
        .filter(function (r) { return !r.fork && !r.archived; })
        .sort(function (a, b) { return b.stargazers_count - a.stargazers_count; });

      if (rest.length === 0) {
        allContainer.innerHTML = '<p>No public repositories found.</p>';
        return;
      }
      allContainer.innerHTML = rest.map(function (r) { return repoCard(r, false); }).join('');
    })
    .catch(function () {
      allContainer.innerHTML = '<p>Could not load repositories right now.</p>';
    });
})();
</script>
