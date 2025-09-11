---
layout: default
title: Image Gallery
---

<h2 style="text-align:center;">📸 Gallery</h2>

<style>
  body {
    font-family: Arial, sans-serif;
    background-size: cover;
    background-position: center;
    padding: 20px;
  }

  /* Container for translucent background */
  .gallery-container {
    background: rgba(255, 255, 255, 0.7); /* 70% white */
    border-radius: 15px;
    padding: 20px;
    max-width: 1100px;
    margin: 20px auto;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  }

  /* Gallery grid */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 15px;
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

  /* Lightbox overlay */
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
  }

  .lightbox img {
    max-width: 90%;
    max-height: 80%;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.5);
  }

  /* Close button */
  .lightbox:after {
    content: "✖";
    position: absolute;
    top: 20px;
    right: 30px;
    font-size: 2rem;
    color: white;
    cursor: pointer;
  }
</style>

<div class="gallery-container">
  <div class="gallery">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=4000&height=1868" width="4000" height="1868" alt="Photo 1">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=4000&height=3000" width="4000" height="3000" alt="Photo 2">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868" width="4000" height="1868" alt="Photo 3">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQREnYJzOGG5QKFqR0lI4V5yASEgyRuybjwEAGRATwiGhfs?width=4000&height=1868" width="4000" height="1868" alt="Photo 4">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQHljFCCJ6xRaTiSmlcb3AiAd5iaK7v4b2_2-1bzWsgtho?width=4000&height=3000" width="4000" height="3000" alt="Photo 5">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAofI0-AnUTKpqNUoQ48lFAd8HzeDD-BWuiC5c8d4-hJk?width=4000&height=3000" width="4000" height="3000" alt="Photo 6">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQZjtGUJtUmSYnkoGskWQCBAQYfs87CMYLADBfw6c1KwHk?width=4000&height=3000" width="4000" height="3000" alt="Photo 7">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQhrBvnTbbRTa4mrzzlL2WqASPvdoV-cAvS0tqiXoF_uBQ?width=4000&height=3000" width="4000" height="3000" alt="Photo 8">
  </div>
</div>

<!-- Lightbox -->
<div class="lightbox" id="lightbox">
  <img id="lightbox-img" src="">
</div>

<script>
  const galleryImages = document.querySelectorAll('.gallery img');
  const lightbox = document.getElementById('lightbox');
  const lightboxImg = document.getElementById('lightbox-img');

  galleryImages.forEach(img => {
    img.addEventListener('click', () => {
      lightboxImg.src = img.src;
      lightbox.style.display = 'flex';
    });
  });

  // Close when clicking outside or on the ✖
  lightbox.addEventListener('click', () => {
    lightbox.style.display = 'none';
  });
</script>
