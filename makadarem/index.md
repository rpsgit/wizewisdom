---
layout: default
title: Makadarem Menu
---

<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Makadarem Menu</title>

<style>
  body {
    font-family: "Poppins", sans-serif;
    background: #f4f6fb url('placeholder-bg.jpg') no-repeat center center fixed;
    background-size: cover;
    color: #222;
    margin: 0;
    padding: 1rem;
  }

  /* 🔴 Delivery Schedule Banner */
  #scheduleBox {
    background: #ff4d4d;
    color: white;
    font-weight: 600;
    padding: 15px;
    border-radius: 10px;
    margin-bottom: 20px;
    text-align: center;
    font-size: 1rem;
    line-height: 1.4rem;
  }

  h2.category-title {
    margin-top: 25px;
    margin-bottom: 10px;
    font-size: 1.3rem;
    color: #333;
  }

  .menu-item {
    display: flex;
    align-items: center;
    background: white;
    border-radius: 12px;
    padding: 10px;
    margin-bottom: 10px;
    box-shadow: 0 2px 6px rgba(0,0,0,0.1);
  }

  .menu-item img {
    width: 80px;
    height: 60px;
    object-fit: cover;
    border-radius: 8px;
    margin-right: 15px;
    cursor: pointer;
  }

  .details {
    flex: 1;
  }

  .details h3 {
    margin: 0;
    font-size: 1.05rem;
  }

  .item-desc {
    font-size: 0.85rem;
    color: #666;
    margin: 2px 0 4px;
    white-space: normal;
    line-height: 1.25rem;
  }

  .menu-item p {
    margin: 3px 0;
    font-size: 0.9rem;
  }

  .actions {
    text-align: center;
  }

  .item-qty {
    width: 45px;
    margin-top: 3px;
  }

  /* Image Modal */
  #imageModal {
    display: none;
    position: fixed;
    z-index: 99999;
    left: 0; top: 0;
    width: 100%; height: 100%;
    background: rgba(0,0,0,0.85);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  #imageModal img {
    max-width: 90%;
    max-height: 90%;
    border-radius: 10px;
  }
</style>

</head>
<body>

<!-- 🔴 Delivery Schedule Box (auto-filled by Google Sheet) -->
<div id="scheduleBox">Loading delivery schedule...</div>

<h1>Makadarem Menu</h1>

<div id="menu"></div>

<!-- Image Zoom Modal -->
<div id="imageModal" onclick="this.style.display='none'">
  <img id="modalImg" src="">
</div>

<script>
/* ==========================
   FETCH MENU + SCHEDULE
   ========================== */

const menuURL = "https://script.google.com/macros/s/AKfycbykjopHttTCH5TcgR_fkHjxDTFJbgKjZ5Qfs-wnJJdD5Z638xYjaAzSerNfsgtAuf41/exec?func=getMenu";
const orderURL = "https://script.google.com/macros/s/AKfycbykjopHttTCH5TcgR_fkHjxDTFJbgKjZ5Qfs-wnJJdD5Z638xYjaAzSerNfsgtAuf41/exec";


// Convert item name to key
function makeKey(name) {
  return name.toLowerCase().replace(/[^a-z0-9]+/g, "_");
}

// Load Google Sheets
async function fetchSheet(url) {
  const res = await fetch(url);
  return await res.json();
}

async function loadData() {
  const menuData = await fetchSheet(sheetURL);
  const orderData = await fetchSheet(orderSheetURL);

  /* ========== LOAD SCHEDULE FROM E1 + F1 ========== */
  const scheduleBox = document.getElementById("scheduleBox");

  const schedLine1 = orderData[0]["E"] || "";
  const schedLine2 = orderData[0]["F"] || "";

  scheduleBox.innerHTML = `
    📅 <b>Delivery Schedule</b><br>
    ${schedLine1}<br>
    ${schedLine2}
  `;

  /* ========== LOAD MENU ========== */
  const menuDiv = document.getElementById("menu");
  menuDiv.innerHTML = "";

  const categories = {};

  menuData.forEach(item => {
    const cat = item.Category || "Others";
    if (!categories[cat]) categories[cat] = [];
    categories[cat].push(item);
  });

  for (const category in categories) {
    const h2 = document.createElement("h2");
    h2.className = "category-title";
    h2.textContent = category;
    menuDiv.appendChild(h2);

    categories[category].forEach(item => {
      let raw = item.Item || "";
      let name = raw;
      let desc = "";

      if (raw.includes(" - ")) {
        const parts = raw.split(" - ");
        name = parts.shift();
        desc = parts.join(" - ");
      }

      const price = Number(item.Price || 0);
      const imgSrc = item.Image || "https://via.placeholder.com/80x60";
      const key = makeKey(name);

      const div = document.createElement("div");
      div.className = "menu-item";

      div.innerHTML = `
        <img data-full="${imgSrc}" 
             src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///ywAAAAAAQABAAACAUwAOw==" 
             data-src="${imgSrc}" 
             alt="${name}" 
             class="lazy-img">

        <div class="details">
          <h3>${name}</h3>
          ${desc ? `<p class="item-desc">${desc}</p>` : ""}
          <p>₱${price.toFixed(0)}</p>
        </div>

        <div class="actions">
          <input type="checkbox" id="cb_${key}">
          <input type="number" id="qty_${key}" class="item-qty" value="1" min="1" style="display:none;">
        </div>
      `;

      // Click image → enlarge
      div.querySelector("img").onclick = function () {
        document.getElementById("modalImg").src = this.getAttribute("data-full");
        document.getElementById("imageModal").style.display = "flex";
      };

      // Show quantity when checkbox is clicked
      div.querySelector(`#cb_${key}`).addEventListener("change", (e) => {
        const qty = div.querySelector(`#qty_${key}`);
        qty.style.display = e.target.checked ? "inline-block" : "none";
      });

      menuDiv.appendChild(div);
    });
  }

  lazyLoadImages();
}


/* ==========================
   LAZY LOAD IMAGES
   ========================== */
function lazyLoadImages() {
  const lazyImages = document.querySelectorAll(".lazy-img");

  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const img = entry.target;
        img.src = img.dataset.src;
        observer.unobserve(img);
      }
    });
  });

  lazyImages.forEach(img => observer.observe(img));
}

loadData();
</script>

</body>
</html>
