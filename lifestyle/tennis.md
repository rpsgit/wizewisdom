---
layout: default
title: Tennis
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/tennis-index.png') no-repeat center center fixed;
    background-size: cover;
    font-family: Arial, sans-serif;
  }

  .page-container {
    max-width: 1000px;
    margin: 40px auto;
    text-align: center;
    padding: 0 15px; /* ✅ Padding for smaller screens */
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

  /* === CONTAINER FOR TENNIS BALLS === */
  .tennis-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap; /* ✅ Allows wrapping on smaller screens */
    gap: 40px;
    background: rgba(255, 255, 255, 0.7);
    padding: 30px 20px;
    border-radius: 25px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.15);
  }

  /* === INDIVIDUAL TENNIS BALL SECTIONS === */
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

  .section-ball {
    width: 100%;
    height: 100%;
    background: url('/assets/images/tennis-ball.png') no-repeat center center;
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
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7); /* ✅ Added back subtle shadow for readability */
  }

  .section:hover {
    transform: scale(1.08);
  }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    h1 {
      font-size: 2.2rem;
    }
    .tennis-container {
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
  <h1>Tennis</h1>

  <div class="tennis-container">

    <a href="/lifestyle/updtc-photos.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">UPDTC</div>
      </div>
    </a>

    <a href="/lifestyle/camp-photos.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">CAMP</div>
      </div>
    </a>

    <a href="/lifestyle/tourney-photos.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">TOURNEY</div>
      </div>
    </a>

    <a href="/lifestyle/other.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">OTHER</div>
      </div>
    </a>

  </div>
</div>
