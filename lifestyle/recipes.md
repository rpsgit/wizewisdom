---
layout: default
title: Recipes
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/recipe-index.png') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
}

.page-container {
  max-width: 1000px;
  margin: 40px auto;
  background: rgba(255, 255, 255, 0.7); /* 70% translucent */
  padding: 40px;
  border-radius: 25px;
  box-shadow: 0 8px 30px rgba(0,0,0,0.35);
  text-align: center;
  line-height: 1.6;
}

/* === PAGE TITLE === */
h1 {
  display: inline-block;
  background: rgba(255, 255, 255, 0.7); /* 70% translucent */
  padding: 15px 30px;
  border-radius: 15px;
  color: #111;
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 40px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

/* === CONTAINER FOR ALL SPOONS === */
.recipe-container {
  display: flex;
  justify-content: center;
  gap: 36px; /* increased for bigger spoons */
  background: rgba(255, 255, 255, 0.7); /* 70% translucent */
  padding: 30px 45px; /* increased for spacing */
  border-radius: 25px;
  flex-wrap: wrap;
  box-shadow: 0 4px 20px rgba(0,0,0,0.15);
}

/* === INDIVIDUAL SPOON SECTIONS === */
.section-link {
  text-decoration: none;
}

.section {
  position: relative;
  width: 168px;  /* 20% bigger */
  height: 168px; /* 20% bigger */
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease;
}

.section-spoon {
  width: 100%;
  height: 100%;
  background: url('/assets/images/spoon.png') no-repeat center center;
  background-size: contain;
  position: relative;
  z-index: 0;
}

.section-title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.3rem; /* increased proportionally */
  font-weight: bold;
  color: #000;
  text-shadow: 2px 2px 5px rgba(255,255,255,0.9), 1px 1px 3px rgba(0,0,0,0.5);
  z-index: 1;
}

.section:hover {
  transform: scale(1.08); /* keeps hover subtle */
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .recipe-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>

<div class="page-container">
  <h1>Recipes</h1>

  <div class="spoon-container">

    <a href="/lifestyle/recipe-photos.html" class="section-link">
      <div class="section">
        <div class="section-spoon"></div>
        <div class="section-title">Recipes</div>
      </div>
    </a>


    <a href="/lifestyle/other.html" class="section-link">
      <div class="section">
        <div class="section-spoon"></div>
        <div class="section-title">OTHER</div>
      </div>
    </a>

  </div>
</div>
