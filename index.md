---
layout: home
title: "Wizewisdom World"
---

<style>
  /* Main container */
  .blog-container {
    text-align: center;
    background: rgba(255, 255, 255, 0.6);
    padding: 30px;
    border-radius: 25px;
    max-width: 700px;
    margin: auto;
    box-shadow: 0 4px 15px rgba(0,0,0,0.2);
    font-family: Arial, sans-serif;
  }

  .links {
    display: flex;
    flex-direction: column;
    gap: 12px;
    align-items: center;
  }

  .links a {
    display: inline-block;
    background: rgba(255, 255, 255, 0.75);
    padding: 12px 18px;
    border-radius: 15px;
    text-decoration: none;
    font-weight: bold;
    box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    transition: transform 0.25s ease;
  }

  .links a:hover {
    transform: scale(1.05);
  }

  /* Icon grid */
  .icon-grid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 25px;
    margin-top: 12vh;
  }

  .icon-card {
    position: relative;
    width: 270px;
    text-align: center;
    text-decoration: none;
    transition: transform 0.25s ease;
  }

  .icon-card img {
    width: 120px;
    height: 120px;
    display: block;
    margin: auto;
  }

  .icon-card span {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.2rem; /* ✅ 20% smaller */
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.7);
    pointer-events: none;
  }

  .icon-card:hover img {
    transform: scale(1.08);
  }

  /* Responsive */
  @media (max-width: 768px) {
    .icon-grid { gap: 15px; }
    .icon-card { width: 200px; }
    .icon-card img { width: 90px; height: 90px; }
    .icon-card span { font-size: 1rem; }
  }

  @media (max-width: 480px) {
    .icon-card { width: 150px; }
    .icon-card img { width: 70px; height: 70px; }
    .icon-card span { font-size: 0.85rem; }
  }
</style>

<div class="blog-container">
  <h2 style="margin-bottom: 20px;">✨ Choose a Blog ✨</h2>
  <div class="links">
    <a href="https://lemons2lemonades.blogspot.com/">🍋 Lemons To Lemonades</a>
    <a href="https://featuresofinterestcom.wordpress.com/">⭐ Features Of Interest</a>
    <a href="https://notorandom.wordpress.com/">🎲 No To Random</a>
  </div>
</div>

<div class="icon-grid">
  <a href="/nerdvana/index.html" class="icon-card">
    <img src="/assets/images/nerdvana-ico.png" alt="Nerdvana Icon">
    <span>Nerdvana</span>
  </a>

  <a href="/geekosystem/index.html" class="icon-card">
    <img src="/assets/images/geekosystem-ico.png" alt="Geekosystem Icon">
    <span>Geekosystem</span>
  </a>

  <a href="/lifestyle/index.html" class="icon-card">
    <img src="/assets/images/leisure-ico.png" alt="Lifestyle Icon">
    <span>Leisure Lab</span>
  </a>

  <a href="/gallery/index.html" class="icon-card">
    <img src="/assets/images/gallery-ico.png" alt="Gallery Icon">
    <span>Lenscape</span>
  </a>
  
  <a href="https://www.facebook.com/groups/lemons2lemonades" class="icon-card">
    <img src="/assets/images/group-ico.png" alt="Group Icon">
    <span>Lemonades</span>
  </a>

  <a href="/macadarem/index.html" class="icon-card">
    <img src="/assets/images/menu-ico.png" alt="Group Icon">
    <span>MACADAREM</span>
  </a>
  
  <a href="/private/index.html" class="icon-card">
    <img src="/assets/images/personal-ico.png" alt="Personal Icon">
    <span>Minevault 🔒</span>
  </a>
</div>






