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
<style>
  .content-box {
    max-width: 1000px;
    margin: 30px auto;
    background: rgba(255, 255, 255, 0.7); /* 70% translucent white */
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.15);
  }
  h1 {
    text-align: center;
    color: #222;
  }

  /* Latest image */
  #latest-image img {
    width: 100%;
    height: auto;
    max-height: 70vh;
    object-fit: contain;
    align-items: center;
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
  .gallery img:hover { transform: scale(1.05); }

  /* Highlighted block */
  .highlighted-block {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 30px 0;
    gap: 15px;
  }
  .highlighted-block button {
    background: #f4f4f4;
    border: none;
    padding: 10px 16px;
    border-radius: 8px;
    cursor: pointer;
    font-size: 16px;
    box-shadow: 0 2px 6px rgba(0,0,0,0.2);
  }
  .highlighted-block img {
    border-radius: 12px;
    border: 6px solid transparent;
    background: linear-gradient(white, rgba(255,255,255,0.6)) padding-box, 
                linear-gradient(to bottom right, rgba(255,255,255,0.9), rgba(255,255,255,0.4)) border-box; 
    box-shadow: 0 4px 10px rgba(0,0,0,0.15); 
    max-width: 100%; 
    height: auto;
  }

  /* Modal */
  .modal {
    display: none;
    position: fixed;
    z-index: 9999;
    padding-top: 60px;
    left: 0; top: 0;
    width: 100%; height: 100%;
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
    top: 15px; right: 30px;
    color: #fff;
    font-size: 40px;
    font-weight: bold;
    cursor: pointer;
  }
  .close:hover { color: #1f9202ff; }

  /* Arrows */
  .prev, .next {
    cursor: pointer;
    position: absolute;
    top: 50%;
    padding: 16px;
    color: white;
    font-weight: bold;
    font-size: 40px;
    user-select: none;
  }
  .prev { left: 20px; }
  .next { right: 20px; }
  .prev:hover, .next:hover { color: #1f9202ff; }

  /* Modal buttons */
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
  }
  .download-btn { background: #22a102e3; color: white; }
  .download-btn:hover { background: #1f9202ff; }
  .share-btn { background: #22a102e3; color: white; }
  .share-btn:hover { background: #1f9202ff; }
</style>

<div class="content-box">
  <h1>Quotes</h1>

  <!-- Latest + Gallery -->
  <div id="latest-image"></div>
  <div class="gallery" id="gallery"></div>

  <!-- Modal -->
  <div id="imgModal" class="modal">
    <span class="close">&times;</span>
    <span class="prev">&#10094;</span>
    <span class="next">&#10095;</span>
    <img class="modal-content" id="modalImg">
    <div id="caption"></div>
    <div class="modal-actions">
      <a id="downloadBtn" download class="download-btn">⬇ Download</a>
      <button id="shareBtn" class="share-btn">🔗 Share</button>
    </div>
  </div>
</div>

<script>
  const username = "rpsgit";       
  const repo = "wizewisdom";       
  const branch = "main";           
  const folder = "assets/images/quotes";  

  const apiUrl = `https://api.github.com/repos/${username}/${repo}/contents/${folder}?ref=${branch}`;
  const gallery = document.getElementById("gallery");
  const latestImageDiv = document.getElementById("latest-image");

  let images = [];
  let currentIndex = 0;

  function naturalSort(a, b) {
    return a.name.localeCompare(b.name, undefined, { numeric: true, sensitivity: 'base' });
  }

  fetch(apiUrl)
    .then(response => response.json())
    .then(files => {
      let imageFiles = files.filter(file => file.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(file.name));
      imageFiles.sort((a, b) => naturalSort(b, a));
      images = imageFiles.map(file => `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${file.name}`);

      if (images.length > 0) {
        const latestImg = document.createElement("img");
        latestImg.src = images[0];
        latestImg.alt = imageFiles[0].name;
        latestImg.addEventListener("click", () => openModal(0));
        latestImageDiv.appendChild(latestImg);
      }

      images.slice(1).forEach((imgUrl, index) => {
        const img = document.createElement("img");
        img.src = imgUrl;
        img.alt = imageFiles[index + 1].name;
        img.addEventListener("click", () => openModal(index + 1));
        gallery.appendChild(img);
      });
    })
    .catch(error => {
      gallery.innerHTML = "<p>⚠️ Oops.. sorry love there seems to be an error.</p>";
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

  document.addEventListener("keydown", (e) => {
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

  shareBtn.onclick = () => {
    const url = images[currentIndex];
    if (navigator.share) {
      navigator.share({
        title: "Check out this quote!",
        text: "Found this inspiring quote",
        url: url
      }).catch(err => console.log("Share canceled", err));
    } else {
      alert(`Share this image:\n🔗 ${url}`);
    }
  };

  // Mobile swipe
  let startX = 0, startY = 0;
  modalImg.addEventListener("touchstart", (e) => {
    startX = e.touches[0].clientX;
    startY = e.touches[0].clientY;
  });
  modalImg.addEventListener("touchend", (e) => {
    if (!startX || !startY) return;
    let endX = e.changedTouches[0].clientX;
    let endY = e.changedTouches[0].clientY;
    let diffX = endX - startX, diffY = endY - startY;
    if (Math.abs(diffX) > Math.abs(diffY)) {
      if (diffX > 50) prevImage();
      else if (diffX < -50) nextImage();
    } else if (diffY > 50) modal.style.display = "none";
    startX = 0; startY = 0;
  });
</script>
