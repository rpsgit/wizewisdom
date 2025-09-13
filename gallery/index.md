---
layout: default
title: Image Gallery
---

<h2 style="text-align:center;">📸 Gallery</h2>

<!-- Navigation Links -->
<nav style="text-align:center; margin-bottom: 20px;">
  <a href="#leisure" style="margin: 0 10px;">Leisure</a>
  <a href="#adventure" style="margin: 0 10px;">Adventures</a>
  <a href="#eatable" style="margin: 0 10px;">Eatables</a>
</nav>

<style>
  body {
    font-family: Arial, sans-serif;
    background-size: cover;
    background-position: center;
    padding: 20px;
  }

  .gallery-container {
    background: rgba(255, 255, 255, 0.7);
    border-radius: 15px;
    padding: 20px;
    max-width: 1100px;
    margin: 30px auto;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  }

  h3.section-title {
    text-align: left;
    margin-top: 0;
    font-size: 1.5rem;
    padding: 10px 0;
    border-bottom: 2px solid rgba(0,0,0,0.1);
  }

  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 15px;
    margin-top: 15px;
  }

  .gallery img {
    width: 100%;
    height: auto;
    border-radius: 12px;
    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);
    transition: transform 0.2s ease-in-out;
    cursor: pointer;
  }

  .gallery img:hover {
    transform: scale(1.05);
  }

  .lightbox {
    display: none;
    position: fixed;
    z-index: 9999;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.9);
    justify-content: center;
    align-items: center;
    flex-direction: column;
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
    font-size: 3rem;
    color: white;
    cursor: pointer;
    user-select: none;
    padding: 10px;
  }

  .lightbox .prev { left: 20px; }
  .lightbox .next { right: 20px; }

  .lightbox .close {
    position: absolute;
    top: 20px;
    right: 30px;
    font-size: 2rem;
    color: white;
    cursor: pointer;
  }
</style>

<!-- Leisure Section -->
<div id="leisure" class="gallery-container">
  <h3 class="section-title">Leisure</h3>
  <div class="gallery">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=4000&height=1868" 
         alt="Leisure 1" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=4000&height=3000" 
         alt="Leisure 2" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868" 
         alt="Leisure 3" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQREnYJzOGG5QKFqR0lI4V5yASEgyRuybjwEAGRATwiGhfs?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQREnYJzOGG5QKFqR0lI4V5yASEgyRuybjwEAGRATwiGhfs?width=4000&height=1868" 
         alt="Leisure 4" loading="lazy">
  </div>
  <div class="lightbox">
    <span class="close">✖</span>
    <span class="nav-arrow prev">⟨</span>
    <img src="">
    <span class="nav-arrow next">⟩</span>
  </div>
</div>

<!-- Adventure Section -->
<div id="adventure" class="gallery-container">
  <h3 class="section-title">Adventures</h3>
  <div class="gallery">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=3920&height=2204" 
         alt="Adventure 1" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=3590&height=2161" 
         alt="Adventure 2" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=3920&height=2204" 
         alt="Adventure 3" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRn6TIri6CAS503qbdNEv6-AdoQRGifJjddtn_LDIafIOc?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRn6TIri6CAS503qbdNEv6-AdoQRGifJjddtn_LDIafIOc?width=3887&height=2521" 
         alt="Adventure 4" loading="lazy">
  </div>
  <div class="lightbox">
    <span class="close">✖</span>
    <span class="nav-arrow prev">⟨</span>
    <img src="">
    <span class="nav-arrow next">⟩</span>
  </div>
</div>

<!-- Eatable Section -->
<div id="eatable" class="gallery-container">
  <h3 class="section-title">Eatables</h3>
  <div class="gallery">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTgk1I9SwuXRbePfpaC8skMAcVdtaUvncNSxhuh9wP3L5g?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTgk1I9SwuXRbePfpaC8skMAcVdtaUvncNSxhuh9wP3L5g?width=4000&height=3000" 
         alt="Eatable 1" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTFvXL2gU83TqpsZL-d0e5_AZ1SY8k0MBJJYJmRJO7vqqQ?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTFvXL2gU83TqpsZL-d0e5_AZ1SY8k0MBJJYJmRJO7vqqQ?width=4000&height=1868" 
         alt="Eatable 2" loading="lazy">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRtitNAvF0jT6TzVPkIqTlsAQ3Lvvd8zY4YN54G_a71VNU?width=400" 
         data-full="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRtitNAvF0jT6TzVPkIqTlsAQ3Lvvd8zY4YN54G_a71VNU?width=4000&height=1868" 
         alt="Eatable 3" loading="lazy">
  </div>
  <div class="lightbox">
    <span class="close">✖</span>
    <span class="nav-arrow prev">⟨</span>
    <img src="">
    <span class="nav-arrow next">⟩</span>
  </div>
</div>

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
      if(e.key==='ArrowLeft') currentIndex=(currentIndex-1+images.length)%images.length, showImage(currentIndex);
      if(e.key==='ArrowRight') currentIndex=(currentIndex+1)%images.length, showImage(currentIndex);
    }
  });
});
</script>
