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
  max-width: 1100px;
  margin: 30px auto;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}

h3.section-title {
  font-size: 1.5rem;
  margin-top: 0;
  padding: 10px 0;
  border-bottom: 2px solid rgba(0,0,0,0.1);
}

.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  gap: 12px;
  margin-top: 15px;
}

.gallery img {
  width: 100%;
  height: auto;
  border-radius: 12px;
  box-shadow: 0 2px 6px rgba(0,0,0,0.15);
  transition: transform 0.2s ease-in-out;
  cursor: pointer;
  object-fit: cover;
}
.gallery img:hover { transform: scale(1.05); }

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
  max-height: 80%;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.5);
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

@media (max-width: 768px){
  .gallery { grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap: 8px; }
  .lightbox .nav-arrow { font-size: 2rem; }
  .lightbox .close { font-size: 1.5rem; }
}
</style>

<h2>Gallery</h2>
<nav>
  <a href="#play">Play</a>
  <a href="#wander">Wander</a>
  <a href="#eat">Eat</a>
</nav>

<!-- Helper function to generate sections -->
{% assign sections = 
  "play,https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=4000&height=1868,https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=4000&height=3000,https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868,
   wander,https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=3920&height=2204,https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=3590&height=2161,https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=3920&height=2204,
   eat,https://1drv.ms/i/c/6118ddcb5316a0a9/IQTgk1I9SwuXRbePfpaC8skMAcVdtaUvncNSxhuh9wP3L5g?width=400|https://1drv.ms/i/c/6118ddcb5316a0a9/IQTgk1I9SwuXRbePfpaC8skMAcVdtaUvncNSxhuh9wP3L5g?width=4000&height=3000
" | split: "," %}

{% assign sec_index = 0 %}
{% while sec_index < sections.size %}
  {% assign sec_name = sections[sec_index] %}
  {% assign sec_index = sec_index | plus: 1 %}
  <div id="{{sec_name}}" class="gallery-container">
    <h3 class="section-title">{{ sec_name | capitalize }}</h3>
    <div class="gallery">
      {% assign imgs = sections[sec_index] | split: "," %}
      {% for img_pair in imgs %}
        {% assign pair = img_pair | split: "|" %}
        <img loading="lazy" src="{{ pair[0] }}" data-full="{{ pair[1] }}" alt="{{ sec_name }} image">
      {% endfor %}
    </div>
    <div class="lightbox">
      <span class="close">✖</span>
      <span class="nav-arrow prev">⟨</span>
      <img src="">
      <span class="nav-arrow next">⟩</span>
    </div>
  </div>
  {% assign sec_index = sec_index | plus: 1 %}
{% endwhile %}

<script>
document.querySelectorAll('.gallery-container').forEach(container => {
  const images = container.querySelectorAll('.gallery img');
  const lightbox = container.querySelector('.lightbox');
  const lightboxImg = lightbox.querySelector('img');
  const closeBtn = lightbox.querySelector('.close');
  const prevBtn = lightbox.querySelector('.prev');
  const nextBtn = lightbox.querySelector('.next');
  let currentIndex = 0;

  function showImage(index) {
    currentIndex = index;
    lightboxImg.src = images[currentIndex].dataset.full;
    lightbox.style.display = 'flex';
    document.body.style.overflow = 'hidden';
  }

  function hideLightbox() {
    lightbox.style.display = 'none';
    document.body.style.overflow = '';
  }

  images.forEach((img, index) => img.addEventListener('click', () => showImage(index)));
  closeBtn.addEventListener('click', hideLightbox);
  prevBtn.addEventListener('click', e => { e.stopPropagation(); currentIndex = (currentIndex - 1 + images.length) % images.length; showImage(currentIndex); });
  nextBtn.addEventListener('click', e => { e.stopPropagation(); currentIndex = (currentIndex + 1) % images.length; showImage(currentIndex); });

  lightbox.addEventListener('click', e => { if(e.target===lightbox) hideLightbox(); });
  document.addEventListener('keydown', e => {
    if(lightbox.style.display==='flex'){
      if(e.key==='Escape') hideLightbox();
      if(e.key==='ArrowLeft') { currentIndex = (currentIndex - 1 + images.length) % images.length; showImage(currentIndex); }
      if(e.key==='ArrowRight') { currentIndex = (currentIndex + 1) % images.length; showImage(currentIndex); }
    }
  });
});
</script>
