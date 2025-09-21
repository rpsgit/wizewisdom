---
layout: default
title: Lifestyle
---

<style>
  .container {
    background: rgba(255, 255, 255, 0.7);
    max-width: 1000px;
    margin: 30px auto;
    padding: 25px;
    border-radius: 20px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    text-align: center;
  }

  .grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 25px;
    margin-top: 20px;
  }

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

  /* === IMAGE ANIMATION === */
  .grid-item img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    filter: brightness(0.7);
    opacity: 0;
    transform: scale(1.05);
    transition: opacity 0.6s ease, transform 0.8s ease;
  }

  .grid-item img.loaded {
    opacity: 1;
    transform: scale(1);
  }

  /* Stagger effect for images */
  .grid-item:nth-child(1) img.loaded {
    transition-delay: 0.1s;
  }

  .grid-item:nth-child(2) img.loaded {
    transition-delay: 0.25s;
  }

  .grid-item:nth-child(3) img.loaded {
    transition-delay: 0.4s;
  }

  /* === TEXT ANIMATION === */
  .grid-text {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -40%);
    opacity: 0;
    color: white;
    font-size: 2rem;
    font-weight: bold;
    text-shadow: 2px 2px 6px rgba(0, 0, 0, 0.8);
    transition: opacity 0.5s ease, transform 0.5s ease;
  }

  .grid-item img.loaded + .grid-text {
    opacity: 1;
    transform: translate(-50%, -50%);
  }

  /* Staggered delay for text (just after images) */
  .grid-item:nth-child(1) img.loaded + .grid-text {
    transition-delay: 0.3s;
  }

  .grid-item:nth-child(2) img.loaded + .grid-text {
    transition-delay: 0.45s;
  }

  .grid-item:nth-child(3) img.loaded + .grid-text {
    transition-delay: 0.6s;
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
      <img loading="lazy" src="assets/images/play.jpg" alt="Tennis">
      <div class="grid-text">🎾 Tennis</div>
    </div>

    <div class="grid-item" onclick="window.location.href='/lifestyle/pickleball.html'">
      <img loading="lazy" src="assets/images/pickle.jpg" alt="Pickleball">
      <div class="grid-text">🏓 Pickleball</div>
    </div>

    <div class="grid-item" onclick="window.location.href='/lifestyle/recipes.html'">
      <img loading="lazy" src="assets/images/eat.jpg" alt="Recipes">
      <div class="grid-text">🍳 Recipes</div>
    </div>
  </div>
</div>

<script>
  document.querySelectorAll('.grid-item img').forEach(img => {
    // Only load when image enters the viewport
    if ('IntersectionObserver' in window) {
      const observer = new IntersectionObserver((entries, observer) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            const image = entry.target;
            image.src = image.dataset.src;
            image.classList.add('loaded');
            observer.unobserve(image);
          }
        });
      });
      observer.observe(img);
    } else {
      // Fallback for old browsers
      img.classList.add('loaded');
    }
  });
</script>
