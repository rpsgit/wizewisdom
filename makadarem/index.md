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
}
.page-container {
  width: 95%;
  max-width: 900px;
  margin: 20px auto;
  padding: 15px;
  background: rgba(255, 255, 255, 0.95);
  border-radius: 20px;
  box-shadow: 0 4px 25px rgba(0, 0, 0, 0.15);
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
  margin-bottom: 25px;
}
.category-container h2 {
  font-size: 1.4rem;
  margin-bottom: 10px;
  color: #4b2e05;
  border-bottom: 2px solid #ff7e5f;
  padding-bottom: 4px;
}
.menu-list {
  display: flex;
  flex-direction: column;
  gap: 8px;
  width: 100%;
}
.menu-item {
  display: flex;
  align-items: center;
  background: #fff;
  border-radius: 10px;
  padding: 6px 10px;
  transition: 0.3s ease;
}
.menu-item:hover {
  transform: scale(1.02);
  box-shadow: 0 4px 15px rgba(0,0,0,0.15);
}
.menu-item img {
  width: 80px;
  height: 60px;
  object-fit: cover;
  border-radius: 6px;
  margin-right: 12px;
  flex-shrink: 0;
}
.menu-item .details {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  word-break: break-word;
}
.menu-item .details h3 {
  margin: 0;
  font-size: 1rem;
  color: #333;
}
.menu-item .details p {
  margin: 2px 0;
  font-size: 0.9rem;
  color: #555;
}
.menu-item .actions {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.menu-item input[type="checkbox"] {
  transform: scale(1.1);
  cursor: pointer;
  margin-bottom: 4px;
}
.menu-item input[type="number"] {
  width: 45px;
  padding: 3px;
  border-radius: 5px;
  border: 1px solid #ccc;
  display: none;
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
.total-price,
.order-summary {
  font-weight: bold;
  font-size: 1.1rem;
  margin-top: 10px;
  color: #ff5722;
  text-align: left;
  white-space: pre-line;
}
.order-number {
  font-weight: bold;
  font-size: 1rem;
  margin-top: 5px;
  color: #4b2e05;
  text-align: center;
}
footer {
  margin-top: 30px;
  text-align: center;
  font-size: 0.9rem;
  color: #555;
}
#gcashSection {
  text-align: center;
  margin-top: 25px;
}
#orderPreviewModal {
  display: none;
  position: fixed;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.6);
  justify-content: center;
  align-items: center;
  z-index: 999;
}
.modal-box {
  background: #fff;
  padding: 20px;
  border-radius: 12px;
  width: 90%;
  max-width: 400px;
  text-align: center;
}
.modal-box h2 { color: #4b2e05; margin-bottom: 10px; }
.modal-box button {
  border: none;
  padding: 8px 15px;
  border-radius: 8px;
  cursor: pointer;
  margin: 5px;
}
.modal-confirm { background: #ff7e5f; color: #fff; }
.modal-cancel { background: #ccc; color: #333; }
#unitError { font-size: 0.85rem; color: red; display: none; }

/* Mobile responsiveness */
@media (max-width: 600px) {
  .menu-item img { width: 60px; height: 50px; margin-right: 8px; }
  .menu-item .details h3 { font-size: 0.95rem; }
  .menu-item .details p { font-size: 0.85rem; }
}
</style>

<div class="page-container">
  <h1>Makadarem for VS2</h1>
  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>

    <div class="order-summary" id="orderSummary"></div>
    <div class="total-price" id="totalPrice">Total: ₱0</div>

    <div class="order-form-section">
      <label>Name</label>
      <input type="text" name="name" maxlength="50" required>
      <label>Contact</label>
      <input type="text" name="contact" placeholder="09XXXXXXXXX" required>
      <label>Unit No.</label>
      <input type="text" name="unit_no" maxlength="5" placeholder="1234A" required id="unitNo">
      <span id="unitError">Unit No. must be 5 alphanumeric characters.</span>
      <label>Notes</label>
      <textarea name="notes" rows="3" placeholder="Add instructions here"></textarea>
    </div>

    <div class="order-number" id="orderNumber"></div>
    <button type="submit" class="order-button">Place Order</button>
  </form>

  <div id="gcashSection">
    <h2>GCash Payment</h2>
    <p>Scan the QR code below or send payment to:</p>
    <p><strong>GCash Number:</strong> 09178664404<br><strong>Account Name:</strong> RE*A P</p>
    <img src="/assets/images/gcash_qr.jpg" alt="GCash QR" style="width:160px; height:160px; border-radius:10px; border:2px solid #ccc;">
    <p style="font-size:0.9rem; color:#555; margin-top:10px;">Include your <strong>Order Number</strong> in the payment note.</p>
  </div>

  <footer>© 2025 Makadarem | Comfort food delivered to your doorstep.</footer>
</div>

<div id="orderPreviewModal">
  <div class="modal-box">
    <h2>Confirm Your Order</h2>
    <button id="confirmOrderBtn" class="modal-confirm">Confirm</button>
    <button id="cancelOrderBtn" class="modal-cancel">Cancel</button>
  </div>
</div>

<script>
const menuURL  = 'https://script.google.com/macros/s/AKfycbwc4ANd6POGZXrjeAOuZ7aIscMRZTUzb66MDr7cbEFJ6KaHYG7uIW92dQr2UtZd98dq/exec?func=getMenu';
const orderURL = 'https://script.google.com/macros/s/AKfycbwc4ANd6POGZXrjeAOuZ7aIscMRZTUzb66MDr7cbEFJ6KaHYG7uIW92dQr2UtZd98dq/exec';

const menuContainer = document.getElementById('menuContainer');
const form = document.getElementById('menuForm');
const unitInput = document.getElementById('unitNo');
const unitError = document.getElementById('unitError');
const contactInput = form.querySelector('input[name="contact"]');
const totalPriceEl = document.getElementById('totalPrice');
const gcashSection = document.getElementById('gcashSection');

const modal = document.getElementById('orderPreviewModal');
const confirmBtn = document.getElementById('confirmOrderBtn');
const cancelBtn = document.getElementById('cancelOrderBtn');

let priceMap = {};
let pendingOrder = null;

// Load Menu
fetch(menuURL)
  .then(res => res.json())
  .then(menuData => {
    menuContainer.innerHTML = '';
    Object.entries(menuData).forEach(([cat, items]) => {
      const catDiv = document.createElement('div');
      catDiv.className = 'category-container';
      catDiv.innerHTML = `<h2>${cat}</h2>`;
      const list = document.createElement('div');
      list.className = 'menu-list';
      items.forEach(item => {
        priceMap[item.name] = item.price;
        const div = document.createElement('div');
        div.className = 'menu-item';
        div.innerHTML = `
          <img src="${item.img}" alt="${item.name}" onerror="this.src='https://via.placeholder.com/80x60'">
          <div class="details">
            <h3>${item.name}</h3>
            <p>₱${item.price}</p>
          </div>
          <div class="actions">
            <input type="checkbox" name="item_${item.name}">
            <input type="number" name="qty_${item.name}" class="item-qty" value="1" min="1" style="display:none;">
          </div>`;
        list.appendChild(div);
      });
      catDiv.appendChild(list);
      menuContainer.appendChild(catDiv);
    });
  })
  .catch(() => menuContainer.innerHTML = '<p style="color:red;">❌ Failed to load menu.</p>');

// Update Total
function updateTotal() {
  let total = 0;
  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb => {
    const name = cb.name.replace('item_', '');
    const qty = Number(form.querySelector(`[name="qty_${name}"]`).value || 1);
    total += (priceMap[name] || 0) * qty;
  });
  totalPriceEl.textContent = `Total: ₱${total}`;
}

// Checkbox / Quantity Logic
menuContainer.addEventListener('change', e => {
  if (e.target.type === 'checkbox') {
    const qty = e.target.parentElement.querySelector('.item-qty');
    qty.style.display = e.target.checked ? 'inline-block' : 'none';
    updateTotal();
  }
});
menuContainer.addEventListener('input', e => {
  if (e.target.classList.contains('item-qty')) updateTotal();
});

// ✅ Contact must stay numeric & max 11 digits
contactInput.addEventListener('input', () => {
  contactInput.value = contactInput.value.replace(/\D/g,'').slice(0,11);
});

// ✅ Unit must be exactly `####A` or `####B`
unitInput.addEventListener('input', () => {
  unitInput.value = unitInput.value.toUpperCase();
  const valid = /^[0-9]{4}[AB]$/.test(unitInput.value);
  unitError.style.display = valid ? 'none' : 'inline';
  unitInput.style.border = valid ? '1px solid #ccc' : '2px solid red';
});

// Submit
form.addEventListener('submit', e => {
  e.preventDefault();

  if (!/^[0-9]{4}[AB]$/.test(unitInput.value))
    return alert("Unit must be 4 digits followed by A or B (e.g., 1234A).");

  if (!/^\d{11}$/.test(contactInput.value))
    return alert("Contact must be exactly 11 digits.");

  if (form.querySelectorAll('input[type="checkbox"]:checked').length === 0)
    return alert("Select at least one item.");

  const fd = new FormData(form);
  let total = 0;
  let itemsList = [];

  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb => {
    const name = cb.name.replace('item_', '');
    const qty = Number(fd.get(`qty_${name}`));
    total += (priceMap[name] || 0) * qty;
    itemsList.push(`${name} × ${qty}`);
  });

  pendingOrder = {
    name: fd.get('name'),
    contact: contactInput.value,
    unit_no: unitInput.value,
    notes: fd.get('notes'),
    items: itemsList.join(', '),
    total
  };

  modal.style.display = 'flex';
});

cancelBtn.onclick = () => modal.style.display = 'none';

confirmBtn.onclick = () => {
  modal.style.display = 'none';

  const fd = new FormData();
  Object.entries(pendingOrder).forEach(([k, v]) => fd.append(k, v));

  fetch(orderURL, { method: 'POST', body: fd })
    .then(r => r.json())
    .then(res => {
      if (res.success) {
        alert(`✅ Order placed!\nOrder Number: ${res.orderNumber}`);
        
        gcashSection.style.display = 'block'; // ✅ Show GCash AFTER order
        
        form.reset();
        document.querySelectorAll('.item-qty').forEach(i => i.style.display='none');
        updateTotal();
      } else {
        alert('❌ Failed to save order.');
      }
    })
    .catch(() => alert('Network error. Try again.'));
};
</script>
