---
layout: default
title: Pickleball
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/pickleball-index.png') no-repeat center center fixed;
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
  color: #000; /* Black text */
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 40px;
  text-shadow: none;
  background: none;
  box-shadow: none;
}

/* === CONTAINER FOR ALL PICKLE BALLS === */
.pickle-container {
  display: flex; /* horizontal layout */
  justify-content: center;
  gap: 50px; /* space between balls */
  background: rgba(255, 255, 255, 0.7);
  padding: 30px 45px;
  border-radius: 25px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.15);
}

/* === INDIVIDUAL PICKLE BALL SECTIONS === */
.section-link {
  text-decoration: none;
}

.section {
  position: relative;
  width: 200px;  /* slightly bigger, similar to Tennis */
  height: 200px; 
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease;
}

.section-ball {
  width: 100%;
  height: 100%;
  background: url('/assets/images/pickle-ball.png') no-repeat center center;
  background-size: contain;
  position: relative;
  z-index: 0;
}

.section-title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.4rem; /* slightly bigger for balance */
  font-weight: bold;
  color: #fff; /* ✅ White text */
  text-shadow: none; /* removed shadow */
  z-index: 1;
}

.section:hover {
  transform: scale(1.08);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .pickle-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>

<div class="page-container">
  <h1>Pickleball</h1>

  <div class="pickle-container">

    <a href="/lifestyle/pickle-photos.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">Tiende</div>
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
