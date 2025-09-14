---
layout: default
title: Lifestyle
---

<style>
.container {
  background: rgba(255, 255, 255, 0.7); /* 70% translucent white */
  max-width: 1000px;
  margin: 30px auto;
  padding: 25px;
  border-radius: 20px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

.grid {
  display: flex;
  flex-direction: column;
  gap: 25px;
  margin-top: 20px;
  height: 100vh; /* Full screen height on desktops */
}

.grid-item {
  position: relative;
  flex: 1; /* Equal height distribution */
  overflow: hidden;
  border-radius: 16px;
  cursor: pointer;
  box-shadow: 0 4px 10px rgba(0,0,0,0.15);
  transition: transform 0.3s ease;
}

.grid-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: brightness(0.7);
  transition: transform 0.3s ease;
}

.grid-item:hover {
  transform: scale(1.02);
}

.grid-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 2px 2px 6px rgba(0,0,0,0.8);
}

/* 📱 Responsive Design */
@media (max-width: 768px) {
  .grid {
    height: auto; /* Let content define height on smaller screens */
  }
  .grid-item {
    height: 220px; /* Fixed smaller height per section */
  }
  .grid-item img {
    height: 100%;
  }
  .grid-text {
    font-size: 1.5rem; /* Slightly smaller text for phones */
  }
}
</style>

<div class="container">
  <h2 style="text-align:center; margin-bottom:20px;">Lifestyle</h2>

  <div class="grid">
    <div class="grid-item" onclick="window.location.href='/lifestyle/recipes.html'">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQSOardx2EZRTLY_X7-H3Rl4AVrnu8fnNhaMfnGlBlXjGvw?width=800&height=600" alt="Recipes">
      <div class="grid-text">🍳 Recipes</div>
    </div>

    <div class="grid-item" onclick="window.location.href='/lifestyle/tennis.html'">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=800&height=600" alt="Tennis">
      <div class="grid-text">🎾 Tennis</div>
    </div>

    <div class="grid-item" onclick="window.location.href='/lifestyle/pickleball.html'">
      <img src="https://1drv.ms/i/c/6118ddcb5316a0a9/IQQBVlpUl-cZT4yMuAvkWm-UARFv-Ku8ZQEGj3yNL2K3wrw?width=800&height=600" alt="Pickleball">
      <div class="grid-text">🏓 Pickleball</div>
    </div>
  </div>
</div>
