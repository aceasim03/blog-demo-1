---
layout: page
title: Map
permalink: /map/
---

<p class="map-intro">
  A small atlas of where these notes were written.
</p>

<div class="flatmap">
  <img class="flatmap-base" src="{{ '/assets/world.svg' | relative_url }}" alt="World map">

  <!-- Dots: positioned by percent (responsive) -->
  <button class="pin pin-nj" data-place="New Jersey">NJ</button>
  <button class="pin pin-bj" data-place="Beijing">BJ</button>
  <button class="pin pin-sh" data-place="Shanghai">SH</button>
  <button class="pin pin-tk" data-place="Takasaki">TK</button>
</div>

<div id="place-panel" class="place-panel" aria-live="polite">
  <div class="place-title">Click a dot</div>
  <div class="place-sub">New Jersey · Beijing · Shanghai · Takasaki</div>
</div>

<script>
  // Build a location index from your posts
  const posts = [
    {% for post in site.posts %}
      {
        title: {{ post.title | jsonify }},
        url: {{ post.url | relative_url | jsonify }},
        date: {{ post.date | date: "%Y-%m-%d" | jsonify }},
        where: {{ post.where | default: "" | jsonify }}
      },
    {% endfor %}
  ];

  function postsFor(place) {
    const p = place.toLowerCase();
    return posts.filter(x => (x.where || "").toLowerCase().includes(p));
  }

  const panel = document.getElementById("place-panel");

  document.querySelectorAll(".pin").forEach(btn => {
    btn.addEventListener("click", () => {
      const place = btn.dataset.place;
      const list = postsFor(place);

      const items = list.length
        ? `<ul class="place-list">
            ${list.map(p => `
              <li>
                <a href="${p.url}">${p.title}</a>
                <span class="place-date">${p.date}</span>
              </li>
            `).join("")}
          </ul>`
        : `<div class="place-empty">No posts tagged with this location yet.</div>`;

      panel.innerHTML = `
        <div class="place-title">${place}</div>
        <div class="place-sub">${list.length} post${list.length === 1 ? "" : "s"}</div>
        ${items}
      `;
    });
  });
</script>




<p class="map-credit">
  Map graphic: <a href="https://mapsvg.com/maps/world" target="_blank" rel="noopener">Creator Name</a>,
  licensed under <a href="https://creativecommons.org/licenses/by/4.0/" target="_blank" rel="noopener">CC BY 4.0</a>.
</p>
