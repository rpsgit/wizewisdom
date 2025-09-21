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

/* === GRID LAYOUT === */
.section-grid {
  display: flex;
  gap: 30px;
  justify-content: center;
  flex-wrap: wrap; /* allow wrapping on small screens */
}

/* === TENNIS BALL SECTIONS === */
.section-link {
  text-decoration: none;
}

.section {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 180px;
  height: 180px;
  background: rgba(255, 255, 255, 0.6); /* 60% translucent */
  border-radius: 50%;
  cursor: pointer;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  text-align: center;
  box-shadow: 0 0 15px rgba(255, 255, 200, 0.5), 0 0 30px rgba(255, 255, 150, 0.3);
}

.section-ball {
  width: 140px; /* slightly bigger */
  height: 140px; /* slightly bigger */
  background: url('/assets/images/tennis-ball.png') no-repeat center center;
  background-size: contain;
  position: absolute; /* behind the text */
}

.section-title {
  position: relative; /* on top of tennis ball */
  font-size: 1.2rem; /* slightly bigger for visibility */
  font-weight: bold;
  color: #000;
  text-shadow: 2px 2px 5px rgba(255, 255, 255, 0.9), 1px 1px 3px rgba(0,0,0,0.5);
  z-index: 1;
}

.section:hover {
  transform: scale(1.08);
  box-shadow: 0 0 25px 8px rgba(255, 255, 200, 0.7), 0 0 50px 15px rgba(255, 255, 150, 0.5);
}

.links {
  display: none; /* hide links, optional */
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .section-grid {
    flex-direction: column;
    align-items: center;
  }
}
</style>

<div class="page-container">
  <h1>🎾 Tennis</h1>

  <div class="section-grid">

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
