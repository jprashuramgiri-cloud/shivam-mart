# shivam-mart
<!DOCTYPE html>
<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Shivam Mart</title>

<style>
body{margin:0;font-family:Arial;background:#f2f2f2;}
header{
background:#0c831f;
color:white;
padding:15px;
text-align:center;
font-size:20px;
}

.section{display:none;padding:10px;}
.active{display:block;}

.products{
display:grid;
grid-template-columns:repeat(2,1fr);
gap:10px;
}

.card{
background:white;
padding:10px;
border-radius:10px;
box-shadow:0 2px 8px rgba(0,0,0,0.1);
}

.card img{
width:100%;
height:100px;
object-fit:cover;
border-radius:8px;
}

button{
background:#0c831f;
color:white;
border:none;
padding:8px;
width:100%;
border-radius:8px;
margin-top:5px;
}

.bottom-nav{
position:fixed;
bottom:0;
width:100%;
background:white;
display:flex;
justify-content:space-around;
border-top:1px solid #ccc;
padding:8px 0;
}

.bottom-nav div{
text-align:center;
font-size:14px;
}

input{
width:100%;
padding:10px;
margin:5px 0;
border-radius:8px;
border:1px solid #ccc;
}
</style>
</head>

<body>

<header>🛒 Shivam Mart</header>

<!-- HOME -->
<div id="home" class="section active">
<div class="products">
<div class="card">
<img src="https://images.unsplash.com/photo-1586201375761-83865001e31c">
<h4>Apples</h4>
<button onclick="addOrder('Apples')">Add</button>
</div>

<div class="card">
<img src="https://images.unsplash.com/photo-1580910051074-3eb694886505">
<h4>Bananas</h4>
<button onclick="addOrder('Bananas')">Add</button>
</div>
</div>
</div>

<!-- ORDERS -->
<div id="orders" class="section">
<h3>Your Orders</h3>
<ul id="orderList"></ul>
</div>

<!-- PROFILE -->
<div id="profile" class="section">
<h3>Profile</h3>
<p id="userInfo">Not Logged In</p>
<button onclick="showSection('login')">Login / Signup</button>
</div>

<!-- LOGIN -->
<div id="login" class="section">
<h3>Login</h3>
<input type="text" id="username" placeholder="Enter Name">
<input type="password" placeholder="Enter Password">
<button onclick="login()">Login</button>
</div>

<!-- BOTTOM NAV -->
<div class="bottom-nav">
<div onclick="showSection('home')">🏠 Home</div>
<div onclick="showSection('orders')">📦 Orders</div>
<div onclick="showSection('profile')">👤 Profile</div>
</div>

<script>
let orders=[];
let user="";

function showSection(id){
document.querySelectorAll('.section').forEach(s=>s.classList.remove('active'));
document.getElementById(id).classList.add('active');
}

function addOrder(item){
orders.push(item);
updateOrders();
alert(item+" added to cart 🛒");
}

function updateOrders(){
let list=document.getElementById("orderList");
list.innerHTML="";
orders.forEach(o=>{
let li=document.createElement("li");
li.textContent=o;
list.appendChild(li);
});
}

function login(){
user=document.getElementById("username").value;
if(user!=""){
document.getElementById("userInfo").innerHTML="Welcome, "+user;
alert("Login Successful 🎉");
showSection('profile');
}
}
</script>

</body>
</html>
