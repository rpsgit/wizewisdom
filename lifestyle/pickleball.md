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
    padding: 0 15px;
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

  /* === CONTAINER FOR PICKLE BALLS === */
  .pickle-container {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 40px;
    background: rgba(255, 255, 255, 0.7);
    padding: 30px 20px;
    border-radius: 25px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.15);
    margin-bottom: 30px;
  }

  /* === INDIVIDUAL PICKLE BALL SECTIONS === */
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
    background: url('/assets/images/pickle-ball.png') no-repeat center center;
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
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.7);
  }

  .section:hover {
    transform: scale(1.08);
  }

  /* === YOUTUBE PLACEHOLDER === */
  .youtube-placeholder {
    background: rgba(0, 0, 0, 0.7);
    border-radius: 20px;
    padding: 20px;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    max-width: 700px;
    margin: 0 auto 40px auto;
  }

  .youtube-placeholder h2 {
    color: #fff;
    margin-bottom: 15px;
  }

  .youtube-embed {
    position: relative;
    padding-bottom: 56.25%; /* 16:9 */
    height: 0;
    overflow: hidden;
    border-radius: 12px;
  }

  .youtube-embed iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: none;
  }

  /* === FALLBACK LINK === */
  .youtube-fallback {
    margin-top: 12px;
  }
  .youtube-fallback a {
    display: inline-block;
    color: #ffdd57;
    text-decoration: none;
    font-weight: bold;
    padding: 8px 16px;
    border: 2px solid #ffdd57;
    border-radius: 8px;
    transition: background 0.3s ease, color 0.3s ease;
  }
  .youtube-fallback a:hover {
    background: #ffdd57;
    color: #000;
  }

  /* === RESPONSIVE === */
  @media (max-width: 1024px) {
    h1 {
      font-size: 2.2rem;
    }
    .pickle-container {
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
  <h1>Pickleball</h1>

  <div class="youtube-placeholder">
    <h2>🏓 Lemon Drop</h2>
    <div class="youtube-embed">
      <iframe
        src="https://www.youtube.com/embed?listType=playlist&list=UU3CbvjtmMUsmuSgBCWQh0Wg"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
      </iframe>
    </div>
    <div class="youtube-fallback">
      <a href="https://www.youtube.com/channel/UC3CbvjtmMUsmuSgBCWQh0Wg" target="_blank">
        📺 Watch on YouTube
      </a>
    </div>
  </div>

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
