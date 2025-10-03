---
layout: default
title: Geekosystem
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/geekosystem-bg.png') no-repeat center center fixed;
    background-size: cover;
    font-family: Arial, sans-serif;
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
    text-align: center;
    font-size: 2.5rem;
    font-weight: 700;
    margin: 50px 0;
    color: #000;
  }

  /* === CATEGORY WRAPPER === */
  .categories-wrapper {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 50px;
    text-align: center;
  }

  /* === CATEGORY SECTIONS === */
  .section-link {
    text-decoration: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
  }

  .section-geek {
    width: 220px;
    height: 220px;
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;
    transition: transform 0.25s ease;
  }

  /* Category-specific background images */
  .section-books .section-geek { background-image: url('/assets/images/tech-ic.png'); }
  .section-science .section-geek { background-image: url('/assets/images/science-ic.png'); }
  .section-language .section-geek { background-image: url('/assets/images/nihongo-ic.png'); }

  /* Category Title Overlay */
  .section-title {
    margin-top: 15px;
    font-size: 1.4rem;
    font-weight: bold;
    color: #000;
  }

  /* Hover Effect */
  .section-link:hover .section-geek { transform: scale(1.08); }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    h2 { font-size: 2.2rem; }
    .section-geek { width: 180px; height: 180px; }
    .section-title { font-size: 1.2rem; }
  }

  @media (max-width: 600px) {
    .section-geek { width: 150px; height: 150px; }
    .section-title { font-size: 1rem; }
  }
</style>

<!-- Home Button -->
<a href="https://www.wizewisdom.com/" class="home-button">
  <span class="home-icon"></span>
</a>

<h2>Geekosystem</h2>

<div class="categories-wrapper">
  <a href="/geekosystem/tech-index.html" class="section-link">
    <div class="section section-books">
      <div class="section-geek"></div>
      <div class="section-title">Tech</div>
    </div>
  </a>

  <a href="/geekosystem/science-index.html" class="section-link">
    <div class="section section-science">
      <div class="section-geek"></div>
      <div class="section-title">Science</div>
    </div>
  </a>

  <a href="/geekosystem/nihongo-index.html" class="section-link">
    <div class="section section-language">
      <div class="section-geek"></div>
      <div class="section-title">Nihongo</div>
    </div>
  </a>
</div>
