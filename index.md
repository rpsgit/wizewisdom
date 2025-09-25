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

  /* Icon grid */
  .icon-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 20px;
    margin-top: 15vh;
  }

  /* Card style */
  .icon-card {
    position: relative;
    overflow: hidden;
    flex: 1 1 120px;
    max-width: 200px;
    text-align: center;
    background: rgba(255,255,255,0.65);
    padding: 20px;
    border-radius: 20px;
    text-decoration: none;
    font-weight: bold;
    box-shadow: 0 3px 10px rgba(0,0,0,0.15);
    display: block;
    transition: transform 0.2s ease, background 0.3s ease, box-shadow 0.3s ease;
  }

  .icon-card img {
    width: 48px;
    height: 48px;
    margin-bottom: 10px;
  }

  .icon-card:hover {
    transform: scale(1.05);
    background: rgba(255, 255, 255, 0.85);
    box-shadow: 0 6px 15px rgba(0, 0, 0, 0.25),
                0 0 10px rgba(0, 123, 255, 0.25);
  }

  /* Special Styling for Nerdvana & Geekosystem */
  .icon-card.nerdvana,
  .icon-card.geekosystem {
    background: none !important;
    box-shadow: none;
    max-width: 250px;
    padding: 0;
    transition: transform 0.25s ease, box-shadow 0.3s ease;
  }

  .icon-card.nerdvana img,
  .icon-card.geekosystem img {
    width: 100px;
    height: 100px;
    display: block;
    margin: 0 auto;
  }

  .icon-card.nerdvana span,
  .icon-card.geekosystem span {
    position: absolute;
    bottom: 10px;
    left: 50%;
    transform: translateX(-50%);
    background: rgba(0,0,0,0.6);
    color: white;
    padding: 5px 12px;
    border-radius: 10px;
    font-size: 1.1rem;
    font-weight: bold;
  }

  /* Stronger Hover Zoom for Nerdvana & Geekosystem */
  .icon-card.nerdvana:hover,
  .icon-card.geekosystem:hover {
    transform: scale(1.15);
    box-shadow: 0 8px 20px rgba(0,0,0,0.3);
  }

  /* Bright Ripple Effect */
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
    .blog-container { padding: 20px; }
    .links a { width: 100%; text-align: center; }
    .icon-grid { gap: 15px; margin-top: 8vh; }
    .icon-card { flex: 1 1 100%; max-width: 90%; margin: auto; padding: 15px; }
    .icon-card img { width: 40px; height: 40px; }
    .icon-card.nerdvana img,
    .icon-card.geekosystem img { width: 80px; height: 80px; }
  }

  @media (max-width: 480px) {
    .icon-card { padding: 12px; font-size: 0.95rem; }
    .icon-card img { width: 36px; height: 36px; }
    .icon-card.nerdvana img,
    .icon-card.geekosystem img { width: 70px; height: 70px; }
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
  <a href="/nerdvana/nerdvana-index.md" class="icon-card nerdvana">
    <img src="/assets/images/nerdvana-icon.png" alt="Nerdvana Icon">
    <span>Nerdvana</span>
  </a>

  <a href="/geekosystem/geekosystem-index.md" class="icon-card geekosystem">
    <img src="/assets/images/geekosystem-icon.png" alt="Geekosystem Icon">
    <span>Geekosystem</span>
  </a>

  <a href="https://www.facebook.com/groups/lemons2lemonades" class="icon-card">
    <img src="/assets/images/Tree.png" alt="Group Icon"><br> Group
  </a>

  <a href="/lifestyle/index.html" class="icon-card">
    <img src="/assets/images/Tennis.png" alt="Lifestyle Icon"><br> Lifestyle
  </a>

  <a href="/gallery/index.html" class="icon-card">
    <img src="/assets/images/Sun.png" alt="Gallery Icon"><br> Gallery
  </a>

  <a href="/private/index.html" class="icon-card">
    <img src="/assets/images/Heart.png" alt="Personal Icon"><br> Personal 🔒
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
