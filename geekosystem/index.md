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

/* === CONTAINER INCLUDING TITLE AND CATEGORIES === */
.geek-container {
  max-width: 1200px;
  margin: 50px auto;
  text-align: center;
  background: rgba(255, 255, 255, 0.7); /* white translucent */
  padding: 50px 60px;
  border-radius: 30px;
  box-shadow: 0 6px 25px rgba(0,0,0,0.2);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 50px;
}

/* === PAGE TITLE INSIDE CONTAINER === */
.geek-container h1 {
  font-size: 3rem;
  font-weight: 700;
  color: #000;
  margin: 0;
}

/* === INDIVIDUAL CATEGORY SECTIONS === */
.section-link {
  text-decoration: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  position: relative;
}

.section {
  width: 220px;
  height: 220px;
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease;
  position: relative;
}

.section-geek {
  width: 100%;
  height: 100%;
  background-color: rgba(44, 122, 123, 0.85); /* semi-transparent blue-green */
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 15px;
}

/* Category-specific images */
.section-books .section-geek {
  background-image: url('/assets/images/tech-icon.png');
}

.section-science .section-geek {
  background-image: url('/assets/images/science-icon.png');
}

.section-language .section-geek {
  background-image: url('/assets/images/language-icon.png');
}

/* Category name overlay on top of icon */
.section-title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.5rem;
  font-weight: bold;
  color: #fff;
  text-align: center;
  text-shadow: 2px 2px 4px rgba(0,0,0,0.7);
  pointer-events: none; /* clicks go to the icon */
}

.section-link:hover .section-geek {
  transform: scale(1.08);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .geek-container {
    gap: 30px;
    padding: 30px 20px;
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

<div class="geek-container">
  <h2>Geekosystem</h2>

   <div class="categories-wrapper" style="display: flex; justify-content: center; flex-wrap: wrap; gap: 60px;">
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
        <div class="section-title">Language</div>
      </div>
    </a>
  </div>
</div>
