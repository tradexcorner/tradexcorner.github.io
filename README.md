<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>TradeXCorner</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>

<style>
body {
  margin:0;
  font-family:Poppins;
  background:linear-gradient(135deg,#e0f7ff,#ffffff);
  color:#0f172a;
  overflow-x:hidden;
}

/* Navbar */
nav {
  position:fixed;
  width:100%;
  background:white;
  display:flex;
  justify-content:space-around;
  padding:15px;
  box-shadow:0 5px 20px rgba(0,0,0,0.1);
  z-index:10;
}

/* Hero */
.hero {
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  flex-direction:column;
  text-align:center;
}

.hero h1 {
  font-size:60px;
  color:#00bcd4;
}

.btn {
  background:#00e5ff;
  padding:12px 25px;
  border-radius:30px;
  border:none;
  cursor:pointer;
  font-weight:bold;
}

/* Sections */
section {
  padding:80px 20px;
  max-width:1100px;
  margin:auto;
}

/* Cards */
.card {
  background:white;
  padding:20px;
  border-radius:15px;
  box-shadow:0 10px 25px rgba(0,0,0,0.1);
  transition:0.4s;
}
.card:hover {
  transform:translateY(-10px) scale(1.05);
}

/* Grid */
.grid {
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
}

/* Ticker */
.ticker {
  background:#00e5ff;
  padding:10px;
  overflow:hidden;
  white-space:nowrap;
}
.ticker span {
  display:inline-block;
  padding-left:100%;
  animation:ticker 12s linear infinite;
}
@keyframes ticker {
  0% { transform:translateX(0); }
  100% { transform:translateX(-100%); }
}

/* Testimonials */
.testimonial {
  font-style:italic;
}

/* CTA Floating */
.whatsapp {
  position:fixed;
  bottom:20px;
  right:20px;
  background:#25D366;
  color:white;
  padding:15px;
  border-radius:50%;
  font-size:20px;
  text-decoration:none;
}

/* Canvas */
#bg {
  position:fixed;
  top:0;
  left:0;
  z-index:-1;
}
</style>
</head>

<body>

<canvas id="bg"></canvas>

<nav>
<a href="#home">Home</a>
<a href="#course">Courses</a>
<a href="#about">About</a>
</nav>

<div class="ticker">
<span>📈 +₹12,500 | +₹8,900 | +₹21,300 | +₹6,700 | Real Students. Real Growth.</span>
</div>

<div class="hero" id="home">
<h1>TradeXCorner</h1>
<p>Learn Smart Trading with Real Market Experience</p>
<button class="btn">Join Mentorship</button>
</div>

<section>
<h2>What We Teach</h2>
<div class="grid">
<div class="card">Price Action</div>
<div class="card">Trading Psychology</div>
<div class="card">Live Trading</div>
<div class="card">Market Structure</div>
</div>
</section>

<section id="course">
<h2>Courses</h2>
<div class="grid">
<div class="card">Price Action - ₹15,000</div>
<div class="card">Psychology - ₹25,000</div>
<div class="card">Mentorship - ₹55,555</div>
<div class="card">Trading Room - ₹12,000</div>
</div>
</section>

<section>
<h2>Testimonials</h2>
<div class="grid">
<div class="card testimonial">"I finally understood trading!"</div>
<div class="card testimonial">"Best mentorship ever."</div>
<div class="card testimonial">"Real results, no fake promises."</div>
</div>
</section>

<section id="about">
<h2>About</h2>
<p>TradeXCorner helps traders build discipline, mindset, and strategies.</p>
</section>

<a class="whatsapp" href="https://wa.me/91XXXXXXXXXX">💬</a>

<script>
// THREE JS PARTICLES
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75, window.innerWidth/window.innerHeight,0.1,1000);
const renderer = new THREE.WebGLRenderer({canvas:document.getElementById('bg'),alpha:true});

renderer.setSize(window.innerWidth,window.innerHeight);
camera.position.z = 5;

const particlesGeometry = new THREE.BufferGeometry();
const particlesCount = 500;

const posArray = new Float32Array(particlesCount*3);

for(let i=0;i<particlesCount*3;i++){
  posArray[i]=(Math.random()-0.5)*10;
}

particlesGeometry.setAttribute('position', new THREE.BufferAttribute(posArray,3));

const material = new THREE.PointsMaterial({size:0.02,color:'#00bcd4'});
const particlesMesh = new THREE.Points(particlesGeometry,material);

scene.add(particlesMesh);

function animate(){
  requestAnimationFrame(animate);
  particlesMesh.rotation.y += 0.001;
  renderer.render(scene,camera);
}
animate();

// GSAP SCROLL
gsap.from(".card",{opacity:0,y:50,stagger:0.2});
</script>

</body>
</html>
