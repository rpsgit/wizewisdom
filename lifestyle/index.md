---
layout: default
title: Lifestyle
---

<style>
.hero {
  position: relative;
  text-align: center;
  color: white;
  margin-bottom: 40px;
}

.hero img {
  width: 100%;
  height: auto;
  border-radius: 20px;
  filter: brightness(0.7);
  cursor: pointer;
}

.hero-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 2px 2px 8px rgba(0,0,0,0.7);
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 20px;
  margin-top: 30px;
}

.grid-item {
  position: relative;
  overflow: hidden;
  border-radius: 16px;
  cursor: pointer;
  box-shadow: 0 4px 10px rgba(0,0,0,0.15);
  transition: transform 0.3s ease;
}

.grid-item img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  filter: brightness(0.7);
  transition: transform 0.3s ease;
}

.grid-item:hover {
  transform: scale(1.03);
}

.grid-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 1.5rem;
  font-weight: bold;
  text-shadow: 2px 2px 6px rgba(0,0,0,0.8);
}
</style>

<!-- Grid of Links -->
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
