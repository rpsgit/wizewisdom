---
layout: default
title: Lifestyle
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/lifestyle-index.png') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
  color: #000;
}

/* ✅ Single Translucent Container */
.container {
  background: rgba(255, 255, 255, 0.7); /* 70% translucent white */
  max-width: 1000px;
  margin: 30px auto;
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
  text-align: center;
}

/* ✅ Heading inside the box */
.container h2 {
  font-size: 2rem;
  margin-bottom: 20px;
  color: #000; /* Keep text black for contrast */
}

/* ✅ Responsive Grid Layout */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 25px;
}

/* ✅ Grid Item Styling */
.grid-item {
  position: relative;
  border-radius: 16px;
  overflow: hidden;
  cursor: pointer;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}

.grid-item:hover {
  transform: scale(1.02);
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.3);
}

/* ✅ Image Styling */
.grid-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  filter: brightness(0.7);
  display: block;
}

/* ✅ Text Overlay Styling */
.grid-text {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: white;
  font-size: 2rem;
  font-weight: bold;
  text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.8);
}

@media (max-width: 768px) {
  .grid {
    grid-template-columns: 1fr;
  }

  .grid-text {
    font-size: 1.5rem;
  }
}
</style>

<div class="container">
  <h2>Lifestyle</h2>

  <div class="grid">
    <div class="grid-item" onclick="window.location.href='/lifestyle/tennis.html'">
      <img src="/assets/images/play.jpg" alt="Tennis">
      <div class="grid-text">Tennis</div>
    </div>

    <div class="grid-item" onclick="window.location.href='/lifestyle/pickleball.html'">
      <img src="/assets/images/pickle.jpg" alt="Pickleball">
      <div class="grid-text">Pickleball</div>
    </div>

    <div class="grid-item" onclick="window.location.href='/lifestyle/recipes.html'">
      <img src="/assets/images/eat.jpg" alt="Recipes">
      <div class="grid-text">Recipes</div>
    </div>
  </div>
</div>
