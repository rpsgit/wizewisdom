---
layout: default
title: Lifestyle
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/leisure-index.png') no-repeat center center fixed;
    background-size: cover;
    font-family: Arial, sans-serif;
    text-align: center;
  }

  /* === HOME & BACK BUTTON ICONS === */
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

  /* === ICON IMAGES (update paths as needed) === */
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
    background-color: rgba(0, 0, 0, 0.75);
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
  .back-button[data-tooltip]::after {
    opacity: 0;
  }

  .home-button[data-tooltip]:hover::after,
  .back-button[data-tooltip]:hover::after {
    opacity: 1;
  }

  /* === PAGE TITLE === */
  h2 {
    font-size: 2.5rem;
    font-weight: 700;
    margin-top: 80px;
    margin-bottom: 50px;
    color: #000;
  }

  /* === ICON SECTIONS === */
  .sections-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 40px;
    margin-bottom: 50px;
  }

  .section-link {
    text-decoration: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    transition: transform 0.25s ease;
    flex: 1 1 200px;
    max-width: 220px;
  }

  .section-link img {
    width: 100%;
    height: auto;
    display: block;
    transition: transform 0.25s ease;
  }

  .section-title {
    margin-top: 10px;
    font-size: 1.4rem;
    font-weight: bold;
    color: #000;
    text-align: center;
  }

  .section-link:hover img {
    transform: scale(1.08);
  }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    h2 { font-size: 2.2rem; }
    .section-link { max-width: 180px; }
    .section-link img { width: 160px; }
    .section-title { font-size: 1.2rem; }
  }

  @media (max-width: 600px) {
    .sections-container {
      flex-direction: column;
      align-items: center;
      gap: 30px;
    }
    .section-link { max-width: 160px; }
    .section-link img { width: 140px; }
    .section-title { font-size: 1rem; }
  }
</style>

<!-- Home Button -->
<a href="https://www.wizewisdom.com/" class="home-button" data-tooltip="Home">
  <span class="home-icon"></span>
</a>

<!-- Back Button -->
<button class="back-button" onclick="if(history.length>1){history.back();}else{window.location='/index.html';}" data-tooltip="Back">
  <span class="back-icon"></span>
</button>

<h2>Leisure Lab</h2>

<div class="sections-container">
  <!-- Tennis Section -->
  <a href="/lifestyle/tennis.html" class="section-link">
    <img src="/assets/images/tennis-ico.png" alt="Tennis Icon">
    <span class="section-title">Tennis</span>
  </a>

  <!-- Pickleball Section -->
  <a href="/lifestyle/pickleball.html" class="section-link">
    <img src="/assets/images/pickle-ico.png" alt="Pickleball Icon">
    <span class="section-title">Pickleball</span>
  </a>

  <!-- Cooking & Baking Section -->
  <a href="/lifestyle/recipes.html" class="section-link">
    <img src="/assets/images/recipe-ico.png" alt="Recipes Icon">
    <span class="section-title">Cooking & Baking</span>
  </a>
</div>
