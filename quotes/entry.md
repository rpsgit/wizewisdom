---
layout: default
title: Quotes
---

# Quotes

<div class="gallery" id="gallery"></div>

<style>
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 15px;
    padding: 20px;
    max-width: 1200px;
    margin: auto;
  }
  .gallery img {
    width: 100%;
    height: auto;
    border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    transition: transform 0.2s;
  }
  .gallery img:hover {
    transform: scale(1.05);
  }
</style>

<script>
  const username = "rpsgit";       // your GitHub username
  const repo = "wizewisdom";       // your repo name
  const branch = "main";           // usually 'main' or 'master'
  const folder = "assets/images";  // folder path in repo (NO leading /)

  const apiUrl = `https://api.github.com/repos/${username}/${repo}/contents/${folder}?ref=${branch}`;
  const gallery = document.getElementById("gallery");

  fetch(apiUrl)
    .then(response => response.json())
    .then(files => {
      files.forEach(file => {
        if (file.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(file.name)) {
          const img = document.createElement("img");
          img.src = `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${file.name}`;
          img.alt = file.name;
          gallery.appendChild(img);
        }
      });
    })
    .catch(error => {
      gallery.innerHTML = "<p>⚠️ Could not load images. Check repo settings.</p>";
      console.error("Error loading images:", error);
    });
</script>
