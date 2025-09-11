---
layout: default
title: Image Gallery
---

<h2 style="text-align:center;">📸 Gallery</h2>

<style>
  body {
    font-family: Arial, sans-serif;
    background: #f7f7f7;
    padding: 20px;
  }

  /* Gallery grid */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
    gap: 15px;
    max-width: 1000px;
    margin: auto;
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

<div class="gallery">
  <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/EXr5D-UN5OBMvUTGkze6Qr4B2ONYjI8klBh0Bnvku15YQg?e=b373Ll" alt="Photo 1">
  <img src="https://onedrive.live.com/embed?resid=ABC123XYZ456!102&width=1024&height=768&cropmode=none" alt="Photo 2">
  <img src="https://onedrive.live.com/embed?resid=ABC123XYZ456!103&width=1024&height=768&cropmode=none" alt="Photo 3">
  <!-- Add more <img> lines here -->
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
