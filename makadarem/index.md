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
.order-form-section input, .order-form-section textarea {
  width: 100%; /* ✅ Ensure full-width clean sizing */
  padding: 8px;
  margin-top: 4px;
  border-radius: 7px;
  border: 1px solid #bbb;
  font-size: 1rem;
}

/* ✅ Center "Place Order" button */
.order-button {
  margin-top: 20px;
  align-self: center;
  padding: 12px 35px;
  border-radius: 25px;
  font-size: 1.05rem;
  background: linear-gradient(135deg, #ff7e5f, #ff5722);
  color: #fff;
  border: none;
  cursor: pointer;
  transition: 0.3s ease;
}

.order-button:hover { background: #ff5722; transform: scale(1.07); }

<p>For inquiries contact: 09178664404 or makadarem@gmail.com</p>
  
/* ✅ Running Summary Style */
#orderSummary {
  width: 100%;
  font-size: 1rem;
  color: #4b2e05;
  margin-top: 12px;
  white-space: pre-line;
  border-left: 3px solid #ff7e5f;
  padding-left: 10px;
}

.total-price {
  font-weight: bold;
  font-size: 1.2rem;
  margin-top: 6px;
  color: #ff5722;
}
</style>

<div class="page-container">
  <h1>Makadarem for VS2</h1>
  <p>Door-to-door delivery</p>

  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>

    <!-- ✅ Running Summary -->
    <div id="orderSummary"></div>

    <div class="total-price" id="totalPrice">Total: ₱0</div>

    <div class="order-form-section">
      <label>Name</label>
      <input type="text" name="name" maxlength="50" required>

      <label>Contact</label>
      <input type="text" name="contact" placeholder="09XXXXXXXXX" required>

      <label>Unit No.</label>
      <input type="text" name="unit_no" maxlength="5" placeholder="1234A" required id="unitNo">
      <span id="unitError" style="color:red; display:none;">Format: 4 digits + A or B (e.g., 1250A)</span>

      <label>Notes</label>
      <textarea name="notes" rows="3" placeholder="Add instructions here"></textarea>
    </div>

    <button type="submit" class="order-button">Place Order</button>
  </form>

  <div id="gcashSection" style="display:none; text-align:center; margin-top:25px;">
    <h2>GCash Payment</h2>
    <p><strong>GCash Number:</strong> 09178664404<br><strong>Account Name:</strong> RE*A P</p>
    <img src="/assets/images/gcash_qr.jpg" style="width:160px; border-radius:10px; border:2px solid #ccc;">
  </div>

  <footer>© 2025 Makadarem</footer>
</div>

<script>
const menuURL  = 'YOUR_GET_MENU_URL_HERE';
const orderURL = 'YOUR_ORDER_POST_URL_HERE';

const form = document.getElementById('menuForm');
const menuContainer = document.getElementById('menuContainer');
const totalPriceEl = document.getElementById('totalPrice');
const summaryEl = document.getElementById('orderSummary');
const unitInput = document.getElementById('unitNo');
const unitError = document.getElementById('unitError');
const contactInput = form.querySelector('input[name="contact"]');
const gcashSection = document.getElementById('gcashSection');

let priceMap = {};

// Load menu
fetch(menuURL)
  .then(r => r.json())
  .then(data => {
    menuContainer.innerHTML = '';
    Object.entries(data).forEach(([cat, items]) => {
      const section = document.createElement('div');
      section.innerHTML = `<h2>${cat}</h2>`;
      items.forEach(item => {
        priceMap[item.name] = item.price;
        section.innerHTML += `
          <label style="display:flex;align-items:center;gap:10px;">
            <input type="checkbox" name="item_${item.name}">
            ${item.name} (₱${item.price})
            <input type="number" name="qty_${item.name}" class="qty" value="1" min="1" style="width:45px;display:none;">
          </label>`;
      });
      menuContainer.appendChild(section);
    });
  });

function updateSummary() {
  let lines = [];
  let total = 0;

  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb => {
    const name = cb.name.replace('item_', '');
    const qty = Number(form.querySelector(`[name="qty_${name}"]`).value);
    const price = priceMap[name] * qty;
    total += price;
    lines.push(`${name} × ${qty}  — ₱${price}`);
  });

  summaryEl.textContent = lines.length ? "Order Summary:\n" + lines.join("\n") : "";
  totalPriceEl.textContent = `Total: ₱${total}`;
}

menuContainer.addEventListener('change', e => {
  if (e.target.type === 'checkbox') {
    const qty = e.target.parentElement.querySelector('.qty');
    qty.style.display = e.target.checked ? 'inline-block' : 'none';
  }
  updateSummary();
});

menuContainer.addEventListener('input', e => {
  if (e.target.classList.contains('qty')) updateSummary();
});

// ✅ Unit No. validation → Must be ####A or ####B
unitInput.addEventListener('input', () => {
  const valid = /^\d{4}[ABab]$/.test(unitInput.value);
  unitError.style.display = valid ? 'none' : 'inline';
  unitInput.style.border = valid ? '1px solid #ccc' : '2px solid red';
});

// ✅ Contact validation
contactInput.addEventListener('input', () => {
  contactInput.style.border = /^\d{11}$/.test(contactInput.value) ? '1px solid #ccc' : '2px solid red';
});

// Submit
form.addEventListener('submit', e => {
  e.preventDefault();
  if (!/^\d{4}[ABab]$/.test(unitInput.value)) return alert("Unit format: 4 digits + A/B (ex: 1240A)");
  if (!/^\d{11}$/.test(contactInput.value)) return alert("Contact must be 11 digits.");
  if (!summaryEl.textContent.trim()) return alert("Select at least one item.");

  // ✅ Place order and reveal GCash
  alert("Order placed ✅");
  gcashSection.style.display = 'block';
  gcashSection.scrollIntoView({ behavior: "smooth" });
});
</script>


