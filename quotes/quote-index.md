---
layout: default
title: Quotes
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: url('/assets/images/nerdvana-bg.png') no-repeat center center fixed;
    background-size: cover;
    font-family: Arial, sans-serif;
  }

  /* === HOME BUTTON === */
  .home-button {
    position: fixed;
    top: 20px;
    left: 20px;
    width: 40px;
    height: 40px;
    z-index: 1000;
    text-decoration: none;
  }

  .home-icon {
    width: 100%;
    height: 100%;
    display: block;
    background: url('/assets/images/home-icon.png') no-repeat center center;
    background-size: contain;
  }

  h1 {
    text-align: center;
    color: #000;
    font-size: 2.4rem;
    margin: 60px auto 30px;
    text-shadow: 1px 1px 3px rgba(255,255,255,0.7);
  }

  .quote-list {
    max-width: 800px;
    margin: 0 auto 50px;
    padding: 0 20px;
    list-style: none;
  }

  .quote-list li {
    margin: 20px 0;
    padding: 15px;
    background: rgba(255,255,255,0.8);
    border-radius: 12px;
    box-shadow: 0 6px 18px rgba(0,0,0,0.2);
    font-size: 1.1rem;
    font-style: italic;
  }
</style>

<!-- Home Button -->
<a href="https://www.wizewisdom.com/" class="home-button">
  <span class="home-icon"></span>
</a>

<h1>Quotes</h1>
<ul class="quote-list">
  <li>“The only true wisdom is in knowing you know nothing.” – Socrates</li>
  <li>“In the middle of difficulty lies opportunity.” – Albert Einstein</li>
  <li>“Your vision will become clear only when you look into your heart.” – Carl Jung</li>
</ul>
