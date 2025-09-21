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
}

h1 {
  text-align: center;
  color: #222;
  margin-bottom: 40px;
  font-size: 2rem;
}

/* === CONTAINER FOR ALL TENNIS BALLS === */
.tennis-container {
  display: flex;
  justify-content: center;
  gap: 30px;
  background: rgba(255, 255, 255, 0.6); /* translucent oblong background */
  padding: 25px 40px;
  border-radius: 25px;
  flex-wrap: wrap; /* wraps on smaller screens */
  box-shadow: 0 4px 20px rgba(0,0,0,0.15);
}

/* === INDIVIDUAL TENNIS BALL SECTIONS === */
.section-link {
  text-decoration: none;
}

.section {
  position: relative;
  width: 140px;
  height: 140px;
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.section-ball {
  width: 100%;
  height: 100%;
  background: url('/assets/images/tennis-ball.png') no-repeat center center;
  background-size: contain;
  position: relative;
  z-index: 0;
}

.section-title {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 1.1rem;
  font-weight: bold;
  color: #000;
  text-shadow: 2px 2px 5px rgba(255,255,255,0.9), 1px 1px 3px rgba(0,0,0,0.5);
  z-index: 1;
}

.section:hover {
  transform: scale(1.08);
  box-shadow: 0 0 25px 8px rgba(255, 255, 200, 0.7), 0 0 50px 15px rgba(255, 255, 150, 0.5);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .tennis-container {
    flex-direction: column;
    align-items: center;
  }
}
</style>

<div class="page-container">
  <h1>🎾 Tennis</h1>

  <div class="tennis-container">

    <a href="/lifestyle/updtc-photos.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">UPDTC</div>
      </div>
    </a>

    <a href="/lifestyle/camp.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">CAMP</div>
      </div>
    </a>

    <a href="/lifestyle/tournament-photos.html" class="section-link">
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
