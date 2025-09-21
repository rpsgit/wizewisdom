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
  max-width: 900px;
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
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 30px;
  justify-items: center;
}

/* === TENNIS BALL SECTIONS === */
.section-link {
  text-decoration: none;
}

.section {
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
  transition: transform 0.25s ease, box-shadow 0.25s ease;
  border-radius: 50%;
}

.section:hover {
  transform: scale(1.08);
  box-shadow: 0 0 20px 5px rgba(255, 255, 0, 0.6), 0 0 40px 10px rgba(255, 255, 0, 0.3);
}

.section-title {
  font-size: 1.1rem;
  font-weight: bold;
  color: #000;
  margin-bottom: 10px;
  text-shadow: 1px 1px 3px rgba(255, 255, 255, 0.7);
}

.links {
  font-size: 0.9rem;
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

    <a href="/lifestyle/camp-aguinaldo-photos.html" class="section-link">
      <div class="section">
        <div class="section-title">Camp Aguinaldo</div>
        <div class="links">
          <a href="/lifestyle/camp-aguinaldo-photos.html" target="_blank">📷</a>
          <a href="/lifestyle/camp-aguinaldo-videos.html" target="_blank">📺</a>
        </div>
      </div>
    </a>

    <a href="/lifestyle/tournament-photos.html" class="section-link">
      <div class="section">
        <div class="section-title">Tournament, etc...</div>
        <div class="links">
          <a href="/lifestyle/tournament-photos.html" target="_blank">📷</a>
          <a href="/lifestyle/tournament-videos.html" target="_blank">📺</a>
        </div>
      </div>
    </a>

    <a href="/lifestyle/other-photos.html" class="section-link">
      <div class="section">
        <div class="section-title">Other Photos</div>
        <div class="links">
          <a href="/lifestyle/other-photos.html" target="_blank">📷</a>
          <a href="/lifestyle/other-videos.html" target="_blank">📺</a>
        </div>
      </div>
    </a>

  </div>
</div>
