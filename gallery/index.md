---
layout: default
title: Gallery
---

<style>
/* === BODY & PAGE CONTAINER === */
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/gallery-index.png') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
  color: #222;
}

.page-container {
  max-width: 900px;
  margin: 50px auto;
  background: rgba(255, 255, 255, 0.88);
  padding: 35px 25px;
  border-radius: 25px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
  text-align: center;
}

/* === HOME BUTTON ICON === */
.home-button {
  position: fixed;
  top: 20px;
  left: 20px;
  z-index: 1000;
  display: inline-block;
  width: 40px;
  height: 40px;
  text-decoration: none;
}

.home-icon {
  width: 100%;
  height: 100%;
  display: block;
  background: url('/assets/images/home-icon.png') no-repeat center center;
  background-size: contain;
}

/* === HEADINGS === */
h1 {
  text-align: center;
  font-size: 3rem;
  color: #000;
  margin-bottom: 30px;
}

h2 {
  color: #333;
  font-size: 1.6rem;
  margin: 25px 0 15px;
}

/* === EMBED CARDS === */
.embed-card {
  background: rgba(255, 255, 255, 0.95);
  border-radius: 20px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.1);
  padding: 20px;
  margin: 25px 0;
  overflow: hidden;
}

.embed-card iframe {
  width: 100%;
  height: 400px;
  border: none;
  border-radius: 15px;
}

.embed-card img {
  width: 100%;
  height: auto;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}

/* === RESPONSIVE === */
@media (max-width: 768px) {
  .page-container {
    padding: 25px 15px;
  }
  h1 {
    font-size: 2.2rem;
  }
  iframe {
    height: 300px;
  }
}
</style>

<!-- Home Button -->
<a href="https://www.wizewisdom.com/" class="home-button">
  <span class="home-icon"></span>
</a>

<div class="page-container">
  <h1>📸 Lenscape</h1>

  <!-- === OneDrive Embeds === -->
  <div class="embed-card">
    <img 
      src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQTQ6Pc4rWAkS5Odign3w7yAAcSapN01g741NQenf6oGoNc?width=4000&height=1868" 
      alt="Landscape Collection" 
      loading="lazy"
    />
  </div>

  <!-- === OneDrive Embeds === -->
  <div class="embed-card">
    <img 
      src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQS_c77d-ZL5QaVzc5JihRlKAai7mLU39Myiw0Mm16Vbj-Q?width=3679&height=1868" 
      alt="Landscape Collection" 
      loading="lazy"
    />
  </div>

  <div class="embed-card">
    <img 
      src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSnv4nA-7HpSq5qbowW7rdLASFCt3cWTbGqujq0F-23Bm0?width=4000&height=3000" 
      alt="Landscape Collection"
      loading="lazy"
    />
  </div>

  <div class="embed-card">
    <img 
      src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSW8dr4WOtRTpomBuB8NXKaAR7XyRDCBXYdA3aISh4XEAY?width=4000&height=1868" 
      alt="Landscape Collection" 
      loading="lazy"
    />
  </div>

</div>
