---
layout: default
title: Menu
---

<style>
body {
  margin: 0;
  padding: 0;
  background: #f5f5f5 url('/assets/images/menu-bg.jpg') no-repeat center center fixed;
  background-size: cover;
  font-family: Arial, sans-serif;
  color: #222;
}
.page-container {
  max-width: 1000px;
  margin: 60px auto;
  background: rgba(255, 255, 255, 0.9);
  padding: 40px 25px;
  border-radius: 25px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
}
h1 { text-align: center; font-size: 2.8rem; color: #000; margin-bottom: 40px; }
h2 {
  text-align: left; font-size: 2rem; color: #333; margin: 50px 0 20px 10px;
  border-left: 6px solid #ff7e5f; padding-left: 12px;
}
.home-button, .back-button {
  position: fixed; top: 20px; width: 40px; height: 40px;
  border: none; background: none; cursor: pointer; z-index: 1000;
}
.home-button { left: 20px; }
.back-button { left: 70px; }
.home-icon, .back-icon {
  display: block; width: 100%; height: 100%;
  background-size: contain; background-repeat: no-repeat;
  background-position: center;
}
.home-icon { background-image: url('/assets/images/home-icon.png'); }
.back-icon { background-image: url('/assets/images/back-ico.png'); }
.menu-grid {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px; justify-items: center;
}
.menu-card {
  background: #fff; border-radius: 20px; overflow: hidden;
  box-shadow: 0 4px 20px rgba(0,0,0,0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  width: 250px; text-align: center; cursor: pointer;
  display: flex; flex-direction: column; align-items: center; padding-bottom: 10px;
}
.menu-card:hover { transform: scale(1.05); box-shadow: 0 6px 25px rgba(0,0,0,0.2); }
.menu-card img { width: 100%; height: 180px; object-fit: cover; display: block; transition: transform 0.3s ease; }
.menu-card:hover img { transform: scale(1.08); }
.menu-card h3 { margin: 10px 0 5px; color: #333; font-size: 1.4rem; }
.menu-card p { font-size: 0.95rem; color: #555; margin-bottom: 5px; }
.menu-card input[type="checkbox"] { margin-top: 5px; transform: scale(1.2); cursor: pointer; }
.menu-card input[type="number"] {
  width: 60px; margin-top: 5px; padding: 4px; border-radius: 5px; border: 1px solid #ccc;
  display: none;
}
.order-button {
  display: inline-block; background-color: #ff7e5f; color: #fff;
  font-size: 1.2rem; font-weight: bold; padding: 12px 30px;
  border-radius: 25px; text-decoration: none; transition: background-color 0.3s ease, transform 0.3s ease;
  margin-top: 40px; cursor: pointer; border: none;
}
.order-button:hover { background-color: #ff5722; transform: scale(1.05); }
#msg { text-align: center; font-weight: bold; margin-top: 20px; font-size: 1.2rem; }
@media (max-width: 768px) {
  .page-container { padding: 25px 15px; }
  h1 { font-size: 2.2rem; }
  h2 { font-size: 1.6rem; }
  .menu-card { width: 90%; }
}
</style>

<a href="https://www.wizewisdom.com/" class="home-button" data-tooltip="Home"><span class="home-icon"></span></a>
<button class="back-button" onclick="if(history.length>1){history.back();}else{window.location='/index.html';}" data-tooltip="Back"><span class="back-icon"></span></button>

<div class="page-container">
  <h1>Makadarem Menu</h1>
  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>
    <div style="text-align: center;">
      <button type="submit" class="order-button">Order Now</button>
    </div>
    <p id="msg"></p>
  </form>
</div>

<script>
const menuContainer = document.getElementById('menuContainer');
const form = document.getElementById('menuForm');
const msg = document.getElementById('msg');

// Replace with your Apps Script URLs
const menuURL = 'https://script.google.com/macros/s/YOUR_MENU_SCRIPT_ID/exec';
const orderURL = 'https://script.google.com/macros/s/YOUR_ORDER_SCRIPT_ID/exec';

// Fetch menu dynamically
fetch(menuURL)
  .then(res => res.json())
  .then(menuData => {
    menuContainer.innerHTML = '';
    for (const category in menuData) {
      const catTitle = document.createElement('h2');
      catTitle.textContent = category;
      menuContainer.appendChild(catTitle);

      const grid = document.createElement('div');
      grid.className = 'menu-grid';

      menuData[category].forEach(item => {
        const label = document.createElement('label');
        label.className = 'menu-card';

        label.innerHTML = `
          <img src="${item.img}" alt="${item.name}">
          <h3>${item.name}</h3>
          <p>₱${item.price}</p>
          <input type="checkbox" class="item-checkbox" name="${category}_${item.name}">
          <input type="number" class="item-qty" name="qty_${item.name}" value="1" min="1">
        `;

        grid.appendChild(label);
      });

      menuContainer.appendChild(grid);
    }
  })
  .catch(err => {
    menuContainer.innerHTML = '<p style="color:red;">❌ Failed to load menu.</p>';
    console.error(err);
  });

// Show/hide quantity input
document.addEventListener('change', e => {
  if(e.target.classList.contains('item-checkbox')) {
    const qty = e.target.parentElement.querySelector('.item-qty');
    qty.style.display = e.target.checked ? 'inline-block' : 'none';
  }
});

// Submit order
form.addEventListener('submit', e => {
  e.preventDefault();
  const formData = new FormData(form);
  const filteredData = new FormData();

  formData.forEach((value, key) => {
    if(key.includes('_')) {
      const checked = formData.get(key);
      const qtyKey = 'qty_' + key.split('_').slice(1).join('_');
      const qty = formData.get(qtyKey);
      if(checked && Number(qty) > 0) {
        const itemName = key.split('_').slice(1).join(' ');
        filteredData.append(itemName, qty);
      }
    }
  });

  fetch(`${orderURL}?${new URLSearchParams(filteredData)}`)
    .then(res => {
      msg.textContent = '✅ Your order has been placed!';
      msg.style.color = 'green';
      form.reset();
      document.querySelectorAll('.item-qty').forEach(i => i.style.display = 'none');
      window.scrollTo({ top: 0, behavior: 'smooth' });
    })
    .catch(err => {
      msg.textContent = '❌ Failed to submit order. Please try again.';
      msg.style.color = 'red';
      console.error(err);
    });
});
</script>
