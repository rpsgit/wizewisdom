---
layout: default
title: Makadarem Menu
---

<style>
/* Your existing CSS */
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
.total-price, .order-summary { font-weight: bold; font-size: 1.1rem; margin-top: 10px; color: #ff5722; text-align: left; white-space: pre-line; }
#unitError { font-size: 0.85rem; color: red; display: none; }
#gcashSection { display: none; margin-top: 25px; text-align: center; }
/* Modal */
#orderPreviewModal { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); justify-content: center; align-items: center; z-index: 999; }
.modal-box { background: #fff; padding: 20px; border-radius: 12px; width: 90%; max-width: 400px; text-align: center; }
@media (max-width: 600px) { .menu-item img { width: 60px; height: 50px; } }
</style>

<div class="page-container">
  <h1>Makadarem for VS2</h1>

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
    <img src="/assets/images/gcash_qr.jpg" style="width:160px; height:160px; border-radius:10px; border:2px solid #ccc;">
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
// Your existing JS (fetch menu, lazy loading, total calculation, order submission)
</script>
