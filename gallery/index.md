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
    cursor: pointer;
  }

  .gallery img:hover {
    transform: scale(1.05);
  }

  /* Lightbox */
  .lightbox {
    display: none;
    position: fixed;
    z-index: 999;
    padding: 20px;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(0,0,0,0.9);
  }

  .lightbox img {
    margin: auto;
    display: block;
    max-width: 90%;
    max-height: 80%;
  }

  .lightbox:target {
    display: block;
  }

  .close {
    position: absolute;
    top: 20px;
    right: 40px;
    color: white;
    font-size: 30px;
    font-weight: bold;
    text-decoration: none;
  }
</style>

<nav>
  <a href="#Play">Play</a>
  <a href="#Wander">Wander</a>
  <a href="#Eat">Eat</a>
</nav>

{% assign gallery = "
Play|
https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868|https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQREnYJzOGG5QKFqR0lI4V5yASEgyRuybjwEAGRATwiGhfs?width=4000&height=1868|https://1drv.ms/i/c/6118ddcb5316a0a9/IQREnYJzOGG5QKFqR0lI4V5yASEgyRuybjwEAGRATwiGhfs?width=4000&height=1868,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQQHljFCCJ6xRaTiSmlcb3AiAd5iaK7v4b2_2-1bzWsgtho?width=4000&height=3000|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQHljFCCJ6xRaTiSmlcb3AiAd5iaK7v4b2_2-1bzWsgtho?width=4000&height=3000,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQQZjtGUJtUmSYnkoGskWQCBAQYfs87CMYLADBfw6c1KwHk?width=4000&height=3000|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQZjtGUJtUmSYnkoGskWQCBAQYfs87CMYLADBfw6c1KwHk?width=4000&height=3000;

Wander|
https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=3920&height=2204|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=3920&height=2204,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=3920&height=2204|https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=3920&height=2204,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=3590&height=2161|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=3590&height=2161,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQRn6TIri6CAS503qbdNEv6-AdoQRGifJjddtn_LDIafIOc?width=3887&height=2521|https://1drv.ms/i/c/6118ddcb5316a0a9/IQRn6TIri6CAS503qbdNEv6-AdoQRGifJjddtn_LDIafIOc?width=3887&height=2521;

Eat|
https://1drv.ms/i/c/6118ddcb5316a0a9/IQSOardx2EZRTLY_X7-H3Rl4AVrnu8fnNhaMfnGlBlXjGvw?width=1024&height=685|https://1drv.ms/i/c/6118ddcb5316a0a9/IQSOardx2EZRTLY_X7-H3Rl4AVrnu8fnNhaMfnGlBlXjGvw?width=1024&height=685,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQRXz-3NuIFHQajUVuA9CfniAch43FTP_iwIp12GfmmsyGE?width=2048&height=1536|https://1drv.ms/i/c/6118ddcb5316a0a9/IQRXz-3NuIFHQajUVuA9CfniAch43FTP_iwIp12GfmmsyGE?width=2048&height=1536,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQTFvXL2gU83TqpsZL-d0e5_AZ1SY8k0MBJJYJmRJO7vqqQ?width=4000&height=1868|https://1drv.ms/i/c/6118ddcb5316a0a9/IQTFvXL2gU83TqpsZL-d0e5_AZ1SY8k0MBJJYJmRJO7vqqQ?width=4000&height=1868,
https://1drv.ms/i/c/6118ddcb5316a0a9/IQRtitNAvF0jT6TzVPkIqTlsAQ3Lvvd8zY4YN54G_a71VNU?width=4000&height=1868|https://1drv.ms/i/c/6118ddcb5316a0a9/IQRtitNAvF0jT6TzVPkIqTlsAQ3Lvvd8zY4YN54G_a71VNU?width=4000&height=1868
" | split: ";" %}

{% for sec in gallery %}
  {% assign parts = sec | split: "|" %}
  {% assign sec_name = parts[0] %}
  <div class="section" id="{{ sec_name }}">
    <h3 class="section-title">{{ sec_name }}</h3>
    <div class="gallery">
      {% assign images = parts[1] | split: "," %}
      {% for img in images %}
        {% assign pair = img | split: "|" %}
        <a href="#img{{ forloop.index0 }}-{{ sec_name }}">
          <img src="{{ pair[0] }}" alt="{{ sec_name }} image">
        </a>
        <div id="img{{ forloop.index0 }}-{{ sec_name }}" class="lightbox">
          <a href="#" class="close">&times;</a>
          <img src="{{ pair[1] }}">
        </div>
      {% endfor %}
    </div>
  </div>
{% endfor %}
