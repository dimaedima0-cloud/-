<!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<meta name="theme-color" content="#090719">
<title>ROYAL FORTUNE — Vegas 3D Demo</title>
<style>
:root{--gold:#ffd66e;--gold2:#a75c18;--red:#8d101d;--pink:#ff3bbf;--cyan:#31eaff;--ink:#080715}
*{box-sizing:border-box}
body{margin:0;min-height:100vh;color:#fff5d8;font-family:Georgia,serif;background:radial-gradient(ellipse at 50% 0%,#48205d 0,#17102e 42%,#070611 100%);padding:12px 9px 28px;overflow-x:hidden}
body:before{content:"";position:fixed;inset:0;pointer-events:none;opacity:.2;background:repeating-linear-gradient(0deg,transparent 0 3px,#000 4px 5px)}
.wrap{max-width:780px;margin:auto;position:relative}
.topline{display:flex;justify-content:space-between;align-items:center;color:#f9d67d;font:10px Arial;letter-spacing:2px;padding:3px 5px}
.marquee{position:relative;text-align:center;padding:12px 5px 15px;margin:7px 0 12px;border:3px solid #ffcf65;border-radius:16px;background:linear-gradient(180deg,#7d112a,#2b071c 60%,#12091d);box-shadow:0 0 0 4px #5c2872,0 0 22px #ff39b8, inset 0 0 22px #ffcf6544}
.marquee:before,.marquee:after{content:"✦  •  ✦  •  ✦  •  ✦";position:absolute;left:0;right:0;color:#ffe58b;font:12px Arial;letter-spacing:5px;text-shadow:0 0 9px #ffdf65;animation:twinkle 1.3s steps(2) infinite}
.marquee:before{top:3px}.marquee:after{bottom:2px}
@keyframes twinkle{50%{opacity:.25}}
.crown{font-size:30px;filter:drop-shadow(0 0 8px #ffc44b)}
.brand{font-weight:bold;font-size:clamp(30px,8vw,52px);letter-spacing:3px;line-height:1.05;color:#fff0a6;text-shadow:0 3px #9d381c,0 5px #4e071d,0 0 9px #ffb52f,0 0 22px #ff28b9}
.tag{font:10px Arial;letter-spacing:4px;color:#68f4ff;margin-top:7px;text-shadow:0 0 9px #26cfff}
.cabinet{padding:10px;border-radius:22px;background:linear-gradient(135deg,#ffd76b,#8e4419 12%,#350b27 27%,#120b25 70%,#e2a93f);box-shadow:0 16px 32px #000c,0 0 0 2px #ffdc7a,inset 0 0 20px #fff4a044;transform:perspective(1000px) rotateX(1deg)}
.cabinet-inner{padding:9px;border-radius:14px;background:linear-gradient(135deg,#31091e,#080817 55%,#3b102c);border:2px solid #f2c25d;box-shadow:inset 0 0 24px #000}
.side-label{display:flex;justify-content:space-between;color:#ffd76b;font:bold 10px Arial;letter-spacing:2px;padding:0 4px 8px}
.reel-frame{perspective:900px;background:linear-gradient(90deg,#180819,#4b1742 4%,#0b0817 10%,#100817 90%,#4b1742 96%,#180819);border:2px solid #e9bd57;border-radius:10px;padding:7px;box-shadow:inset 0 0 18px #000,0 0 18px #ff32b8aa}
.reels{display:grid;grid-template-columns:repeat(5,minmax(0,1fr));gap:5px}
.reel-window{height:clamp(230px,67vw,340px);max-height:340px;overflow:hidden;position:relative;border-radius:7px;background:linear-gradient(90deg,#160c22,#3b1944 48%,#10091d);border:1px solid #bd914a;box-shadow:inset 0 0 18px #000, inset 0 0 4px #fff7}
.reel-window:before,.reel-window:after{content:"";position:absolute;z-index:3;left:0;right:0;height:22px;pointer-events:none}
.reel-window:before{top:0;background:linear-gradient(#070511,transparent)}
.reel-window:after{bottom:0;background:linear-gradient(transparent,#070511)}
.reel-strip{position:absolute;left:0;right:0;top:0;will-change:transform;transform:translate3d(0,0,0);backface-visibility:hidden}
.symbol{height:clamp(57px,16.5vw,82px);display:flex;align-items:center;justify-content:center;position:relative;background:linear-gradient(180deg,#fff5d0 0,#d7a94e 7%,#4d1737 18%,#25102d 52%,#541a39 88%,#e0b55b 100%);border-bottom:1px solid #e8c56c;color:#fff3c6;font-family:Arial,sans-serif;font-size:clamp(27px,8vw,48px);text-shadow:0 3px 2px #000,0 0 9px #ffe5a0;box-shadow:inset 0 0 12px #0008}
.symbol:after{content:"";position:absolute;inset:3px;border:1px solid #fff2;border-radius:4px;pointer-events:none}
.symbol.word{font-size:clamp(13px,3.5vw,20px);font-weight:900;letter-spacing:1px;color:#ffdf76}
.symbol.wild{color:#fff4a0;text-shadow:0 0 8px #ffbd3b,0 0 20px #ff31bf}
.payline{height:2px;background:#69f5ff;box-shadow:0 0 8px #31eaff;position:absolute;left:0;right:0;z-index:4;opacity:0;pointer-events:none}
.reels.show-lines .payline{opacity:.85}
.meters{display:grid;grid-template-columns:1fr 1fr 1fr;gap:6px;margin-top:9px}
.meter{background:linear-gradient(#330e2d,#100817);border:1px solid #b37a35;border-radius:8px;padding:8px 3px;text-align:center;box-shadow:inset 0 0 12px #000}
.meter small{display:block;font:9px Arial;letter-spacing:1px;color:#f3c66a}
.meter strong{display:block;font:bold 17px Arial;color:#fff2bf;margin-top:4px}
.controls{display:flex;justify-content:center;align-items:center;gap:8px;flex-wrap:wrap;margin-top:12px}
button{font-weight:bold;border:1px solid #ffe79b;border-radius:9px;padding:10px 13px;color:#390c22;background:linear-gradient(#fff0a5,#d18a2e 48%,#74301d);box-shadow:0 3px 0 #45142a,0 0 10px #ffbd5577;touch-action:manipulation}
button:active{transform:translateY(2px);box-shadow:0 1px 0 #45142a}
button:disabled{opacity:.45}
.betbox{display:flex;align-items:center;gap:6px;padding:5px 7px;background:#16091e;border:1px solid #a86b36;border-radius:9px}
.betbox span{font:10px Arial;color:#f9d37a}
.betbox button{padding:6px 11px}
.spin{width:82px;height:62px;border-radius:50%;font-size:16px;background:radial-gradient(circle at 35% 25%,#fff8c4,#ffcc4d 43%,#c44b25 75%,#591128);border:3px double #fff2ad;box-shadow:0 0 0 3px #77224d,0 0 20px #ff3bbf,0 4px 0 #3b1023}
.status{text-align:center;min-height:31px;padding:12px 4px 2px;color:#ffe58d;font-weight:bold;font-size:17px;text-shadow:0 0 9px #ffae34}
.substatus{text-align:center;min-height:17px;color:#72eaff;font:11px Arial}
.bottom-grid{display:grid;grid-template-columns:1fr 1fr;gap:9px;margin-top:12px}
.info{background:#12091d;border:1px solid #80522e;border-radius:9px;padding:10px}
.info h3{margin:0 0 7px;color:#ffd675;font-size:14px}
.info p{margin:4px 0;color:#e9d6ae;font:11px/1.45 Arial}
.info .pay{display:flex;justify-content:space-between;padding:3px 0;border-bottom:1px solid #fff1;font:11px Arial}
.footer{text-align:center;color:#b49a72;font:9px/1.5 Arial;margin:13px 5px}
@media(max-width:380px){.cabinet{padding:6px}.cabinet-inner{padding:6px}.reel-frame{padding:4px}.reels{gap:3px}.controls{gap:5px}.spin{width:68px;height:57px}.bottom-grid{grid-template-columns:1fr}}
</style>
</head>
<body>
<div class="wrap">
<div class="topline"><span>★ LAS VEGAS · NEVADA ★</span><span>EST. 1989</span></div>
<header class="marquee"><div class="crown">♛</div><div class="brand">ROYAL FORTUNE</div><div class="tag">VEGAS NIGHTS · LUCK NEVER SLEEPS</div></header>
<main class="cabinet"><div class="cabinet-inner">
<div class="side-label"><span>★ JACKPOT CLUB ★</span><span>5 REELS · 4 ROWS</span></div>
<div class="reel-frame"><div class="reels" id="reels"></div></div>
<div class="meters">
 <div class="meter"><small>VIRTUAL BALANCE</small><strong id="balance">1 000</strong></div>
 <div class="meter"><small>BET</small><strong id="betDisplay">10</strong></div>
 <div class="meter"><small>WIN</small><strong id="win">0</strong></div>
</div>
<div class="controls">
 <div class="betbox"><button id="minus">−</button><span>BET</span><button id="plus">+</button></div>
 <button class="spin" id="spin">SPIN</button>
 <button id="max">MAX</button>
</div>
<div class="status" id="message">WELCOME TO VEGAS — GOOD LUCK!</div>
<div class="substatus" id="bonus">FREE SPINS: 0</div>
</div></main>
<section class="bottom-grid">
<div class="info"><h3>PAYTABLE · DEMO</h3>
<div class="pay"><span>🐂 Bull ×3</span><b>×8</b></div><div class="pay"><span>🍎 Apples ×3</span><b>×6</b></div><div class="pay"><span>🔫 Lucky 38 ×3</span><b>×5</b></div><div class="pay"><span>💰 Money ×3</span><b>×4</b></div><div class="pay"><span>🎲 Dice ×3</span><b>×3</b></div><div class="pay"><span>🍋 Lemon ×3</span><b>×2</b></div>
<p>Пять демонстрационных линий, выплаты слева направо.</p></div>
<div class="info"><h3>SPECIAL SYMBOLS</h3><p>👑 <b>WILD</b> — заменяет обычные символы.</p><p>⭐ <b>SCATTER</b> — 3+ символа дают 10 бесплатных вращений.</p><p>Бесплатные вращения не списывают виртуальную ставку.</p></div>
</section>
<div class="footer">DEMO ONLY · Виртуальные кредиты без денежной стоимости. Локальная демонстрационная случайность, не сертифицированный RNG.</div>
</div>
<script>
'use strict';
const S=[
 {id:'bull',e:'🐂',name:'Bull',pay:8},
 {id:'apple',e:'🍎',name:'Apple',pay:6},
 {id:'revolver',e:'🔫',name:'Lucky 38',pay:5},
 {id:'money',e:'💰',name:'Money',pay:4},
 {id:'dice',e:'🎲',name:'Dice',pay:3},
 {id:'lemon',e:'🍋',name:'Lemon',pay:2},
 {id:'wild',e:'👑',name:'WILD',pay:0},
 {id:'scatter',e:'⭐',name:'SCATTER',pay:0}
];
const W=[12,14,9,12,16,17,9,5];
const LINES=[[0,0,0,0,0],[1,1,1,1,1],[2,2,2,2,2],[3,3,3,3,3],[0,1,2,1,0]];
const $=id=>document.getElementById(id);
let balance=1000,bet=10,free=0,busy=false,grid=[],spinToken=0;
const sleep=ms=>new Promise(resolve=>setTimeout(resolve,ms));
function pick(){let n=Math.random()*W.reduce((a,b)=>a+b,0);for(let i=0;i<S.length;i++){n-=W[i];if(n<0)return S[i]}return S[0]}
function makeGrid(){return Array.from({length:5},()=>Array.from({length:4},pick))}
function symbolNode(sym){const el=document.createElement('div');el.className='symbol'+(sym.id==='wild'?' wild':'')+(sym.id==='revolver'?' word':'');el.textContent=sym.e;el.setAttribute('aria-label',sym.name);return el}
function createReels(){
 const root=$('reels');root.innerHTML='';
 for(let col=0;col<5;col++){
  const win=document.createElement('div');win.className='reel-window';win.dataset.col=col;
  const strip=document.createElement('div');strip.className='reel-strip';
  for(let row=0;row<4;row++)strip.appendChild(symbolNode(pick()));
  win.appendChild(strip);root.appendChild(win);
 }
}
function renderFinal(){
 const windows=[...document.querySelectorAll('.reel-window')];
 windows.forEach((win,col)=>{
  const strip=win.firstElementChild;strip.style.transition='none';strip.style.transform='translate3d(0,0,0)';strip.innerHTML='';
  for(let row=0;row<4;row++)strip.appendChild(symbolNode(grid[col][row]));
  win.style.transform='rotateY(0deg)';
 });
}
function update(){
 $('balance').textContent=balance.toLocaleString('en-US',{maximumFractionDigits:0});
 $('betDisplay').textContent=bet;$('bonus').textContent='FREE SPINS: '+free;
 $('minus').disabled=busy||bet<=1;$('plus').disabled=busy||bet>=100;
 $('max').disabled=busy;$('spin').disabled=busy||(!free&&balance<bet);
}
function calculate(){
 let total=0,hits=[];
 for(let k=0;k<LINES.length;k++){
  const seq=LINES[k].map((row,col)=>grid[col][row]);
  let base=seq.find(x=>x.id!=='wild'&&x.id!=='scatter');
  if(!base)base=S[0];
  let count=0;for(const x of seq){if(x.id===base.id||x.id==='wild')count++;else break}
  if(count>=3){const mult=base.pay*(count===3?1:count===4?2:5);total+=bet*mult/5;hits.push(k)}
 }
 return {total,hits};
}
function animateColumn(win,finalColumn,col,token){
 return new Promise(resolve=>{
  const strip=win.firstElementChild;
  const cellH=win.clientHeight/4;
  const duration=1050+col*260;
  const start=performance.now();
  let lastFrame=0,offset=0;
  const tick=(now)=>{
   if(token!==spinToken){resolve();return}
   if(now-start<duration){
    if(now-lastFrame>=33){lastFrame=now;offset=(offset+cellH*0.72)%(cellH*4);strip.innerHTML='';
     for(let i=0;i<8;i++)strip.appendChild(symbolNode(pick()));
     strip.style.transform=`translate3d(0,${-offset}px,0)`;
     win.style.transform=`rotateY(${Math.sin(now/95)*2.2}deg)`;
    }
    requestAnimationFrame(tick);
   }else{
    strip.style.transition='transform 160ms cubic-bezier(.2,.8,.25,1)';
    strip.style.transform='translate3d(0,0,0)';
    setTimeout(()=>{
     strip.style.transition='none';strip.innerHTML='';
     finalColumn.forEach(sym=>strip.appendChild(symbolNode(sym)));
     win.style.transform='rotateY(0deg)';
     resolve();
    },170);
   }
  };
  requestAnimationFrame(tick);
 });
}
async function spin(){
 if(busy||(!free&&balance<bet))return;
 busy=true;const token=++spinToken;const freeSpin=free>0;
 if(freeSpin)free--;else balance-=bet;
 $('win').textContent='0';$('message').textContent='GOOD LUCK…';update();
 try{
  const final=makeGrid(),windows=[...document.querySelectorAll('.reel-window')];
  await Promise.all(windows.map((win,col)=>animateColumn(win,final[col],col,token)));
  grid=final;
  const scatter=grid.flat().filter(x=>x.id==='scatter').length;
  const result=calculate();balance+=result.total;
  if(scatter>=3)free+=10;
  $('win').textContent=result.total.toFixed(0);
  if(scatter>=3)$('message').textContent='★ BONUS! +10 FREE SPINS ★';
  else if(result.total>0)$('message').textContent='WIN! '+result.total.toFixed(0)+' VIRTUAL CREDITS';
  else $('message').textContent=freeSpin?'FREE SPIN COMPLETE':'NO WIN — TRY AGAIN';
  if(result.total>0||scatter>=3){$('reels').classList.add('show-lines');setTimeout(()=>$('reels').classList.remove('show-lines'),800)}
 }catch(e){console.error(e);$('message').textContent='ROUND RESET — PRESS SPIN'}
 finally{busy=false;update()}
}
$('spin').addEventListener('click',spin);
$('minus').addEventListener('click',()=>{if(!busy){bet=Math.max(1,bet-1);update()}});
$('plus').addEventListener('click',()=>{if(!busy){bet=Math.min(100,bet+1);update()}});
$('max').addEventListener('click',()=>{if(!busy){bet=Math.max(1,Math.min(100,balance));update()}});
createReels();update();
</script>
</body>
</html>
