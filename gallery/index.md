---
layout: default
title: Image Gallery
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/gallery-index.png') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
}

h2 { text-align:center; margin-top: 20px; }
nav { text-align:center; margin-bottom: 20px; }
nav a { margin: 0 10px; text-decoration: none; color: #000; font-weight: bold; }
nav a:hover { text-decoration: underline; }

.gallery-container {
  background: rgba(255, 255, 255, 0.85);
  border-radius: 15px;
  padding: 20px;
  max-width: 1200px;
  margin: 30px auto;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

h3.section-title {
  font-size: 1.5rem;
  margin-top: 0;
  padding: 10px 0;
  border-bottom: 2px solid rgba(0,0,0,0.1);
}

/* Masonry-style collage */
.gallery {
  column-count: 4;
  column-gap: 12px;
}

.gallery img {
  width: 100%;
  margin-bottom: 12px;
  border-radius: 8px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.15);
  transition: transform 0.2s ease-in-out;
  cursor: pointer;
  display: block;
}

.gallery img:hover { transform: scale(1.05); }

/* Lightbox */
.lightbox {
  display: none;
  position: fixed;
  z-index: 9999;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.9);
  justify-content: center;
  align-items: center;
  flex-direction: column;
  padding: 10px;
}

.lightbox img {
  max-width: 90%;
  max-height: 85vh;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.5);
  display: none;
}

.lightbox .nav-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  font-size: 2.5rem;
  color: white;
  cursor: pointer;
  user-select: none;
  padding: 10px;
}

.lightbox .prev { left: 10px; }
.lightbox .next { right: 10px; }

.lightbox .close {
  position: absolute;
  top: 10px; right: 15px;
  font-size: 2rem;
  color: white;
  cursor: pointer;
}

.lightbox .spinner {
  position: absolute;
  top: 50%; left: 50%;
  transform: translate(-50%, -50%);
  border: 4px solid rgba(255,255,255,0.3);
  border-top: 4px solid #fff;
  border-radius: 50%;
  width: 40px;
  height: 40px;
  animation: spin 1s linear infinite;
  display: none;
  z-index: 10000;
}

@keyframes spin {
  from { transform: translate(-50%, -50%) rotate(0deg); }
  to { transform: translate(-50%, -50%) rotate(360deg); }
}

/* Responsive */
@media (max-width: 1200px) { .gallery { column-count: 3; } }
@media (max-width: 900px) { .gallery { column-count: 2; } }
@media (max-width: 600px) { .gallery { column-count: 1; } }
</style>

<h2>Gallery</h2>
<nav>
  <a href="#play">Play</a>
  <a href="#wander">Wander</a>
  <a href="#eat">Eat</a>
</nav>

{% assign gallery = "
Play|https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=4000&height=1868,https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=4000&height=3000,https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868;
Wander|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=3920&height=2204,https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=3590&height=2161,https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=3920&height=2204;
Eat|https://1drv.ms/i/c/6118ddcb5316a0a9/IQTgk1I9SwuXRbePfpaC8skMAcVdtaUvncNSxhuh9wP3L5g?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQTgk1I9SwuXRbePfpaC8skMAcVdtaUvncNSxhuh9wP3L5g?width=4000&height=3000
" | split: ";" %}

{% for section in gallery %}
  {% assign parts = section | split: "|" %}
  {% assign sec_name = parts[0] %}
  {% assign imgs = parts[1] | split: "," %}
  <div id="{{ sec_name }}" class="gallery-container">
    <h3 class="section-title">{{ sec_name | capitalize }}</h3>
    <div class="gallery">
      {% for img_pair in imgs %}
        {% assign pair = img_pair | split: "|" %}
        <img src="{{ pair[0] }}" data-full="{{ pair[1] }}" alt="{{ sec_name }} image" loading="eager">
      {% endfor %}
    </div>
    <div class="lightbox">
      <span class="close">✖</span>
      <span class="nav-arrow prev">⟨</span>
      <div class="spinner"></div>
      <img src="">
      <span class="nav-arrow next">⟩</span>
    </div>
  </div>
{% endfor %}

<script>
// Preload full-size images
window.addEventListener('load', () => {
  document.querySelectorAll('.gallery img').forEach(img => {
    const fullSrc = img.dataset.full;
    if (fullSrc) {
      const preload = new Image();
      preload.src = fullSrc;
    }
  });
});

// Lightbox functionality
document.querySelectorAll('.gallery-container').forEach(container => {
  const images = container.querySelectorAll('.gallery img');
  const lightbox = container.querySelector('.lightbox');
  const lightboxImg = lightbox.querySelector('img');
  const closeBtn = lightbox.querySelector('.close');
  const prevBtn = lightbox.querySelector('.prev');
  const nextBtn = lightbox.querySelector('.next');
  const spinner = lightbox.querySelector('.spinner');
  let currentIndex = 0;

  function showImage(index) {
    currentIndex = index;
    spinner.style.display = 'block';
    lightboxImg.style.display = 'none';
    lightbox.style.display = 'flex';
    document.body.style.overflow = 'hidden';

    const fullSrc = images[currentIndex].dataset.full;
    const tempImg = new Image();
    tempImg.src = fullSrc;
    tempImg.onload = () => {
      lightboxImg.src = fullSrc;
      spinner.style.display = 'none';
      lightboxImg.style.display = 'block';
    };
  }

  function hideLightbox() {
    lightbox.style.display = 'none';
    document.body.style.overflow = '';
  }

  images.forEach((img, index) => img.addEventListener('click', () => showImage(index)));
  closeBtn.addEventListener('click', hideLightbox);
  prevBtn.addEventListener('click', e => { e.stopPropagation(); showImage((currentIndex - 1 + images.length) % images.length); });
  nextBtn.addEventListener('click', e => { e.stopPropagation(); showImage((currentIndex + 1) % images.length); });

  lightbox.addEventListener('click', e => { if (e.target === lightbox) hideLightbox(); });
  document.addEventListener('keydown', e => {
    if (lightbox.style.display === 'flex') {
      if (e.key === 'Escape') hideLightbox();
      if (e.key === 'ArrowLeft') showImage((currentIndex - 1 + images.length) % images.length);
      if (e.key === 'ArrowRight') showImage((currentIndex + 1) % images.length);
    }
  });
});
</script>
