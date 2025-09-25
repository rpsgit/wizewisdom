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

.page-container {
  max-width: 1200px;
  margin: 50px auto;
  text-align: center;
}

/* === PAGE TITLE === */
h1 {
  display: inline-block;
  padding: 20px 40px;
  border-radius: 15px;
  color: #000;
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 50px;
  text-shadow: none;
  background: none;
  box-shadow: none;
}

/* === CONTAINER FOR CATEGORIES === */
.geek-container {
  display: flex;
  justify-content: center;
  gap: 60px;
  background: rgba(255, 255, 255, 0.7); /* white translucent */
  padding: 50px 60px;
  border-radius: 30px;
  box-shadow: 0 6px 25px rgba(0,0,0,0.2);
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

.section-geek {
  width: 100%;
  height: 100%;
  background-color: transparent; /* transparent background */
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  border-radius: 15px;
  margin-bottom: 15px;
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

/* Category title below the icon */
.section-title {
  font-size: 1.5rem;
  font-weight: bold;
  color: #000;
  text-align: center;
}

.section-link:hover .section-geek {
  transform: scale(1.08);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .geek-container {
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
  <h1>Geekosystem</h1>

  <div class="geek-container">

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
