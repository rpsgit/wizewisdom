---
layout: default
title: Geekosystem
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/geekvana-index.png') no-repeat center center fixed;
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
.geek-container {
  display: flex;
  justify-content: center;
  gap: 50px;
  background: rgba(255, 255, 255, 0.7);
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

.section-geek {
  width: 100%;
  height: 100%;
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  z-index: 0;
}

/* Category-specific images */
.section-books .section-geek {
  background-image: url('/assets/images/tech-index.png');
}

.section-quotes .section-geek {
  background-image: url('/assets/images/science-index.png');
}

.section-quotes .section-geek {
  background-image: url('/assets/images/language-index.png');
}
/* You can add more categories like this: */
/*
.section-movies .section-geek {
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
  .geek-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>

<div class="page-container">
  <h1>geekvana</h1>

  <div class="geek-container">

    <a href="/geekosystem/tech/index.html" class="section-link">
      <div class="section section-books">
        <div class="section-geek"></div>
        <div class="section-title">Tech</div>
      </div>
    </a>

    <a href="/geekosystem/science/index.html" class="section-link">
      <div class="section section-quotes">
        <div class="section-geek"></div>
        <div class="section-title">Science</div>
      </div>

    <a href="/geekosystem/language/index.html" class="section-link">
      <div class="section section-quotes">
        <div class="section-geek"></div>
        <div class="section-title">Language</div>
      </div>
  
    </a>

  </div>
</div>
