---
layout: default
title: Pickleball
---

<style>
  /* === BODY & PAGE CONTAINER === */
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

  h1 {
    display: inline-block;
    color: #000;
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 30px;
  }

  /* === FLEX CONTAINER FOR PICKLEBALL === */
  .pickle-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: nowrap; /* horizontal on desktop */
    gap: 40px;
    background: rgba(255, 255, 255, 0.7);
    padding: 30px 20px;
    border-radius: 25px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.15);
    margin-bottom: 30px;
    overflow-x: auto; /* allow horizontal scroll if needed */
  }

  .section-link {
    text-decoration: none;
    display: flex;
    justify-content: center;
  }

  /* === CATEGORY BALLS 20% SMALLER === */
  .section {
    position: relative;
    width: 160px; /* 200px × 0.8 */
    height: 160px;
    text-align: center;
    cursor: pointer;
    transition: transform 0.25s ease;
    flex-shrink: 0; /* prevent shrinking in horizontal layout */
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
    font-size: 1.05rem; /* scaled down */
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
    padding-bottom: 56.25%; /* 16:9 ratio */
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
    .pickle-container {
      flex-wrap: wrap; /* wrap on tablets */
      gap: 30px;
    }
  }

  @media (max-width: 768px) {
    .section {
      width: 130px;
      height: 130px;
    }
    .section-title {
      font-size: 0.85rem;
    }
  }

  @media (max-width: 480px) {
    .pickle-container {
      gap: 20px;
    }
    .section {
      width: 100px;
      height: 100px;
    }
    .section-title {
      font-size: 0.7rem;
    }
  }
</style>

<div class="page-container">
  <h1>Pickleball</h1>

  <div class="youtube-placeholder">
    <h2>Lemon Drop</h2>
    <div class="youtube-embed">
      <iframe
        src="https://www.youtube.com/embed/videoseries?list=UU3CbvjtmMUsmuSgBCWQh0Wg"
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen>
      </iframe>
    </div>
    <div class="youtube-fallback">
      <a href="https://www.youtube.com/channel/UC3CbvjtmMUsmuSgBCWQh0Wg" target="_blank">
        Watch on YouTube
      </a>
    </div>
  </div>

  <div class="pickle-container">
    <a href="/lifestyle/lsgh-photos.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">LSGH</div>
      </div>
    </a>

    <a href="/lifestyle/tiende-photos.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">TIENDE</div>
      </div>
    </a>

    <a href="/lifestyle/other.html" class="section-link">
      <div class="section">
        <div class="section-ball"></div>
        <div class="section-title">POTPOURRI</div>
      </div>
    </a>
  </div>
</div>
