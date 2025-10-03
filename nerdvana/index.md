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

  /* === MAIN CONTAINER === */
  .nerd-container {
    max-width: 1200px;
    margin: 50px auto;
    text-align: center;
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
  }

  .section {
    position: relative;
    width: 220px;
    height: auto;
    text-align: center;
    cursor: pointer;
    transition: transform 0.25s ease;
  }

  /* Use actual images instead of background blocks */
  .section img {
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
  }

  .section-link:hover img {
    transform: scale(1.08);
  }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    .nerd-container h2 { font-size: 2.2rem; }
    .section { width: 180px; }
    .section-title { font-size: 1.2rem; }
  }

  @media (max-width: 600px) {
    .section { width: 150px; }
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
      <div class="section">
        <img src="/assets/images/book-ic.png" alt="Books">
        <div class="section-title">Books</div>
      </div>
    </a>

    <!-- Quotes Section -->
    <a href="/quotes/quote-index.html" class="section-link">
      <div class="section">
        <img src="/assets/images/quote-ic.png" alt="Quotes">
        <div class="section-title">Quotes</div>
      </div>
    </a>

    <!-- Memes Section -->
    <a href="/nerdvana/meme-index.html" class="section-link">
      <div class="section">
        <img src="/assets/images/meme-ic.png" alt="Memes">
        <div class="section-title">Memes</div>
      </div>
    </a>
  </div>
</div>
