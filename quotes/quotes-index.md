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
    cursor: pointer;
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

  fetch(apiUrl)
    .then(res => res.json())
    .then(files => {
      const imageFiles = files.filter(f => f.type === "file" && /\.(jpg|jpeg|png|gif|webp)$/i.test(f.name));
      imageFiles.sort((a, b) => a.name.localeCompare(b.name, undefined, { numeric: true, sensitivity: 'base' }));
      images = imageFiles.map(f => `https://raw.githubusercontent.com/${username}/${repo}/${branch}/${folder}/${f.name}`);

      if(images.length > 0){
        // Show latest quote
        const latest = document.createElement("img");
        latest.src = images[0];
        latest.alt = imageFiles[0].name;
        latest.addEventListener("click", ()=>openModal(0));
        latestImageDiv.appendChild(latest);
      }

      // Gallery for remaining quotes
      images.slice(1).forEach((url,i)=>{
        const img = document.createElement("img");
        img.src = url;
        img.alt = imageFiles[i+1].name;
        img.addEventListener("click", ()=>openModal(i+1));
        gallery.appendChild(img);
      });
    })
    .catch(err => {
      gallery.innerHTML = "<p>⚠️ Could not load quotes.</p>";
      console.error(err);
    });

  const modal = document.getElementById("imgModal");
  const modalImg = document.getElementById("modalImg");
  const caption = document.getElementById("caption");
  const closeBtn = document.querySelector(".close");
  const prevBtn = document.querySelector(".prev");
  const nextBtn = document.querySelector(".next");

  function openModal(index){
    currentIndex = index;
    modalImg.src = images[currentIndex];
    caption.textContent = images[currentIndex].split("/").pop();
    modal.style.display = "flex";
    document.body.style.overflow = "hidden";
  }

  function closeModal(){
    modal.style.display = "none";
    document.body.style.overflow = "";
  }

  function prevImage(){
    currentIndex = (currentIndex - 1 + images.length) % images.length;
    modalImg.src = images[currentIndex];
    caption.textContent = images[currentIndex].split("/").pop();
  }

  function nextImage(){
    currentIndex = (currentIndex + 1) % images.length;
    modalImg.src = images[currentIndex];
    caption.textContent = images[currentIndex].split("/").pop();
  }

  closeBtn.onclick = closeModal;
  prevBtn.onclick = prevImage;
  nextBtn.onclick = nextImage;
  modal.onclick = e => { if(e.target===modal) closeModal(); };

  document.addEventListener("keydown", e => {
    if(modal.style.display === "flex"){
      if(e.key === "Escape") closeModal();
      if(e.key === "ArrowLeft") prevImage();
      if(e.key === "ArrowRight") nextImage();
    }
  });

  // Swipe support for mobile
  let startX = 0;
  modalImg.addEventListener("touchstart", e => startX = e.touches[0].clientX);
  modalImg.addEventListener("touchend", e => {
    const diff = e.changedTouches[0].clientX - startX;
    if(diff>50) prevImage();
    if(diff<-50) nextImage();
  });
</script>
