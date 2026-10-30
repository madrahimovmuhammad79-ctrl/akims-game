# akims-game
Public <!doctype html>
<html lang="ru">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no">
<meta name="theme-color" content="#111827">
<title>AKIM’S GAME</title>
<style>
:root{--bg:#0b1020;--panel:#171f35;--panel2:#202b46;--gold:#ffd447;--text:#f8fafc;--muted:#aab6d0;--blue:#72a7ff}
*{box-sizing:border-box}body{margin:0;background:radial-gradient(ellipse at top,#273b70 0,#111a32 43%,#080d19 100%);color:var(--text);font-family:system-ui,-apple-system,Segoe UI,sans-serif;min-height:100vh}
main{max-width:620px;margin:auto;padding:16px 14px 30px}
header{text-align:center;padding:22px 12px 18px;background:linear-gradient(135deg,#263d83,#713bb0);border:1px solid #ffffff26;border-radius:22px;box-shadow:0 12px 35px #0005}
.kicker{font-size:11px;letter-spacing:4px;font-weight:900;color:#dce6ff}.logo{font-size:clamp(29px,8vw,43px);font-weight:1000;letter-spacing:1px;margin:4px 0}.subtitle{font-size:12px;color:#e0e7ff}
.stats{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin:12px 0}
.stat,.panel{background:#151e33eF;border:1px solid #ffffff18;border-radius:16px;padding:13px;text-align:center}
.stat small{display:block;color:var(--muted);font-size:11px}.stat strong{display:block;font-size:22px;margin-top:3px}
.section-title{font-weight:900;font-size:17px;margin:18px 2px 9px}
.tapzone{padding:17px;text-align:center;background:linear-gradient(180deg,#202d4b,#151e33);border:1px solid #ffffff20;border-radius:20px}
#coin{width:160px;height:160px;border-radius:50%;border:0;background:radial-gradient(circle at 35% 28%,#fff4a7,#ffd447 38%,#d88a13 78%);box-shadow:0 8px 0 #995c0b,0 15px 30px #0007,inset 0 -7px 12px #b36d00;display:grid;place-items:center;font-size:76px;margin:3px auto 14px;touch-action:manipulation}
#coin:active{transform:translateY(5px);box-shadow:0 3px 0 #995c0b,0 8px 15px #0007}
button{font:inherit;cursor:pointer;color:var(--text)}
.hint{color:var(--muted);font-size:12px}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:9px}
.item{background:var(--panel);border:1px solid #ffffff20;border-radius:15px;padding:12px;text-align:left;min-height:105px}
.item b{display:block;font-size:14px}.item small{display:block;color:var(--muted);font-size:11px;margin:4px 0 10px}
.buy{width:100%;border:0;border-radius:10px;background:#324a78;padding:9px;font-weight:800;font-size:12px}
.buy:disabled{opacity:.42;cursor:not-allowed}
.progress{height:10px;border-radius:99px;background:#303b55;overflow:hidden;margin-top:9px}.bar{height:100%;width:0;background:linear-gradient(90deg,#43d9a3,#b8f36b);transition:width .2s}
.row{display:flex;justify-content:space-between;align-items:center;font-size:12px;color:var(--muted)}
#notice{min-height:22px;color:#ffe58a;font-size:13px;margin-top:10px;font-weight:700}
footer{text-align:center;color:#8090b0;font-size:11px;margin-top:18px}
.reset{margin-top:12px;background:transparent;border:1px solid #ffffff25;border-radius:10px;padding:8px 12px;font-size:12px;color:#c0cbe0}
@media(max-width:360px){.stats{gap:5px}.stat{padding:9px 4px}.stat strong{font-size:18px}.grid{gap:7px}}
</style>
</head>
<body>
<main>
<header><div class="kicker">WELCOME TO</div><div class="logo">👑 AKIM’S GAME</div><div class="subtitle">COIN SIMULATOR • СТАНЬ ЛЕГЕНДОЙ</div></header>
<section class="stats">
 <div class="stat"><small>🪙 МОНЕТЫ</small><strong id="coins">0</strong></div>
 <div class="stat"><small>⭐ УРОВЕНЬ</small><strong id="level">1</strong></div>
 <div class="stat"><small>⚡ ЗА КЛИК</small><strong id="power">1</strong></div>
</section>
<section class="tapzone">
 <div class="hint">Нажимай на золотую монету!</div>
 <button id="coin" aria-label="Собрать монеты">🪙</button>
 <div class="hint">Каждое нажатие приносит монеты</div>
 <div id="notice" aria-live="polite">Твоя большая история начинается!</div>
</section>
<div class="section-title">🏪 Магазин улучшений</div>
<section class="grid">
 <div class="item"><b>⚡ Сильный клик</b><small>Больше монет за нажатие</small><button class="buy" id="buyPower">Купить · 25 🪙</button></div>
 <div class="item"><b>🤖 Авто-доход</b><small>Получай монеты каждую секунду</small><button class="buy" id="buyAuto">Купить · 75 🪙</button></div>
 <div class="item"><b>🐣 Яйцо питомца</b><small>Питомец увеличит силу клика</small><button class="buy" id="buyPet">Открыть · 150 🪙</button></div>
 <div class="item"><b>🌟 Удача</b><small>Постоянный бонус к клику</small><button class="buy" id="buyLuck">Купить · 300 🪙</button></div>
</section>
<div class="section-title">🏆 Твой прогресс</div>
<section class="panel">
 <div class="row"><b style="color:white">Опыт до следующего уровня</b><span id="xpText">0 / 100</span></div>
 <div class="progress"><div class="bar" id="xpBar"></div></div>
 <div class="row" style="margin-top:12px"><span>🤖 Авто-доход</span><b id="autoRate" style="color:white">0 / сек</b></div>
 <div class="row" style="margin-top:8px"><span>🐾 Питомцы</span><b id="pets" style="color:white">0</b></div>
 <div class="row" style="margin-top:8px"><span>✨ Всего заработано</span><b id="total" style="color:white">0</b></div>
</section>
<div style="text-align:center"><button class="reset" id="reset">Начать заново</button></div>
<footer>AKIM’S GAME · Твоя игра, твои рекорды<br>Прогресс сохраняется в этом браузере на этом устройстве.</footer>
</main>
<script>
(()=>{
 const $=id=>document.getElementById(id);
 const defaults={coins:0,level:1,power:1,auto:0,pets:0,luck:0,xp:0,total:0,powerCost:25,autoCost:75,petCost:150,luckCost:300};
 let s={...defaults};
 try{const saved=JSON.parse(localStorage.getItem('akimsGameSave'));if(saved&&typeof saved==='object')s={...s,...saved}}catch(e){}
 const fmt=n=>Math.floor(n).toLocaleString('ru-RU');
 function save(){try{localStorage.setItem('akimsGameSave',JSON.stringify(s))}catch(e){}}
 function notify(t){$('notice').textContent=t}
 function earn(n){s.coins+=n;s.total+=n;s.xp+=n;while(s.xp>=s.level*100){s.xp-=s.level*100;s.level++;notify('🎉 Новый уровень: '+s.level+'!')}render();save()}
 function purchase(costKey,apply,nextCost){if(s.coins<s[costKey])return; s.coins-=s[costKey];apply();s[costKey]=Math.ceil(s[costKey]*nextCost);render();save()}
 function render(){
  $('coins').textContent=fmt(s.coins);$('level').textContent=s.level;$('power').textContent=fmt(s.power);
  $('autoRate').textContent=fmt(s.auto)+' / сек';$('pets').textContent=fmt(s.pets);$('total').textContent=fmt(s.total);
  $('xpText').textContent=fmt(s.xp)+' / '+fmt(s.level*100);$('xpBar').style.width=Math.min(100,s.xp/(s.level*100)*100)+'%';
  const buttons=[['buyPower','powerCost','⚡ Купить · '],['buyAuto','autoCost','🤖 Купить · '],['buyPet','petCost','🐣 Открыть · '],['buyLuck','luckCost','🌟 Купить · ']];
  buttons.forEach(([id,key,label])=>{$(id).textContent=label+fmt(s[key])+' 🪙';$(id).disabled=s.coins<s[key]});
 }
 $('coin').addEventListener('click',()=>{let amount=s.power+s.pets*2+s.luck;earn(amount);notify('✨ +'+fmt(amount)+' монет!')});
 $('buyPower').onclick=()=>purchase('powerCost',()=>{s.power++},1.55);
 $('buyAuto').onclick=()=>purchase('autoCost',()=>{s.auto++},1.7);
 $('buyPet').onclick=()=>purchase('petCost',()=>{s.pets++;notify('🐣 У тебя новый питомец!')},1.9);
 $('buyLuck').onclick=()=>purchase('luckCost',()=>{s.luck++;notify('🌟 Удача увеличена!')},2);
 $('reset').onclick=()=>{if(confirm('Точно начать игру заново?')){s={...defaults};save();render();notify('Новая игра началась!')}};
 setInterval(()=>{if(s.auto>0)earn(s.auto)},1000);
 render();
})();
</script>
</body>
</html>