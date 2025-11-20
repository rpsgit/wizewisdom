---
layout: default
title: Makadarem Menu
---

<style>
/* === Page Styles === */
body {
  background: #f5f5f5 url('{{ "/assets/images/menu/bg.png" | relative_url }}') no-repeat center center fixed;
  background-size: cover;
  font-family: "Poppins", Arial, sans-serif;
  color: #222;
  margin: 0;
  padding: 0;
}
.page-container {
  width: 95%;
  max-width: 900px;
  margin: 20px auto;
  padding: 15px;
  background: rgba(255,255,255,0.95);
  border-radius: 20px;
  box-shadow: 0 4px 25px rgba(0,0,0,0.15);
  display: flex;
  flex-direction: column;
  align-items: center;
}
h1 { text-align: center; font-size: 2rem; margin-bottom: 20px; font-weight: bold; color: #4b2e05; }
.category-container { width: 100%; margin-bottom: 25px; }
.category-container h2 {
  font-size: 1.4rem;
  margin-bottom: 10px;
  color: #4b2e05;
  border-bottom: 2px solid #ff7e5f;
  padding-bottom: 4px;
}
.menu-list { display: flex; flex-direction: column; gap: 8px; width: 100%; }
.menu-item {
  display: flex;
  align-items: center;
  background: #fff;
  border-radius: 10px;
  padding: 6px 10px;
  transition: 0.3s ease;
}
.menu-item:hover { transform: scale(1.02); box-shadow: 0 4px 15px rgba(0,0,0,0.15); }
.menu-item img { width: 80px; height: 60px; object-fit: cover; border-radius: 6px; margin-right: 12px; flex-shrink: 0; }
.details { flex-grow: 1; display: flex; flex-direction: column; }
.details h3 { margin: 0; font-size: 1rem; color: #333; }
.details p { margin: 2px 0; font-size: 0.9rem; color: #555; }
.actions { display: flex; flex-direction: column; align-items: center; }
.actions input[type="checkbox"] { transform: scale(1.1); cursor: pointer; margin-bottom: 4px; }
.actions input[type="number"] { width: 45px; padding: 3px; border-radius: 5px; border: 1px solid #ccc; display: none; }
.order-form-section { width: 100%; margin-top: 15px; display: flex; flex-direction: column; align-items: center; }
.order-form-section label { width: 90%; margin-top: 8px; font-size: 0.9rem; }
.order-form-section input, .order-form-section textarea { width: 90%; padding: 6px; margin-top: 3px; border-radius: 5px; border: 1px solid #ccc; font-size: 0.9rem; }
.order-button { margin-top: 20px; padding: 10px 25px; border-radius: 20px; font-size: 1rem; background: linear-gradient(135deg, #ff7e5f, #ff5722); color: #fff; border: none; cursor: pointer; transition: 0.3s ease; }
.order-button:hover { background: #ff5722; transform: scale(1.05); }
.total-price { font-weight: bold; font-size: 1.1rem; margin-top: 10px; color: #ff5722; text-align: left; white-space: pre-line; }
#unitError { font-size: 0.85rem; color: red; display: none; }
#gcashSection { display: none; margin-top: 25px; text-align: center; }
/* Modal */
#orderPreviewModal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); justify-content: center; align-items: center; z-index: 999; }
.modal-box { background: #fff; padding: 20px; border-radius: 12px; width: 90%; max-width: 400px; text-align: center; }
@media (max-width: 600px) { .menu-item img { width: 60px; height: 50px; } }
</style>

<div class="page-container">
  <h1>Makadarem for VS2</h1>

  <!-- Schedule highlighted in red -->
  <h2 style="color: red; font-weight: bold;">Delivery Schedule for November 21, Fri</h2>
  <h3 style="color: red;">9:00 AM～12:00 MN and 3:00～12:00MN </h3>

  <form id="menuForm">
    <div id="menuContainer">Loading menu...</div>

    <div class="total-price" id="totalPrice">Total: ₱0</div>

    <div class="order-form-section">
      <label>Name</label>
      <input type="text" name="name" maxlength="50" required>

      <label>Contact</label>
      <input type="text" name="contact" placeholder="09XXXXXXXXX" required>

      <label>Unit No.</label>
      <input type="text" name="unit_no" maxlength="5" placeholder="1234A" required id="unitNo">
      <span id="unitError">Unit No. must be 4 digits + A/B.</span>

      <label>Notes</label>
      <textarea name="notes" rows="3" placeholder="Add instructions"></textarea>
    </div>

    <button type="submit" class="order-button">Place Order</button>
  </form>

  <div id="gcashSection">
    <h2>GCash Payment</h2>
    <p><strong>GCash:</strong> 09178664404<br><strong>Name:</strong> RE*A P</p>
    <img src="{{ '/assets/images/gcash_qr.jpg' | relative_url }}" style="width:160px; height:160px; border-radius:10px; border:2px solid #ccc;">
  </div>
</div>

<div id="orderPreviewModal">
  <div class="modal-box">
    <h2>Confirm Order?</h2>
    <button id="confirmOrderBtn">Confirm</button>
    <button id="cancelOrderBtn">Cancel</button>
  </div>
</div>

<script>
const menuURL = "https://script.google.com/macros/s/AKfycbwc4ANd6POGZXrjeAOuZ7aIscMRZTUzb66MDr7cbEFJ6KaHYG7uIW92dQr2UtZd98dq/exec?func=getMenu";
const orderURL = "https://script.google.com/macros/s/AKfycbwc4ANd6POGZXrjeAOuZ7aIscMRZTUzb66MDr7cbEFJ6KaHYG7uIW92dQr2UtZd98dq/exec";

const menuContainer = document.getElementById("menuContainer");
const form = document.getElementById("menuForm");
const totalPriceEl = document.getElementById("totalPrice");
const unitInput = document.getElementById("unitNo");
const unitError = document.getElementById("unitError");
const gcashSection = document.getElementById("gcashSection");

let priceMap = {};
let pendingOrder = null;

/* Helper */
function makeKey(name) { return name.replace(/\s+/g,"_").replace(/[^a-zA-Z0-9_-]/g,"").toLowerCase(); }

/* Fetch & render menu */
fetch(menuURL)
  .then(res => res.json())
  .then(data => {
    menuContainer.innerHTML = "";
    Object.entries(data).forEach(([category, items]) => {
      const catDiv = document.createElement("div");
      catDiv.className = "category-container";
      catDiv.innerHTML = `<h2>${category}</h2>`;
      const list = document.createElement("div");
      list.className = "menu-list";

      items.forEach(item => {
        const name = item.name || item.title || "";
        const price = Number(item.price || item.cost || 0);
        const imgSrc = item.image || item.img || "";

        const key = makeKey(name);
        priceMap[key] = price;

        let finalImg = imgSrc;
        if (imgSrc.includes("raw.githubusercontent.com")) {
          finalImg = imgSrc.replace("raw.githubusercontent.com", "cdn.jsdelivr.net/gh").replace("/main/", "/");
        } else if (!imgSrc.startsWith("http")) {
          finalImg = "{{ '/assets/images/menu/' | relative_url }}" + imgSrc;
        }

        const div = document.createElement("div");
        div.className = "menu-item";
        div.innerHTML = `
          <img data-src="${finalImg}" src="data:image/gif;base64,R0lGODlhAQABAIAAAAAAAP///ywAAAAAAQABAAACAUwAOw==" alt="${name}" loading="lazy" onerror="this.src='https://via.placeholder.com/80x60'">
          <div class="details"><h3>${name}</h3><p>₱${price.toFixed(0)}</p></div>
          <div class="actions">
            <input type="checkbox" id="cb_${key}" name="item_${key}">
            <input type="number" id="qty_${key}" name="qty_${key}" class="item-qty" value="1" min="1" style="display:none;">
          </div>
        `;
        list.appendChild(div);
      });

      catDiv.appendChild(list);
      menuContainer.appendChild(catDiv);
    });

    initLazyLoading();
  })
  .catch(err => { console.error(err); menuContainer.innerHTML='<p style="color:red;">❌ Failed to load menu.</p>'; });

function initLazyLoading() {
  const lazyImages = document.querySelectorAll("img[data-src]");
  if (!("IntersectionObserver" in window)) { lazyImages.forEach(img => { img.src = img.dataset.src; img.removeAttribute("data-src"); }); return; }
  const observer = new IntersectionObserver((entries, obs) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        const img = entry.target;
        img.src = img.dataset.src;
        img.onload = () => img.removeAttribute("data-src");
        img.onerror = () => { img.src="https://via.placeholder.com/80x60"; img.removeAttribute("data-src"); };
        obs.unobserve(img);
      }
    });
  }, { rootMargin:"200px" });
  lazyImages.forEach(img => observer.observe(img));
}

/* Total & form logic */
function updateTotal() {
  let total=0;
  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb=>{
    const key=cb.name.replace('item_','');
    const qtyEl=form.querySelector(`[name="qty_${key}"]`);
    const qty=Number(qtyEl?qtyEl.value:1);
    total+=(priceMap[key]||0)*qty;
  });
  totalPriceEl.textContent=`Total: ₱${total}`;
}

menuContainer.addEventListener('change',e=>{
  if(e.target.matches('input[type="checkbox"]')){
    const parent=e.target.closest('.actions');
    const key=e.target.name.replace('item_','');
    const qty=parent?parent.querySelector('.item-qty'):null;
    if(qty) qty.style.display=e.target.checked?'inline-block':'none';
    updateTotal();
  }
});
menuContainer.addEventListener('input',e=>{if(e.target.classList.contains('item-qty'))updateTotal();});

unitInput.addEventListener('input',()=>{unitInput.value=unitInput.value.toUpperCase(); unitError.style.display=/^[0-9]{4}[AB]$/.test(unitInput.value)?'none':'block';});

form.addEventListener('submit',e=>{
  e.preventDefault();
  if(!/^[0-9]{4}[AB]$/.test(unitInput.value)) return alert("Invalid unit number.");
  if(form.querySelectorAll('input[type="checkbox"]:checked').length===0) return alert("Select at least one item.");
  const fd=new FormData(form);
  let total=0;
  const itemsList=[];
  form.querySelectorAll('input[type="checkbox"]:checked').forEach(cb=>{
    const key=cb.name.replace('item_','');
    const qty=Number(fd.get(`qty_${key}`))||1;
    const displayName=document.querySelector(`#cb_${key}`).closest('.menu-item').querySelector('.details h3').textContent;
    itemsList.push(`${displayName} × ${qty}`);
    total+=(priceMap[key]||0)*qty;
  });
  pendingOrder={name:fd.get('name'),contact:fd.get('contact'),unit_no:fd.get('unit_no'),notes:fd.get('notes'),items:itemsList.join(', '),total};
  document.getElementById('orderPreviewModal').style.display='flex';
});

document.getElementById('cancelOrderBtn').onclick=()=>{document.getElementById('orderPreviewModal').style.display='none';};
document.getElementById('confirmOrderBtn').onclick=()=>{
  const fd=new FormData();
  Object.entries(pendingOrder).forEach(([k,v])=>fd.append(k,v));
  fetch(orderURL,{method:"POST",body:fd})
    .then(r=>r.json())
    .then(res=>{
      gcashSection.style.display='block';
      form.reset();
      document.querySelectorAll('.item-qty').forEach(el=>el.style.display='none');
      updateTotal();
      document.getElementById('orderPreviewModal').style.display='none';
      alert("✅ Order placed!");
    }).catch(err=>{console.error(err);alert("❌ Failed to place order.");document.getElementById('orderPreviewModal').style.display='none';});
};
</script>
