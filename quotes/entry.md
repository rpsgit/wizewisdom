---
layout: default
title: Quotes
---

# Quotes

<div class="gallery" id="gallery"></div>

<!-- Modal for full-size view -->
<div id="imgModal" class="modal">
  <span class="close">&times;</span>
  <img class="modal-content" id="modalImg">
  <div id="caption"></div>
</div>

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
    cursor: pointer;
    transition: transform 0.2s;
  }
  .gallery img:hover {
    transform: scale(1.05);
  }

  /* Modal styles */
  .modal {
    display: none;
    position: fixed;
    z-index: 9999;
    padding-top: 60px;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    overflow: auto;
    background-color: rgba(0,0,0,0.9);
  }
  .modal-content {
    display: block;
    margin: auto;
    max-width: 90%;
    max-height: 80vh;
    border-radius: 10px;
  }
  #caption {
    margin: 15px auto;
    text-align: center;
    color: #ccc;
    font-size: 18px;
  }
  .close {
    position: absolute;
    top: 15px;
    right: 30px;
    color: #fff;
    font-size: 40px;
    font-weight: bold;
    cursor: pointer;
    transition: color 0.3s;
  }
  .close:hover {
    color: #f00;
  }
</style>

<script>
  const username = "rpsgit";       
  const repo = "wizewisdom";       
  const branch = "main";           
  const folder = "assets/images";  

  const apiUrl = `https://api.github.com/repos/${username}/${repo}/contents/${folder}?ref=${branch}`;
  const gallery = document.getElementById("gallery");

  fetch(apiUrl)
    .then(response => response.json())
    .then(files => {
      // Sort filenames in descending order
      files.sort((a, b) => b.name.localeCompare(a.name));

      files.forEach(file => {
        if (file.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(file.name)) {
          const img = document.createElement("img");
          img.src = `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${file.name}`;
          img.alt = file.name;

          // Add click event to open modal
          img.addEventListener("click", () => openModal(img.src, img.alt));
          gallery.appendChild(img);
        }
      });
    })
    .catch(error => {
      gallery.innerHTML = "<p>⚠️ Could not load images. Check repo settings.</p>";
      console.error("Error loading images:", error);
    });

  // Modal logic
  const modal = document.getElementById("imgModal");
  const modalImg = document.getElementById("modalImg");
  const captionText = document.getElementById("caption");
  const closeBtn = document.getElementsByClassName("close")[0];

  function openModal(src, alt) {
    modal.style.display = "block";
    modalImg.src = src;
    captionText.innerHTML = alt;
  }

  closeBtn.onclick = function() {
    modal.style.display = "none";
  }

  modal.onclick = function(e) {
    if (e.target === modal) {
      modal.style.display = "none";
    }
  }

  document.addEventListener("keydown", function(e) {
    if (e.key === "Escape") {
      modal.style.display = "none";
    }
  });
</script>
