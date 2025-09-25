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

  /* Icon grid - show all in one row, wrap if needed */
  .icon-grid {
    display: flex;
    justify-content: center;
    flex-wrap: wrap;
    gap: 25px;
    margin-top: 12vh;
  }

  /* Rectangular translucent card */
  .icon-card {
    position: relative;
    width: 180px;
    text-align: center;
    background: rgba(255, 255, 255, 0.7); /* translucent white */
    padding: 20px 15px;
    border-radius: 20px;
    text-decoration: none;
    box-shadow: 0 4px 10px rgba(0,0,0,0.15);
    transition: transform 0.25s ease, box-shadow 0.3s ease;
  }

  .icon-card img {
    width: 80px;
    height: 80px;
    display: block;
    margin: 0 auto 10px auto;
  }

  .icon-card span {
    display: block;
    font-size: 1.1rem;
    font-weight: bold;
    color: #333; /* dark gray */
  }

  .icon-card:hover {
    transform: scale(1.08);
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

  /* RESPONSIVE */
  @media (max-width: 768px) {
    .icon-grid { gap: 15px; }
    .icon-card { width: 150px; padding: 15px; }
    .icon-card img { width: 65px; height: 65px; }
    .icon-card span { font-size: 1rem; }
  }

  @media (max-width: 480px) {
    .icon-card { width: 130px; padding: 12px; }
    .icon-card img { width: 55px; height: 55px; }
    .icon-card span { font-size: 0.9rem; }
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
