<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MOMO STATION - Fresh Finds, Best Prices</title>
<style>
  :root{
    --primary:#e63946;
    --primary-dark:#c1121f;
    --accent:#ff8c42;
    --whatsapp:#25d366;
    --whatsapp-dark:#1ebe57;
    --dark:#1d1d1f;
    --gray:#6b6b6b;
    --bg:#faf7f5;
    --card:#ffffff;
    --radius:16px;
  }
  *{margin:0;padding:0;box-sizing:border-box;font-family:'Segoe UI',Roboto,Helvetica,Arial,sans-serif;}
  body{background:var(--bg);color:var(--dark);padding-bottom:40px;}
  img{display:block;max-width:100%;}

  /* NAVBAR */
  .navbar{
    position:sticky;top:0;z-index:1000;
    background:linear-gradient(90deg,var(--primary),var(--primary-dark));
    color:#fff;display:flex;align-items:center;justify-content:space-between;
    padding:14px 20px;box-shadow:0 2px 10px rgba(0,0,0,.15);
  }
  .brand{display:flex;flex-direction:column;line-height:1.1;}
  .brand h1{font-size:1.4rem;letter-spacing:0.5px;}
  .brand span{font-size:0.72rem;opacity:0.9;font-weight:300;}
  .avatar{
    width:42px;height:42px;border-radius:50%;
    background:#fff;color:var(--primary);
    display:flex;align-items:center;justify-content:center;
    font-weight:700;font-size:1.1rem;cursor:pointer;
    border:2px solid rgba(255,255,255,0.6);
    transition:transform .2s;
  }
  .avatar:hover{transform:scale(1.08);}

  /* HERO */
  .hero{
    position:relative;height:38vh;min-height:260px;
    background:url('https://images.unsplash.com/photo-1625246333195-78d9c38ad449?auto=format&fit=crop&w=1200&q=80') center/cover no-repeat;
    display:flex;align-items:center;justify-content:center;text-align:center;
  }
  .hero::after{content:'';position:absolute;inset:0;background:rgba(0,0,0,.45);}
  .hero-content{position:relative;z-index:2;color:#fff;padding:0 20px;}
  .hero-content h2{font-size:2.2rem;margin-bottom:8px;text-shadow:0 2px 8px rgba(0,0,0,.4);}
  .hero-content p{font-size:1.05rem;opacity:.95;}

  /* MENU */
  .menu-wrap{max-width:1100px;margin:0 auto;padding:30px 16px 120px;}
  .menu-title{font-size:1.5rem;margin-bottom:18px;color:var(--dark);border-left:5px solid var(--primary);padding-left:10px;}
  .admin-bar{
    display:none;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:10px;
    background:#fff3e9;border:1px solid #ffd8b8;border-radius:12px;padding:12px 16px;margin-bottom:20px;
  }
  .admin-bar.active{display:flex;}
  .admin-bar .info{font-size:0.9rem;color:var(--gray);}
  .btn{
    border:none;border-radius:8px;padding:9px 16px;font-size:0.88rem;font-weight:600;
    cursor:pointer;transition:all .2s;
  }
  .btn-primary{background:var(--primary);color:#fff;}
  .btn-primary:hover{background:var(--primary-dark);}
  .btn-outline{background:transparent;border:1.5px solid var(--primary);color:var(--primary);}
  .btn-outline:hover{background:var(--primary);color:#fff;}
  .btn-green{background:var(--whatsapp);color:#fff;}
  .btn-green:hover{background:var(--whatsapp-dark);}
  .btn-gray{background:#e9e9e9;color:#333;}
  .btn-gray:hover{background:#dcdcdc;}
  .btn:disabled{opacity:.5;cursor:not-allowed;}

  .food-grid{
    display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:20px;
  }
  .food-card{
    background:var(--card);border-radius:var(--radius);overflow:hidden;
    box-shadow:0 4px 16px rgba(0,0,0,.08);display:flex;flex-direction:column;
    transition:transform .2s,box-shadow .2s;position:relative;
  }
  .food-card:hover{transform:translateY(-4px);box-shadow:0 8px 24px rgba(0,0,0,.12);}
  .food-card img{height:150px;width:100%;object-fit:cover;}
  .food-body{padding:14px;display:flex;flex-direction:column;gap:6px;flex:1;}
  .food-name{font-size:1.02rem;font-weight:700;color:var(--dark);}
  .price-row{display:flex;align-items:baseline;gap:8px;}
  .sell-price{color:var(--primary);font-weight:800;font-size:1.15rem;}
  .orig-price{color:#999;text-decoration:line-through;font-size:0.88rem;}
  .card-actions{margin-top:auto;display:flex;gap:8px;align-items:center;}
  .add-btn{
    flex:1;background:var(--primary);color:#fff;border:none;border-radius:8px;
    padding:9px 0;font-weight:700;cursor:pointer;transition:background .2s;
  }
  .add-btn:hover{background:var(--primary-dark);}
  .qty-control{
    display:flex;align-items:center;justify-content:space-between;flex:1;
    background:#fff0ec;border-radius:8px;overflow:hidden;
  }
  .qty-control button{
    background:var(--primary);color:#fff;border:none;width:34px;height:34px;
    font-size:1.1rem;cursor:pointer;
  }
  .qty-control span{font-weight:700;}
  .admin-controls{display:flex;gap:6px;padding:0 14px 14px;}
  .admin-controls button{flex:1;font-size:0.78rem;padding:6px 0;}

  /* FLOATING NEXT BAR */
  .float-bar{
    position:fixed;bottom:20px;right:20px;left:20px;max-width:420px;margin:0 auto;
    background:var(--dark);color:#fff;border-radius:50px;padding:12px 22px;
    display:none;align-items:center;justify-content:space-between;
    box-shadow:0 8px 24px rgba(0,0,0,.35);z-index:900;
  }
  .float-bar.active{display:flex;}
  .float-bar .items-count{font-size:0.92rem;}
  .float-bar .items-count b{color:var(--accent);}
  .next-btn{
    background:var(--primary);color:#fff;border:none;border-radius:30px;
    padding:10px 20px;font-weight:700;cursor:pointer;
  }
  .next-btn:hover{background:var(--primary-dark);}

  /* WHATSAPP FLOAT ICON */
  .wa-float{
    position:fixed;bottom:24px;left:20px;width:56px;height:56px;border-radius:50%;
    background:var(--whatsapp);display:flex;align-items:center;justify-content:center;
    box-shadow:0 6px 18px rgba(0,0,0,.3);z-index:900;cursor:pointer;
    transition:transform .2s;
  }
  .wa-float:hover{transform:scale(1.08);}
  .wa-float svg{width:30px;height:30px;fill:#fff;}

  /* MODALS */
  .overlay{
    position:fixed;inset:0;background:rgba(0,0,0,.55);z-index:2000;
    display:none;align-items:center;justify-content:center;padding:16px;
  }
  .overlay.active{display:flex;}
  .modal{
    background:#fff;border-radius:var(--radius);padding:24px;width:100%;max-width:420px;
    max-height:90vh;overflow-y:auto;position:relative;animation:pop .2s ease;
  }
  @keyframes pop{from{transform:scale(.92);opacity:0;}to{transform:scale(1);opacity:1;}}
  .modal h3{margin-bottom:16px;color:var(--dark);font-size:1.25rem;}
  .modal .close-x{
    position:absolute;top:14px;right:16px;font-size:1.3rem;cursor:pointer;color:#999;
  }
  .field{margin-bottom:14px;}
  .field label{display:block;font-size:0.85rem;font-weight:600;margin-bottom:5px;color:#444;}
  .field input{
    width:100%;padding:10px 12px;border:1.5px solid #ddd;border-radius:8px;font-size:0.95rem;
    outline:none;transition:border .2s;
  }
  .field input:focus{border-color:var(--primary);}
  .modal-actions{display:flex;gap:10px;margin-top:6px;}
  .modal-actions .btn{flex:1;}
  .error-msg{color:var(--primary);font-size:0.82rem;margin-top:-6px;margin-bottom:10px;min-height:16px;}

  /* CHECKOUT SCREEN */
  .checkout-screen{display:none;max-width:600px;margin:0 auto;padding:20px 16px 60px;}
  .checkout-screen.active{display:block;}
  .menu-wrap.hidden, .hero.hidden{display:none;}
  .summary-card{
    background:#fff;border-radius:var(--radius);padding:18px;box-shadow:0 4px 16px rgba(0,0,0,.08);margin-bottom:18px;
  }
  .summary-item{display:flex;justify-content:space-between;padding:8px 0;border-bottom:1px dashed #eee;font-size:0.92rem;}
  .summary-item:last-child{border-bottom:none;}
  .summary-total-row{display:flex;justify-content:space-between;padding:6px 0;font-size:0.94rem;}
  .summary-total-row.grand{font-weight:800;font-size:1.1rem;color:var(--primary);border-top:2px solid #f0f0f0;margin-top:8px;padding-top:10px;}
  .back-link{
    display:inline-flex;align-items:center;gap:6px;color:var(--primary);font-weight:600;
    cursor:pointer;margin-bottom:14px;font-size:0.92rem;
  }
  .confirm-btn{
    width:100%;background:var(--whatsapp);color:#fff;border:none;border-radius:10px;
    padding:14px 0;font-size:1.05rem;font-weight:700;cursor:pointer;margin-top:6px;
    display:flex;align-items:center;justify-content:center;gap:8px;
  }
  .confirm-btn:disabled{background:#a8d9bd;cursor:not-allowed;}
  .confirm-btn:not(:disabled):hover{background:var(--whatsapp-dark);}

  .empty-state{text-align:center;color:var(--gray);padding:40px 0;font-size:0.95rem;}

  footer{text-align:center;color:var(--gray);font-size:0.82rem;padding:20px;}

  @media(max-width:480px){
    .brand h1{font-size:1.15rem;}
    .hero-content h2{font-size:1.6rem;}
  }
</style>
</head>
<body>

<!-- NAVBAR -->
<div class="navbar">
  <div class="brand">
    <h1>MOMO STATION</h1>
    <span>Fresh Finds, Best Prices</span>
  </div>
  <div class="avatar" id="avatarBtn" title="Admin Login">M</div>
</div>

<!-- HERO -->
<div class="hero" id="heroSection">
  <div class="hero-content">
    <h2>MOMO STATION</h2>
    <p>Fresh Finds, Best Prices</p>
  </div>
</div>

<!-- MENU SECTION -->
<div class="menu-wrap" id="menuWrap">
  <div class="admin-bar" id="adminBar">
    <div class="info">👑 Logged in as Owner — Full menu control enabled</div>
    <div style="display:flex;gap:8px;flex-wrap:wrap;">
      <button class="btn btn-primary" id="addItemBtn">+ Add Item</button>
      <button class="btn btn-outline" id="editDeliveryBtn">Delivery Fee</button>
      <button class="btn btn-gray" id="logoutBtn">Logout</button>
    </div>
  </div>

  <h2 class="menu-title">Our Menu</h2>
  <div class="food-grid" id="foodGrid"></div>
</div>

<!-- FLOATING NEXT BAR -->
<div class="float-bar" id="floatBar">
  <div class="items-count"><b id="cartCount">0</b> items selected</div>
  <button class="next-btn" id="nextBtn">Next ➔</button>
</div>

<!-- WHATSAPP FLOAT ICON -->
<div class="wa-float" id="waFloat" title="Chat with us">
  <svg viewBox="0 0 32 32"><path d="M16.001 3C9.373 3 4 8.373 4 15c0 2.646.86 5.093 2.316 7.084L4 29l7.148-2.276A11.94 11.94 0 0 0 16.001 27C22.63 27 28 21.627 28 15S22.63 3 16.001 3zm0 21.818a9.78 9.78 0 0 1-4.98-1.362l-.357-.212-4.24 1.35 1.377-4.13-.232-.37A9.77 9.77 0 0 1 6.18 15c0-5.415 4.406-9.818 9.821-9.818S25.82 9.585 25.82 15 21.416 24.818 16 24.818zm5.4-7.34c-.297-.148-1.755-.867-2.028-.966-.273-.099-.472-.148-.67.148-.198.297-.767.966-.94 1.164-.173.198-.347.223-.644.075-.297-.149-1.254-.462-2.39-1.474-.883-.788-1.48-1.762-1.653-2.06-.173-.297-.019-.458.13-.606.134-.133.297-.347.446-.52.148-.173.198-.297.297-.495.099-.198.05-.372-.025-.52-.074-.148-.67-1.613-.917-2.21-.242-.58-.487-.502-.67-.511l-.57-.01c-.198 0-.52.074-.792.372-.273.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.876 1.213 3.074.148.198 2.096 3.2 5.08 4.488.71.306 1.263.489 1.694.626.712.227 1.36.195 1.873.118.571-.085 1.755-.718 2.003-1.412.248-.694.248-1.288.173-1.412-.074-.124-.272-.198-.57-.347z"/></svg>
</div>

<!-- CHECKOUT SCREEN -->
<div class="checkout-screen" id="checkoutScreen">
  <div class="back-link" id="backToMenu">← Back to Menu</div>
  <h2 class="menu-title">Order Summary</h2>
  <div class="summary-card" id="orderSummary"></div>

  <h2 class="menu-title">Your Details</h2>
  <div class="summary-card">
    <div class="field">
      <label>Full Name *</label>
      <input type="text" id="custName" placeholder="Enter your full name">
    </div>
    <div class="field">
      <label>Phone Number *</label>
      <input type="tel" id="custPhone" placeholder="Enter phone number">
    </div>
    <div class="field">
      <label>Delivery Address / Table Number *</label>
      <input type="text" id="custAddress" placeholder="Address or table number">
    </div>
    <button class="confirm-btn" id="confirmOrderBtn" disabled>✅ Confirm Order via WhatsApp</button>
  </div>
</div>

<footer>© <span id="year"></span> MOMO STATION. All rights reserved.</footer>

<!-- LOGIN MODAL -->
<div class="overlay" id="loginOverlay">
  <div class="modal">
    <span class="close-x" data-close="loginOverlay">&times;</span>
    <h3>🔐 Admin Login</h3>
    <div class="field">
      <label>Email</label>
      <input type="email" id="loginEmail" placeholder="Admin email">
    </div>
    <div class="field">
      <label>Password</label>
      <input type="password" id="loginPassword" placeholder="Password">
    </div>
    <div class="error-msg" id="loginError"></div>
    <div class="modal-actions">
      <button class="btn btn-primary" id="loginSubmit" style="width:100%;">Login</button>
    </div>
  </div>
</div>

<!-- ADD/EDIT ITEM MODAL -->
<div class="overlay" id="itemOverlay">
  <div class="modal">
    <span class="close-x" data-close="itemOverlay">&times;</span>
    <h3 id="itemModalTitle">Add New Item</h3>
    <input type="hidden" id="itemId">
    <div class="field">
      <label>Item Name</label>
      <input type="text" id="itemName" placeholder="e.g. Classic Steamed Momos">
    </div>
    <div class="field">
      <label>Selling Price (₹)</label>
      <input type="number" id="itemSellPrice" placeholder="e.g. 80">
    </div>
    <div class="field">
      <label>Original Price (₹)</label>
      <input type="number" id="itemOrigPrice" placeholder="e.g. 100">
    </div>
    <div class="field">
      <label>Image URL</label>
      <input type="text" id="itemImage" placeholder="https://...">
    </div>
    <div class="error-msg" id="itemError"></div>
    <div class="modal-actions">
      <button class="btn btn-gray" id="itemCancel" style="flex:1;">Cancel</button>
      <button class="btn btn-primary" id="itemSave" style="flex:1;">Save Item</button>
    </div>
  </div>
</div>

<!-- DELIVERY FEE MODAL -->
<div class="overlay" id="deliveryOverlay">
  <div class="modal">
    <span class="close-x" data-close="deliveryOverlay">&times;</span>
    <h3>🚚 Delivery Charge</h3>
    <div class="field">
      <label>Delivery Fee (₹) — set 0 for Free Delivery</label>
      <input type="number" id="deliveryInput" placeholder="e.g. 30">
    </div>
    <div class="modal-actions">
      <button class="btn btn-primary" id="deliverySave" style="width:100%;">Save</button>
    </div>
  </div>
</div>

<script>
(function(){
  "use strict";

  /* ---------- CONFIG ---------- */
  const WHATSAPP_NUMBER = "917602562944";
  const ADMIN_EMAIL = "sumanvlogs246@gmail.com";
  const ADMIN_PASSWORD = "Summonermomostation@999";

  const DEFAULT_ITEMS = [
    {
      id: "item_1",
      name: "Classic Steamed Momos",
      sellPrice: 80,
      origPrice: 100,
      image: "https://images.unsplash.com/photo-1534422298391-e4f8c172dddb?auto=format&fit=crop&w=600&q=80"
    },
    {
      id: "item_2",
      name: "Crispy Fried Momos",
      sellPrice: 100,
      origPrice: 120,
      image: "https://images.unsplash.com/photo-1498654896293-37aacf113fd9?auto=format&fit=crop&w=600&q=80"
    }
  ];

  /* ---------- STATE ---------- */
  let items = [];
  let deliveryFee = 30;
  let cart = {}; // id -> qty
  let isAdmin = false;

  /* ---------- STORAGE ---------- */
  function loadState(){
    try{
      const savedItems = localStorage.getItem("momo_items");
      items = savedItems ? JSON.parse(savedItems) : DEFAULT_ITEMS.slice();
    }catch(e){ items = DEFAULT_ITEMS.slice(); }

    try{
      const savedFee = localStorage.getItem("momo_delivery_fee");
      deliveryFee = savedFee !== null ? Number(savedFee) : 30;
    }catch(e){ deliveryFee = 30; }
  }
  function saveItems(){ localStorage.setItem("momo_items", JSON.stringify(items)); }
  function saveDeliveryFee(){ localStorage.setItem("momo_delivery_fee", String(deliveryFee)); }

  /* ---------- HELPERS ---------- */
  function $(id){ return document.getElementById(id); }
  function openOverlay(id){ $(id).classList.add("active"); }
  function closeOverlay(id){ $(id).classList.remove("active"); }
  function fmt(n){ return "₹" + Number(n).toFixed(0); }

  /* ---------- RENDER MENU ---------- */
  function renderMenu(){
    const grid = $("foodGrid");
    grid.innerHTML = "";

    if(items.length === 0){
      grid.innerHTML = '<div class="empty-state">No items available right now.</div>';
      return;
    }

    items.forEach(item => {
      const qty = cart[item.id] || 0;
      const card = document.createElement("div");
      card.className = "food-card";

      card.innerHTML = `
        <img src="${escapeHtml(item.image)}" alt="${escapeHtml(item.name)}" onerror="this.src='https://images.unsplash.com/photo-1541592106381-b31e9677c0e5?auto=format&fit=crop&w=600&q=80'">
        <div class="food-body">
          <div class="food-name">${escapeHtml(item.name)}</div>
          <div class="price-row">
            <span class="sell-price">${fmt(item.sellPrice)}</span>
            ${item.origPrice && item.origPrice > item.sellPrice ? `<span class="orig-price">${fmt(item.origPrice)}</span>` : ""}
          </div>
          <div class="card-actions" id="actions_${item.id}"></div>
        </div>
        ${isAdmin ? `<div class="admin-controls">
            <button class="btn btn-outline" data-edit="${item.id}">✏️ Edit</button>
            <button class="btn btn-gray" data-delete="${item.id}">🗑️ Delete</button>
          </div>` : ""}
      `;
      grid.appendChild(card);
      renderCardActions(item.id);
    });

    // bind admin buttons
    grid.querySelectorAll("[data-edit]").forEach(btn=>{
      btn.addEventListener("click", ()=> openEditItem(btn.getAttribute("data-edit")));
    });
    grid.querySelectorAll("[data-delete]").forEach(btn=>{
      btn.addEventListener("click", ()=> deleteItem(btn.getAttribute("data-delete")));
    });
  }

  function renderCardActions(itemId){
    const container = $("actions_" + itemId);
    if(!container) return;
    const qty = cart[itemId] || 0;

    if(qty === 0){
      container.innerHTML = `<button class="add-btn" data-add="${itemId}">+ Add</button>`;
      container.querySelector("[data-add]").addEventListener("click", ()=> addToCart(itemId));
    }else{
      container.innerHTML = `
        <div class="qty-control">
          <button data-dec="${itemId}">−</button>
          <span>${qty}</span>
          <button data-inc="${itemId}">+</button>
        </div>`;
      container.querySelector("[data-dec]").addEventListener("click", ()=> decreaseQty(itemId));
      container.querySelector("[data-inc]").addEventListener("click", ()=> addToCart(itemId));
    }
  }

  function escapeHtml(str){
    const div = document.createElement("div");
    div.innerText = str == null ? "" : str;
    return div.innerHTML;
  }

  /* ---------- CART LOGIC ---------- */
  function addToCart(itemId){
    cart[itemId] = (cart[itemId] || 0) + 1;
    renderCardActions(itemId);
    updateFloatBar();
  }
  function decreaseQty(itemId){
    if(!cart[itemId]) return;
    cart[itemId] -= 1;
    if(cart[itemId] <= 0) delete cart[itemId];
    renderCardActions(itemId);
    updateFloatBar();
  }

  function cartTotalItems(){
    return Object.values(cart).reduce((a,b)=>a+b, 0);
  }
  function cartSubtotal(){
    let sub = 0;
    Object.keys(cart).forEach(id=>{
      const item = items.find(i=>i.id === id);
      if(item) sub += item.sellPrice * cart[id];
    });
    return sub;
  }

  function updateFloatBar(){
    const count = cartTotalItems();
    $("cartCount").textContent = count;
    const bar = $("floatBar");
    if(count > 0){ bar.classList.add("active"); }
    else{ bar.classList.remove("active"); }
  }

  /* ---------- CHECKOUT SCREEN ---------- */
  function goToCheckout(){
    if(cartTotalItems() === 0) return;
    renderOrderSummary();
    $("menuWrap").classList.add("hidden");
    $("heroSection").classList.add("hidden");
    $("floatBar").classList.remove("active");
    $("checkoutScreen").classList.add("active");
    window.scrollTo({top:0, behavior:"smooth"});
    validateForm();
  }

  function backToMenu(){
    $("checkoutScreen").classList.remove("active");
    $("menuWrap").classList.remove("hidden");
    $("heroSection").classList.remove("hidden");
    updateFloatBar();
    window.scrollTo({top:0, behavior:"smooth"});
  }

  function renderOrderSummary(){
    const box = $("orderSummary");
    let
