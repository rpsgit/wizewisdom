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
  font-family: Arial, sans-serif;
  color: #222;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
.page-container {
  width: 100%;
  max-width: 900px;
  background: rgba(255,255,255,0.95);
  padding: 30px;
  border-radius: 20px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 30px;
}
.menu-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
  gap: 20px;
  justify-items: center;
  width: 100%;
}
.menu-card {
  background: #fff;
  border-radius: 15px;
  overflow: hidden;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 10px;
  width: 220px;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}
.menu-card:hover {
  transform: scale(1.05);
  box-shadow: 0 6px 25px rgba(0,0,0,0.2);
}
.menu-card img {
  width: 100%;
  height: 140px;
  object-fit: cover;
  border-radius: 10px;
  margin-bottom: 8px;
}
.menu-card h3 {
  margin: 5px 0;
  font-size: 1.1rem;
  color: #333;
}
.menu-card p {
  margin: 3px 0;
  color: #555;
}
.menu-card input[type="checkbox"] {
  margin-top: 5px;
  transform: scale(1.2);
  cursor: pointer;
}
.menu-card input[type="number"] {
  width: 50px;
  margin-top: 5px;
  padding: 4px;
  border-radius: 5px;
  border: 1px solid #ccc;
  display: none;
}
label {
  width: 100%;
}
.order-form-section {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-top: 20px;
}
.order-form-section label {
  width: 90%;
  margin-top: 10px;
}
.order-form-section input,
.order-form-section textarea {
  width: 90%;
  padding: 8px;
  margin-top: 5px;
  border-radius: 5px;
  border: 1px solid #ccc;
}
.order-button {
  margin-top: 25px;
  padding: 12px 30px;
  border-radius: 25px;
  font-size: 1.2rem;
  background: #ff7e5f;
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
  font-size: 1.5rem;
  margin-top: 15px;
  color: #ff5722;
  text-align: center;
}
#msg {
  font-weight: bold;
  margin-top: 15px;
  font-size: 1.2rem;
  text-align: center;
}

@media (max-width: 600px) {
  .menu-grid {
    grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
  }
  .menu-card {
    width: 180px;
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
      <input type="text" name="contact" required>
      <label>Notes</label>
      <textarea name="notes" rows="3"></textarea>
    </div>

    <div class="total-price" id="totalPrice">Total: ₱0</div>

    <button type="submit" class="order-button">Place Order</button>
    <p id="msg"></p>
  </form>
</div>

<script>
const menuURL  = 'https://script.google.com/macros/s/AKfycbyqzykyyL-6mqdlkm_cUYNYX_Kh43CtRB-LwNslLcKxt3MObKgeSqCGI-yk9t0MSur6/exec?func=getMenu';
const orderURL = 'https://script.google.com/macros/s/AKfycbyqzykyyL-6mqdlkm_cUYNYX_Kh43CtRB-LwNslLcKxt3MObKgeSqCGI-yk9t0MSur6/exec';

const menuContainer = document.getElementById('menuContainer');
const form = document.getElementById('menuForm');
const msg = document.getElementById('msg');
const totalPriceEl = document.getElementById('totalPrice');

let menuDataGlobal = {};

// Update total
function updateTotal() {
  let total = 0;
  Object.keys(menuDataGlobal).forEach(cat => {
    menuDataGlobal[cat].forEach(item => {
      const cb = form.querySelector(`input[name="item_${item.name}"]`);
      const qty = form.querySelector(`input[name="qty_${item.name}"]`);
      if(cb && cb.checked) {
        total += Number(item.price) * (Number(qty.value) || 1);
      }
    });
  });
  totalPriceEl.textContent = `Total: ₱${total}`;
  return total;
}

// Load menu
fetch(menuURL)
  .then(res => res.json())
  .then(menuData => {
    menuDataGlobal = menuData;
    menuContainer.innerHTML = '';

    for (const cat in menuData) {
      const catTitle = document.createElement('h2');
      catTitle.textContent = cat;
      menuContainer.appendChild(catTitle);

      const grid = document.createElement('div');
      grid.className = 'menu-grid';

      menuData[cat].forEach(item => {
        const label = document.createElement('label');
        label.className = 'menu-card';
        label.innerHTML = `
          <input type="checkbox" name="item_${item.name}">
          <img src="${item.img}" alt="${item.name}">
          <h3>${item.name}</h3>
          <p>₱${item.price}</p>
          <input type="number" class="item-qty" name="qty_${item.name}" value="1" min="1">
        `;
        grid.appendChild(label);
      });

      menuContainer.appendChild(grid);
    }

    // Checkbox logic
    document.querySelectorAll('.menu-card input[type="checkbox"]').forEach(cb => {
      cb.addEventListener('change', e => {
        const qty = e.target.parentElement.querySelector('.item-qty');
        if(e.target.checked) {
          qty.style.display = 'inline-block';
          qty.required = true;
          e.target.parentElement.style.border = '3px solid #ff7e5f';
        } else {
          qty.style.display = 'none';
          qty.required = false;
          qty.value = 1;
          e.target.parentElement.style.border = 'none';
        }
        updateTotal();
      });
    });

    // Qty input change
    document.querySelectorAll('.item-qty').forEach(q => q.addEventListener('input', updateTotal));

  }).catch(err => {
    menuContainer.innerHTML = '<p style="color:red;">❌ Failed to load menu.</p>';
    console.error(err);
  });

// Submit order
form.addEventListener('submit', e => {
  e.preventDefault();
  const formData = new FormData(form);
  const filteredData = new FormData();

  filteredData.append('name', formData.get('name'));
  filteredData.append('contact', formData.get('contact'));
  filteredData.append('notes', formData.get('notes'));
  filteredData.append('total', updateTotal()); // save total

  // Only include checked items
  formData.forEach((val, key) => {
    if(key.startsWith('item_')) {
      const cb = form.querySelector(`[name="${key}"]`);
      if(cb.checked) {
        const qty = formData.get(`qty_${key.replace('item_','')}`) || 1;
        filteredData.append(key.replace('item_',''), qty);
      }
    }
  });

  fetch(orderURL, { method:'POST', body: filteredData })
    .then(res => res.json())
    .then(() => {
      msg.textContent = '✅ Your order has been placed!';
      msg.style.color = 'green';
      form.reset();
      document.querySelectorAll('.item-qty').forEach(i => i.style.display='none');
      document.querySelectorAll('.menu-card').forEach(card => card.style.border='none');
      updateTotal();
      window.scrollTo({ top: 0, behavior: 'smooth' });
      setTimeout(()=> msg.textContent='', 5000);
    })
    .catch(err => {
      msg.textContent = '❌ Failed to submit order. Please try again.';
      msg.style.color = 'red';
      console.error(err);
    });
});
</script>
