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

  /* Container for translucent background */
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

  /* Gallery grid */
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
    flex-direction: column;
  }

  .lightbox img {
    max-width: 90%;
    max-height: 80%;
    border-radius: 12px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.5);
  }

  /* Navigation arrows */
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

  .lightbox .prev {
    left: 20px;
  }

  .lightbox .next {
    right: 20px;
  }

  /* Close button */
  .lightbox .close {
    position: absolute;
    top: 20px;
    right: 30px;
    font-size: 2rem;
    color: white;
    cursor: pointer;
  }
</style>

<!-- Section 1 -->
<div id="leisure" class="gallery-container">
  <h3 class="section-title">Leisure</h3>
  <div class="gallery">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=4000&height=1868" alt="Photo 1">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQdhWxz9pXQYGqN64XY2mCAfWR0tWHTOh03quOpKk04SE?width=4000&height=3000" alt="Photo 2">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAMNKPCLSYTaE5vnCNgTWgAQ20oxXfsyUQA0apry-PI-w?width=4000&height=1868" alt="Photo 3">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQREnYJzOGG5QKFqR0lI4V5yASEgyRuybjwEAGRATwiGhfs?width=4000&height=1868" alt="Photo 4">
        <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQHljFCCJ6xRaTiSmlcb3AiAd5iaK7v4b2_2-1bzWsgtho?width=4000&height=3000" alt="Photo 5">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRAofI0-AnUTKpqNUoQ48lFAd8HzeDD-BWuiC5c8d4-hJk?width=4000&height=3000" alt="Photo 6">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQZjtGUJtUmSYnkoGskWQCBAQYfs87CMYLADBfw6c1KwHk?width=4000&height=3000" alt="Photo 7">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQhrBvnTbbRTa4mrzzlL2WqASPvdoV-cAvS0tqiXoF_uBQ?width=4000&height=3000" alt="Photo 8">
  </div>
  <div class="lightbox">
    <span class="close">✖</span>
    <span class="nav-arrow prev">⟨</span>
    <img src="">
    <span class="nav-arrow next">⟩</span>
  </div>
</div>

<!-- Section 2 -->
<div id="adventure" class="gallery-container">
  <h3 class="section-title">Adventures</h3>
  <div class="gallery">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtMLVRdoUvSbYfz9tnV3iBAezWbN4sS2aV5JbKANjFQoo?width=3920&height=2204" width="3920" height="2204" alt="Photo 1">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQvIkPTK9UsTYQO1WcaYIA_AQujOHWcHwTIO4wJHnYXib8?width=3590&height=2161" width="3590" height="2161" alt="Photo 2">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSqEIPFgZ7_QqAxIav70E7TAU7EkbuOVCkXAogyim6y3x4?width=3920&height=2204" width="3920" height="2204" alt="Photo 3">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRn6TIri6CAS503qbdNEv6-AdoQRGifJjddtn_LDIafIOc?width=3887&height=2521" width="3887" height="2521" alt="Photo 4">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQgIH2KQCOvTIMgoCjXKTwuATEOtRc4BwnT_cPsUH_Bmy8?width=4096&height=2730" width="4096" height="2730" alt="Photo 5">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRQg5mjpKuZSrcoRuau1IWJAdwX1s54jbIdVov9hE5cvww?width=4096&height=2730" width="4096" height="2730" alt="Photo 6">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSUzRT3AQd3RYayjlz3ms-wAVmjNHXI2LNq0kFbY7IhGNA?width=4096&height=2730" width="4096" height="2730" alt="Photo 7">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSjE29sFm3NRqk51sVV_ZOEAeKSy27yLJZCN1_smw6ORlI?width=4096&height=2730" width="4096" height="2730" alt="Photo 8">
  </div>
  <div class="lightbox">
    <span class="close">✖</span>
    <span class="nav-arrow prev">⟨</span>
    <img src="">
    <span class="nav-arrow next">⟩</span>
  </div>
</div>

<!-- Section 3 -->
<div id="eatable" class="gallery-container">
  <h3 class="section-title">Eatables</h3>
  <div class="gallery">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTgk1I9SwuXRbePfpaC8skMAcVdtaUvncNSxhuh9wP3L5g?width=4000&height=3000" alt="Photo 1">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTFvXL2gU83TqpsZL-d0e5_AZ1SY8k0MBJJYJmRJO7vqqQ?width=4000&height=1868" alt="Photo 2">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRtitNAvF0jT6TzVPkIqTlsAQ3Lvvd8zY4YN54G_a71VNU?width=4000&height=1868" alt="Photo 3">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQtq9aZVhVSSbhPJISxICYsAbpF6gCQkA6_yuVQKfMjMgg?width=4032&height=2268" alt="Photo 4">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQj-3t9zzCpQY6NX4EoUHbzAXfwhk4L3qIIa6x-LgnFQQA?width=4032&height=1908" alt="Photo 5">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRXz-3NuIFHQajUVuA9CfniAch43FTP_iwIp12GfmmsyGE?width=2048&height=1536" alt="Photo 6">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSOardx2EZRTLY_X7-H3Rl4AVrnu8fnNhaMfnGlBlXjGvw?width=0&height=" alt="Photo 7">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQR-WGP4YU7uSpHBYyfV3ROLAYlbwtE5X-q2v1aG7pRP7JA?width=0&height=" alt="Photo 8">
    <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQRsEHuCoyTNS66LrIczUUC3AZ8mY9pHqsCCDFK1pW6YxvY?width=608&height=960" alt="Photo 9">

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
      lightboxImg.src = images[currentIndex].src;
      lightbox.style.display = 'flex';
      document.body.style.overflow = 'hidden'; // prevent background scroll
    }

    function hideLightbox() {
      lightbox.style.display = 'none';
      document.body.style.overflow = ''; 
    }

    images.forEach((img, index) => {
      img.addEventListener('click', () => showImage(index));
    });

    closeBtn.addEventListener('click', hideLightbox);

    prevBtn.addEventListener('click', e => {
      e.stopPropagation();
      currentIndex = (currentIndex - 1 + images.length) % images.length;
      showImage(currentIndex);
    });

    nextBtn.addEventListener('click', e => {
      e.stopPropagation();
      currentIndex = (currentIndex + 1) % images.length;
      showImage(currentIndex);
    });

    // Close when clicking outside the image
    lightbox.addEventListener('click', e => {
      if (e.target === lightbox) hideLightbox();
    });

    // Keyboard navigation
    document.addEventListener('keydown', e => {
      if (lightbox.style.display === 'flex') {
        if (e.key === 'Escape') hideLightbox();
        if (e.key === 'ArrowLeft') currentIndex = (currentIndex - 1 + images.length) % images.length, showImage(currentIndex);
        if (e.key === 'ArrowRight') currentIndex = (currentIndex + 1) % images.length, showImage(currentIndex);
      }
    });
  });
</script>
