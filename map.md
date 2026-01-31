---
layout: page
title: Map
permalink: /map/
---

<p class="map-intro">
  A small atlas of where these notes were written.
</p>

<div class="map-shell">
  <div id="post-map"></div>

  <div class="map-legend">
    <span class="map-legend-dot"></span>
    <span class="map-legend-text">
      Dots mark where each fragment was written.
    </span>
  </div>
</div>

<div class="map-list-intro">
  Recent fragments on the map
</div>

<ul class="map-list">
  {% for post in site.posts limit: 8 %}
    {% if post.lat and post.lng %}
      <li class="map-list-item">
        <div class="map-list-meta">
          <span class="map-list-date">
            {{ post.date | date: "%B %d, %Y" }}
          </span>
          {% if post.where %}
            <span class="map-list-where"> · {{ post.where }}</span>
          {% endif %}
        </div>
        <a class="map-list-title" href="{{ post.url | relative_url }}">
          {{ post.title }}
        </a>
      </li>
    {% endif %}
  {% endfor %}
</ul>

<link
  rel="stylesheet"
  href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
/>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"></script>

<script>
  const posts = [
    {% for post in site.posts %}
      {% if post.lat and post.lng and post.where %}
        {
          title: {{ post.title | jsonify }},
          url: {{ post.url | relative_url | jsonify }},
          date: {{ post.date | date: "%Y-%m-%d" | jsonify }},
          where: {{ post.where | jsonify }},
          lat: {{ post.lat }},
          lng: {{ post.lng }}
        },
      {% endif %}
    {% endfor %}
  ];

  // Group by place name and keep the most recent post per place
  const latestByPlaceMap = new Map();

  posts.forEach(p => {
    const key = p.where || "Somewhere";
    const existing = latestByPlaceMap.get(key);
    if (!existing) {
      latestByPlaceMap.set(key, p);
    } else {
      // compare ISO dates as strings
      if (p.date > existing.date) {
        latestByPlaceMap.set(key, p);
      }
    }
  });

  const latestByPlace = Array.from(latestByPlaceMap.values());

  const map = L.map("post-map", {
    zoomControl: false,
    scrollWheelZoom: false,
    dragging: true,
    doubleClickZoom: false,
    attributionControl: false
  }).setView([25, 10], 2);

  L.tileLayer(
    "https://{s}.basemaps.cartocdn.com/light_nolabels/{z}/{x}/{y}{r}.png",
    { maxZoom: 10 }
  ).addTo(map);

  const dotIcon = L.divIcon({
    className: "post-dot",
    iconSize: [14, 14]
  });

  const bounds = [];
  latestByPlace.forEach(p => {
    const m = L.marker([p.lat, p.lng], { icon: dotIcon }).addTo(map);

    m.on("click", () => {
      window.location.href = p.url;
    });

    m.bindTooltip(
      `${p.where}: ${p.title}`,
      { direction: "top", offset: [0, -8], opacity: 0.9 }
    );

    bounds.push([p.lat, p.lng]);
  });

  if (bounds.length) {
    map.fitBounds(bounds, { padding: [30, 30] });
  }

  // Build the “Recent fragments on the map” list from latestByPlace
  document.addEventListener("DOMContentLoaded", () => {
    const listEl = document.querySelector(".map-list");
    if (!listEl) return;

    // Sort by date descending
    const sorted = [...latestByPlace].sort((a, b) => (a.date < b.date ? 1 : -1));

    listEl.innerHTML = "";
    sorted.forEach(p => {
      const li = document.createElement("li");
      li.className = "map-list-item";
      li.innerHTML = `
        <div class="map-list-meta">
          <span class="map-list-date">${p.date}</span>
          <span class="map-list-where"> · ${p.where}</span>
        </div>
        <a class="map-list-title" href="${p.url}">
          ${p.title}
        </a>
      `;
      listEl.appendChild(li);
    });
  });
</script>

