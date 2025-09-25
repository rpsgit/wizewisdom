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

/* === CONTAINER INCLUDING TITLE AND CATEGORIES === */
.nerd-container {
  max-width: 1200px;
  margin: 50px auto;
  text-align: center;
  background: rgba(255, 255, 255, 0.7); /* white translucent */
  padding: 50px 60px;
  border-radius: 30px;
  box-shadow: 0 6px 25px rgba(0,0,0,0.2);
  display: flex;
  flex-direction: column; /* title on top, categories below */
  align-items: center;
  gap: 50px; /* space between title and categories */
}

/* === PAGE TITLE INSIDE CONTAINER === */
.nerd-container h1 {
  font-size: 3rem;
  font-weight: 700;
  color: #000;
  margin: 0;
}

/* === CATEGORY WRAPPER === */
.categories-wrapper {
  display: flex;
  justify-content: center;
  flex-wrap: wrap; /* wrap on smaller screens */
  gap: 60px;
}

/* === INDIVIDUAL CATEGORY SECTIONS === */
.section-link {
  text-decoration: none;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.section {
  width: 220px;
  height: 220px;
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease;
}

.section-nerd {
  width: 100%;
  height: 100%;
  background-color: #2C7A7B; /* sophisticated blue-green background */
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

/* Category title below the icon */
.section-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #fff; /* change text to white for contrast */
  text-align: center;
}

.section-link:hover .section-nerd {
  transform: scale(1.08);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .categories-wrapper {
    flex-direction: column;
    align-items: center;
    gap: 40px;
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

<div class="nerd-container">
  <h1>Nerdvana</h1>

  <div class="categories-wrapper">
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
