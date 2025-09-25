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
  max-width: 1200px; /* made container wider */
  margin: 50px auto;
  text-align: center;
}

/* === PAGE TITLE === */
h1 {
  display: inline-block;
  padding: 20px 40px;
  border-radius: 15px;
  color: #000;
  font-size: 3rem; /* larger font */
  font-weight: 700;
  margin-bottom: 50px;
  text-shadow: none;
  background: none;
  box-shadow: none;
}

/* === CONTAINER FOR CATEGORIES === */
.nerd-container {
  display: flex;
  justify-content: center;
  gap: 60px;
  background: rgba(255, 255, 255, 0.7); /* white translucent */
  padding: 50px 60px; /* larger padding */
  border-radius: 30px;
  box-shadow: 0 6px 25px rgba(0,0,0,0.2); /* slightly stronger shadow */
}

/* === INDIVIDUAL CATEGORY SECTIONS === */
.section-link {
  text-decoration: none;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.section {
  width: 220px; /* larger icon container */
  height: 220px;
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease;
}

.section-nerd {
  width: 100%;
  height: 100%;
  background-color: transparent; /* removed white background */
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 15px;
  margin-bottom: 15px;
}

/* Category-specific images */
.section-books .section-nerd {
  background-image: url('/assets/images/book-index.png');
}

.section-quotes .section-nerd {
  background-image: url('/assets/images/quote-index.png');
}

.section-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #000;
  text-align: center;
}

.section-link:hover .section-nerd {
  transform: scale(1.08);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .nerd-container {
    flex-direction: column;
    align-items: center;
  }

  .section {
    width: 180px;
    height: 180px;
  }

  .section-title {
    font-size: 1.3rem;
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
