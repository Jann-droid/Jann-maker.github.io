# Jann-maker.github.io
Destroy inefficiency


<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no">
<title>Clean Administrative & Regulatory Burdens</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@700;900&family=Share+Tech+Mono&display=swap');

- { margin:0; padding:0; box-sizing:border-box; }

body {
background:#000a1a;
display:flex; flex-direction:column; align-items:center; justify-content:flex-start;
min-height:100vh; overflow:hidden;
font-family:‘Share Tech Mono’,monospace;
}

body::before {
content:’’; position:fixed; inset:0; pointer-events:none; z-index:0;
background-image:
radial-gradient(1px 1px at 8% 12%,  #fff 0%,transparent 100%),
radial-gradient(1px 1px at 22% 55%, #adf 0%,transparent 100%),
radial-gradient(1px 1px at 47% 8%,  #fff 0%,transparent 100%),
radial-gradient(1px 1px at 63% 78%, #ffd 0%,transparent 100%),
radial-gradient(1px 1px at 85% 33%, #fff 0%,transparent 100%),
radial-gradient(1px 1px at 14% 70%, #adf 0%,transparent 100%),
radial-gradient(1px 1px at 38% 42%, #fff 0%,transparent 100%),
radial-gradient(1px 1px at 75% 18%, #fff 0%,transparent 100%),
radial-gradient(1px 1px at 92% 60%, #ffd 0%,transparent 100%),
radial-gradient(1px 1px at 55% 88%, #adf 0%,transparent 100%),
radial-gradient(1px 1px at 3%  45%, #fff 0%,transparent 100%),
radial-gradient(1px 1px at 97% 25%, #fff 0%,transparent 100%);
}

.title {
font-family:‘Orbitron’,monospace; font-weight:900;
font-size:clamp(12px,2vw,19px); color:#ff6a00;
text-shadow:0 0 12px #ff6a00,0 0 30px #ff4400;
letter-spacing:2px; text-align:center;
padding:10px 16px 4px; position:relative; z-index:10;
animation:glow 2s ease-in-out infinite alternate;
}
@keyframes glow {
from { text-shadow:0 0 8px #ff6a00,0 0 20px #ff4400; }
to   { text-shadow:0 0 18px #ffaa00,0 0 50px #ff6600; }
}

.hud {
display:flex; justify-content:space-between;
width:min(800px,100vw); padding:2px 12px 4px;
color:#00ff88; font-size:13px; position:relative; z-index:10;
}

.game-wrapper {
position:relative; width:min(800px,100vw); z-index:10;
}

canvas {
display:block; width:100%; height:auto;
border:2px solid #ff6a00;
box-shadow:0 0 24px rgba(255,106,0,.45),0 0 70px rgba(255,106,0,.15);
background:#000a1a;
}

/* OVERLAY — sits inside .game-wrapper */
.overlay {
position:absolute; inset:0;
background:rgba(0,5,20,.88);
display:flex; flex-direction:column; align-items:center; justify-content:center;
z-index:50; font-family:‘Orbitron’,monospace;
}
.overlay h2 {
font-size:clamp(26px,6vw,50px); color:#ff6a00;
text-shadow:0 0 24px #ff6a00; margin-bottom:12px;
}
.overlay .msg {
font-family:‘Share Tech Mono’,monospace; color:#00ff88;
font-size:clamp(11px,2vw,16px); margin-bottom:6px;
text-align:center; padding:0 20px;
}
.overlay .hint { color:#445; font-size:clamp(10px,1.4vw,12px); margin-top:4px; }
.start-btn {
margin-top:22px; padding:12px 42px;
background:transparent; border:2px solid #ff6a00;
color:#ff6a00; font-family:‘Orbitron’,monospace;
font-size:clamp(13px,2vw,17px); cursor:pointer;
letter-spacing:2px; text-shadow:0 0 10px #ff6a00;
box-shadow:0 0 20px rgba(255,106,0,.3); transition:all .18s;
}
.start-btn:hover,.start-btn:active {
background:#ff6a00; color:#000;
box-shadow:0 0 40px rgba(255,106,0,.9);
}

/* ─── CONTROLS ─── */
.controls {
display:flex; justify-content:center; align-items:stretch;
gap:14px; padding:14px 0 10px;
position:relative; z-index:10; width:min(800px,100vw);
}

.ctrl-btn {
display:flex; flex-direction:column;
align-items:center; justify-content:center;
font-family:‘Orbitron’,monospace; font-weight:700;
cursor:pointer; border-radius:14px;
user-select:none; -webkit-user-select:none;
touch-action:none; -webkit-tap-highlight-color:transparent;
transition:transform .08s, filter .08s, box-shadow .08s;
border:none; outline:none;
}

/* LEFT / RIGHT */
.btn-move {
width:100px; height:76px;
background:linear-gradient(155deg,#1c2e40 0%,#0a1822 100%);
border:2.5px solid #ff6a00;
color:#ff6a00; font-size:32px;
box-shadow:0 0 16px rgba(255,106,0,.35),inset 0 1px 0 rgba(255,180,80,.12);
}
.btn-move .lbl { font-size:10px; letter-spacing:1.5px; opacity:.55; margin-top:3px; }
.btn-move:hover { box-shadow:0 0 22px rgba(255,106,0,.6); }
.btn-move.pressed,
.btn-move:active {
transform:scale(.9);
background:linear-gradient(155deg,#3a1800 0%,#1a0a00 100%);
box-shadow:0 0 32px rgba(255,106,0,.9),inset 0 0 12px rgba(255,106,0,.25);
filter:brightness(1.3);
}

/* FIRE */
.btn-fire {
width:140px; height:76px;
background:linear-gradient(155deg,#001c12 0%,#000d08 100%);
border:2.5px solid #00ff88;
color:#00ff88; font-size:16px; letter-spacing:2px;
box-shadow:0 0 16px rgba(0,255,136,.32),inset 0 1px 0 rgba(0,255,136,.08);
}
.btn-fire .lbl { font-size:10px; letter-spacing:1px; opacity:.5; margin-top:3px; }
.btn-fire:hover { box-shadow:0 0 22px rgba(0,255,136,.6); }
.btn-fire.pressed,
.btn-fire:active {
transform:scale(.9);
background:linear-gradient(155deg,#00351a 0%,#001a0d 100%);
box-shadow:0 0 32px rgba(0,255,136,.9),inset 0 0 12px rgba(0,255,136,.25);
filter:brightness(1.3);
}

/* ─── METRO LOGO ─── */
.metro-logo {
position:fixed; bottom:14px; right:16px; z-index:100;
filter:drop-shadow(0 2px 10px rgba(0,60,140,.7));
}
</style>

</head>
<body>

<div class="title">⚡ Clean Administrative &amp; Regulatory Burdens ⚡</div>

<div class="hud">
  <span>SCORE: <span id="scoreDisplay">0</span></span>
  <span>LIVES: <span id="livesDisplay">❤❤❤</span></span>
  <span>WAVE: <span id="waveDisplay">1</span></span>
</div>

<div class="game-wrapper">
  <canvas id="gameCanvas" width="800" height="520"></canvas>
  <div class="overlay" id="gameOverlay">
    <h2 id="overlayTitle">SPACE CLEANER</h2>
    <p class="msg" id="overlayMsg">Destroy the bureaucratic document invaders!</p>
    <p class="hint">Arrow keys · SPACE to fire · P to pause</p>
    <button class="start-btn" id="startBtn">▶ START MISSION</button>
  </div>
</div>

<!-- Big clear control buttons -->

<div class="controls">
  <button class="ctrl-btn btn-move" id="btnLeft">
    ◀
    <span class="lbl">LEFT</span>
  </button>

  <button class="ctrl-btn btn-fire" id="btnShoot">
    🔥 FIRE
    <span class="lbl">SPACE</span>
  </button>

  <button class="ctrl-btn btn-move" id="btnRight">
    ▶
    <span class="lbl">RIGHT</span>
  </button>
</div>

<!-- METRO AG Logo — SVG recreation matching the uploaded image exactly -->

<div class="metro-logo">
  <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 110 110" width="64" height="64">
    <!-- White rounded square background -->
    <rect width="110" height="110" rx="18" fill="#ffffff"/>
    <!-- Blue M shape: two outer legs + V notch in middle -->
    <!-- Left outer leg -->
    <polygon points="8,14 30,14 55,48 55,72 30,38 30,90 8,90" fill="#003087"/>
    <!-- Right outer leg -->
    <polygon points="102,14 80,14 55,48 55,72 80,38 80,90 102,90" fill="#003087"/>
    <!-- Gold/yellow rectangle — right side accent block -->
    <rect x="80" y="58" width="22" height="32" rx="2" fill="#F5A800"/>
  </svg>
</div>

<script>
// ════════════════════════════════════════════════════
//  SPACE INVADERS — Clean Burdens Edition
// ════════════════════════════════════════════════════
const canvas = document.getElementById('gameCanvas');
const ctx    = canvas.getContext('2d');
const W = canvas.width, H = canvas.height;

let score=0, lives=3, wave=1, gameState='idle';
let animFrame, lastTime=0;

// ── INPUT (works fully without keyboard focus) ────────────────────────────────
const keys = {};

window.addEventListener('keydown', e => {
  keys[e.code]=true;
  if(e.code==='Space') e.preventDefault();
  if(e.code==='KeyP') togglePause();
}, {passive:false});
window.addEventListener('keyup', e => { keys[e.code]=false; });

function togglePause(){
  if(gameState==='playing') gameState='paused';
  else if(gameState==='paused') gameState='playing';
}

// Pointer-based button binding — reliable in iframes, no focus needed
function bindBtn(id, keyCode){
  const el = document.getElementById(id);
  if(!el) return;
  const dn = e => { e.preventDefault(); keys[keyCode]=true;  el.classList.add('pressed'); };
  const up = e => { e.preventDefault(); keys[keyCode]=false; el.classList.remove('pressed'); };
  el.addEventListener('pointerdown',   dn, {passive:false});
  el.addEventListener('pointerup',     up, {passive:false});
  el.addEventListener('pointerleave',  up, {passive:false});
  el.addEventListener('pointercancel', up, {passive:false});
  // capture so dragging off still fires
  el.addEventListener('pointerdown', e => { try{ el.setPointerCapture(e.pointerId); }catch(_){} });
}
bindBtn('btnLeft',  'ArrowLeft');
bindBtn('btnRight', 'ArrowRight');
bindBtn('btnShoot', 'Space');

document.getElementById('startBtn').addEventListener('pointerdown', e => {
  e.preventDefault(); startGame();
});
canvas.addEventListener('pointerdown', ()=>{ if(gameState==='paused') gameState='playing'; });

// ── ENTITIES ─────────────────────────────────────────────────────────────────
let player, bullets, invaderBullets, invaders, barriers, particles;
let invaderDir=1, invaderMovePeriod=0.55, invaderMoveTimer=0;
let invaderDropAmt=16, invaderShootTimer=0, invaderShootInterval=1.3;

function updateHUD(){
  document.getElementById('scoreDisplay').textContent = score;
  document.getElementById('livesDisplay').textContent = '❤'.repeat(Math.max(0,lives));
  document.getElementById('waveDisplay').textContent  = wave;
}

function initGame(){ score=0; lives=3; wave=1; updateHUD(); setupWave(); }

function setupWave(){
  invaderDir=1;
  invaderMovePeriod    = Math.max(0.09, 0.55-(wave-1)*0.06);
  invaderShootInterval = Math.max(0.38, 1.3-(wave-1)*0.1);
  invaderMoveTimer=0; invaderShootTimer=0;

  player = {x:W/2,y:H-52,w:60,h:44,speed:230,shootCooldown:0,invincible:0};
  bullets=[]; invaderBullets=[]; particles=[];

  invaders=[];
  const types=['pdf','doc','folder','xls','form'];
  for(let r=0;r<5;r++) for(let c=0;c<10;c++)
    invaders.push({x:52+c*70,y:52+r*52,w:44,h:40,type:types[r%5],alive:true});

  barriers=[];
  for(let i=0;i<4;i++) barriers.push({x:70+i*188,y:H-115,w:64,h:30,health:4});
}

// ── DRAWING ───────────────────────────────────────────────────────────────────

function drawCrab(cx,cy,flash){
  ctx.save(); ctx.translate(cx,cy);
  if(flash) ctx.globalAlpha=(Math.sin(Date.now()*.08)>0)?.2:1;

  const bw=26,bh=16;
  const bg=ctx.createRadialGradient(-4,-4,2,0,0,bw);
  bg.addColorStop(0,'#ffb830'); bg.addColorStop(.6,'#ff7a00'); bg.addColorStop(1,'#c04000');
  ctx.beginPath(); ctx.ellipse(0,2,bw,bh,0,0,Math.PI*2);
  ctx.fillStyle=bg; ctx.fill(); ctx.strokeStyle='#ff4400'; ctx.lineWidth=1.5; ctx.stroke();

  function claw(s){
    ctx.save(); ctx.scale(s,1); ctx.translate(bw+2,0);
    ctx.beginPath(); ctx.ellipse(8,-7,10,5,-.3,0,Math.PI*2);
    ctx.fillStyle='#ff8c00'; ctx.fill(); ctx.strokeStyle='#c04000'; ctx.lineWidth=1; ctx.stroke();
    ctx.beginPath(); ctx.ellipse(8,5,10,5,.3,0,Math.PI*2);
    ctx.fillStyle='#ff8c00'; ctx.fill(); ctx.stroke();
    ctx.beginPath(); ctx.moveTo(0,-3); ctx.lineTo(4,-6); ctx.moveTo(0,3); ctx.lineTo(4,4);
    ctx.strokeStyle='#ff7000'; ctx.lineWidth=3; ctx.stroke();
    ctx.restore();
  }
  claw(1); claw(-1);

  for(let i=-1;i<=1;i++) [1,-1].forEach(s=>{
    ctx.beginPath(); ctx.moveTo(s*8+s*i*3,bh); ctx.lineTo(s*14+s*i*5,bh+13);
    ctx.strokeStyle='#ff7700'; ctx.lineWidth=1.8; ctx.stroke();
  });

  [-11,11].forEach((ex,idx)=>{
    ctx.beginPath(); ctx.arc(ex,-3,5.5,0,Math.PI*2);
    ctx.fillStyle='white'; ctx.fill();
    ctx.beginPath(); ctx.arc(ex+1.2,-2,3,0,Math.PI*2);
    ctx.fillStyle='#111'; ctx.fill();
    ctx.beginPath(); ctx.moveTo(ex-5,-9); ctx.quadraticCurveTo(ex,-12+(idx?4:0),ex+5,-9+(idx?4:0));
    ctx.strokeStyle='#8b2000'; ctx.lineWidth=2; ctx.stroke();
  });

  ctx.beginPath(); ctx.moveTo(-9,5); ctx.quadraticCurveTo(1,13,11,4);
  ctx.strokeStyle='#5a1000'; ctx.lineWidth=2.5; ctx.stroke();
  ctx.fillStyle='#fffae0';
  [-4,0,4].forEach(tx=>ctx.fillRect(tx-2,5,4,5));
  ctx.beginPath(); ctx.arc(11,5,2,0,Math.PI*2);
  ctx.fillStyle='#c04000'; ctx.fill();

  ctx.beginPath();
  ctx.moveTo(-7,-bh); ctx.quadraticCurveTo(-16,-bh*2,-20,-bh*2.4);
  ctx.moveTo(7,-bh);  ctx.quadraticCurveTo(16,-bh*2,20,-bh*2.4);
  ctx.strokeStyle='#ff9933'; ctx.lineWidth=1.5; ctx.stroke();
  [[-20,-bh*2.4],[20,-bh*2.4]].forEach(([ax,ay])=>{
    ctx.beginPath(); ctx.arc(ax,ay,2.5,0,Math.PI*2); ctx.fillStyle='#ffdd00'; ctx.fill();
  });
  ctx.restore();
}

function drawInvader(inv){
  const cx=inv.x+inv.w/2, cy=inv.y+inv.h/2;
  const bob=Math.sin(Date.now()/380+inv.x*.05)*2;
  ctx.save(); ctx.translate(cx,cy+bob);
  switch(inv.type){
    case 'pdf':    docIcon(0,0,inv.w,inv.h,'#d32f2f','#ff8a80','PDF'); break;
    case 'doc':    docIcon(0,0,inv.w,inv.h,'#1565c0','#82b1ff','DOC'); break;
    case 'xls':    docIcon(0,0,inv.w,inv.h,'#2e7d32','#b9f6ca','XLS'); break;
    case 'folder': folderIcon(0,0,inv.w,inv.h); break;
    case 'form':   formIcon(0,0,inv.w,inv.h);   break;
  }
  ctx.restore();
}

function docIcon(x,y,w,h,col,lite,lbl){
  const hw=w*.42,hh=h*.48;
  ctx.beginPath(); ctx.roundRect(x-hw,y-hh,hw*2,hh*2,3);
  const g=ctx.createLinearGradient(x-hw,y-hh,x+hw,y+hh);
  g.addColorStop(0,lite); g.addColorStop(1,col);
  ctx.fillStyle=g; ctx.fill(); ctx.strokeStyle=col; ctx.lineWidth=1.5; ctx.stroke();
  ctx.beginPath(); ctx.moveTo(x+hw-9,y-hh); ctx.lineTo(x+hw,y-hh+9); ctx.lineTo(x+hw-9,y-hh+9); ctx.closePath();
  ctx.fillStyle='rgba(0,0,0,.22)'; ctx.fill();
  ctx.strokeStyle='rgba(255,255,255,.5)'; ctx.lineWidth=1;
  for(let i=0;i<3;i++){ctx.beginPath();ctx.moveTo(x-hw+5,y-4+i*7);ctx.lineTo(x+hw-13,y-4+i*7);ctx.stroke();}
  ctx.fillStyle='#fff'; ctx.font=`bold ${w*.22}px monospace`; ctx.textAlign='center'; ctx.textBaseline='middle';
  ctx.fillText(lbl,x,y+hh-8);
}

function folderIcon(x,y,w,h){
  const hw=w*.43,hh=h*.44;
  ctx.beginPath(); ctx.roundRect(x-hw,y-hh-5,hw*.65,9,3); ctx.fillStyle='#e65100'; ctx.fill();
  ctx.beginPath(); ctx.roundRect(x-hw,y-hh,hw*2,hh*2,4);
  const g=ctx.createLinearGradient(x,y-hh,x,y+hh);
  g.addColorStop(0,'#ffca28'); g.addColorStop(1,'#e65100');
  ctx.fillStyle=g; ctx.fill(); ctx.strokeStyle='#bf360c'; ctx.lineWidth=1.5; ctx.stroke();
  ctx.fillStyle='rgba(0,0,0,.3)'; ctx.font=`bold ${w*.38}px monospace`; ctx.textAlign='center'; ctx.textBaseline='middle';
  ctx.fillText('!',x+9,y+3);
}

function formIcon(x,y,w,h){
  const hw=w*.42,hh=h*.48;
  ctx.beginPath(); ctx.roundRect(x-hw,y-hh,hw*2,hh*2,3);
  const g=ctx.createLinearGradient(x-hw,y-hh,x+hw,y+hh);
  g.addColorStop(0,'#ece9d8'); g.addColorStop(1,'#c5b96a');
  ctx.fillStyle=g; ctx.fill(); ctx.strokeStyle='#9a8a30'; ctx.lineWidth=1.5; ctx.stroke();
  ctx.strokeStyle='#555'; ctx.lineWidth=1;
  for(let i=0;i<3;i++){
    ctx.strokeRect(x-hw+5,y-hh+8+i*11,8,8);
    if(i===1){ctx.beginPath();ctx.moveTo(x-hw+6,y-hh+14+i*11);ctx.lineTo(x-hw+9,y-hh+17+i*11);ctx.lineTo(x-hw+14,y-hh+11+i*11);ctx.stroke();}
    ctx.fillStyle='#555'; ctx.fillRect(x-hw+17,y-hh+12+i*11,hw*1.1,2);
  }
  ctx.fillStyle='#333'; ctx.font=`bold ${w*.2}px monospace`; ctx.textAlign='center'; ctx.textBaseline='middle';
  ctx.fillText('FORM',x,y+hh-8);
}

function drawBullet(b){
  const c=b.fromPlayer?'#00ffaa':'#ff4040';
  ctx.save(); ctx.shadowColor=c; ctx.shadowBlur=10;
  ctx.fillStyle=c; ctx.beginPath(); ctx.roundRect(b.x-2.5,b.y-9,5,18,2); ctx.fill();
  ctx.restore();
}

function drawBarrier(bar){
  if(bar.health<=0)return;
  ctx.save(); ctx.globalAlpha=bar.health/4;
  ctx.beginPath(); ctx.roundRect(bar.x,bar.y,bar.w,bar.h,6);
  ctx.fillStyle='#00aa55'; ctx.fill(); ctx.strokeStyle='#00ff88'; ctx.lineWidth=1.5; ctx.stroke();
  ctx.fillStyle='#00cc66';
  for(let i=0;i<3;i++) ctx.fillRect(bar.x+8+i*19,bar.y-7,11,9);
  ctx.restore();
}

function spawnParticles(x,y,col,n=12){
  for(let i=0;i<n;i++){
    const a=Math.random()*Math.PI*2,sp=40+Math.random()*130;
    particles.push({x,y,vx:Math.cos(a)*sp,vy:Math.sin(a)*sp,r:2+Math.random()*4,
      col,life:.7+Math.random()*.6,max:.7+Math.random()*.6});
  }
}

const tCol={pdf:'#ff4444',doc:'#4488ff',folder:'#ffcc00',xls:'#44ff88',form:'#cccc66'};

// ── UPDATE ────────────────────────────────────────────────────────────────────
function update(dt){
  if(gameState!=='playing')return;

  if(keys['ArrowLeft']||keys['KeyA'])  player.x-=player.speed*dt;
  if(keys['ArrowRight']||keys['KeyD']) player.x+=player.speed*dt;
  player.x=Math.max(player.w/2,Math.min(W-player.w/2,player.x));

  player.shootCooldown-=dt;
  if(keys['Space']&&player.shootCooldown<=0){
    bullets.push({x:player.x,y:player.y-22,vy:-430,fromPlayer:true});
    player.shootCooldown=0.24;
  }
  if(player.invincible>0) player.invincible-=dt;

  // Invader march
  invaderMoveTimer+=dt;
  if(invaderMoveTimer>=invaderMovePeriod){
    invaderMoveTimer=0;
    const alive=invaders.filter(i=>i.alive); let edge=false;
    alive.forEach(i=>{i.x+=invaderDir*16;if(i.x+i.w>W-8||i.x<8)edge=true;});
    if(edge){
      invaderDir*=-1;
      alive.forEach(i=>{i.y+=invaderDropAmt;i.x+=invaderDir*16;});
      invaderMovePeriod=Math.max(0.07,invaderMovePeriod*.97);
    }
  }

  invaderShootTimer-=dt;
  if(invaderShootTimer<=0){
    invaderShootTimer=invaderShootInterval*(.4+Math.random());
    const alive=invaders.filter(i=>i.alive);
    if(alive.length){
      const s=alive[Math.floor(Math.random()*alive.length)];
      invaderBullets.push({x:s.x+s.w/2,y:s.y+s.h,vy:190+Math.random()*90,fromPlayer:false});
    }
  }

  bullets.forEach(b=>b.y+=b.vy*dt);
  invaderBullets.forEach(b=>b.y+=b.vy*dt);

  for(let bi=bullets.length-1;bi>=0;bi--){
    const b=bullets[bi]; if(b.y<0){bullets.splice(bi,1);continue;}
    let hit=false;
    for(const inv of invaders){
      if(!inv.alive)continue;
      if(b.x>inv.x&&b.x<inv.x+inv.w&&b.y>inv.y&&b.y<inv.y+inv.h){
        inv.alive=false; spawnParticles(inv.x+inv.w/2,inv.y+inv.h/2,tCol[inv.type]);
        score+=10*wave; updateHUD(); bullets.splice(bi,1); hit=true; break;
      }
    }
    if(!hit) for(const bar of barriers){
      if(bar.health<=0)continue;
      if(b.x>bar.x&&b.x<bar.x+bar.w&&b.y>bar.y&&b.y<bar.y+bar.h){
        bar.health--; spawnParticles(b.x,b.y,'#00ff88',5); bullets.splice(bi,1); break;
      }
    }
  }

  for(let bi=invaderBullets.length-1;bi>=0;bi--){
    const b=invaderBullets[bi]; if(b.y>H){invaderBullets.splice(bi,1);continue;}
    let hit=false;
    for(const bar of barriers){
      if(bar.health<=0)continue;
      if(b.x>bar.x&&b.x<bar.x+bar.w&&b.y>bar.y&&b.y<bar.y+bar.h){
        bar.health--; spawnParticles(b.x,b.y,'#00ff88',3); invaderBullets.splice(bi,1); hit=true; break;
      }
    }
    if(!hit&&player.invincible<=0){
      if(b.x>player.x-25&&b.x<player.x+25&&b.y>player.y-20&&b.y<player.y+20){
        lives--; updateHUD(); spawnParticles(player.x,player.y,'#ff6a00',22);
        invaderBullets.splice(bi,1); player.invincible=2;
        if(lives<=0){endGame(false);return;}
      }
    }
  }

  if(invaders.some(i=>i.alive&&i.y+i.h>H-38)){endGame(false);return;}
  if(!invaders.some(i=>i.alive)){wave++;updateHUD();setupWave();}

  for(let pi=particles.length-1;pi>=0;pi--){
    const p=particles[pi];
    p.x+=p.vx*dt; p.y+=p.vy*dt; p.vy+=65*dt; p.life-=dt;
    if(p.life<=0)particles.splice(pi,1);
  }
}

// ── DRAW ──────────────────────────────────────────────────────────────────────
function draw(){
  ctx.clearRect(0,0,W,H);
  ctx.fillStyle='rgba(0,8,28,.25)'; ctx.fillRect(0,0,W,H);
  if(gameState==='idle'||gameState==='gameover'||gameState==='win') return;

  barriers.forEach(drawBarrier);
  ctx.strokeStyle='rgba(255,106,0,.22)'; ctx.lineWidth=2;
  ctx.beginPath(); ctx.moveTo(0,H-32); ctx.lineTo(W,H-32); ctx.stroke();

  invaders.filter(i=>i.alive).forEach(drawInvader);

  particles.forEach(p=>{
    ctx.save(); ctx.globalAlpha=p.life/p.max;
    ctx.fillStyle=p.col; ctx.shadowColor=p.col; ctx.shadowBlur=7;
    ctx.beginPath(); ctx.arc(p.x,p.y,p.r,0,Math.PI*2); ctx.fill(); ctx.restore();
  });

  bullets.forEach(drawBullet);
  invaderBullets.forEach(drawBullet);
  drawCrab(player.x,player.y,player.invincible>0);

  if(gameState==='paused'){
    ctx.fillStyle='rgba(0,5,20,.78)'; ctx.fillRect(0,0,W,H);
    ctx.fillStyle='#ff6a00'; ctx.shadowColor='#ff6a00'; ctx.shadowBlur=24;
    ctx.font="bold 52px 'Orbitron',monospace"; ctx.textAlign='center'; ctx.textBaseline='middle';
    ctx.fillText('PAUSED',W/2,H/2); ctx.shadowBlur=0;
    ctx.font="15px 'Share Tech Mono',monospace"; ctx.fillStyle='#00ff88';
    ctx.fillText('Press P · click canvas · or use buttons',W/2,H/2+50);
  }
}

function gameLoop(ts){
  const dt=Math.min((ts-lastTime)/1000,.05); lastTime=ts;
  update(dt); draw();
  animFrame=requestAnimationFrame(gameLoop);
}

function startGame(){
  document.getElementById('gameOverlay').style.display='none';
  initGame(); gameState='playing'; lastTime=performance.now();
  if(animFrame) cancelAnimationFrame(animFrame);
  animFrame=requestAnimationFrame(gameLoop);
}

function endGame(won){
  gameState=won?'win':'gameover';
  document.getElementById('overlayTitle').textContent = won?'VICTORY!':'DEFEATED';
  document.getElementById('overlayMsg').textContent   = won
    ? `All bureaucracy obliterated! Score: ${score}`
    : `The paperwork piled up... Score: ${score}`;
  document.getElementById('startBtn').textContent = won?'▶ NEXT WAVE':'▶ TRY AGAIN';
  document.getElementById('gameOverlay').style.display='flex';
}
</script>

</body>
</html>
