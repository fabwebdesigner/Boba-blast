# Boba-blast<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Boba Blast</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600&display=swap" rel="stylesheet">

<style>
*{
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:Poppins;
}

body{
  background: linear-gradient(135deg,#ffe6f0,#e6f7ff,#fff3e6);
  min-height:100vh;
  overflow-x:hidden;
  color:#1c1c1c;
}

/* floating bubbles */
.bubble{
  position:fixed;
  bottom:-50px;
  width:20px;
  height:20px;
  background:rgba(255,255,255,0.5);
  border-radius:50%;
  animation:rise 12s infinite linear;
}

@keyframes rise{
  to{transform:translateY(-120vh);opacity:0;}
}

/* HERO */
.hero{
  text-align:center;
  padding:80px 20px 40px;
}

.hero h1{
  font-size:3.5rem;
  font-weight:600;
  letter-spacing:-1px;
}

.hero p{
  opacity:0.7;
  margin-top:10px;
}

/* MENU GRID (instagram feed style) */
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(260px,1fr));
  gap:20px;
  padding:30px;
}

/* GLASS CARD */
.card{
  background:rgba(255,255,255,0.4);
  backdrop-filter:blur(14px);
  border-radius:20px;
  padding:16px;
  box-shadow:0 10px 30px rgba(0,0,0,0.05);
  transition:0.3s;
}

.card:hover{
  transform:translateY(-6px);
}

.img{
  height:160px;
  border-radius:16px;
  background-size:cover;
  background-position:center;
}

.btn{
  margin-top:10px;
  padding:10px 14px;
  border:none;
  border-radius:999px;
  background:#ff4fa3;
  color:white;
  cursor:pointer;
}

/* CART */
.cart{
  position:fixed;
  right:20px;
  bottom:20px;
  background:white;
  padding:14px 16px;
  border-radius:999px;
  box-shadow:0 10px 25px rgba(0,0,0,0.1);
  font-weight:500;
}

/* MODAL */
.modal{
  display:none;
  position:fixed;
  inset:0;
  background:rgba(0,0,0,0.5);
  align-items:center;
  justify-content:center;
}

.modal-box{
  background:white;
  padding:20px;
  border-radius:20px;
  width:300px;
}

select{
  width:100%;
  padding:8px;
  margin:6px 0;
  border-radius:10px;
  border:1px solid #eee;
}
</style>
</head>

<body>

<!-- bubbles -->
<div class="bubble" style="left:10%;animation-delay:0s"></div>
<div class="bubble" style="left:25%;animation-delay:2s"></div>
<div class="bubble" style="left:50%;animation-delay:4s"></div>
<div class="bubble" style="left:70%;animation-delay:1s"></div>

<div class="hero">
  <h1>Boba Blast 🧋</h1>
  <p>soft • sweet • aesthetic bubble tea made fresh</p>
</div>

<!-- MENU -->
<div class="grid">

  <div class="card">
    <div class="img" style="background-image:url('https://images.unsplash.com/photo-1558857563-b371033873b8')"></div>
    <h3>Brown Sugar Milk Tea</h3>
    <p>£5.85</p>
    <button class="btn" onclick="openModal('Brown Sugar Milk Tea',5.85)">Add</button>
  </div>

  <div class="card">
    <div class="img" style="background-image:url('https://images.unsplash.com/photo-1556679343-c7306c1976bc')"></div>
    <h3>Blue Lychee Tea</h3>
    <p>£5.10</p>
    <button class="btn" onclick="openModal('Blue Lychee Tea',5.10)">Add</button>
  </div>

  <div class="card">
    <div class="img" style="background-image:url('https://images.unsplash.com/photo-1558857563-2b2a8b4b0c1f')"></div>
    <h3>Ube Taro Milk Tea</h3>
    <p>£5.85</p>
    <button class="btn" onclick="openModal('Ube Taro Milk Tea',5.85)">Add</button>
  </div>

</div>

<!-- CART -->
<div class="cart">
🛒 <span id="count">0</span> items
</div>

<!-- MODAL -->
<div class="modal" id="modal">
  <div class="modal-box">
    <h3 id="title"></h3>

    <label>Sweetness</label>
    <select>
      <option>100%</option>
      <option>75%</option>
      <option>50%</option>
      <option>25%</option>
    </select>

    <label>Ice</label>
    <select>
      <option>Regular</option>
      <option>Less</option>
      <option>No Ice</option>
    </select>

    <button class="btn" onclick="add()">Add to Cart</button>
  </div>
</div>

<script>
let cart=0;
let current="";

function openModal(name){
  current=name;
  document.getElementById("title").innerText=name;
  document.getElementById("modal").style.display="flex";
}

function add(){
  cart++;
  document.getElementById("count").innerText=cart;
  document.getElementById("modal").style.display="none";
}
</script>

</body>
</html>
