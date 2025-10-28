---
layout: default
title: Menu
---

<style>
/* ... your previous styles remain the same ... */
.total-price {
  text-align: center;
  font-size: 1.5rem;
  font-weight: bold;
  margin-top: 20px;
  color: #ff5722;
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

    <div class="total-price" id="totalPrice">Total: ₱0</div>

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
const totalPriceEl = document.getElementById('totalPrice');

let menuDataGlobal = {}; // store prices

// Update total price
function updateTotal() {
  let total = 0;
  Object.keys(menuDataGlobal).forEach(category => {
    menuDataGlobal[category].forEach(item => {
      const checkbox = form.querySelector(`input[name="item_${item.name}"]`);
      const qtyInput = form.querySelector(`input[name="qty_${item.name}"]`);
      if (checkbox && checkbox.checked) {
        const qty = Number(qtyInput.value) || 1;
        total += Number(item.price) * qty;
      }
    });
  });
  totalPriceEl.textContent = `Total: ₱${total}`;
}

// Load menu dynamically
fetch(menuURL)
  .then(res => res.json())
  .then(menuData => {
    menuDataGlobal = menuData; // save globally
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

    // Checkbox change
    document.querySelectorAll('.menu-card input[type="checkbox"]').forEach(cb => {
      cb.addEventListener('change', e => {
        const qty = e.target.parentElement.querySelector('.item-qty');
        if (e.target.checked) {
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

    // Quantity change
    document.querySelectorAll('.item-qty').forEach(qtyInput => {
      qtyInput.addEventListener('input', updateTotal);
    });

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

  // Basic info
  filteredData.append('name', formData.get('name'));
  filteredData.append('contact', formData.get('contact'));
  filteredData.append('notes', formData.get('notes'));

  // Only include checked items
  formData.forEach((value, key) => {
    if(key.startsWith('item_')) {
      const checkbox = form.querySelector(`[name="${key}"]`);
      if(checkbox.checked) {
        const qty = formData.get(`qty_${key.replace('item_','')}`) || 1;
        filteredData.append(key.replace('item_',''), qty);
      }
    }
  });

  fetch(orderURL, { method:'POST', body: filteredData })
    .then(res => res.json())
    .then(result => {
      msg.textContent = '✅ Your order has been placed!';
      msg.style.color = 'green';
      form.reset();
      document.querySelectorAll('.item-qty').forEach(i => i.style.display = 'none');
      document.querySelectorAll('.menu-card').forEach(card => card.style.border = 'none');
      updateTotal();
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
