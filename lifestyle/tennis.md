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
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 180px;
  height: 180px;
  background: url('/assets/images/tennis-ball.png') no-repeat center center;
  background-size: contain;
  text-align: center;
  cursor: pointer;
  border-radius: 50%;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  z-index: 1;
}

.section:hover {
  transform: scale(1.08);
  box-shadow: 0 0 20px 5px rgba(255, 255, 255, 0.6), 0 0 40px 10px rgba(255, 255, 255, 0.3);
}

/* === GLASS EFFECT BEHIND TENNIS BALL === */
.section::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.3);
  backdrop-filter: blur(6px);
  z-index: -1;
}

.section-title {
  font-size: 1.1rem;
  font-weight: bold;
  color: #000;
  margin-bottom: 10px;
  text-shadow: 1px 1px 3px rgba(255, 255, 255, 0.7);
  z-index: 2;
}

.links {
  font-size: 0.9rem;
  z-index: 2;
}

.links a {
  display: inline-block;
  margin: 0 5px;
  text-decoration: none;
  color: #0056b3;
  font-weight: 600;
}

.links a:hover {
  text-decoration: underline;
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
        <div class="section-title">UPDTC</div>
        <div class="links">
          <a href="/lifestyle/updtc-photos.html" target="_blank">📷</a>
          <a href="/lifestyle/updtc-videos.html" target="_blank">📺</a>
        </div>
      </div>
    </a>

    <a href="/lifestyle/camp.html" class="section-link">
      <div class="section">
        <div class="section-title">CAMP</div>
        <div class="links">
          <a href="/lifestyle/camp-photos.html" target="_blank">📷</a>
          <a href="/lifestyle/camp-videos.html" target="_blank">📺</a>
        </div>
      </div>
    </a>

    <a href="/lifestyle/tournament-photos.html" class="section-link">
      <div class="section">
        <div class="section-title">TOURNEY</div>
        <div class="links">
          <a href="/lifestyle/tournament-photos.html" target="_blank">📷</a>
          <a href="/lifestyle/tournament-videos.html" target="_blank">📺</a>
        </div>
      </div>
    </a>

    <a href="/lifestyle/other.html" class="section-link">
      <div class="section">
        <div class="section-title">Other</div>
        <div class="links">
          <a href="/lifestyle/others.html" target="_blank">📷</a>
          <a href="/lifestyle/other-videos.html" target="_blank">📺</a>
        </div>
      </div>
    </a>

  </div>
</div>
