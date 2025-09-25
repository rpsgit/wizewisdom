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

  /* Icon card */
  .icon-card {
    position: relative;
    width: 270px; /* 50% larger than before */
    text-align: center;
    text-decoration: none;
    transition: transform 0.25s ease, box-shadow 0.3s ease;
  }

  .icon-card img {
    width: 120px; /* 50% larger */
    height: 120px;
    display: block;
    margin: 0 auto;
  }

  /* Category name overlay */
  .icon-card span {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 1.5rem;
    font-weight: bold;
    color: #fff;
    text-shadow: 2px 2px 4px rgba(0,0,0,0.7);
    pointer-events: none; /* click goes to icon */
    text-align: center;
  }

  .icon-card:hover img {
    transform: scale(1.08);
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
    .icon-card { width: 200px; }
    .icon-card img { width: 90px; height: 90px; }
    .icon-card span { font-size: 1.2rem; }
  }

  @media (max-width: 480px) {
    .icon-card { width: 150px; }
    .icon-card img { width: 70px; height: 70px; }
    .icon-card span { font-size: 1rem; }
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
    <img src="/assets/images/nerdvana-icon.png" alt="Nerdvana Icon">
    <span>Nerdvana</span>
  </a>

  <a href="/geekosystem/index.html" class="icon-card">
    <img src="/assets/images/geekosystem-icon.png" alt="Geekosystem Icon">
    <span>Geekosystem</span>
  </a>

  <a href="/lifestyle/index.html" class="icon-card">
    <img src="/assets/images/lifestyle-icon.png" alt="Lifestyle Icon">
    <span>Lifelark</span>
  </a>

  <a href="/gallery/index.html" class="icon-card">
    <img src="/assets/images/gallery-icon.png" alt="Gallery Icon">
    <span>Lenscape</span>
  </a>
  
  <a href="https://www.facebook.com/groups/lemons2lemonades" class="icon-card">
    <img src="/assets/images/group-icon.png" alt="Group Icon">
    <span>Lemonades</span>
  </a>
  
  <a href="/private/index.html" class="icon-card">
    <img src="/assets/images/personal-icon.png" alt="Personal Icon">
    <span>Minevault 🔒</span>
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
