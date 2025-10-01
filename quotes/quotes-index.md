---
layout: default
title: Quotes
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/quotes-index.png') no-repeat center center fixed;
    background-size: cover;
    font-family: Arial, sans-serif;
  }

  .content-box {
    max-width: 1000px;
    margin: 40px auto;
    background: rgba(255, 255, 255, 0.7);
    padding: 40px;
    border-radius: 20px;
    box-shadow: 0 6px 20px rgba(0,0,0,0.25);
  }

  h1 {
    text-align: center;
    color: #000;
    font-size: 2.4rem;
    margin-bottom: 30px;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
  }

  /* Latest (featured) image */
  #latest-image img {
    width: 100%;
    height: auto;
    max-height: 600px; /* keep it elegant on large screens */
    border-radius: 20px;
    box-shadow: 0 8px 24px rgba(0,0,0,0.3);
    margin-bottom: 40px;
    cursor: pointer;
    transition: transform 0.3s ease;
  }

  #latest-image img:hover {
    transform: scale(1.04);
  }

  /* Gallery thumbnails */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 15px;
    margin-top: 10px;
  }

  .gallery img {
    width: 100%;
    height: 160px;
    object-fit: cover;
    border-radius: 15px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.2);
    cursor: pointer;
    transition: transform 0.3s ease;
  }

  .gallery img:hover {
    transform: scale(1.03);
  }

  /* Modal (fullscreen view) */
  .modal {
    display: none;
    position: fixed;
    z-index: 1000;
    padding: 20px;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background: rgba(0,0,0,0.85);
    justify-content: center;
    align-items: center;
  }

  .modal img {
    max-width: 95%;
    max-height: 90%;
    border-radius: 12px;
    box-shadow: 0 8px 30px rgba(0,0,0,0.5);
  }

  .modal-close {
    position: absolute;
    top: 20px;
    right: 30px;
    font-size: 2rem;
    color: #fff;
    cursor: pointer;
  }

  /* Mobile view: show all full images stacked */
  @media (max-width: 768px) {
    .content-box { padding: 25px; }
    h1 { font-size: 2rem; }

    #latest-image img {
      max-height: none; /* no height restriction */
    }

    .gallery {
      display: block; /* stack images */
    }

    .gallery img {
      width: 100%;
      height: auto;   /* no cropping */
      margin-bottom: 20px;
      object-fit: contain;
    }
  }
</style>

<div class="content-box">
  <h1>Quotes</h1>
  <div id="latest-image"></div>
  <div class="gallery" id="gallery"></div>
</div>

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

      // Sort descending (newest first by name)
      imageFiles.sort((a, b) => b.name.localeCompare(a.name, undefined, { numeric: true, sensitivity: 'base' }));

      const images = imageFiles.map(f => `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${f.name}`);

      if (images.length > 0) {
        // Show latest quote at the top (featured)
        const latest = document.createElement("img");
        latest.src = images[0];
        latest.alt = imageFiles[0].name;
        latest.onclick = () => openModal(latest.src);
        latestImageDiv.appendChild(latest);
      }

      // Show remaining quotes in the gallery
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
