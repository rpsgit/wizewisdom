---
layout: default
title: Quotes
---

# Quotes

<div id="latest-image"></div>
<div class="gallery" id="gallery"></div>

<!-- Modal for full-size view -->
<div id="imgModal" class="modal">
  <span class="close">&times;</span>
  <span class="prev">&#10094;</span>
  <span class="next">&#10095;</span>
  <img class="modal-content" id="modalImg">
  <div id="caption"></div>

  <!-- Buttons -->
  <div class="modal-actions">
    <a id="downloadBtn" download class="download-btn">⬇ Download</a>
    <button id="shareBtn" class="share-btn">🔗 Share</button>
  </div>
</div>

<style>
  /* Latest image styling */
  #latest-image img {
    width: 100%;
    height: auto;
    max-height: 70vh;
    object-fit: contain;
    border-radius: 12px;
    margin-bottom: 30px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.15);
    cursor: pointer;
  }

  /* Gallery */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 15px;
    padding: 10px;
    max-width: 1200px;
    margin: auto;
  }
  .gallery img {
    width: 100%;
    height: 140px;
    object-fit: cover;
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
    overflow: hidden;
    background-color: rgba(0,0,0,0.9);
  }
  .modal-content {
    display: block;
    margin: auto;
    max-width: 90%;
    max-height: 80vh;
    border-radius: 10px;
    transition: transform 0.3s ease;
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
  .close:hover { color: #f00; }

  /* Arrows */
  .prev, .next {
    cursor: pointer;
    position: absolute;
    top: 50%;
    padding: 16px;
    color: white;
    font-weight: bold;
    font-size: 40px;
    transition: 0.3s;
    user-select: none;
  }
  .prev { left: 20px; }
  .next { right: 20px; }
  .prev:hover, .next:hover { color: #f00; }

  /* Action buttons (download + share) */
  .modal-actions {
    position: absolute;
    bottom: 40px;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    gap: 15px;
  }
  .download-btn, .share-btn {
    padding: 10px 18px;
    border-radius: 6px;
    font-size: 16px;
    font-weight: bold;
    text-decoration: none;
    cursor: pointer;
    transition: background 0.3s;
  }
  .download-btn {
    background: #28a745;
    color: white;
  }
  .download-btn:hover { background: #218838; }
  .share-btn {
    background: #007bff;
    color: white;
    border: none;
  }
  .share-btn:hover { background: #0069d9; }
</style>

<script>
  const username = "rpsgit";       
  const repo = "wizewisdom";       
  const branch = "main";           
  const folder = "assets/images";  

  const apiUrl = `https://api.github.com/repos/${username}/${repo}/contents/${folder}?ref=${branch}`;
  const gallery = document.getElementById("gallery");
  const latestImageDiv = document.getElementById("latest-image");

  let images = [];
  let currentIndex = 0;

  fetch(apiUrl)
    .then(response => response.json())
    .then(files => {
      files.sort((a, b) => b.name.localeCompare(a.name));
      files.forEach((file, index) => {
        if (file.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(file.name)) {
          const imgUrl = `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${file.name}`;
          images.push(imgUrl);

          const img = document.createElement("img");
          img.src = imgUrl;
          img.alt = file.name;
          img.addEventListener("click", () => openModal(index));

          if (index === 0) {
            latestImageDiv.appendChild(img);
          } else {
            gallery.appendChild(img);
          }
        }
      });
    })
    .catch(error => {
      gallery.innerHTML = "<p>⚠️ Could not load images. Check repo settings.</p>";
      console.error("Error loading images:", error);
    });

  const modal = document.getElementById("imgModal");
  const modalImg = document.getElementById("modalImg");
  const captionText = document.getElementById("caption");
  const closeBtn = document.getElementsByClassName("close")[0];
  const prevBtn = document.querySelector(".prev");
  const nextBtn = document.querySelector(".next");
  const downloadBtn = document.getElementById("downloadBtn");
  const shareBtn = document.getElementById("shareBtn");

  function openModal(index) {
    modal.style.display = "block";
    currentIndex = index;
    updateModalImage();
  }

  function updateModalImage() {
    modalImg.src = images[currentIndex];
    captionText.innerHTML = images[currentIndex].split("/").pop();
    downloadBtn.href = images[currentIndex];
  }

  closeBtn.onclick = () => modal.style.display = "none";
  modal.onclick = (e) => { if (e.target === modal) modal.style.display = "none"; };

  document.addEventListener("keydown", function(e) {
    if (e.key === "Escape") modal.style.display = "none";
    if (e.key === "ArrowRight") nextImage();
    if (e.key === "ArrowLeft") prevImage();
  });

  prevBtn.onclick = prevImage;
  nextBtn.onclick = nextImage;

  function prevImage() {
    currentIndex = (currentIndex - 1 + images.length) % images.length;
    updateModalImage();
  }
  function nextImage() {
    currentIndex = (currentIndex + 1) % images.length;
    updateModalImage();
  }

  // Share button logic
  shareBtn.onclick = () => {
    const url = images[currentIndex];
    if (navigator.share) {
      navigator.share({
        title: "Check out this quote!",
        text: "Found this inspiring quote image ✨",
        url: url
      }).catch(err => console.log("Share canceled", err));
    } else {
      // Fallback: prompt options
      const shareOptions = `
        Share this image:
        🔗 Copy Link: ${url}
        🐦 Twitter: https://twitter.com/intent/tweet?url=${encodeURIComponent(url)}
        📘 Facebook: https://www.facebook.com/sharer/sharer.php?u=${encodeURIComponent(url)}
      `;
      alert(shareOptions);
    }
  };

  // Swipe support (mobile)
  let startX = 0, startY = 0;
  modalImg.addEventListener("touchstart", (e) => {
    startX = e.touches[0].clientX;
    startY = e.touches[0].clientY;
  });
  modalImg.addEventListener("touchend", (e) => {
    if (!startX || !startY) return;
    let endX = e.changedTouches[0].clientX;
    let endY = e.changedTouches[0].clientY;
    let diffX = endX - startX;
    let diffY = endY - startY;
    if (Math.abs(diffX) > Math.abs(diffY)) {
      if (diffX > 50) prevImage();
      else if (diffX < -50) nextImage();
    } else {
      if (diffY > 50) modal.style.display = "none";
    }
    startX = 0; startY = 0;
  });
</script>
