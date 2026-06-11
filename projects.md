---
layout: page
title: Projects
permalink: /projects/
---

A selection of my public GitHub repositories — loaded live from the GitHub API,
sorted by stars. See [my full profile](https://github.com/markjbrown) for everything.

<div id="repos" style="margin-top:1.5rem;">Loading repositories…</div>

<script>
(function () {
  var container = document.getElementById('repos');
  fetch('https://api.github.com/users/markjbrown/repos?per_page=100&sort=updated')
    .then(function (r) { return r.json(); })
    .then(function (repos) {
      if (!Array.isArray(repos)) {
        container.innerHTML = '<p>Could not load repositories right now.</p>';
        return;
      }
      var top = repos
        .filter(function (r) { return !r.fork && !r.archived; })
        .sort(function (a, b) { return b.stargazers_count - a.stargazers_count; })
        .slice(0, 24);

      if (top.length === 0) {
        container.innerHTML = '<p>No public repositories found.</p>';
        return;
      }

      container.innerHTML = top.map(function (r) {
        var desc = r.description ? escapeHtml(r.description) : '<em>No description.</em>';
        var lang = r.language ? '<span style="opacity:0.7;">' + escapeHtml(r.language) + '</span>' : '';
        return '' +
          '<div style="border:1px solid #444;border-radius:8px;padding:1rem;margin-bottom:0.75rem;">' +
            '<div style="display:flex;justify-content:space-between;gap:1rem;align-items:baseline;">' +
              '<a href="' + r.html_url + '" style="font-weight:600;font-size:1.05rem;">' + escapeHtml(r.name) + '</a>' +
              '<span style="white-space:nowrap;font-size:0.9rem;opacity:0.8;">' +
                '★ ' + r.stargazers_count + ' &nbsp; ' + lang +
              '</span>' +
            '</div>' +
            '<p style="margin:0.5rem 0 0;">' + desc + '</p>' +
          '</div>';
      }).join('');
    })
    .catch(function () {
      container.innerHTML = '<p>Could not load repositories right now.</p>';
    });

  function escapeHtml(s) {
    return String(s)
      .replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;').replace(/'/g, '&#39;');
  }
})();
</script>
