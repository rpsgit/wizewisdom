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
  .menu-item {
    flex-direction: row;
  }
  .menu-item img { width: 60px; height: 50px; margin-right: 8px; }
  .menu-item .details h3 { font-size: 0.95rem; }
  .menu-item .details p { font-size: 0.85rem; }
}
</style>

<div class="page-container">
  <h1>Makadarem Menu</h1>
  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>

    <div class="order-summary" id="orderSummary"></div>
    <div class="total-price" id="totalPrice">Total: ₱0</div>

    <div class="order-form-section">
      <label>Name</label>
      <input type="text" name="name" maxlength="50" required>
      <label>Contact</label>
      <input type="text" name="contact" placeholder="09000000000" required>
      <label>Unit No.</label>
      <input type="text" name="unit_no" maxlength="5" placeholder="Exactly 5 alphanumeric" required id="unitNo">
      <span id="unitError">Unit No. must be exactly 5 alphanumeric characters.</span>
      <label>Notes</label>
      <textarea name="notes" rows="3"></textarea>
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

  <footer>© 2025 Makadarem | Comfort home-cooking delivered to your doorstep.</footer>
</div>

<div id="orderPreviewModal">
  <div class="modal-box">
    <h2>Confirm Your Order</h2>
    <button id="confirmOrderBtn" class="modal-confirm">Confirm</button>
    <button id="cancelOrderBtn" class="modal-cancel">Cancel</button>
  </div>
</div>

<script>
const menuURL  = 'https://script.google.com/macros/s/AKfycbwUJv7GyJ9JMshdYcJl9wHmeAa8YsGPzfMEJDCLm78w4rpItc4ahBj8cdvyLe6x1V_P/exec?func=getMenu';
const orderURL = 'https://script.google.com/macros/s/AKfycbwUJv7GyJ9JMshdYcJl9wHmeAa8YsGPzfMEJDCLm78w4rpItc4ahBj8cdvyLe6x1V_P/exec';

const menuContainer = document.getElementById('menuContainer');
const form = document.getElementById('menuForm');
const totalPriceEl = document.getElementById('totalPrice');
const orderSummaryEl = document.getElementById('orderSummary');
const orderNumberEl = document.getElementById('orderNumber');
const modal = document.getElementById('orderPreviewModal');
const confirmBtn = document.getElementById('confirmOrderBtn');
const cancelBtn = document.getElementById('cancelOrderBtn');
const unitInput = document.getElementById('unitNo');
const unitError = document.getElementById('unitError');

let menuDataGlobal = {};
let priceMap = {};
let pendingOrder = null;

// Live Unit No. validation
unitInput.addEventListener('input', () => {
  const valid = /^[a-zA-Z0-9]{5}$/.test(unitInput.value);
  if (!valid) { unitInput.style.border='2px solid red'; unitError.style.display='inline'; }
  else { unitInput.style.border='1px solid #ccc'; unitError.style.display='none'; }
});

function updateTotal() {
  let total = 0;
  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb => {
    const itemName = cb.name.replace('item_','');
    const qty = Number(form.querySelector(`input[name="qty_${itemName}"]`).value || 1);
    total += (priceMap[itemName] || 0) * qty;
  });
  totalPriceEl.textContent = `Total: ₱${total}`;
}

function createMenuCard(item) {
  priceMap[item.name] = item.price;
  const card = document.createElement('div');
  card.className = 'menu-item';
  card.innerHTML = `
    <img data-src="${item.img?.trim() || 'https://via.placeholder.com/80x60?text=No+Image'}" alt="${item.name}" loading="lazy">
    <div class="details">
      <h3>${item.name}</h3>
      <p>₱${item.price}</p>
    </div>
    <div class="actions">
      <input type="checkbox" name="item_${item.name}">
      <input type="number" name="qty_${item.name}" class="item-qty" value="1" min="1">
    </div>
  `;
  return card;
}

function lazyLoadImages() {
  const images = document.querySelectorAll('img[data-src]');
  const observer = new IntersectionObserver((entries, obs) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const img = entry.target;
        img.src = img.dataset.src;
        img.removeAttribute('data-src');
        obs.unobserve(img);
      }
    });
  }, { rootMargin: '100px' });
  images.forEach(img => observer.observe(img));
}

// Load menu
fetch(menuURL)
  .then(res => res.json())
  .then(menuData => {
    menuDataGlobal = menuData;
    menuContainer.innerHTML = '';
    const frag = document.createDocumentFragment();
    Object.keys(menuData).forEach(cat => {
      const catBox = document.createElement('div');
      catBox.className='category-container';
      const catTitle = document.createElement('h2');
      catTitle.textContent=cat;
      catBox.appendChild(catTitle);
      const list = document.createElement('div');
      list.className='menu-list';
      menuData[cat].forEach(item => list.appendChild(createMenuCard(item)));
      catBox.appendChild(list);
      frag.appendChild(catBox);
    });
    menuContainer.appendChild(frag);
    lazyLoadImages();
  })
  .catch(err => { menuContainer.innerHTML='<p style="color:red;">❌ Failed to load menu.</p>'; console.error(err); });

// Show quantity inputs
menuContainer.addEventListener('change', e=>{
  if(e.target.type==='checkbox'){
    const qty = e.target.parentElement.querySelector('.item-qty');
    qty.style.display = e.target.checked?'inline-block':'none';
    qty.required = e.target.checked;
    if(!e.target.checked) qty.value=1;
    updateTotal();
  }
});
menuContainer.addEventListener('input', e=>{
  if(e.target.classList.contains('item-qty')) updateTotal();
});

// Modal preview
form.addEventListener('submit', e=>{
  e.preventDefault();
  if(!/^[a-zA-Z0-9]{5}$/.test(unitInput.value)){ unitInput.focus(); alert("Unit No. must be exactly 5 alphanumeric characters."); return; }
  if(form.querySelectorAll('input[type="checkbox"]:checked').length===0){ alert("Select at least one item."); return; }

  const fd = new FormData(form);
  const name=fd.get('name'), contact=fd.get('contact'), unitNo=fd.get('unit_no'), notes=fd.get('notes');
  if(!name||!contact) { alert("Name and Contact are required."); return; }
  if(name.length>50) { alert("Name cannot exceed 50 characters."); return; }
  if(!/^\d{11}$/.test(contact)) { alert("Contact number must be 11 digits."); return; }

  let total=0, itemsList='';
  form.querySelectorAll('input[type="checkbox"]:checked').forEach((cb, idx)=>{
    const itemName=cb.name.replace('item_','');
    const qty=Number(fd.get(`qty_${itemName}`)||1);
    const price=priceMap[itemName]||0;
    total+=price*qty;
    itemsList+=`${itemName} × ${qty}${idx<document.querySelectorAll('input[type="checkbox"]:checked').length-1?', ':'')}`;
  });

  pendingOrder={ fd, name, contact, unitNo, notes, total, itemsList };
  modal.style.display='flex';
});

cancelBtn.onclick = ()=>modal.style.display='none';

confirmBtn.onclick = ()=>{
  modal.style.display='none';
  const { fd, name, contact, unitNo, notes, total, itemsList } = pendingOrder;

  const filteredData = new FormData();
  filteredData.append('name', name);
  filteredData.append('contact', contact);
  filteredData.append('unit_no', unitNo);
  filteredData.append('item', itemsList);
  filteredData.append('total', total);
  filteredData.append('notes', notes);

  fetch(orderURL,{method:'POST', body:filteredData})
    .then(res=>res.json())
    .then(resp=>{
      if(resp.success){
        alert(`✅ Order placed!\n\nOrder No: ${resp.orderNumber}\n\nItems:\n${itemsList}\n\nTotal: ₱${total}`);
        form.reset();
        menuContainer.querySelectorAll('.item-qty').forEach(i=>i.style.display='none');
        updateTotal();
      } else alert('❌ Failed: '+resp.message);
    })
    .catch(err=>{alert('❌ Failed to submit order.'); console.error(err);});
};
</script>
