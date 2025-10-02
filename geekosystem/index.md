---
layout: default
title: Geekosystem
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/geekosystem-index.png') no-repeat center center fixed;
    background-size: cover;
    font-family: Arial, sans-serif;
  }

  /* === MAIN CONTAINER === */
  .geek-container {
    max-width: 1200px;
    margin: 50px auto;
    text-align: center;
    background: rgba(255, 255, 255, 0.7);
    padding: 40px 50px;
    border-radius: 30px;
    box-shadow: 0 6px 25px rgba(0,0,0,0.2);
  }

  /* === PAGE TITLE === */
  .geek-container h2 {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 40px;
    color: #000;
  }

  /* === CATEGORY WRAPPER === */
  .categories-wrapper {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 50px;
  }

  /* === CATEGORY SECTIONS === */
  .section-link {
    text-decoration: none;
    display: flex;
    flex-direction: column;
    align-items: center;
    position: relative;
  }

  .section {
    position: relative;
    width: 220px;
    height: 220px;
    text-align: center;
    cursor: pointer;
    transition: transform 0.25s ease;
  }

  .section-geek {
    width: 100%;
    height: 100%;
    background-color: rgba(44, 122, 123, 0.85); /* Sophisticated blue-green */
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;
    border-radius: 20px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    transition: transform 0.25s ease;
  }

  /* Category-specific background images */
  .section-books .section-geek {
    background-image: url('/assets/images/tech-index.png');
  }
  .section-science .section-geek {
    background-image: url('/assets/images/science-index.png');
  }
  .section-language .section-geek {
    background-image: url('/assets/images/nihongo-index.png');
  }

  /* Category Title Overlay */
  .section-title {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.4rem;
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
    pointer-events: none;
  }

  /* Hover Effect */
  .section-link:hover .section-geek {
    transform: scale(1.08);
  }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    .geek-container h2 {
      font-size: 2.2rem;
    }
    .section {
      width: 180px;
      height: 180px;
    }
    .section-title {
      font-size: 1.2rem;
    }
  }

  @media (max-width: 600px) {
    .section {
      width: 150px;
      height: 150px;
    }
    .section-title {
      font-size: 1rem;
    }
  }
</style>

<div class="geek-container">
  <h2>Geekosystem</h2>

  <div class="categories-wrapper">
    <a href="/geekosystem/tech/index.html" class="section-link">
      <div class="section section-books">
        <div class="section-geek"></div>
        <div class="section-title">Tech</div>
      </div>
    </a>

    <a href="/geekosystem/science/index.html" class="section-link">
      <div class="section section-science">
        <div class="section-geek"></div>
        <div class="section-title">Science</div>
      </div>
    </a>

    <a href="/geekosystem/language/index.html" class="section-link">
      <div class="section section-language">
        <div class="section-geek"></div>
        <div class="section-title">Nihongo</div>
      </div>
    </a>
  </div>
</div>
