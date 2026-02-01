# Ideathon<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>EcoCycle | Waste to Value Marketplace</title>
<meta name="viewport" content="width=device-width, initial-scale=1">

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>
*{box-sizing:border-box}
body{
  margin:0;
  font-family:'Poppins','Segoe UI',Arial,sans-serif;
  color:#0f172a;

  background:
    linear-gradient(
      rgba(200,230,215,0.7),
      rgba(170,215,195,0.8)
    ),
    url("https://images.unsplash.com/photo-1500530855697-b586d89ba3ee");

  background-size:cover;
  background-position:center;
  background-attachment:fixed;
}
.hidden{display:none}

/* HEADER */
header{
  background:linear-gradient(120deg,#14532d,#22c55e);
  color:white;
  padding:18px 24px;
  display:flex;
  align-items:center;
  position:sticky;
  top:0;
  z-index:200;
}
header h1{font-weight:600}
header i{font-size:26px;cursor:pointer;margin-right:16px}

/* MENU */
.menu{
  position:fixed;
  top:0;
  left:-340px;
  width:340px;
  height:100vh;

  background:
    linear-gradient(rgba(20,83,45,0.95),rgba(12,64,35,0.97)),
    url("https://images.unsplash.com/photo-1441974231531-c6227db76b6e");

  background-size:cover;
  background-position:center;

  color:#ecfdf5;
  padding:28px;
  transition:.3s ease;
  overflow:auto;
  z-index:9999;
}

.menu a{
  display:flex;
  align-items:center;
  gap:10px;
  margin:18px 0;
  padding:12px 16px;

  color:#ecfdf5;
  font-size:15px;
  font-weight:500;
  text-decoration:none;
  cursor:pointer;

  background:rgba(255,255,255,0.15);
  border-radius:12px;
  transition:.25s;
}
.menu a:hover{
  background:rgba(255,255,255,0.25);
  transform:translateX(6px);
}
.menu a i{color:#86efac;font-size:18px}

/* SEARCH */
.top-bar{
  background:#dcfce7;
  padding:14px;
  display:flex;
  gap:12px;
}
.top-bar input,.top-bar select{
  flex:1;
  padding:12px;
  border-radius:8px;
  border:1px solid #86efac;
  color:#064e3b;
  font-family:'Poppins',sans-serif;
}

/* SCREENS */
.screen{padding:30px}

/* HERO */
.hero{
  background:linear-gradient(120deg,#14532d,#22c55e);
  color:white;
  padding:40px;
  border-radius:20px;
  margin-bottom:35px;
}
.hero h2{font-weight:600}
.hero p{opacity:.96}
.hero-stats{
  display:flex;
  gap:25px;
  margin-top:20px;
  flex-wrap:wrap
}
.hero-stats div{
  background:rgba(255,255,255,.22);
  padding:16px 22px;
  border-radius:14px;
  text-align:center;
  font-weight:500;
}

/* PRODUCTS */
.products{
  display:grid;
  grid-template-columns:repeat(auto-fill,minmax(250px,1fr));
  gap:24px;
}
.card{
  background:#ffffff;
  border-radius:16px;
  overflow:hidden;
  box-shadow:0 6px 18px rgba(0,0,0,.18);
}
.card img{width:100%;height:180px;object-fit:cover}
.card-body{padding:16px}
.card-body h4{color:#14532d;font-weight:600}
.card-body p{color:#374151}
.price{font-weight:600;font-size:18px;color:#15803d}
.rating{color:#f59e0b}
.seller{font-size:13px;color:#475569}
.verified{
  display:inline-block;
  background:#dcfce7;
  color:#14532d;
  padding:4px 10px;
  border-radius:12px;
  font-size:12px;
  margin-top:6px;
  font-weight:500;
}

/* BUTTON */
button{
  width:100%;
  padding:12px;
  background:#22c55e;
  color:white;
  border:none;
  border-radius:8px;
  cursor:pointer;
  font-family:'Poppins',sans-serif;
  font-weight:500;
}
button:hover{background:#16a34a}

/* FORMS */
input,textarea,select{
  width:100%;
  padding:12px;
  margin:8px 0;
  border-radius:8px;
  border:1px solid #86efac;
  color:#064e3b;
  font-family:'Poppins',sans-serif;
}

/* MISC */
.ticket{
  background:#ecfdf5;
  padding:14px;
  border-radius:10px;
  margin:10px 0;
  font-weight:500;
}
.summary{
  background:#ecfdf5;
  padding:18px;
  border-radius:12px;
}
</style>
</head>

<body>

<header>
  <i class="fa fa-bars" onclick="toggleMenu()"></i>
  <h1>EcoCycle ♻</h1>
</header>

<div class="menu" id="menu">
  <a onclick="openScreen('home')"><i class="fa fa-store"></i>Marketplace</a>
  <a onclick="openScreen('sellerProfiles')"><i class="fa fa-users"></i>Seller Profiles</a>
  <a onclick="openScreen('sell')"><i class="fa fa-plus"></i>Sell Product</a>
  <a onclick="openScreen('about')"><i class="fa fa-circle-info"></i>About Platform</a>
  <a onclick="openScreen('backend')"><i class="fa fa-diagram-project"></i>Backend & System</a>
  <a onclick="openScreen('support')"><i class="fa fa-headset"></i>Customer Care</a>
  <a onclick="openScreen('policy')"><i class="fa fa-shield"></i>Seller Policy</a>
</div>

<div class="top-bar">
  <input id="search" placeholder="Search product / seller / city">
  <select id="cityFilter">
    <option value="">All Cities</option>
    <option>Nagpur</option><option>Pune</option>
    <option>Mumbai</option><option>Delhi</option><option>Indore</option>
  </select>
</div>

<!-- HOME -->
<div id="home" class="screen">
  <div class="hero">
    <h2>Turning Small Plastic Waste into Valuable Products</h2>
    <p>EcoCycle aggregates ignored plastic waste and converts it into useful, sustainable products.</p>
    <div class="hero-stats">
      <div><b>280+ kg</b><br>Plastic Recycled</div>
      <div><b>230+ kg</b><br>CO₂ Reduced</div>
      <div><b>52+</b><br>Verified Sellers</div>
      <div><b>35+</b><br>Eco Products</div>
    </div>
  </div>
  <div class="products" id="productGrid"></div>
</div>

<!-- SELLER PROFILES -->
<div id="sellerProfiles" class="screen hidden">
  <h2>Seller Profiles</h2>
  <input id="sellerSearch" placeholder="Search seller..." oninput="renderSellerList()">
  <div id="sellerList"></div>
</div>

<!-- SELLER DASHBOARD -->
<div id="sellerDashboard" class="screen hidden">
  <h2 id="sellerTitle"></h2>
  <div id="sellerProducts"></div>
</div>

<!-- SELL PRODUCT -->
<div id="sell" class="screen hidden">
  <h2>Add New Product</h2>
  <input id="sname" placeholder="Seller Name">
  <input id="scity" placeholder="City">
  <input id="pname" placeholder="Product Name">
  <input id="pprice" placeholder="Price">
  <input id="pqty" placeholder="Quantity">
  <input id="pimg" placeholder="Image URL">
  <textarea id="pdesc" placeholder="Product Description"></textarea>
  <button onclick="addProduct()">Submit Product</button>
</div>

<!-- ABOUT -->
<div id="about" class="screen hidden">
  <h2>🌱 About EcoCycle</h2>
  <p>
EcoCycle is a waste-to-value digital marketplace that transforms ignored small plastic waste into useful eco-friendly products.
<br><br>
🔹 Problem<br>
Small plastic items have low individual value and are often ignored by recycling systems, causing environmental pollution.
<br><br>
🔹 Solution<br>
EcoCycle aggregates low-value plastic waste, verifies and recycles it through trusted sellers, and converts it into products like tiles, panels, furniture, and utility items.
<br><br>
🔹 Impact<br>
Reduces plastic waste and CO₂ emissions, supports a circular economy, and creates income opportunities for recyclers.
  </p>
  <img src="https://t3.ftcdn.net/jpg/05/02/12/08/360_F_502120874_QDFnpp3PT3sLzetUNEOn5FnN7AuZBIv9.jpg" width="90%">
</div>

<!-- BACKEND -->
<div id="backend" class="screen hidden">
    <h2>⚙ Backend & System Flow<br><br>
EcoCycle follows a structured waste-to-value workflow.<br><br>
⚙ Backend & System Flow

<i></i>EcoCycle follows a structured waste-to-value workflow to ensure quality, transparency, and efficiency.<br><br>

🔹 Step-by-Step Flow

Waste Collection
Small plastic waste is collected from verified sources and recyclers.<br><br>

Verification & Sorting
Waste is inspected, cleaned, and sorted to ensure recyclability and quality.<br><br>

Recycling Process
Verified plastic is processed into reusable raw material.<br><br>

Manufacturing
Recycled material is used to manufacture construction, utility, and décor products.<br><br>

Marketplace Listing
Products are listed on the EcoCycle platform by verified sellers.<br><br>

Order & Payment
Buyers place orders using secure payment options (COD, UPI, Card, EMI).<br><br>

Delivery & Tracking
Orders are delivered within an estimated time window.<br><br>

🔹 System Logic

Product, seller, and order data are managed digitally

Local storage simulates backend data handling

Ensures reliable data flow and system stability

EcoCycle ensures that plastic waste moves through a controlled, transparent, and scalable system.
Collection → Verification → Recycling → Manufacturing → Marketplace → Delivery</h2></i>
  <img src="https://i.ytimg.com/vi/-P3yncrXMeQ/maxresdefault.jpg" width="90%">
</div>

<!-- SUPPORT -->
<div id="support" class="screen hidden">
  <h2>Customer Care</h2>
  <p>Email: support@ecocycle.in<br>Phone: +91-98765-43210</p>
  <div class="ticket">Ticket #EC1023 – Resolved</div>
</div>

<!-- POLICY -->
<div id="policy" class="screen hidden">
  <h2>Seller Policy</h2>
  <ul>
    <li>Only verified dry-waste-based products allowed</li>
    <li>Fake listings → Permanent Ban</li>
    <li>Mandatory quality audits</li>
  </ul>
</div>

<script>
const screens=document.querySelectorAll(".screen");
const productGrid=document.getElementById("productGrid");
const sellerList=document.getElementById("sellerList");
const sellerProducts=document.getElementById("sellerProducts");
let products=JSON.parse(localStorage.getItem("products"))||[];

if(products.length===0){
  for(let i=1;i<=30;i++){
    products.push({
      n:"Eco Product "+i,
      p:300+i*15,
      qty:20,
      s:"GreenSeller"+(i%5+1),
      city:["Nagpur","Pune","Mumbai","Delhi","Indore"][i%5],
      i:"https://picsum.photos/400/300?random="+i,
      d:"Converted recycled plastic waste to decorative tiles"
    });
  }
  localStorage.setItem("products",JSON.stringify(products));
}

function toggleMenu(){
  menu.style.left = menu.style.left==="0px"?"-340px":"0px";
}
function openScreen(id){
  screens.forEach(s=>s.classList.add("hidden"));
  document.getElementById(id).classList.remove("hidden");
  menu.style.left="-340px";
}

function renderProducts(list=products){
  productGrid.innerHTML="";
  list.forEach(p=>{
    productGrid.innerHTML+=`
    <div class="card">
      <img src="${p.i}">
      <div class="card-body">
        <h4>${p.n}</h4>
        <p>${p.d}</p>
        <div class="rating">⭐⭐⭐⭐☆</div>
        <div class="price">₹${p.p}</div>
        <div class="seller">${p.s}, ${p.city}</div>
        <span class="verified">✔ Verified Seller</span>
        <button onclick="alert('Buy flow demo')">Buy</button>
      </div>
    </div>`;
  });
}

search.oninput=cityFilter.onchange=()=>{
  const v=search.value.toLowerCase();
  const c=cityFilter.value;
  renderProducts(products.filter(p=>
    (p.n+p.s+p.city).toLowerCase().includes(v) &&
    (c===""||p.city===c)
  ));
};

function renderSellerList(){
  sellerList.innerHTML="";
  [...new Set(products.map(p=>p.s))].forEach(s=>{
    sellerList.innerHTML+=`
    <div class="ticket">
      <b>${s}</b>
      <button onclick="openSellerProfile('${s}')">View Profile</button>
    </div>`;
  });
}
function openSellerProfile(name){
  openScreen("sellerDashboard");
  sellerTitle.innerText=name;
  sellerProducts.innerHTML="";
  products.forEach((p,index)=>{
    if(p.s===name){
      sellerProducts.innerHTML+=`
      <div class="ticket">
        <b>${p.n}</b><br>
        Price <input value="${p.p}" onchange="products[${index}].p=this.value;save();renderProducts()"><br>
        Quantity <input value="${p.qty}" onchange="products[${index}].qty=this.value;save();renderProducts()"><br>
        <button style="background:#dc2626" onclick="deleteProduct(${index})">Delete</button>
      </div>`;
    }
  });
}
function deleteProduct(i){
  if(!confirm("Delete this product?"))return;
  products.splice(i,1);
  save();
  renderProducts();
}
function addProduct(){
  products.unshift({
    n:pname.value,
    p:+pprice.value,
    qty:+pqty.value,
    s:sname.value,
    city:scity.value,
    i:pimg.value||"https://picsum.photos/400/300?random="+Math.random(),
    d:pdesc.value
  });
  save();
  renderProducts();
  openScreen("home");
}
function save(){localStorage.setItem("products",JSON.stringify(products));}

renderProducts();
renderSellerList();
openScreen("home");
</script>

</body>
</html>
