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
  background: rgba(255, 255, 255, 0.95);
  padding: 40px 25px;
  border-radius: 25px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
}
h1 { text-align: center; font-size: 2.8rem; color: #000; margin-bottom: 40px; }
h2 {
  text-align: left; font-size: 2rem; color: #333; margin: 50px 0 20px 10px;
  border-left: 6px solid #ff7e5f; padding-left: 12px;
}
.menu-grid {
  display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px; justify-items: center;
}
.menu-card {
  background: #fff; border-radius: 20px; overflow: hidden;
  box-shadow: 0 4px 20px rgba(0,0,0,0.1);
  width: 250px; text-align: center; cursor: pointer;
  display: flex; flex-direction: column; align-items: center; padding-bottom: 10px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.menu-card:hover { transform: scale(1.05); box-shadow: 0 6px 25px rgba(0,0,0,0.2); }
.menu-card img { width: 100%; height: 180px; object-fit: cover; margin-bottom: 10px; border-radius: 10px; }
.menu-card h3 { margin: 5px 0; color: #333; font-size: 1.2rem; }
.menu-card p { font-size: 1rem; color: #555; margin: 5px 0; }
.menu-card input[type="radio"] { margin-top: 5px; transform: scale(1.2); cursor: pointer; }
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

<div class="page-container">
  <h1>Makadarem Menu</h1>
  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>
    <div style="margin-top:20px;">
      <label>Name</label>
      <input type="text" name="name" required>
      <label>Contact</label>
      <input type="text" name="contact" required>
      <label>Notes</label>
      <textarea name="notes" rows="3"></textarea>
    </div>
    <div style="text-align:center; margin-top:30px;">
      <button type="submit" class="order-button">Place Order</button>
    </div>
    <p id="msg"></p>
  </form>
</div>

<script>
// Replace with your Apps Script URLs
const menuURL  = 'https://script.google.com/macros/s/AKfycbyqzykyyL-6mqdlkm_cUYNYX_Kh43CtRB-LwNslLcKxt3MObKgeSqCGI-yk9t0MSur6/exec?func=getMenu';
const orderURL = 'https://script.google.com/macros/s/AKfycbyqzykyyL-6mqdlkm_cUYNYX_Kh43CtRB-LwNslLcKxt3MObKgeSqCGI-yk9t0MSur6/exec';

const menuContainer = document.getElementById('menuContainer');
const form = document.getElementById('menuForm');
const msg = document.getElementById('msg');

// Load menu dynamically
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
          <input type="radio" name="${category}" value="${item.name}">
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

// Show/hide quantity input for selected radio button
document.addEventListener('change', e => {
  if(e.target.type === 'radio') {
    const radios = document.getElementsByName(e.target.name);
    radios.forEach(r => {
      const qty = r.parentElement.querySelector('.item-qty');
      qty.style.display = r.checked ? 'inline-block' : 'none';
    });
  }
});

// Submit order
form.addEventListener('submit', e => {
  e.preventDefault();
  const formData = new FormData(form);
  const filteredData = new FormData();

  filteredData.append('name', formData.get('name'));
  filteredData.append('contact', formData.get('contact'));
  filteredData.append('notes', formData.get('notes'));

  // Include selected items
  for (const pair of formData.entries()) {
    const key = pair[0];
    const value = pair[1];
    if(key.startsWith('qty_') && Number(value) > 0) {
      const itemName = key.replace('qty_', '');
      filteredData.append(itemName, value);
    }
  }

  fetch(orderURL, { method:'POST', body: filteredData })
    .then(res => res.json())
    .then(result => {
      msg.textContent = '✅ Your order has been placed!';
      msg.style.color = 'green';
      form.reset();
      document.querySelectorAll('.item-qty').forEach(i => i.style.display = 'none');
      window.scrollTo({ top: 0, behavior: 'smooth' });
      setTimeout(() => msg.textContent = '', 5000);
    })
    .catch(err => {
      msg.textContent = '❌ Failed to submit order. Please try again.';
      msg.style.color = 'red';
      console.error(err);
    });
});
</script>
