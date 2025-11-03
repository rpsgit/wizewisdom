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
      <input type="text" name="contact" required>
      <label>Notes</label>
      <textarea name="notes" rows="3"></textarea>
    </div>

    <div class="total-price" id="totalPrice">Total: ₱0</div>

    <button type="submit" class="order-button">Place Order</button>
  </form>

  <footer>
    © 2025 Makadarem | Freshly Brewed. Locally Loved.
  </footer>
</div>

<script>
const menuURL  = 'https://script.google.com/macros/s/AKfycbxOITTEHIiCBABYVqaMvr65QO1O7I7VW3-n899SKxsiMvbN-_0CJd8h7xqcnOQ1KvfD/exec?func=getMenu';
const orderURL = 'https://script.google.com/macros/s/AKfycbxOITTEHIiCBABYVqaMvr65QO1O7I7VW3-n899SKxsiMvbN-_0CJd8h7xqcnOQ1KvfD/exec';

const menuContainer = document.getElementById('menuContainer');
const form = document.getElementById('menuForm');
const totalPriceEl = document.getElementById('totalPrice');

let menuDataGlobal = {};

// Calculate total
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

// Load menu dynamically
fetch(menuURL)
  .then(res => res.json())
  .then(menuData => {
    menuDataGlobal = menuData;
    menuContainer.innerHTML = '';

    for (const cat in menuData) {
      const catBox = document.createElement('div');
      catBox.className = 'category-container';

      const catTitle = document.createElement('h2');
      catTitle.textContent = cat;
      catBox.appendChild(catTitle);

      const grid = document.createElement('div');
      grid.className = 'menu-grid';

      menuData[cat].forEach(item => {
        const card = document.createElement('label');
        card.className = 'menu-card';

        // If image is empty, use placeholder
        const imgSrc = item.img && item.img.trim() !== "" ? item.img : "https://via.placeholder.com/220x130?text=No+Image";

        card.innerHTML = `
          <input type="checkbox" name="item_${item.name}">
          <img src="${imgSrc}" alt="${item.name}">
          <h3>${item.name}</h3>
          <p>₱${item.price}</p>
          <input type="number" class="item-qty" name="qty_${item.name}" value="1" min="1">
        `;

        grid.appendChild(card);
      });

      catBox.appendChild(grid);
      menuContainer.appendChild(catBox);
    }

    // Checkbox logic
    document.querySelectorAll('.menu-card input[type="checkbox"]').forEach(cb => {
      cb.addEventListener('change', e => {
        const qty = e.target.parentElement.querySelector('.item-qty');
        if(e.target.checked) {
          qty.style.display = 'inline-block';
          qty.required = true;
          e.target.parentElement.style.border = '2px solid #ff7e5f';
        } else {
          qty.style.display = 'none';
          qty.required = false;
          qty.value = 1;
          e.target.parentElement.style.border = 'none';
        }
        updateTotal();
      });
    });

    document.querySelectorAll('.item-qty').forEach(q => q.addEventListener('input', updateTotal));
  })
  .catch(err => {
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
  filteredData.append('total', updateTotal());

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
    .then(resp => {
      if(resp.success) {
        alert('✅ Your order has been placed!');
        form.reset();
        document.querySelectorAll('.item-qty').forEach(i => i.style.display='none');
        document.querySelectorAll('.menu-card').forEach(card => card.style.border='none');
        updateTotal();
      } else {
        alert('❌ Failed to submit order: ' + resp.message);
      }
    })
    .catch(err => {
      alert('❌ Failed to submit order. Please try again.');
      console.error(err);
    });
});
</script>
