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
  background: rgba(255, 255, 255, 0.7); /* white translucent */
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
  background-color: #fff; /* solid white background for icons */
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  position: relative;
  z-index: 0;
  border-radius: 15px; /* optional rounded corners for icons */
  box-shadow: 0 2px 10px rgba(0,0,0,0.1); /* subtle shadow for icons */
}

/* Category-specific images */
.section-books .section-geek {
  background-image: url('/assets/images/tech-index.png');
}

.section-science .section-geek {
  background-image: url('/assets/images/science-index.png');
}

.section-language .section-geek {
  background-image: url('/assets/images/language-index.png');
}

.section-title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.4rem;
  font-weight: bold;
  color: #000; /* black text to contrast white icon background */
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
