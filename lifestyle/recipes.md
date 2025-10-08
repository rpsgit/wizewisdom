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
    text-align: center;
    padding: 0 15px; /* ✅ Mobile padding */
  }

  /* === PAGE TITLE === */
  h1 {
    display: inline-block;
    color: #000;
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 30px;
    background: none;
    box-shadow: none;
  }

  /* === CONTAINER FOR lemonS === */
  .recipe-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap; /* ✅ Allows wrapping */
    gap: 40px;
    background: rgba(255, 255, 255, 0.7);
    padding: 30px 20px;
    border-radius: 25px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.15);
  }

  /* === INDIVIDUAL lemon SECTIONS === */
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

  .section-lemon {
    width: 100%;
    height: 100%;
    background: url('/assets/images/lemon-ico.png') no-repeat center center;
    background-size: contain;
  }

  .section-title {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.3rem;
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7); /* ✅ Added for readability */
  }

  .section:hover {
    transform: scale(1.08);
  }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    h1 {
      font-size: 2.2rem;
    }
    .recipe-container {
      gap: 30px;
      padding: 20px;
    }
  }

  @media (max-width: 768px) {
    .section {
      width: 160px;
      height: 160px;
    }
    .section-title {
      font-size: 1.2rem;
    }
  }

  @media (max-width: 480px) {
    .section {
      width: 130px;
      height: 130px;
    }
    .section-title {
      font-size: 1rem;
    }
  }
</style>

<div class="page-container">
  <h1>Recipes</h1>

  <div class="recipe-container">

    <a href="/lifestyle/recipe-photos.html" class="section-link">
      <div class="section">
        <div class="section-lemon"></div>
        <div class="section-title">Recipes</div>
      </div>
    </a>

    <a href="/lifestyle/other.html" class="section-link">
      <div class="section">
        <div class="section-lemon"></div>
        <div class="section-title">OTHER</div>
      </div>
    </a>

  </div>
</div>
