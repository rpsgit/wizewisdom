---
layout: default
title: Nerdvana
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/nerdvana-bg.png') no-repeat center center fixed;
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
    width: 40px;   /* adjust size if needed */
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

  /* === MAIN CONTAINER === */
  .nerd-container {
    max-width: 1200px;
    margin: 50px auto;
    text-align: center;
    background: rgba(255, 255, 255, 0.7);
    padding: 40px 50px;
    border-radius: 30px;
    box-shadow: 0 6px 25px rgba(0,0,0,0.2);
  }

  /* === PAGE TITLE === */
  .nerd-container h2 {
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

  .section-nerd {
    width: 100%;
    height: 100%;
    background-color: rgba(44, 122, 123, 0.85);
    background-size: contain;
    background-position: center;
    background-repeat: no-repeat;
    border-radius: 20px;
    box-shadow: 0 4px 12px rgba(0,0,0,0.2);
    transition: transform 0.25s ease;
  }

  /* Category-specific background images */
  .section-books .section-nerd {
    background-image: url('/assets/images/book-icon.png');
  }
  .section-quotes .section-nerd {
    background-image: url('/assets/images/quote-icon.png');
  }
  .section-memes .section-nerd {
    background-image: url('/assets/images/meme-icon.png');
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
  .section-link:hover .section-nerd {
    transform: scale(1.08);
  }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    .nerd-container h2 { font-size: 2.2rem; }
    .section { width: 180px; height: 180px; }
    .section-title { font-size: 1.2rem; }
  }

  @media (max-width: 600px) {
    .section { width: 150px; height: 150px; }
    .section-title { font-size: 1rem; }
  }
</style>

<!-- Home Button -->
<a href="https://www.wizewisdom.com/" class="home-button">
  <span class="home-icon"></span>
</a>

<div class="nerd-container">
  <h2>Nerdvana</h2>

  <div class="categories-wrapper">
    <!-- Books Section -->
    <a href="/books/book-index.html" class="section-link">
      <div class="section section-books">
        <div class="section-nerd"></div>
        <div class="section-title">Books</div>
      </div>
    </a>

    <!-- Quotes Section -->
    <a href="/quotes/quote-index.html" class="section-link">
      <div class="section section-quotes">
        <div class="section-nerd"></div>
        <div class="section-title">Quotes</div>
      </div>
    </a>

    <!-- Memes Section -->
    <a href="/nerdvana/meme-index.html" class="section-link">
      <div class="section section-memes">
        <div class="section-nerd"></div>
        <div class="section-title">Memes</div>
      </div>
    </a>
  </div>
</div>
