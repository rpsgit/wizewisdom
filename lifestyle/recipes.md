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
    max-width: 800px;
    margin: 60px auto;
    text-align: center;
    padding: 0 15px;
  }

  /* === PAGE TITLE === */
  h1 {
    color: #000;
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 40px;
  }

  /* === RECIPE LIST CONTAINER === */
  .recipe-list {
    background: rgba(255, 255, 255, 0.7);
    padding: 30px 25px;
    border-radius: 25px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.15);
    text-align: left;
  }

  /* === INDIVIDUAL RECIPE LINKS === */
  .recipe-item {
    display: flex;
    align-items: center;
    margin-bottom: 20px;
    text-decoration: none;
    transition: transform 0.2s ease;
  }

  .recipe-item:hover {
    transform: translateX(5px);
  }

  .recipe-icon {
    width: 40px;
    height: 40px;
    background: url('/assets/images/lemon-ico.png') no-repeat center center;
    background-size: contain;
    margin-right: 15px;
    flex-shrink: 0;
  }

  .recipe-text {
    font-size: 1.3rem;
    font-weight: 600;
    color: #000;
  }

  .recipe-item:hover .recipe-text {
    color: #333;
  }

  /* === RESPONSIVE === */
  @media (max-width: 768px) {
    .recipe-text { font-size: 1.1rem; }
    .recipe-icon { width: 32px; height: 32px; }
  }

  @media (max-width: 480px) {
    h1 { font-size: 2rem; }
    .recipe-list { padding: 20px; }
    .recipe-item { margin-bottom: 15px; }
    .recipe-text { font-size: 1rem; }
    .recipe-icon { width: 28px; height: 28px; }
  }
</style>

<div class="page-container">
  <h1>Recipes</h1>

  <div class="recipe-list">
    <a href="/lifestyle/recipe/recipe-photos.html" class="recipe-item">
      <div class="recipe-icon"></div>
      <div class="recipe-text">Recipe Photos</div>
    </a>


    <a href="/lifestyle/desserts.html" class="recipe-item">
      <div class="recipe-icon"></div>
      <div class="recipe-text">Desserts</div>
    </a>

    <a href="/lifestyle/savory.html" class="recipe-item">
      <div class="recipe-icon"></div>
      <div class="recipe-text">Savory Dishes</div>
    </a>

    <a href="/lifestyle/drinks.html" class="recipe-item">
      <div class="recipe-icon"></div>
      <div class="recipe-text">Drinks & Smoothies</div>
    </a>

    <a href="/lifestyle/other.html" class="recipe-item">
      <div class="recipe-icon"></div>
      <div class="recipe-text">Other Recipes</div>
    </a>
  </div>
</div>
