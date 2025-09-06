---
layout: default
title: Quotes
---

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

  /* Image containers with action buttons */
  .image-container {
    position: relative;
    display: inline-block;
  }
  .image-container img {
    width: 100%;
    height: auto;
    border-radius: 10px;
    display: block;
    cursor: pointer;
    box-shadow: 0 4px 10px rgba(0,0,0,0.15);
  }
  .image-actions {
    position: absolute;
    bottom: 8px;
    right: 8px;
    display: flex;
    gap: 6px;
  }
  .image-actions button, 
  .image-actions a {
    background: rgba(255,255,255,0.9);
    border: none;
    padding: 6px 10px;
    border-radius: 6px;
    cursor: pointer;
    font-size: 14px;
    box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    transition: background 0.2s;
    text-decoration: none;
    color: #222;
    font-weight: bold;
  }
  .image-actions button:hover,
  .image-actions a:hover {
    background: #f0f0f0;
  }

  /* Gallery grid */
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
    gap: 15px;
    margin: auto;
  }
  .gallery .image-container img {
    height: 140px;
    object-fit: cover;
  }

  /* Latest image styling */
  #latest-image .image-container img {
    width: 100%;
    max-height: 70vh;
    object-fit: contain;
    margin-bottom: 30px;
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
    user-select: none;
  }
  .prev { left: 20px; }
  .next { right: 20px; }
  .prev:hover, .next:hover { color: #f00; }

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
  .download-btn { background: #28a745; color: white; }
  .download-btn:hover { background: #218838; }
  .share-btn { background: #007bff; color: white; border: none; }
  .share-btn:hover { background: #0069d9; }
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
        const latestImgContainer = document.createElement("div");
        latestImgContainer.className = "image-container";
        
        const latestImg = document.createElement("img");
        latestImg.src = images[0];
        latestImg.alt = imageFiles[0].name;
        latestImg.addEventListener("click", () => openModal(0));

        const actions = createImageActions(images[0], 0);

        latestImgContainer.appendChild(latestImg);
        latestImgContainer.appendChild(actions);
        latestImageDiv.appendChild(latestImgContainer);
      }

      images.slice(1).forEach((imgUrl, index) => {
        const container = document.createElement("div");
        container.className = "image-container";

        const img = document.createElement("img");
        img.src = imgUrl;
        img.alt = imageFiles[index + 1].name;
        img.addEventListener("click", () => openModal(index + 1));

        const actions = createImageActions(imgUrl, index + 1);

        container.appendChild(img);
        container.appendChild(actions);
        gallery.appendChild(container);
      });
    })
    .catch(error => {
      gallery.innerHTML = "<p>⚠️ Error loading images.</p>";
      console.error("Error loading images:", error);
    });

  function createImageActions(imgUrl, index) {
    const actionsDiv = document.createElement("div");
    actionsDiv.className = "image-actions";

    const reactBtn = document.createElement("button");
    reactBtn.innerHTML = "❤️";
    reactBtn.onclick = (e) => {
      e.stopPropagation();
      alert("You reacted ❤️");
    };

    const downloadLink = document.createElement("a");
    downloadLink.href = imgUrl;
    downloadLink.download = "";
    downloadLink.innerHTML = "⬇";

    const shareBtn = document.createElement("button");
    shareBtn.innerHTML = "🔗";
    shareBtn.onclick = (e) => {
      e.stopPropagation();
      if (navigator.share) {
        navigator.share({
          title: "Check this out",
          url: imgUrl
        });
      } else {
        alert(`Share this link:\n${imgUrl}`);
      }
    };

    actionsDiv.appendChild(reactBtn);
    actionsDiv.appendChild(downloadLink);
    actionsDiv.appendChild(shareBtn);
    return actionsDiv;
  }

  // Modal logic
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
        title: "Check this out",
        url: url
      });
    } else {
      alert(`Share this link:\n${url}`);
    }
  };
</script>
