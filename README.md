
<html lang="ru">
<head>

<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0">

<title>Gipsy Sell Car</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
}

body{
font-family:'Poppins',sans-serif;
background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);
color:white;
min-height:100vh;
}

header{
text-align:center;
padding:50px 20px;
background:rgba(0,0,0,0.4);
backdrop-filter:blur(10px);
}

header h1{
font-size:40px;
}

header p{
color:#ccc;
margin-top:10px;
}

/* SEARCH */

.filters{

display:flex;
gap:10px;
justify-content:center;
flex-wrap:wrap;
padding:20px;

}

input{

padding:10px;
border-radius:6px;
border:none;
}

button.filter{

padding:10px 20px;
border:none;
background:#ff416c;
color:white;
border-radius:6px;
cursor:pointer;

}

/* GRID */

.cars{

max-width:1200px;
margin:auto;
display:grid;
grid-template-columns:repeat(auto-fit,minmax(280px,1fr));
gap:25px;
padding:20px;

}

.card{

background:rgba(255,255,255,0.05);
border-radius:15px;
overflow:hidden;
box-shadow:0 10px 30px rgba(0,0,0,0.6);
transition:0.3s;

}

.card:hover{

transform:translateY(-8px);

}

.card img{

width:100%;
height:200px;
object-fit:cover;

}

.card-body{

padding:15px;
text-align:center;

}

.price{

color:#00ff9d;
font-size:22px;
margin:10px 0;

}

.btn{

background:linear-gradient(45deg,#ff512f,#dd2476);
border:none;
padding:10px;
width:100%;
color:white;
border-radius:8px;
cursor:pointer;

}

/* MODAL */

.modal{

position:fixed;
top:0;
left:0;
width:100%;
height:100%;
background:rgba(0,0,0,0.8);
display:none;
justify-content:center;
align-items:center;

}

.modal-content{

background:#1e2a38;
padding:20px;
border-radius:10px;
max-width:500px;
width:90%;
text-align:center;

}

.modal img{

width:100%;
border-radius:8px;
margin-bottom:10px;

}

.close{

cursor:pointer;
float:right;
font-size:22px;

}

/* WHATSAPP */

.whatsapp{

position:fixed;
bottom:20px;
right:20px;
background:#25D366;
width:60px;
height:60px;
border-radius:50%;
display:flex;
align-items:center;
justify-content:center;
font-size:30px;
color:white;
text-decoration:none;

}

</style>

</head>

<body>

<header>

<h1>Gipsy Sell Car</h1>

<p>Продажа автомобилей в Европе</p>

</header>

<div class="filters">

<input id="search" placeholder="Поиск машины">
<input id="minPrice" placeholder="Мин €">
<input id="maxPrice" placeholder="Макс €">

<button class="filter" onclick="filterCars()">Фильтр</button>

</div>

<div class="cars" id="cars"></div>

<div class="modal" id="modal">

<div class="modal-content">

<span class="close" onclick="closeModal()">✖️</span>

<img id="modalImg">

<h2 id="modalTitle"></h2>

<p id="modalInfo"></p>

<p class="price" id="modalPrice"></p>

<button class="btn" id="buyBtn">Купить</button>

</div>

</div>

<a class="whatsapp" href="https://wa.me/380984763293">💬</a>

<script>

const cars=[

{
name:"BMW E46",
year:2000,
type:"Седан",
engine:"2.0 бензин",
price:1500,
img:"https://upload.wikimedia.org/wikipedia/commons/7/7d/BMW_E46_320i.jpg"
},

{
name:"Ford Mondeo",
year:2001,
type:"Универсал",
engine:"2.0 бензин",
price:1400,
img:"https://upload.wikimedia.org/wikipedia/commons/4/46/Ford_Mondeo_Mk3.jpg"
},

{
name:"Opel Astra",
year:2011,
type:"Универсал",
engine:"1.3 дизель",
price:2500,
img:"https://upload.wikimedia.org/wikipedia/commons/0/0e/Opel_Astra_J_Sports_Tourer.jpg"
},

{
name:"BMW E46 Touring",
year:2000,
type:"Универсал",
engine:"2.0 бензин",
price:1500,
img:"https://upload.wikimedia.org/wikipedia/commons/9/9b/BMW_E46_Touring.jpg"
}

];

function renderCars(list){

const container=document.getElementById("cars");

container.innerHTML="";

list.forEach(car=>{

container.innerHTML+=`

<div class="card">

<img src="${car.img}">

<div class="card-body">

<h3>${car.name}</h3>

<p>${car.year} | ${car.type} | ${car.engine}</p>

<p class="price">€${car.price}</p>

<button class="btn" onclick="openModal('${car.name}','${car.year} | ${car.type} | ${car.engine}','${car.price}','${car.img}')">

Подробнее

</button>

</div>

</div>

`;

});

}

function openModal(name,info,price,img){

document.getElementById("modal").style.display="flex";

document.getElementById("modalTitle").innerText=name;

document.getElementById("modalInfo").innerText=info;

document.getElementById("modalPrice").innerText="€"+price;

document.getElementById("modalImg").src=img;

document.getElementById("buyBtn").onclick=()=>{

window.open("https://wa.me/380984763293","_blank");

};

}

function closeModal(){

document.getElementById("modal").style.display="none";

}

function filterCars(){

const search=document.getElementById("search").value.toLowerCase();

const min=document.getElementById("minPrice").value;

const max=document.getElementById("maxPrice").value;

let filtered=cars.filter(car=>{

return (

car.name.toLowerCase().includes(search)

&& (min=="" || car.price>=min)

&& (max=="" || car.price<=max)

);

});

renderCars(filtered);

}

renderCars(cars);

</script>

</body>
</html>
