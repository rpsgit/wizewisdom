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

.order-form-section input,
.order-form-section textarea {
  width: 90%;
}

/* Shorter inputs */
input[name="contact"] { width: 140px !important; }
input[name="unit_no"] { width: 110px !important; }

#unitError {
  font-size: 0.85rem;
  color: red;
  display: none;
}

footer {
  margin-top: 30px;
  text-align: center;
  font-size: 0.9rem;
  color: #555;
}
</style>


<div class="page-container">
<h1>Makadarem for VS2</h1>
<p>Door-to-door delivery</p>

<form id="menuForm">

<div id="menuContainer">Loading menu...</div>

<div class="order-summary" id="orderSummary"></div>
<div class="total-price" id="totalPrice">Total: ₱0</div>

<div class="order-form-section">
<label>Name</label>
<input type="text" name="name" maxlength="50" required>

<label>Contact</label>
<input type="text" name="contact" placeholder="09XXXXXXXXX" maxlength="11" required>

<label>Unit No.</label>
<input type="text" name="unit_no" id="unitNo" maxlength="5" placeholder="XXXXA" required>
<span id="unitError">Unit No. must be 4 digits + A or B (1234A).</span>

<label>Notes</label>
<textarea name="notes" rows="3" placeholder="Add instructions here"></textarea>
</div>

<div class="order-number" id="orderNumber"></div>
<button type="submit" class="order-button">Place Order</button>

<p>For inquiries please contact 09178664404</p>

</form>


<div id="gcashSection" style="display:none; text-align:center; margin-top:25px;">
<h2>GCash Payment</h2>
<p><strong>GCash Number:</strong> 09178664404<br><strong>Account Name:</strong> RE*A P</p>
<img src="/assets/images/gcash_qr.jpg" style="width:160px;height:160px;border-radius:10px;border:2px solid #ccc;">
<p style="font-size:0.9rem;color:#555;margin-top:10px;">Include your <strong>Order Number</strong>.</p>
</div>

<footer>© 2025 Makadarem</footer>
</div>


<script>
const menuURL = 'https://script.google.com/macros/s/AKfycbwc4ANd6POGZXrjeAOuZ7aIscMRZTUzb66MDr7cbEFJ6KaHYG7uIW92dQr2UtZd98dq/exec?func=getMenu'; 
const orderURL = 'https://script.google.com/macros/s/AKfycbwc4ANd6POGZXrjeAOuZ7aIscMRZTUzb66MDr7cbEFJ6KaHYG7uIW92dQr2UtZd98dq/exec';

const form = document.getElementById('menuForm');
const unitInput = document.getElementById('unitNo');
const contactInput = document.querySelector('input[name="contact"]');
const unitError = document.getElementById('unitError');

// Unit validation (4 digits + A or B)
unitInput.addEventListener('input', () => {
  const valid = /^[0-9]{4}[ABab]$/.test(unitInput.value);
  unitError.style.display = valid ? 'none' : 'inline';
  unitInput.style.border = valid ? '1px solid #ccc' : '2px solid red';
});

// Contact validation (11 digits)
contactInput.addEventListener('input', () => {
  contactInput.style.border = /^\d{11}$/.test(contactInput.value)
    ? '1px solid #ccc'
    : '2px solid red';
});

// Submit
form.addEventListener('submit', e => {
  e.preventDefault();

  if (!/^\d{11}$/.test(contactInput.value))
    return alert('Contact must be 11 digits.');

  if (!/^[0-9]{4}[ABab]$/.test(unitInput.value))
    return alert('Unit No. must be 4 digits + A or B (Example: 1234A).');

  // Continue sending order (unchanged logic)...
});
</script>
