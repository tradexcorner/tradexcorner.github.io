<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>TradeXCorner</title>

<link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;800&display=swap" rel="stylesheet">

<script src="https://cdnjs.cloudflare.com/ajax/libs/three.js/r134/three.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>

<style>
:root {
  --primary:#00E5FF;
  --accent:#7CFFCB;
  --dark:#0B1220;
}

* {
  margin:0;
  padding:0;
  box-sizing:border-box;
  font-family:'Inter',sans-serif;
}

body {
  background:linear-gradient(135deg,#f0fbff,#ffffff);
  color:var(--dark);
  overflow-x:hidden;
}

/* NAVBAR */
nav {
  position:fixed;
  width:100%;
  display:flex;
  justify-content:space-between;
  padding:20px 40px;
  background:rgba(255,255,255,0.8);
  backdrop-filter:blur(10px);
  z-index:10;
}

nav h2 {
  color:var(--primary);
}

nav a {
  margin-left:20px;
  text-decoration:none;
  color:#333;
  font-weight:500;
}

/* HERO */
.hero {
  height:100vh;
  display:flex;
  justify-content:center;
  align-items:center;
  text-align:center;
  flex-direction:column;
}

.hero h1 {
  font-size:65px;
  background:linear-gradient(45deg,#00E5FF,#7CFFCB);
  -webkit-background-clip:text;
  color:transparent;
}

.hero p {
  margin-top:15px;
  max-width:600px;
  opacity:0.7;
}

.btn {
  margin-top:25px;
  padding:14px 30px;
  border-radius:30px;
  border:none;
  background:var(--primary);
  color:#000;
  font-weight:600;
  cursor:pointer;
  transition:0.3s;
}

.btn:hover {
  transform:scale(1.05);
}

/* SECTION */
section {
  padding:100px 20px;
  max-width:1100px;
  margin:auto;
}

/* GRID */
.grid {
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:25px;
}

/* CARD */
.card {
  background:white;
  padding:25px;
  border-radius:18px;
  box-shadow:0 15px 40px rgba(0,0,0,0.08);
  transition:0.4s;
}

.card:hover {
  transform:translateY(-10px);
}

/* TICKER */
.ticker {
  background:var(--primary);
  padding:10px;
  color:#000;
  font-weight:600;
  overflow:hidden;
}

.ticker span {
  display:inline-block;
  padding-left:100%;
  animation:ticker 15s linear infinite;
}

@keyframes ticker {
  0% { transform:translateX(0); }
  100% { transform:translateX(-100%); }
}

/* TESTIMONIAL */
.testimonial {
  font-style:italic;
}

/* CTA FLOAT */
.whatsapp {
  position:fixed;
  bottom:20px;
  right:20px;
  background:#25D366;
  padding:16px;
  border-radius:50%;
  color:white;
  font-size:22px;
  text-decoration:none;
}

/* THREE BG */
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
<h2>TradeXCorner</h2>
<div>
<a href="#learn">Learn</a>
<a href="#course">Courses</a>
<a href="#about">About</a>
</div>
</nav>

<div class="ticker">
<span>📈 +₹12,450 | +₹8,200 | +₹21,900 | +₹6,500 | Real Learning • Real Growth</span>
</div>

<!-- HERO -->
<div class="hero">
<h1>Master Smart Trading</h1>
<p>Build mindset, strategy, and discipline with real market experience.</p>
<button class="btn">Start Your Journey</button>
</div>

<!-- LEARNING -->
<section id="learn">
<h2>What You Will Learn</h2>
<div class="grid">
<div class="card">Price Action</div>
<div class="card">Market Structure</div>
<div class="card">Trading Psychology</div>
<div class="card">Live Sessions</div>
</div>
</section>

<!-- COURSES -->
<section id="course">
<h2>Mentorship Programs</h2>
<div class="grid">
<div class="card">Price Action - ₹15,000</div>
<div class="card">Psychology - ₹25,000</div>
<div class="card">Mentorship - ₹55,555</div>
<div class="card">Trading Room - ₹12,000/year</div>
</div>
</section>

<!-- STORY -->
<section>
<h2>Why TradeXCorner?</h2>
<div class="grid">
<div class="card">Simplified Learning</div>
<div class="card">Real Market Exposure</div>
<div class="card">Lifetime Support</div>
<div class="card">Proven Strategies</div>
</div>
</section>

<!-- TESTIMONIAL -->
<section>
<h2>What Our Students Say</h2>
<div class="grid">
<div class="card testimonial">"Finally understood trading clearly."</div>
<div class="card testimonial">"No theory, pure practical."</div>
<div class="card testimonial">"Best decision I made."</div>
</div>
</section>

<!-- ABOUT -->
<section id="about">
<h2>About Us</h2>
<p>
TradeXCorner helps traders develop a profitable mindset, discipline, and real strategies.
</p>
</section>

<a class="whatsapp" href="https://wa.me/91XXXXXXXXXX">💬</a>

<script>
// THREE JS BACKGROUND
const scene = new THREE.Scene();
const camera = new THREE.PerspectiveCamera(75,window.innerWidth/window.innerHeight,0.1,1000);
const renderer = new THREE.WebGLRenderer({canvas:document.getElementById('bg'),alpha:true});

renderer.setSize(window.innerWidth,window.innerHeight);
camera.position.z = 5;

const geometry = new THREE.BufferGeometry();
const count = 800;
const positions = new Float32Array(count*3);

for(let i=0;i<count*3;i++){
  positions[i]=(Math.random()-0.5)*10;
}

geometry.setAttribute('position',new THREE.BufferAttribute(positions,3));

const material = new THREE.PointsMaterial({size:0.02,color:'#00E5FF'});
const mesh = new THREE.Points(geometry,material);

scene.add(mesh);

function animate(){
  requestAnimationFrame(animate);
  mesh.rotation.y += 0.001;
  renderer.render(scene,camera);
}
animate();

// GSAP ANIMATIONS
gsap.from(".hero h1",{opacity:0,y:-60,duration:1});
gsap.from(".hero p",{opacity:0,y:40,duration:1,delay:0.3});
gsap.from(".card",{opacity:0,y:50,stagger:0.2,duration:1});
</script>

</body>
</html>
