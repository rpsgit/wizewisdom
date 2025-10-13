---
layout: default
title: Gallery
---

<style>
/* === BODY & PAGE CONTAINER === */
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/gallery-index.png') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
  color: #222;
}

.page-container {
  max-width: 1000px;
  margin: 50px auto;
  background: rgba(255, 255, 255, 0.88);
  padding: 35px 25px;
  border-radius: 25px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
  text-align: center;
}

/* === HOME & BACK BUTTONS === */
.home-button,
.back-button {
  position: fixed;
  top: 20px;
  width: 40px;
  height: 40px;
  border: none;
  background: none;
  cursor: pointer;
  z-index: 1000;
}

.home-button { left: 20px; }
.back-button { left: 70px; }

.home-icon,
.back-icon {
  display: block;
  width: 100%;
  height: 100%;
  background-size: contain;
  background-repeat: no-repeat;
  background-position: center;
}

.home-icon { background-image: url('/assets/images/home-icon.png'); }
.back-icon { background-image: url('/assets/images/back-ico.png'); }

/* === TOOLTIP LABELS === */
.home-button[data-tooltip]:hover::after,
.back-button[data-tooltip]:hover::after {
  content: attr(data-tooltip);
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  background-color: rgba(0,0,0,0.75);
  color: #fff;
  padding: 4px 8px;
  border-radius: 5px;
  font-size: 0.85rem;
  white-space: nowrap;
  margin-top: 6px;
  pointer-events: none;
  opacity: 1;
  transition: opacity 0.2s ease;
  z-index: 1001;
}

.home-button[data-tooltip]::after,
.back-button[data-tooltip]::after { opacity: 0; }
.home-button[data-tooltip]:hover::after,
.back-button[data-tooltip]:hover::after { opacity: 1; }

/* === HEADINGS === */
h1 {
  font-size: 3rem;
  color: #000;
  margin-bottom: 30px;
}

/* === GALLERY GRID === */
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
  margin-top: 20px;
}

.gallery-card {
  background: rgba(255,255,255,0.95);
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.3s ease;
}

.gallery-card img {
  width: 100%;
  height: 160px;
  object-fit: cover;
  display: block;
  transition: transform 0.2s ease;
}

.gallery-card:hover img {
  transform: scale(1.05);
}

.modal {
  display: none;
  position: fixed;
  z-index: 1500;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0,0,0,0.8);
}

.modal-content {
  margin: 60px auto;
  display: block;
  max-width: 90%;
  max-height: 80%;
  border-radius: 15px;
}

.close-modal {
  position: absolute;
  top: 30px;
  right: 30px;
  color: #fff;
  font-size: 2rem;
  font-weight: bold;
  cursor: pointer;
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  h1 { font-size: 2.2rem; }
  .gallery-card img { height: 140px; }
}

@media (max-width: 480px) {
  .gallery-card img { height: 120px; }
}
</style>

<!-- Home & Back Buttons -->
<a href="https://www.wizewisdom.com/" class="home-button" data-tooltip="Home">
  <span class="home-icon"></span>
</a>

<button class="back-button" onclick="if(history.length>1){history.back();}else{window.location='/index.html';}" data-tooltip="Back">
  <span class="back-icon"></span>
</button>

<div class="page-container">
  <h1>Gallery</h1>

  <div class="gallery-grid">
    <div class="gallery-card">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQ6Pc4rWAkS5Odign3w7yAAcSapN01g741NQenf6oGoNc?width=400&height=187" alt="Landscape 1">
    </div>
    <div class="gallery-card">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQS_c77d-ZL5QaVzc5JihRlKAai7mLU39Myiw0Mm16Vbj-Q?width=400&height=187" alt="Landscape 2">
    </div>
    <div class="gallery-card">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSnv4nA-7HpSq5qbowW7rdLASFCt3cWTbGqujq0F-23Bm0?width=400&height=300" alt="Landscape 3">
    </div>
    <div class="gallery-card">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSW8dr4WOtRTpomBuB8NXKaAR7XyRDCBXYdA3aISh4XEAY?width=400&height=187" alt="Landscape 4">
    </div>
    <div class="gallery-card">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTC09oKxZ0WS6QRNiqRBzTlAb8dyT2bQwV49nX8rpHNX3k?width=346&height=163" alt="Landscape 5">
    </div>
  </div>
</div>

<!-- === MODAL FOR IMAGE VIEW === -->
<div id="imgModal" class="modal">
  <span class="close-modal">&times;</span>
  <img class="modal-content" id="modalImg">
</div>

<script>
// Modal functionality
const modal = document.getElementById("imgModal");
const modalImg = document.getElementById("modalImg");
const closeBtn = document.querySelector(".close-modal");

document.querySelectorAll(".gallery-card img").forEach(img => {
  img.onclick = () => {
    modal.style.display = "block";
    modalImg.src = img.src.replace('width=400','width=1200'); // load bigger version
  };
});

closeBtn.onclick = () => modal.style.display = "none";
modal.onclick = () => modal.style.display = "none";
</script>
