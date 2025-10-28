---
layout: default
title: Menu
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/menu/bg.png') no-repeat center center fixed;
  background-size: cover;
  font-family: "Poppins", Arial, sans-serif;
  color: #222;
  display: flex;
  justify-content: center;
  align-items: flex-start;
  min-height: 100vh;
}

.page-container {
  width: 95%;
  max-width: 1000px;
  background: rgba(255, 255, 255, 0.8);
  padding: 20px;
  border-radius: 20px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
  margin: 40px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h1 {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 20px;
  font-weight: bold;
  color: #4b2e05;
}

.category-container {
  width: 100%;
  background: rgba(255,255,255,0.95);
  border-radius: 15px;
  padding: 15px;
  margin-bottom: 25px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.category-container h2 {
  text-align: center;
  font-size: 1.4rem;
  margin-bottom: 10px;
  color: #4b2e05;
  border-bottom: 2px solid #ff7e5f;
  display: inline-block;
  padding-bottom: 4px;
}

.menu-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  justify-items: center;
  width: 100%;
}

.menu-card {
  background: #fff;
  border-radius: 12px;
  overflow: hidden;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 5px;
  width: 100%;
  max-width: 220px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.menu-card:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 25px rgba(0,0,0,0.2);
}

.menu-card img {
  width: 100%;
  height: 130px;
  object-fit: cover;
  border-radius: 8px;
  margin-bottom: 5px;
}

.menu-card h3 {
  margin: 5px 0;
  font-size: 1rem;
  color: #333;
}

.menu-card p {
  margin: 3px 0;
  font-size: 0.9rem;
  color: #555;
}

.menu-card input[type="checkbox"] {
  margin-top: 5px;
  transform: scale(1.1);
  cursor: pointer;
}

.menu-card input[type="number"] {
  width: 45px;
  margin-top: 4px;
  padding: 3px;
  border-radius: 5px;
  border: 1px solid #ccc;
  display: none;
  font-size: 0.9rem;
}

.order-form-section {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 15px;
}

.order-form-section label {
  width: 90%;
  margin-top: 8px;
  font-size: 0.9rem;
}

.order-form-section input,
.order-form-section textarea {
  width: 90%;
  padding: 6px;
  margin-top: 3px;
  border-radius: 5px;
  border: 1px solid #ccc;
  font-size: 0.9rem;
}

.order-button {
  margin-top: 20px;
  padding: 10px 25px;
  border-radius: 20px;
  font-size: 1rem;
  background: linear-gradient(135deg, #ff7e5f, #ff5722);
  color: #fff;
  border: none;
  cursor: pointer;
  transition: 0.3s ease;
}

.order-button:hover {
  background: #ff5722;
  transform: scale(1.05);
}

.total-price {
  font-weight: bold;
  font-size: 1.2rem;
  margin-top: 10px;
  color: #ff5722;
  text-align: center;
}

footer {
  margin-top: 30px;
  text-align: center;
  font-size: 0.9rem;
  color: #555;
}

@media (max-width: 900px) {
  .menu-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 600px) {
  .menu-grid {
    grid-template-columns: 1fr;
  }

  .menu-card {
    max-width: 100%;
  }
}
</style>

<div class="page-container">
  <h1>Makadarem Menu</h1>

  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>

    <div class="order-form-section">
      <label>Name</label>
      <input type="text" name="name" required>
      <label>Contact</label>
      <input type="text" name="contact
