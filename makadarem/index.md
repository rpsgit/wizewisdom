---
layout: default
title: Menu
---

<style>
body { margin:0; padding:0; background:#f5f5f5 url('/assets/images/menu/bg.png') no-repeat center center fixed; background-size:cover; font-family:"Poppins", Arial, sans-serif; color:#222; }
.page-container { width:95%; max-width:1200px; margin:20px auto; padding:15px; background:rgba(255,255,255,0.9); border-radius:20px; box-shadow:0 4px 25px rgba(0,0,0,0.15); display:flex; flex-direction:column; align-items:center; }
h1 { text-align:center; font-size:2rem; margin-bottom:20px; font-weight:bold; color:#4b2e05; }
.category-container { width:100%; margin-bottom:25px; }
.category-container h2 { text-align:center; font-size:1.4rem; margin-bottom:10px; color:#4b2e05; border-bottom:2px solid #ff7e5f; display:inline-block; padding-bottom:4px; }
.menu-grid { display:grid; grid-template-columns: repeat(4, 1fr); gap:12px; width:100%; }
@media (max-width: 1024px) { .menu-grid { grid-template-columns: repeat(3, 1fr); } }
@media (max-width: 768px) { .menu-grid { grid-template-columns: repeat(2, 1fr); } }
@media (max-width: 480px) { .menu-grid { grid-template-columns: 1fr; } }
.menu-card { width:100%; background:#fff; border-radius:12px; text-align:center; display:flex; flex-direction:column; align-items:center; padding-bottom:5px; transition:transform 0.3s ease, box-shadow 0.3s ease; }
.menu-card:hover { transform:scale(1.05); box-shadow:0 6px 25px rgba(0,0,0,0.2); }
.menu-card img { width:100%; height:130px; object-fit:cover; border-radius:8px; margin-bottom:5px; display:block; background:#eee; }
.menu-card h3 { margin:5px 0; font-size:1rem; color:#333; }
.menu-card p { margin:3px 0; font-size:0.9rem; color:#555; }
.menu-card input[type="checkbox"] { margin-top:5px; transform:scale(1.1); cursor:pointer; }
.menu-card input[type="number"] { width:45px; margin-top:4px; padding:3px; border-radius:5px; border:1px solid #ccc; display:none; }
.order-form-section { width:100%; display:flex; flex-direction:column; align-items:center; margin-top:15px; }
.order-form-section label { width:90%; margin-top:8px; font-size:0.9rem; }
.order-form-section input, .order-form-section textarea { width:90%; padding:6px; margin-top:3px; border-radius:5px; border:1px solid #ccc; font-size:0.9rem; }
.order-button { margin-top:20px; padding:10px 25px; border-radius:20px; font-size:1rem; background:linear-gradient(135deg,#ff7e5f,#ff5722); color:#fff; border:none; cursor:pointer; transition:0.3s ease; }
.order-button:hover { background:#ff5722; transform:scale(1.05); }
.total-price, .order-summary { font-weight:bold; font-size:1.2rem; margin-top:10px; color:#ff5722; text-align:center; white-space: pre-line; }
.order-number { font-weight:bold; font-size:1rem; margin-top:5px; color:#4b2e05; text-align:center; }
footer { margin-top:30px; text-align:center; font-size:0.9rem; color:#555; }
</style>

<div class="page-container">
  <h1>Makadarem Menu</h1>
  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>

    <!-- Order summary & total -->
    <div class="order-summary" id="orderSummary"></div>
    <div class="total-price" id="totalPrice">Total: ₱0</div>

    <div class="order-form-section">
      <label>Name</label>
      <input type="text" name="name" maxlength="50" required>
      <label>Contact</label>
      <input type="text" name="contact" placeholder="09000000000" required>
      <label>Unit No.</label>
      <input type="text" name="unit_no" maxlength="5" placeholder="Max 5 alphanumeric" required>
      <label>Notes</label>
      <textarea name="notes" rows="3"></textarea>
    </div>

    <div class="order-number" id="orderNumber"></div>
    <button type="submit" class="order-button">Place Order</button>
  </form>

  <footer>
    © 2025 Makadarem | Comfort home-cooking delivered to your doorstep.
  </footer>
</div>

<script>
const menuURL  = 'https://script.google.com/macros/s/AKfycby1kjAyM3oFi6CEXWBg9Z-0AVVorKraPEZ62hvrvxp8nUEWxfp20n0X55bi-tzLOygj/exec?func=getMenu';
const orderURL = 'https://script.google.com/macros/s/AKfycby1kjAyM3oFi6CEXWBg9Z-0AVVorKraPEZ62hvrvxp8nUEWxfp20n0X55bi-tzLOygj/exec';

const menuContainer = document.getElementById('menuContainer');
const form = document.getElementById('menuForm');
const totalPriceEl = document.getElementById('totalPrice');
const orderSummaryEl = document.getElementById('orderSummary');
const orderNumberEl = document.getElementById('orderNumber');

let menuDataGlobal = {};
let priceMap = {};

// Update total and summary
function updateTotal() {
  let total = 0, summary = '';
  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb=>{
    const itemName = cb.name.replace('item_','');
    const qty = Number(form.querySelector(`input[name="qty_${itemName}"]`).value || 1);
    const price = priceMap[itemName] || 0;
    total += price * qty;
    summary += `${itemName} x ${qty} = ₱${price*qty}\n`;
  });
  orderSummaryEl.textContent = summary;
  totalPriceEl.textContent = `Total: ₱${total}`;
}

// Create a menu card element
function createMenuCard(item) {
  priceMap[item.name] = item.price;
  const card = document.createElement('label');
  card.className = 'menu-card';
  card.innerHTML = `
    <input type="checkbox" name="item_${item.name}">
    <img data-src="${item.img?.trim()||'https://via.placeholder.com/220x130?text=No+Image'}" alt="${item.name}" loading="lazy">
    <h3>${item.name}</h3>
    <p>₱${item.price}</p>
    <input type="number" class="item-qty" name="qty_${item.name}" value="1" min="1" style="display:none;">
  `;
  return card;
}

// Lazy-load images with IntersectionObserver
function lazyLoadImages() {
  const images = document.querySelectorAll('img[data-src]');
  const observer = new IntersectionObserver((entries, obs)=>{
    entries.forEach(entry=>{
      if(entry.isIntersecting){
        const img = entry.target;
        img.src = img.dataset.src;
        img.removeAttribute('data-src');
        obs.unobserve(img);
      }
    });
  }, {rootMargin:'100px'});
  images.forEach(img=>observer.observe(img));
}

// Fetch menu
fetch(menuURL)
  .then(res => res.json())
  .then(menuData => {
    menuDataGlobal = menuData;
    menuContainer.innerHTML = '';
    const frag = document.createDocumentFragment();

    Object.keys(menuData).forEach(cat=>{
      const catBox = document.createElement('div');
      catBox.className = 'category-container';
      const catTitle = document.createElement('h2');
      catTitle.textContent = cat;
      catBox.appendChild(catTitle);

      const grid = document.createElement('div');
      grid.className = 'menu-grid';
      menuData[cat].forEach(item => grid.appendChild(createMenuCard(item)));
      catBox.appendChild(grid);
      frag.appendChild(catBox);
    });
    menuContainer.appendChild(frag);
    lazyLoadImages();
  })
  .catch(err => { menuContainer.innerHTML='<p style="color:red;">❌ Failed to load menu.</p>'; console.error(err); });

// Event delegation
menuContainer.addEventListener('change', e=>{
  if(e.target.type==='checkbox'){
    const qty = e.target.parentElement.querySelector('.item-qty');
    if(e.target.checked){ qty.style.display='inline-block'; qty.required=true; e.target.parentElement.style.border='2px solid #ff7e5f'; }
    else{ qty.style.display='none'; qty.required=false; qty.value=1; e.target.parentElement.style.border='none'; }
    updateTotal();
  }
});

menuContainer.addEventListener('input', e=>{
  if(e.target.classList.contains('item-qty')) updateTotal();
});

// Form submit
form.addEventListener('submit', e=>{
  e.preventDefault();
  const fd = new FormData(form);
  const name = fd.get('name'), contact = fd.get('contact'), unitNo = fd.get('unit_no');
  if(!name||!contact||!unitNo){ alert("Name, Contact, and Unit No. are required."); return; }
  if(name.length>50){ alert("Name cannot exceed 50 characters."); return; }
  if(!/^\d{11}$/.test(contact)){ alert("Contact number must be 11 digits."); return; }
  if(!/^[a-zA-Z0-9]{1,5}$/.test(unitNo)){ alert("Unit No. must be 1-5 alphanumeric."); return; }
  if(form.querySelectorAll('input[type="checkbox"]:checked').length===0){ alert("Select at least one item."); return; }

  const now = new Date();
  const pad = n=>n.toString().padStart(2,'0');
  const orderNumber = `${now.getFullYear().toString().slice(2)}${pad(now.getMonth()+1)}${pad(now.getDate())}${pad(now.getHours())}${pad(now.getMinutes())}${pad(now.getSeconds())}${Math.floor(Math.random()*999999+1).toString().padStart(6,'0')}`;
  orderNumberEl.textContent = `Your Order Number: ${orderNumber}`;

  const filteredData = new FormData();
  filteredData.append('name', name); filteredData.append('contact', contact);
  filteredData.append('unit_no', unitNo); filteredData.append('notes', fd.get('notes'));
  filteredData.append('order_number', orderNumber);

  let total=0, summaryText='';
  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb=>{
    const itemName = cb.name.replace('item_','');
    const qty = Number(fd.get(`qty_${itemName}`)||1);
    const price = priceMap[itemName]||0;
    total += price*qty;
    summaryText += `${itemName} x ${qty} = ₱${price*qty}\n`;
    filteredData.append(itemName, qty);
  });
  filteredData.append('total', total);

  fetch(orderURL, {method:'POST', body:filteredData})
    .then(res=>res.json())
    .then(resp=>{
      if(resp.success){
        alert(`✅ Order placed!\nOrder No: ${orderNumber}\n\n${summaryText}Total: ₱${total}`);
        form.reset();
        menuContainer.querySelectorAll('.item-qty').forEach(i=>i.style.display='none');
        menuContainer.querySelectorAll('.menu-card').forEach(card=>card.style.border='none');
        updateTotal(); orderNumberEl.textContent=''; orderSummaryEl.textContent='';
      } else alert('❌ Failed: '+resp.message);
    })
    .catch(err=>{ alert('❌ Failed to submit order.'); console.error(err); });
});
</script>
