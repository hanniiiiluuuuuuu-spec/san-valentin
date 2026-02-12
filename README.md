# san-valentin
te amo
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Nuestro Para Siempre ❤️</title>

<style>
body{
margin:0;
font-family:'Segoe UI',sans-serif;
background:black;
color:white;
overflow:hidden;
text-align:center;
}

/* Fondo estrellas */
canvas{
position:fixed;
top:0;
left:0;
z-index:-2;
}

/* Pantalla inicial */
#bloqueo{
position:fixed;
width:100%;
height:100%;
background:linear-gradient(45deg,#ff3366,#ff99aa);
display:flex;
flex-direction:column;
justify-content:center;
align-items:center;
z-index:10;
}

input{
padding:12px;
border-radius:10px;
border:none;
font-size:18px;
margin-top:10px;
}

button{
padding:12px 25px;
border:none;
border-radius:20px;
font-size:18px;
cursor:pointer;
margin:10px;
}

#contenido{
display:none;
padding:20px;
}

.carta{
background:rgba(255,255,255,0.1);
padding:20px;
border-radius:20px;
width:85%;
margin:auto;
min-height:120px;
}

.galeria{
position:relative;
width:280px;
height:180px;
margin:20px auto;
overflow:hidden;
border-radius:15px;
}

.galeria img{
width:100%;
height:100%;
position:absolute;
transition:opacity 1s;
}

#no{
position:absolute;
background:#444;
color:white;
}

#final{
display:none;
position:fixed;
width:100%;
height:100%;
background:black;
justify-content:center;
align-items:center;
flex-direction:column;
font-size:35px;
z-index:20;
}

/* Anillo */
#anillo{
font-size:80px;
cursor:pointer;
animation:latido 1.5s infinite;
}

@keyframes latido{
0%,100%{transform:scale(1);}
50%{transform:scale(1.2);}
}
</style>
</head>

<body>

<canvas id="estrellas"></canvas>

<div id="bloqueo">
<h1>Ingresa nuestra fecha especial 💖</h1>
<input type="password" id="clave">
<button onclick="verificar()">Entrar</button>
</div>

<div id="contenido">

<h1>Nuestra Historia ❤️</h1>
<h3 id="contador"></h3>

<div class="carta">
<p id="texto"></p>
</div>

<h2>📸 Recuerdos</h2>
<div class="galeria">
<img src="FOTO1.jpeg" style="opacity:1">
<img src="FOTO2.jpeg" style="opacity:0">
<img src="FOTO3.jpeg" style="opacity:0">
</div>

<h2>¿Aceptas seguir escribiendo esta historia conmigo? 💍</h2>

<div id="anillo" onclick="abrirAnillo()">💍</div>

<button onclick="aceptar()">SI 💖</button>
<button id="no">NO 😢</button>

</div>

<div id="final">
🎆 DIJO QUE SÍ 🎆
<br><br>
Prometo elegirte todos los días ❤️
</div>

<audio autoplay loop>
<source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
</audio>

<script>

/* PERSONALIZAR */
const claveCorrecta="14022024";
const fechaInicio=new Date("2024-02-14");

/* VERIFICAR */
function verificar(){
if(document.getElementById("clave").value===claveCorrecta){
document.getElementById("bloqueo").style.display="none";
document.getElementById("contenido").style.display="block";
escribirTexto();
iniciarContador();
iniciarGaleria();
}
}

/* CARTA ANIMADA */
const mensaje=`Desde que llegaste a mi vida, todo cambió.
No somos perfectos, pero somos reales.
Te elegiría en todas mis vidas.
Quiero un para siempre contigo. ❤️`;

let i=0;
function escribirTexto(){
if(i<mensaje.length){
document.getElementById("texto").innerHTML+=mensaje.charAt(i);
i++;
setTimeout(escribirTexto,40);
}
}

/* CONTADOR EXACTO */
function iniciarContador(){
setInterval(()=>{
const ahora=new Date();
const diff=ahora-fechaInicio;

const dias=Math.floor(diff/(1000*60*60*24));
const horas=Math.floor((diff/(1000*60*60))%24);
const minutos=Math.floor((diff/(1000*60))%60);
const segundos=Math.floor((diff/1000)%60);

document.getElementById("contador").innerText=
`${dias} días ${horas}h ${minutos}m ${segundos}s juntos`;
},1000);
}

/* GALERÍA */
function iniciarGaleria(){
let index=0;
const imgs=document.querySelectorAll(".galeria img");
setInterval(()=>{
imgs.forEach(img=>img.style.opacity=0);
index=(index+1)%imgs.length;
imgs[index].style.opacity=1;
},3000);
}

/* BOTÓN NO */
const noBtn=document.getElementById("no");
noBtn.addEventListener("mouseover",()=>{
noBtn.style.top=Math.random()*500+"px";
noBtn.style.left=Math.random()*500+"px";
});

/* ANILLO */
function abrirAnillo(){
alert("Prometo cuidarte, respetarte y amarte siempre ❤️");
}

/* FINAL + FUEGOS */
function aceptar(){
document.getElementById("final").style.display="flex";
fuegos();
}

function fuegos(){
setInterval(()=>{
const f=document.createElement("div");
f.innerHTML="✨";
f.style.position="fixed";
f.style.left=Math.random()*100+"vw";
f.style.top=Math.random()*100+"vh";
f.style.fontSize="25px";
document.body.appendChild(f);
setTimeout(()=>f.remove(),1000);
},100);
}

/* ESTRELLAS */
const canvas=document.getElementById("estrellas");
const ctx=canvas.getContext("2d");
canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let estrellas=[];
for(let i=0;i<120;i++){
estrellas.push({
x:Math.random()*canvas.width,
y:Math.random()*canvas.height,
r:Math.random()*2
});
}

function dibujar(){
ctx.clearRect(0,0,canvas.width,canvas.height);
ctx.fillStyle="white";
estrellas.forEach(e=>{
ctx.beginPath();
ctx.arc(e.x,e.y,e.r,0,Math.PI*2);
ctx.fill();
});
requestAnimationFrame(dibujar);
}
dibujar();

/* MENSAJES SECRETOS AL TOCAR */
document.addEventListener("click",function(){
const mensajes=[
"Eres mi persona favorita ❤️",
"Gracias por existir 💕",
"Te elegiría siempre 💍",
"Mi lugar seguro eres tú ✨"
];
const m=document.createElement("div");
m.innerText=mensajes[Math.floor(Math.random()*mensajes.length)];
m.style.position="fixed";
m.style.left=Math.random()*80+"vw";
m.style.top=Math.random()*80+"vh";
m.style.color="#ff99cc";
document.body.appendChild(m);
setTimeout(()=>m.remove(),2000);
});
</script>

</body>
</html>