---
layout: page
title: Speaking
permalink: /speaking/
---

I speak regularly at conferences and events on distributed systems, Azure Cosmos DB,
AI/LLM application patterns, and cloud architecture. My full speaker profile,
including upcoming events and past session recordings, is on
[Sessionize](https://sessionize.com/mark-brown/).

<div id="sessions" style="margin-top:1.5rem;">Loading sessions…</div>

<script>
(function () {
  var container = document.getElementById('sessions');

  fetch('https://sessionize.com/api/v2/mark-brown/view/Sessions')
    .then(function (r) {
      if (!r.ok) { throw new Error('non-2xx'); }
      return r.json();
    })
    .then(function (data) {
      // Sessionize returns an array of group objects, each with a "sessions" array.
      var sessions = [];
      if (Array.isArray(data)) {
        data.forEach(function (group) {
          if (group.sessions && Array.isArray(group.sessions)) {
            group.sessions.forEach(function (s) { sessions.push(s); });
          } else if (group.id && group.title) {
            // flat session list
            sessions.push(group);
          }
        });
      }

      if (sessions.length === 0) {
        showFallback();
        return;
      }

      sessions.sort(function (a, b) {
        var dateA = a.startsAt ? new Date(a.startsAt).getTime() : Number.NEGATIVE_INFINITY;
        var dateB = b.startsAt ? new Date(b.startsAt).getTime() : Number.NEGATIVE_INFINITY;
        return dateB - dateA;
      });

      container.innerHTML = sessions.map(function (s) {
        var title = escapeHtml(s.title || 'Untitled');
        var desc  = s.description
          ? (function () {
              var escaped = escapeHtml(s.description);
              return '<p style="margin:0.5rem 0 0;font-size:0.95rem;">' +
                escaped.slice(0, 300) + (escaped.length > 300 ? '…' : '') + '</p>';
            }())
          : '';
        var date  = s.startsAt
          ? '<span style="opacity:0.7;font-size:0.85rem;">' +
              new Date(s.startsAt).toLocaleDateString('en-US', {year:'numeric',month:'long',day:'numeric'}) +
            '</span>'
          : '';
        var room  = s.room ? ' &nbsp;·&nbsp; <span style="opacity:0.7;font-size:0.85rem;">' + escapeHtml(s.room) + '</span>' : '';
        return '' +
          '<div style="border:1px solid #444;border-radius:8px;padding:1rem;margin-bottom:0.75rem;">' +
            '<div style="font-weight:600;font-size:1.05rem;margin-bottom:0.25rem;">' + title + '</div>' +
            '<div>' + date + room + '</div>' +
            desc +
          '</div>';
      }).join('');
    })
    .catch(function () {
      showFallback();
    });

  function showFallback() {
    container.innerHTML =
      '<p>Session data is not available right now. ' +
      'View my full speaking history on ' +
      '<a href="https://sessionize.com/mark-brown/">Sessionize</a>.</p>';
  }

  function escapeHtml(s) {
    return String(s)
      .replace(/&/g, '&amp;').replace(/</g, '&lt;').replace(/>/g, '&gt;')
      .replace(/"/g, '&quot;').replace(/'/g, '&#39;');
  }
})();
</script>
