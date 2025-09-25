---
layout: default
title: Nerdvana
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/nerdvana-index.png') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
}

.page-container {
  max-width: 1000px;
  margin: 40px auto;
  text-align: center;
}

/* === PAGE TITLE === */
h1 {
  display: inline-block;
  padding: 15px 30px;
  border-radius: 15px;
  color: #000;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 40px;
  text-shadow: none;
  background: none;
  box-shadow: none;
}

/* === CONTAINER FOR CATEGORIES === */
.nerd-container {
  display: flex;
  justify-content: center;
  gap: 50px;
  background: rgba(128, 128, 128, 0.7); /* gray translucent */
  padding: 30px 45px;
  border-radius: 25px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.15);
}

/* === INDIVIDUAL CATEGORY SECTIONS === */
.section-link {
  text-decoration: none;
}

.section {
  position: relative;
  width: 200px;
  height: 200px;
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease;
}

.section-nerd {
  width: 100%;
  height: 100%;
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  z-index: 0;
}

/* Category-specific images */
.section-books .section-nerd {
  background-image: url('/assets/images/book-index.png');
}

.section-quotes .section-nerd {
  background-image: url('/assets/images/quote-index.png');
}

/* You can add more categories like this: */
/*
.section-movies .section-nerd {
  background-image: url('/assets/images/movies-icon.png');
}
*/

.section-title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.4rem;
  font-weight: bold;
  color: #fff;
  text-shadow: none;
  z-index: 1;
}

.section:hover {
  transform: scale(1.08);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .nerd-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>

<div class="page-container">
  <h1>Nerdvana</h1>

  <div class="nerd-container">

    <a href="/books/index.html" class="section-link">
      <div class="section section-books">
        <div class="section-nerd"></div>
        <div class="section-title">Books</div>
      </div>
    </a>

    <a href="/quotes/index.html" class="section-link">
      <div class="section section-quotes">
        <div class="section-nerd"></div>
        <div class="section-title">Quotes</div>
      </div>
    </a>

  </div>
</div>
