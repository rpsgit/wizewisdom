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

/* === PAGE TITLE === */
h1 {
  display: inline-block;
  padding: 15px 30px;
  border-radius: 15px;
  color: #fff; /* White text */
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 40px;
  text-shadow: 2px 2px 8px rgba(0, 0, 0, 0.7); /* subtle dark shadow for contrast */
  background: none; /* ✅ Removed white background */
  box-shadow: none;
}

/* === CONTAINER FOR ALL TENNIS BALLS === */
.tennis-container {
  display: flex;
  justify-content: center;
  gap: 40px;
  background: rgba(255, 255, 255, 0.7);
  padding: 30px 45px;
  border-radius: 25px;
  flex-wrap: wrap;
  box-shadow: 0 4px 20px rgba(0,0,0,0.15);
}

/* === INDIVIDUAL TENNIS BALL SECTIONS === */
.section-link {
  text-decoration: none;
}

.section {
  position: relative;
  width: 182px;  /* ✅ 30% bigger */
  height: 182px; /* ✅ 30% bigger */
  text-align: center;
  cursor: pointer;
  transition: transform 0.25s ease;
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
  font-size: 1.4rem; /* slightly bigger for balance */
  font-weight: bold;
  color: #fff; /* ✅ White text */
  text-shadow: 
    0 0 6px #adff2f,   /* ✅ Yellow-green glow */
    0 0 10px #adff2f, 
    2px 2px 6px rgba(0,0,0,0.6); /* slight dark shadow for readability */
  z-index: 1;
}

.section:hover {
  transform: scale(1.08);
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
  <h1>Tennis</h1>

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
