---
layout: default
title: Lifestyle
---

<style>
.hero {
  position: relative;
  text-align: center;
  color: white;
  margin-bottom: 30px;
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
.links {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
  margin-top: 20px;
}
.links a {
  background: rgba(255, 255, 255, 0.8);
  padding: 12px 20px;
  border-radius: 12px;
  text-decoration: none;
  color: #333;
  font-weight: bold;
  transition: 0.3s ease;
  box-shadow: 0 3px 6px rgba(0,0,0,0.1);
}
.links a:hover {
  background: rgba(255, 255, 255, 1);
  transform: scale(1.05);
}
</style>

<div class="hero" onclick="window.location.href='/lifestyle/recipes'">
  <img src="/assets/images/lifestyle-hero.jpg" alt="Lifestyle">
</div>

<div class="links">
  <a href="[/lifestyle/recipes](https://1drv.ms/i/c/6118ddcb5316a0a9/IQSOardx2EZRTLY_X7-H3Rl4AVrnu8fnNhaMfnGlBlXjGvw?width=1024&height=685)">🍳 Recipes</a>
  <a href="/[lifestyle/tennis](https://1drv.ms/i/c/6118ddcb5316a0a9/IQR6-Q_lDeTgTL1ExpM3ukK-Ac68m5EqMxbAFlgyW8I5vs0?width=4000&height=1868)">🎾 Tennis</a>
  <a href="[/lifestyle/pickleball](https://1drv.ms/i/c/6118ddcb5316a0a9/IQQBVlpUl-cZT4yMuAvkWm-UARFv-Ku8ZQEGj3yNL2K3wrw?width=2271&height=1109)">🏓 Pickleball</a>
</div>
