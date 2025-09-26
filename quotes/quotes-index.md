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

  #latest-image img, .gallery img {
    width: 100%;
    border-radius: 15px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.2);
    transition: transform 0.3s ease;
  }

  #latest-image img:hover, .gallery img:hover {
    transform: scale(1.02);
  }

  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 15px;
    margin-top: 30px;
  }

  .gallery img {
    height: 140px;
    object-fit: cover;
  }

  @media (max-width: 768px) {
    .content-box { padding: 25px; }
    h1 { font-size: 2rem; }
    .gallery img { height: 120px; }
  }
</style>

<div class="content-box">
  <h1>Quotes</h1>
  <div id="latest-image"></div>
  <div class="gallery" id="gallery"></div>
</div>

<script>
  const username = "rpsgit";
  const repo = "wizewisdom";
  const branch = "main";
  const folder = "assets/images/quotes";

  const apiUrl = `https://api.github.com/repos/${username}/${repo}/contents/${folder}?ref=${branch}`;
  const gallery = document.getElementById("gallery");
  const latestImageDiv = document.getElementById("latest-image");

  fetch(apiUrl)
    .then(res => res.json())
    .then(files => {
      const imageFiles = files.filter(f => f.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(f.name));
      imageFiles.sort((a, b) => a.name.localeCompare(b.name, undefined, { numeric: true, sensitivity: 'base' }));
      const images = imageFiles.map(f => `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${f.name}`);

      if (images.length > 0) {
        // Show latest quote at the top
        const latest = document.createElement("img");
        latest.src = images[0];
        latest.alt = imageFiles[0].name;
        latestImageDiv.appendChild(latest);
      }

      // Show remaining quotes in the gallery
      images.slice(1).forEach((url, i) => {
        const img = document.createElement("img");
        img.src = url;
        img.alt = imageFiles[i+1].name;
        gallery.appendChild(img);
      });
    })
    .catch(err => {
      gallery.innerHTML = "<p>⚠️ Could not load quotes.</p>";
      console.error(err);
    });
</script>
