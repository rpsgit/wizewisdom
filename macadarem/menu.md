---
layout: default
title: Menu
---

<style>
/* === GENERAL PAGE STYLE === */
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/menu-bg.jpg') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
  color: #222;
}

/* === PAGE CONTAINER === */
.page-container {
  max-width: 1000px;
  margin: 60px auto;
  background: rgba(255, 255, 255, 0.9);
  padding: 40px 25px;
  border-radius: 25px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
}

/* === HEADER === */
h1 {
  text-align: center;
  font-size: 2.8rem;
  color: #000;
  margin-bottom: 40px;
}

/* === CATEGORY HEADINGS === */
h2 {
  text-align: left;
  font-size: 2rem;
  color: #333;
  margin: 50px 0 20px 10px;
  border-left: 6px solid #ff7e5f;
  padding-left: 12px;
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

/* === TOOLTIP === */
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
}

/* === MENU GRID === */
.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
  justify-items: center;
}

.menu-card {
  background: #fff;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 4px 20px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  width: 250px;
  text-align: center;
  cursor: pointer;
}

.menu-card:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 25px rgba(0,0,0,0.2);
}

.menu-card img {
  width: 100%;
  height: 180px;
  object-fit: cover;
  display: block;
  transition: transform 0.3s ease;
}

.menu-card:hover img {
  transform: scale(1.08);
}

.menu-card h3 {
  margin: 15px 0 8px;
  color: #333;
  font-size: 1.4rem;
}

.menu-card p {
  font-size: 0.95rem;
  color: #555;
  margin-bottom: 15px;
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .page-container { padding: 25px 15px; }
  h1 { font-size: 2.2rem; }
  h2 { font-size: 1.6rem; }
  .menu-card { width: 90%; }
}
</style>

<!-- Home & Back Buttons -->
<a href="https://www.wizewisdom.com/" class="home-button" data-tooltip="Home">
  <span class="home-icon"></span>
</a>

<button class="back-button" onclick="if(history.length>1){history.back();}else{window.location='/index.html';}" data-tooltip="Back">
  <span class="back-icon"></span>
</button>

<!-- Main Container -->
<div class="page-container">
  <h1>Macadarem Menu</h1>

  <!-- === DRINKS SECTION === -->
  <h2>Drinks & Smoothies</h2>
  <div class="menu-grid">
    <div class="menu-card">
      <img src="/assets/images/menu/milk-coffee.jpg" alt="Milk Coffee" loading="lazy">
      <h3>Milk Coffee 8oz</h3>
      <p>₱50</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/menu/matcha-latte.jpg" alt="Matcha Latte" loading="lazy">
      <h3>Matcha Latte 8oz</h3>
      <p>₱50</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/menu/ube-latte.jpg" alt="Ube Latte" loading="lazy">
      <h3>Ube Latte 8oz</h3>
      <p>₱50</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/menu/houjicha-latte.jpg" alt="Houjicha Latte" loading="lazy">
      <h3>Houjicha Latte 8oz</h3>
      <p>₱65</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images//menu/alamansi.jpg" alt="Kalamansi" loading="lazy">
      <h3>Kalamansi 16oz</h3>
      <p>₱65</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/menu/lemonade.jpg" alt="Lemonade" loading="lazy">
      <h3>Lemonade 16oz</h3>
      <p>₱65</p>
    </div>
  </div>

  <!-- === MEALS SECTION === -->
  <h2>Meals</h2>
  <div class="menu-grid">
    <div class="menu-card">
      <img src="/assets/images/meal1.jpg" alt="Pork Sisig" loading="lazy">
      <h3>Pork Sisig</h3>
      <p>₱110</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/meal2.jpg" alt="Longsilog" loading="lazy">
      <h3>Longsilog</h3>
      <p>₱110</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/meal3.jpg" alt="Tocilog" loading="lazy">
      <h3>Tocilog</h3>
      <p>₱110</p>
    </div>
  </div>

  <!-- === DESSERTS SECTION === -->
  <h2>Desserts</h2>
  <div class="menu-grid">
    <div class="menu-card">
      <img src="/assets/images/dessert1.jpg" alt="Leche Flan" loading="lazy">
      <h3>Leche Flan</h3>
      <p>₱110</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/dessert2.jpg" alt="Ube Halaya" loading="lazy">
      <h3>Ube Halaya</h3>
      <p>₱65</p>
    </div>
    <div class="menu-card">
      <img src="/assets/images/dessert3.jpg" alt="Apple Crumble" loading="lazy">
      <h3>Apple Crumble</h3>
      <p>₱50</p>
    </div>
  </div>
</div>
