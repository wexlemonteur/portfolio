<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Portfolio Montage Vidéo</title>

<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;600;800&family=Inter:wght@300;400;600&display=swap" rel="stylesheet">

<style>
:root{
  --blue:#00c3ff;
  --purple:#7a00ff;
  --black:#07070c;
  --glass:rgba(255,255,255,0.06);
}

*{
  margin:0;
  padding:0;
  box-sizing:border-box;
}

body{
  font-family:Inter;
  background:var(--black);
  color:white;
  overflow-x:hidden;
}

/* PARTICLES BACKGROUND */
#particles{
  position:fixed;
  inset:0;
  z-index:-1;
}

/* HEADER */
header{
  position:fixed;
  top:0;
  width:100%;
  display:flex;
  justify-content:space-between;
  padding:15px 40px;
  backdrop-filter:blur(15px);
  background:rgba(0,0,0,0.4);
  z-index:1000;
}

header h1{
  font-family:Orbitron;
  color:var(--blue);
  font-size:18px;
}

nav a{
  color:white;
  margin-left:20px;
  text-decoration:none;
  opacity:0.7;
  transition:0.3s;
}

nav a:hover{
  opacity:1;
  color:var(--purple);
}

/* HERO */
.hero{
  height:100vh;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  text-align:center;
}

.hero h2{
  font-family:Orbitron;
  font-size:50px;
  background:linear-gradient(90deg,var(--blue),var(--purple));
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

.hero p{
  margin-top:15px;
  opacity:0.8;
  max-width:600px;
}

.btn{
  margin-top:25px;
  padding:12px 25px;
  border:none;
  border-radius:8px;
  cursor:pointer;
  font-weight:bold;
  background:linear-gradient(90deg,var(--blue),var(--purple));
  transition:0.3s;
}

.btn:hover{
  transform:scale(1.05);
  box-shadow:0 0 20px rgba(0,195,255,0.4);
}

/* SECTIONS */
section{
  padding:80px 10%;
}

/* GLASS CARD */
.card{
  background:var(--glass);
  border:1px solid rgba(255,255,255,0.1);
  padding:20px;
  border-radius:15px;
  backdrop-filter:blur(10px);
  transition:0.3s;
}

.card:hover{
  transform:translateY(-8px);
  border-color:var(--blue);
}

/* GRID */
.grid{
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
  gap:20px;
}

/* TITLE */
h3{
  font-family:Orbitron;
  margin-bottom:20px;
  color:var(--blue);
}

/* COUNTER */
.counter{
  font-size:60px;
  font-family:Orbitron;
  color:var(--purple);
}

/* CONTACT */
input,textarea{
  width:100%;
  margin-top:10px;
  padding:12px;
  border:none;
  border-radius:8px;
  background:rgba(255,255,255,0.05);
  color:white;
}

.socials a{
  margin-right:10px;
  color:var(--blue);
}

/* FADE ANIMATION */
.fade{
  opacity:0;
  transform:translateY(30px);
  transition:1s;
}

.fade.show{
  opacity:1;
  transform:translateY(0);
}
</style>
</head>

<body>

<canvas id="particles"></canvas>

<header>
  <h1>VIDEO EDIT PORTFOLIO</h1>
  <nav>
    <a href="#about">À propos</a>
    <a href="#portfolio">Portfolio</a>
    <a href="#pricing">Tarifs</a>
    <a href="#contact">Contact</a>
  </nav>
</header>

<section class="hero">
  <h2>Monteur Vidéo Fortnite Pro</h2>
  <p>Montages dynamiques, effets gaming, et vidéos optimisées pour TikTok, YouTube Shorts et streamers.</p>
  <button class="btn" onclick="document.getElementById('contact').scrollIntoView()">Me contacter</button>
</section>

<section id="about" class="fade">
  <h3>À propos</h3>
  <div class="card">
    Passionné par le montage vidéo Fortnite, je crée des contenus dynamiques sur Adobe Premiere Pro.
    Chaque montage est optimisé pour garder l’attention et booster l’engagement.
  </div>
</section>

<section id="portfolio" class="fade">
  <h3>Portfolio</h3>
  <div class="grid">
    <div class="card">🎬 Highlight Fortnite</div>
    <div class="card">⚡ Kill Montage</div>
    <div class="card">🔥 TikTok Edit</div>
  </div>
</section>

<section id="pricing" class="fade">
  <h3>Tarifs</h3>
  <div class="grid">
    <div class="card">
      <h4>Short</h4>
      <p style="color:var(--purple);font-size:28px;">3€</p>
      <p>TikTok / Reels / Shorts</p>
    </div>
    <div class="card">
      <h4>Vidéo complète</h4>
      <p style="color:var(--purple);font-size:28px;">5€</p>
      <p>Montage gaming professionnel</p>
    </div>
  </div>
</section>

<section class="fade">
  <h3>Projets réalisés</h3>
  <div class="counter" id="counter">0</div>
</section>

<section id="contact" class="fade">
  <h3>Contact</h3>

  <div class="card">
    <input placeholder="Nom"/>
    <input placeholder="Email"/>
    <textarea rows="4" placeholder="Message"></textarea>
    <button class="btn">Envoyer</button>

    <div class="socials" style="margin-top:15px;">
      Discord | TikTok | YouTube | Instagram
    </div>

    <p style="margin-top:10px;opacity:0.8;">
      Prêt à améliorer vos vidéos ? Contactez-moi dès maintenant !
    </p>
  </div>
</section>

<script>
/* FADE ON SCROLL */
const els=document.querySelectorAll('.fade');
const obs=new IntersectionObserver(e=>{
  e.forEach(x=>{
    if(x.isIntersecting) x.target.classList.add('show');
  });
});
els.forEach(e=>obs.observe(e));

/* COUNTER */
let c=0;
const counter=document.getElementById("counter");
setInterval(()=>{
  if(c<150){
    c++;
    counter.innerText=c+"+";
  }
},20);

/* PARTICLES SIMPLE */
const canvas=document.getElementById("particles");
const ctx=canvas.getContext("2d");

canvas.width=window.innerWidth;
canvas.height=window.innerHeight;

let particles=[];
for(let i=0;i<80;i++){
  particles.push({
    x:Math.random()*canvas.width,
    y:Math.random()*canvas.height,
    r:Math.random()*2,
    dx:(Math.random()-0.5)*0.5,
    dy:(Math.random()-0.5)*0.5
  });
}

function draw(){
  ctx.clearRect(0,0,canvas.width,canvas.height);
  ctx.fillStyle="white";

  particles.forEach(p=>{
    ctx.beginPath();
    ctx.arc(p.x,p.y,p.r,0,Math.PI*2);
    ctx.fill();

    p.x+=p.dx;
    p.y+=p.dy;

    if(p.x<0||p.x>canvas.width) p.dx*=-1;
    if(p.y<0||p.y>canvas.height) p.dy*=-1;
  });

  requestAnimationFrame(draw);
}
draw();
</script>

</body>
</html>
