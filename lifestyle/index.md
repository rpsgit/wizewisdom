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

  /* === HOME BUTTON ICON === */
  .home-button {
    position: fixed;
    top: 20px;
    left: 20px;
    z-index: 1000;
    display: inline-block;
    width: 40px;
    height: 40px;
    text-decoration: none;
  }

  .home-icon {
    width: 100%;
    height: 100%;
    display: block;
    background: url('/assets/images/home-icon.png') no-repeat center center;
    background-size: contain;
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
    flex: 1 1 200px; /* responsive width */
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
    display: block;
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
<a href="https://www.wizewisdom.com/" class="home-button">
  <span class="home-icon"></span>
</a>

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

  <!-- Recipes Section -->
  <a href="/lifestyle/recipes.html" class="section-link">
    <img src="/assets/images/recipe-ico.png" alt="Recipes Icon">
    <span class="section-title">Recipes</span>
  </a>
</div>
