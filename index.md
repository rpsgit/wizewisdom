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
    transition: 0.3s;
  }

  /* Icon grid - single row */
  .icon-grid {
    display: flex;
    justify-content: center;
    gap: 30px;
    margin-top: 12vh;
    flex-wrap: nowrap;
    overflow-x: auto;
    padding-bottom: 15px;
  }

  /* Circle icon cards */
  .icon-card {
    position: relative;
    width: 140px;
    height: 140px;
    border-radius: 50%;
    background: rgba(255, 255, 0, 0.7); /* 70% translucent yellow */
    display: flex;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    overflow: hidden;
    transition: transform 0.25s ease, box-shadow 0.3s ease;
    box-shadow: 0 4px 10px rgba(0,0,0,0.15);
  }

  .icon-card img {
    width: 70%;
    height: 70%;
    object-fit: contain;
    z-index: 0;
  }

  /* Foreground text overlay */
  .icon-card span {
    position: absolute;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
    color: #333;
    font-size: 1rem;
    font-weight: bold;
    text-shadow: 1px 1px 3px rgba(255, 255, 255, 0.7);
    z-index: 1;
  }

  .icon-card:hover {
    transform: scale(1.15);
    box-shadow: 0 8px 20px rgba(0,0,0,0.3);
  }

  /* Ripple effect */
  .ripple {
    position: absolute;
    border-radius: 50%;
    transform: scale(0);
    background: rgba(255, 255, 255, 0.6);
    animation: ripple-animation 0.6s ease-out;
    pointer-events: none;
  }

  @keyframes ripple-animation {
    to {
      transform: scale(4);
      opacity: 0;
    }
  }

  /* RESPONSIVENESS */
  @media (max-width: 768px) {
    .icon-grid {
      gap: 20px;
      margin-top: 8vh;
    }
    .icon-card {
      width: 110px;
      height: 110px;
    }
    .icon-card span {
      font-size: 0.9rem;
    }
  }

  @media (max-width: 480px) {
    .icon-card {
      width: 90px;
      height: 90px;
    }
    .icon-card span {
      font-size: 0.8rem;
    }
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
  <a href="/nerdvana/nerdvana-index.md" class="icon-card">
    <img src="/assets/images/nerdvana-icon.png" alt="Nerdvana Icon">
    <span>Nerdvana</span>
  </a>

  <a href="/geekosystem/geekosystem-index.md" class="icon-card">
    <img src="/assets/images/geekosystem-icon.png" alt="Geekosystem Icon">
    <span>Geekosystem</span>
  </a>

  <a href="https://www.facebook.com/groups/lemons2lemonades" class="icon-card">
    <img src="/assets/images/group-icon.png" alt="Group Icon">
    <span>Group</span>
  </a>

  <a href="/lifestyle/index.html" class="icon-card">
    <img src="/assets/images/lifestyle-icon.png" alt="Lifestyle Icon">
    <span>Lifestyle</span>
  </a>

  <a href="/gallery/index.html" class="icon-card">
    <img src="/assets/images/gallery-icon.png" alt="Gallery Icon">
    <span>Gallery</span>
  </a>

  <a href="/private/index.html" class="icon-card">
    <img src="/assets/images/personal-icon.png" alt="Personal Icon">
    <span>Personal 🔒</span>
  </a>
</div>

<script>
  document.querySelectorAll('.icon-card').forEach(card => {
    card.addEventListener('click', function (e) {
      const ripple = document.createElement('span');
      ripple.classList.add('ripple');
      const size = Math.max(card.clientWidth, card.clientHeight);
      ripple.style.width = ripple.style.height = size + 'px';
      ripple.style.left = e.clientX - card.getBoundingClientRect().left - size / 2 + 'px';
      ripple.style.top = e.clientY - card.getBoundingClientRect().top - size / 2 + 'px';
      card.appendChild(ripple);
      setTimeout(() => ripple.remove(), 600);
    });
  });
</script>
