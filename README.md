# Boba-blast
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Boba Blast — Order</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
body{
  margin:0;
  font-family:Inter;
  background:#faf7f4;
  color:#1d1d1d;
}

header{
  padding:20px 40px;
  background:white;
  display:flex;
  justify-content:space-between;
  align-items:center;
  border-bottom:1px solid #eee;
}

h1{font-size:20px}

.container{
  display:flex;
  gap:20px;
  padding:20px;
}

/* MENU */
.menu{
  flex:2;
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(220px,1fr));
  gap:16px;
}

.card{
  background:white;
  padding:14px;
  border-radius:14px;
  box-shadow:0 10px 25px rgba(0,0,0,0.05);
}

button{
  background:#00754a;
  color:white;
  border:none;
  padding:8px 12px;
  border-radius:20px;
  cursor:pointer;
}

/* CART */
.cart{
  flex:1;
  background:white;
  padding:16px;
  border-radius:14px;
  height:fit-content;
  position:sticky;
  top:20px;
  box-shadow:0 10px 25px rgba(0,0,0,0.05);
}

.item{
  border-bottom:1px solid #eee;
  padding:10px 0;
  font-size:14px;
}

.small{
  font-size:12px;
  opacity:0.7;
}

.total{
  font-weight:700;
  margin-top:10px;
}

/* MODAL */
.modal{
  position:fixed;
  top:0;left:0;
  width:100%;
  height:100%;
  background:rgba(0,0,0,0.5);
  display:none;
  align-items:center;
  justify-content:center;
}

.modal-content{
  background:white;
  padding:20px;
  border-radius:14px;
  width:320px;
}

select{
  width:100%;
  padding:8px;
  margin:6px 0;
}
</style>
</head>

<body>

<header>
  <h1>Boba Blast 🍓</h1>
  <div id="cartCount">Cart: 0</div>
</header>

<div class="container">

<!-- MENU -->
<div class="menu">

  <div class="card">
    <h3>Brown Sugar Milk Tea</h3>
    <p>£5.85</p>
    <button onclick="openCustom('Brown Sugar Milk Tea',5.85)">Add</button>
  </div>

  <div class="card">
    <h3>Ube Taro Milk Tea</h3>
    <p>£5.85</p>
    <button onclick="openCustom('Ube Taro Milk Tea',5.85)">Add</button>
  </div>

  <div class="card">
    <h3>Blue Lychee Tea</h3>
    <p>£5.10</p>
    <button onclick="openCustom('Blue Lychee Tea',5.10)">Add</button>
  </div>

  <div class="card">
    <h3>Matcha Latte</h3>
    <p>£5.85</p>
    <button onclick="openCustom('Matcha Latte',5.85)">Add</button>
  </div>

</div>

<!-- CART -->
<div class="cart">
  <h3>Your Order</h3>
  <div id="cart"></div>
  <div class="total" id="total">Total: £0.00</div>
</div>

</div>

<!-- MODAL -->
<div class="modal" id="modal">
  <div class="modal-content">

    <h3 id="drinkName"></h3>

    <label>Size</label>
    <select id="size">
      <option value="0">Regular</option>
      <option value="0.5">Large (+£0.50)</option>
    </select>

    <label>Sweetness</label>
    <select id="sweet">
      <option>100%</option>
      <option>75%</option>
      <option>50%</option>
      <option>25%</option>
      <option>0%</option>
    </select>

    <label>Ice</label>
    <select id="ice">
      <option>Regular</option>
      <option>Less</option>
      <option>No Ice</option>
    </select>

    <button onclick="addToCart()">Add to Cart</button>
    <button onclick="closeModal()" style="background:#999;margin-top:10px;">Close</button>

  </div>
</div>

<script>
let cart = [];
let currentDrink = null;
let basePrice = 0;

function openCustom(name, price){
  currentDrink = name;
  basePrice = price;
  document.getElementById("drinkName").innerText = name;
  document.getElementById("modal").style.display = "flex";
}

function closeModal(){
  document.getElementById("modal").style.display = "none";
}

function addToCart(){
  let size = parseFloat(document.getElementById("size").value);
  let price = basePrice + size;

  cart.push({
    name: currentDrink,
    price: price
  });

  updateCart();
  closeModal();
}

function removeItem(index){
  cart.splice(index,1);
  updateCart();
}

function updateCart(){
  let cartDiv = document.getElementById("cart");
  cartDiv.innerHTML = "";

  let total = 0;

  cart.forEach((item,i)=>{
    total += item.price;

    cartDiv.innerHTML += `
      <div class="item">
        ${item.name} - £${item.price.toFixed(2)}
        <div class="small"><button onclick="removeItem(${i})">Remove</button></div>
      </div>
    `;
  });

  document.getElementById("total").innerText = "Total: £" + total.toFixed(2);
  document.getElementById("cartCount").innerText = "Cart: " + cart.length;
}
</script>

</body>
</html>
