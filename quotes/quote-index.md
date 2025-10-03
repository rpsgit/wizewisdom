---
layout: default
title: Quotes
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/nerdvana-bg.png') no-repeat center center fixed;
    background-size: cover;
    font-family: Arial, sans-serif;
  }

  /* === HOME BUTTON === */
  .home-button {
    position: fixed;
    top: 20px;
    left: 20px;
    width: 40px;
    height: 40px;
    z-index: 1000;
    text-decoration: none;
  }

  .home-icon {
    width: 100%;
    height: 100%;
    display: block;
    background: url('/assets/images/home-icon.png') no-repeat center center;
    background-size: contain;
  }

  /* Page Title */
  h1 {
    text-align: center;
    color: #000;
    font-size: 2.4rem;
    margin: 60px auto 30px;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
  }

  /* Featured (latest) image */
  #latest-image img {
    display: block;
    max-width: 100%;
    height: auto;           /* keeps aspect ratio */
    max-height: 600px;      /* prevents overly tall images */
    margin: 0 auto 40px;
    border-radius: 20px;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    cursor: pointer;
    transition: transform 0.3s ease;
    object-fit: contain;    /* ensures no stretch/crop */
  }

  #latest-image img:hover {
    transform: scale(1.04);
  }

  /* Gallery thumbnails - square */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 15px;
    margin: 0 auto 40px;
    max-width: 1000px;
    padding: 0 20px;
  }

  .gallery img {
    width: 100%;
    aspect-ratio: 1 / 1; /* square thumbnails */
    object-fit: cover;
    border-radius: 15px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.2);
    cursor: pointer;
    transition: transform 0.3s ease;
  }

  .gallery img:hover {
    transform: scale(1.03);
  }

  /* Modal for enlarged image */
  .modal {
    display: none;
    position: fixed;
    z-index: 2000;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.85);
    justify-content: center;
    align-items: center;
    padding: 20px;
  }

  .modal img {
    max-width: 95%;
    max-height: 90%;
    height: auto;          /* natural proportions */
    width: auto;           /* natural proportions */
    border-radius: 12px;
    box-shadow: 0 8px 30px rgba(0,0,0,0.5);
    object-fit: contain;   /* ensures no distortion */
  }

  .modal-close {
    position: absolute;
    top: 20px;
    right: 30px;
    font-size: 2rem;
    color: #fff;
    cursor: pointer;
  }

  /* Mobile responsiveness */
  @media (max-width: 768px) {
    h1 { font-size: 2rem; }
    #latest-image img { max-height: none; }
    .gallery { grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); }
  }

  @media (max-width: 480px) {
    .gallery {
      grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
      gap: 10px;
    }
  }
</style>

<!-- Home Button -->
<a href="https://www.wizewisdom.com/" class="home-button">
  <span class="home-icon"></span>
</a>

<h1>Quotes</h1>
<div id="latest-image"></div>
<div class="gallery" id="gallery"></div>

<!-- Modal for enlarged image -->
<div class="modal" id="imageModal">
  <span class="modal-close" id="modalClose">&times;</span>
  <img id="modalImg" src="" alt="Enlarged view">
</div>

<script>
  const username = "rpsgit";
  const repo = "wizewisdom";
  const branch = "main";
  const folder = "assets/images/quotes";

  const apiUrl = `https://api.github.com/repos/${username}/${repo}/contents/${folder}?ref=${branch}`;
  const gallery = document.getElementById("gallery");
  const latestImageDiv = document.getElementById("latest-image");

  const modal = document.getElementById("imageModal");
  const modalImg = document.getElementById("modalImg");
  const modalClose = document.getElementById("modalClose");

  fetch(apiUrl)
    .then(res => res.json())
    .then(files => {
      const imageFiles = files.filter(f => f.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(f.name));

      // Sort newest first
      imageFiles.sort((a, b) => b.name.localeCompare(a.name, undefined, { numeric: true, sensitivity: 'base' }));

      const images = imageFiles.map(f => `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${f.name}`);

      if (images.length > 0) {
        // Featured image
        const latest = document.createElement("img");
        latest.src = images[0];
        latest.alt = imageFiles[0].name;
        latest.onclick = () => openModal(latest.src);
        latestImageDiv.appendChild(latest);
      }

      // Gallery images
      images.slice(1).forEach((url, i) => {
        const img = document.createElement("img");
        img.src = url;
        img.alt = imageFiles[i+1].name;
        img.onclick = () => openModal(url);
        gallery.appendChild(img);
      });
    })
    .catch(err => {
      gallery.innerHTML = "<p>⚠️ Could not load quotes.</p>";
      console.error(err);
    });

  function openModal(src) {
    modal.style.display = "flex";
    modalImg.src = src;
  }

  modalClose.onclick = () => { modal.style.display = "none"; }
  modal.onclick = (e) => { if (e.target === modal) modal.style.display = "none"; }
</script>
