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

#latest-image img {
  width: 100%;
  max-height: 70vh;
  object-fit: contain;
  border-radius: 15px;
  box-shadow: 0 6px 18px rgba(0,0,0,0.2);
  margin-bottom: 30px;
  cursor: pointer;
  transition: transform 0.3s ease;
}
#latest-image img:hover {
  transform: scale(1.02);
}

.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 15px;
}
.gallery img {
  width: 100%;
  height: 140px;
  object-fit: cover;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.15);
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.gallery img:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 14px rgba(0,0,0,0.25);
}

.modal {
  display: none;
  position: fixed;
  z-index: 9999;
  left: 0; top: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: 20px;
}

.modal-content {
  max-width: 90%;
  max-height: 80vh;
  border-radius: 15px;
  box-shadow: 0 6px 20px rgba(0,0,0,0.5);
}

#caption {
  margin-top: 15px;
  text-align: center;
  color: #ccc;
  font-size: 1rem;
}

.close {
  position: absolute;
  top: 20px; right: 30px;
  font-size: 40px;
  font-weight: bold;
  color: #fff;
  cursor: pointer;
  transition: color 0.2s;
}
.close:hover { color: #1f9202ff; }

.prev, .next {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  font-size: 40px;
  font-weight: bold;
  color: white;
  cursor: pointer;
  padding: 10px;
  user-select: none;
  transition: color 0.2s;
}
.prev { left: 20px; }
.next { right: 20px; }
.prev:hover, .next:hover { color: #1f9202ff; }

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

  <div id="imgModal" class="modal">
    <span class="close">&times;</span>
    <span class="prev">&#10094;</span>
    <span class="next">&#10095;</span>
    <img class="modal-content" id="modalImg">
    <div id="caption"></div>
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
  .then(res => res.json())
  .then(files => {
    const imageFiles = files.filter(f => f.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(f.name));
    imageFiles.sort((a, b) => naturalSort(b, a));
    images = imageFiles.map(file => `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${file.name}`);

    if (images.length > 0) {
      const latestImg = document.createElement("img");
      latestImg.src = images[0];
      latestImg.alt = imageFiles[0].name;
      latestImg.addEventListener("click", () => openModal(0));
      latestImageDiv.appendChild(latestImg);
    }

    images.slice(1).forEach((url, i) => {
      const img = document.createElement("img");
      img.src = url;
      img.alt = imageFiles[i + 1].name;
      img.addEventListener("click", () => openModal(i + 1));
      gallery.appendChild(img);
    });
  })
  .catch(err => {
    gallery.innerHTML = "<p>⚠️ Sorry, there was an error loading the images.</p>";
    console.error("Error loading images:", err);
  });

const modal = document.getElementById("imgModal");
const modalImg = document.getElementById("modalImg");
const caption = document.getElementById("caption");
const closeBtn = document.querySelector(".close");
const prevBtn = document.querySelector(".prev");
const nextBtn = document.querySelector(".next");

function openModal(index) {
  modal.style.display = "flex";
  currentIndex = index;
  updateModal();
}

function updateModal() {
  modalImg.src = images[currentIndex];
  caption.textContent = images[currentIndex].split("/").pop();
}

closeBtn.onclick = () => modal.style.display = "none";
modal.onclick = e => { if (e.target === modal) modal.style.display = "none"; };
prevBtn.onclick = prevImage;
nextBtn.onclick = nextImage;

document.addEventListener("keydown", e => {
  if (e.key === "Escape") modal.style.display = "none";
  if (e.key === "ArrowRight") nextImage();
  if (e.key === "ArrowLeft") prevImage();
});

function prevImage() {
  currentIndex = (currentIndex - 1 + images.length) % images.length;
  updateModal();
}

function nextImage() {
  currentIndex = (currentIndex + 1) % images.length;
  updateModal();
}

// Swipe for mobile
let startX = 0;
modalImg.addEventListener("touchstart", e => startX = e.touches[0].clientX);
modalImg.addEventListener("touchend", e => {
  const diffX = e.changedTouches[0].clientX - startX;
  if (diffX > 50) prevImage();
  else if (diffX < -50) nextImage();
});
</script>
