---
layout: default
title: Book Feature
---

<style>
  body {
    margin: 0;
    padding: 0;
    background: #f5f5f5 url('/assets/images/nerdvana-bg.png') no-repeat center center fixed;
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

  /* === MAIN CONTENT CONTAINER (no translucent box now) === */
  .content {
    max-width: 900px;
    margin: 80px auto 40px;
    padding: 20px;
  }

  /* === PAGE TITLE === */
  h1 {
    text-align: center;
    color: #000;
    font-size: 2.4rem;
    margin-bottom: 30px;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
  }

  /* === BOOK LIST TABLE === */
  table {
    border-collapse: collapse;
    width: 100%;
    max-width: 700px;
    margin: 0 auto;
    font-size: 1rem;
    background: rgba(255, 255, 255, 0.7); /* 70% transparent */
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 3px 10px rgba(0,0,0,0.1);
  }

  thead tr {
    background-color: rgba(44, 122, 123, 0.85);
    color: white;
    font-weight: bold;
    text-shadow: 1px 1px 3px rgba(0,0,0,0.3);
  }

  th, td {
    padding: 14px 16px;
    border: 1px solid #ddd;
    text-align: left;
  }

  /* === LINK STYLING === */
  a {
    text-decoration: none;
    color: #2a5d9f;
    font-weight: bold;
    transition: color 0.2s ease;
  }

  a:hover {
    color: #1f4b7a;
    text-decoration: underline;
  }

  /* === RESPONSIVE === */
  @media (max-width: 768px) {
    .content {
      padding: 25px 20px;
    }
    h1 {
      font-size: 2rem;
    }
    table {
      font-size: 0.95rem;
    }
    th, td {
      padding: 10px;
    }
  }
</style>

<!-- Home Button -->
<a href="https://www.wizewisdom.com/" class="home-button">
  <span class="home-icon"></span>
</a>

<div class="content">
  <h1>Book Feature</h1>

  <table>
    <thead>
      <tr>
        <th>Title</th>
        <th>Author</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><a href="/books/feature1.html">“Map of Consciousness”</a></td>
        <td>David R. Hawkins</td>
      </tr>
      <tr>
        <td><a href="/books/feature2.html">“Zen and the Art of Motorcycle Maintenance”</a></td>
        <td>Robert M. Pirsig</td>
      </tr>
      <tr>
        <td><a href="/books/feature3.html">“Journey of Souls”</a></td>
        <td>Michael Newton</td>
      </tr>
      <tr>
        <td><a href="/books/feature4.html">“The Hidden Messages in Water”</a></td>
        <td>Masaru Emoto</td>
      </tr>
      <tr>
        <td><a href="/books/feature5.html">“Synchronicity: An Acausal Connecting Principle”</a></td>
        <td>Carl Jung</td>
      </tr>
      <tr>
        <td><a href="/books/feature6.html">“My Big TOE”</a></td>
        <td>Thomas Campbell</td>
      </tr>
    </tbody>
  </table>
</div>
