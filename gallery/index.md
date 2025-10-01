---
layout: default
title: Gallery
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/gallery-index.png') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
}

nav {
  text-align: center;
  padding: 20px;
}

nav a {
  margin: 0 10px;
  text-decoration: none;
  color: #000;
  font-weight: bold;
  text-transform: capitalize;
}

.section {
  padding: 40px 20px;
  max-width: 1200px;
  margin: auto;
}

h3.section-title {
  font-size: 1.5rem;
  margin-top: 0;
  padding: 10px 0;
  border-bottom: 2px solid rgba(0,0,0,0.1);
  text-transform: capitalize;
}

.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 15px;
  margin-top: 20px;
}

.gallery img {
  width: 100%;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  transition: transform 0.3s;
}

.gallery img:hover {
  transform: scale(1.05);
}
</style>

<nav>
  <a href="#Play">Play</a>
  <a href="#Wander">Wander</a>
  <a href="#Eat">Eat</a>
</nav>

{% assign gallery = "
Play|
https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQREnYJzOGG5QKFqR0lI4V5yASEgyRuybjwEAGRATwiGhfs?width=4000&height=1868;

Wander|
https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=3920&height=2204,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=3920&height=2204;

Eat|
https://1drv.ms/i/c/6118ddcb5316a0a9/IQSOardx2EZRTLY_X7-H3Rl4AVrnu8fnNhaMfnGlBlXjGvw?width=1024&height=685,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQRXz-3NuIFHQajUVuA9CfniAch43FTP_iwIp12GfmmsyGE?width=2048&height=1536
" | strip | split: ";" %}

{% for sec in gallery %}
  {% if sec != "" %}
    {% assign parts = sec | strip | split: "|" %}
    {% assign sec_name = parts[0] %}
    <div class="section" id="{{ sec_name }}">
      <h3 class="section-title">{{ sec_name }}</h3>
      <div class="gallery">
        {% assign images = parts[1] | strip | split: "," %}
        {% for img in images %}
          {% if img != "" %}
            <img src="{{ img | strip }}" alt="{{ sec_name }} image">
          {% endif %}
        {% endfor %}
      </div>
    </div>
  {% endif %}
{% endfor %}
