<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>💌 یه دعوتِ خاص برای یه نفرِ خاص</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Vazirmatn:wght@300;400;600;800&display=swap" rel="stylesheet">
<style>
  *{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
  html,body{height:100%}
  body{
    font-family:'Vazirmatn',sans-serif;color:#5a2a4a;
    background:linear-gradient(160deg,#ffe3ee 0%,#f9c5d8 45%,#e3c4f0 100%);
    transition:background 1.2s ease;overflow-x:hidden;min-height:100vh;
  }
  body.sad{background:linear-gradient(160deg,#e8eef7 0%,#cdd9ec 50%,#dcd3e8 100%)}

  #hearts{position:fixed;inset:0;pointer-events:none;z-index:1;overflow:hidden}
  .f-heart{position:absolute;bottom:-50px;animation:floatUp linear forwards;opacity:0}
  @keyframes floatUp{
    0%{transform:translateY(0) rotate(0deg);opacity:0}
    12%{opacity:.9}
    100%{transform:translateY(-115vh) rotate(25deg);opacity:0}
  }

  #stage{position:relative;z-index:2;min-height:100vh;display:flex;align-items:center;justify-content:center;padding:24px 16px}
  .screen{display:none;width:100%;max-width:430px}
  .screen.active{display:block;animation:pop .7s cubic-bezier(.2,.9,.3,1.2)}
  @keyframes pop{from{opacity:0;transform:translateY(30px) scale(.94)}to{opacity:1;transform:none}}

  .card{
    background:rgba(255,255,255,.72);
    -webkit-backdrop-filter:blur(14px);backdrop-filter:blur(14px);
    border:1.5px solid rgba(255,255,255,.95);border-radius:30px;
    padding:38px 26px;text-align:center;
    box-shadow:0 24px 70px rgba(214,51,132,.20);
  }
  .big{font-size:52px;margin-bottom:10px;animation:float 3s ease-in-out infinite}
  @keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-8px)}}
  h1{font-size:1.5rem;font-weight:800;margin-bottom:14px}
  .lead{font-size:1rem;line-height:2;margin-bottom:6px}
  .question{font-size:1.2rem;font-weight:800;margin:14px 0 20px;color:#e0447c}
  .tiny{font-size:.8rem;opacity:.65;margin-top:18px}

  .btn{
    display:inline-block;border:none;cursor:pointer;font-family:inherit;
    font-size:1.05rem;font-weight:600;padding:14px 26px;border-radius:999px;
    margin:8px 5px;transition:transform .2s,box-shadow .2s,opacity .2s;
  }
  .btn:active{transform:scale(.96)}
  .btn:disabled{opacity:.6;cursor:wait}
  .btn-yes{background:linear-gradient(135deg,#ff6fa5,#ff9770);color:#fff;box-shadow:0 10px 24px rgba(255,111,165,.45)}
  .btn-yes:hover{transform:translateY(-3px) scale(1.03);box-shadow:0 14px 30px rgba(255,111,165,.55)}
  .btn-no{background:#fff;color:#c2426e;border:2px solid #ffb3c9}
  .btn-no:hover{transform:translateY(-3px)}

  .info{margin:20px 0;display:flex;flex-direction:column;gap:10px}
  .info-box{
    background:rgba(255,255,255,.85);border:1.5px dashed #ffb3c9;border-radius:16px;
    padding:12px 16px;font-size:.98rem;text-align:right;
  }
  .env-title{text-align:center;margin-bottom:4px;font-size:1.3rem}

  .envelope{
    position:relative;width:280px;height:180px;margin:28px auto 16px;cursor:pointer;
    perspective:900px;user-select:none;
    filter:drop-shadow(0 18px 35px rgba(214,51,132,.28));transition:transform .3s;
  }
  .envelope:hover{transform:translateY(-6px)}
  .env-back{position:absolute;inset:0;background:linear-gradient(135deg,#ff8fb1,#f76a97);border-radius:14px;z-index:1}
  .letter{
    position:absolute;left:14px;right:14px;top:12px;height:calc(100% - 24px);
    background:#fff;border-radius:10px;z-index:2;display:flex;flex-direction:column;
    align-items:center;justify-content:center;gap:4px;
    box-shadow:0 4px 14px rgba(0,0,0,.06);
    transition:transform .9s cubic-bezier(.2,.8,.3,1.1) .35s;
  }
  .letter span{font-size:38px}
  .letter p{font-size:.82rem;font-weight:600;color:#ff6fa5}
  .env-left,.env-right{position:absolute;top:0;width:0;height:0;z-index:3}
  .env-left{left:0;border-top:90px solid transparent;border-bottom:90px solid transparent;border-right:140px solid #ff7aa2}
  .env-right{right:0;border-top:90px solid transparent;border-bottom:90px solid transparent;border-left:140px solid #ff7aa2}
  .env-front{position:absolute;bottom:0;left:0;width:0;height:0;z-index:4;
    border-left:140px solid transparent;border-right:140px solid transparent;border-bottom:96px solid #ff8fb1}
  .flap{
    position:absolute;top:0;left:0;width:0;height:0;z-index:5;
    border-left:140px solid transparent;border-right:140px solid transparent;border-top:104px solid #f76a97;
    transform-origin:top center;transition:transform .8s ease;
  }
  .seal{position:absolute;top:82px;left:50%;transform:translateX(-50%);font-size:24px;z-index:6;transition:opacity .3s}
  .envelope.open .flap{transform:rotateX(180deg)}
  .envelope.open .seal{opacity:0}
  .envelope.open .letter{transform:translateY(-95px)}
  .hint{text-align:center;font-size:.85rem;opacity:.7;animation:blink 1.6s ease-in-out infinite}
  @keyframes blink{0%,100%{opacity:.35}50%{opacity:.9}}

  .burst{position:fixed;left:50%;top:50%;font-size:22px;pointer-events:none;z-index:99;animation:burst 1.3s ease-out forwards}
  @keyframes burst{
    from{transform:translate(-50%,-50%) scale(.4);opacity:1}
    to{transform:translate(calc(-50% + var(--x)),calc(-50% + var(--y))) scale(1.25);opacity:0}
  }
</style>
</head>
<body>

<div id="hearts"></div>

<div id="stage">

  <section id="screen-envelope" class="screen active">
    <h1 class="env-title">نامه‌ای برای تو 💌</h1>
    <div class="envelope" id="envelope" onclick="openEnvelope()" role="button" aria-label="باز کردن نامه">
      <div class="env-back"></div>
      <div class="letter"><span>🌷</span><p>برایِ تو</p></div>
      <div class="env-left"></div>
      <div class="env-right"></div>
      <div class="env-front"></div>
      <div class="flap"></div>
      <div class="seal">❤️</div>
    </div>
    <p class="hint">روی پاکت بزن تا نامه باز بشه 👆</p>
  </section>

  <section id="screen-invite" class="screen">
    <div class="card">
      <div class="big">🌷</div>
      <h1>سلام <span id="girlName1"></span> جان!</h1>
      <p class="lead">اینجا <b id="boyName1"></b>‌ام...</p>
      <p class="lead">یه سؤال کوچولو ازت دارم، که جوابش فقط به تو بستگی داره:</p>
      <p class="question">حاضری یه عصرِ رویایی رو با من بسازیم؟ ✨</p>
      <div>
        <button class="btn btn-yes" onclick="acceptInvite()">آره، قبوله! 💖</button>
        <button class="btn btn-no" onclick="declineInvite()">نه 🥺</button>
      </div>
      <p class="tiny">قول میدم عجیب‌ترین و قشنگ‌ترین غروبت باشه 🌇</p>
    </div>
  </section>

  <section id="screen-details" class="screen">
    <div class="card">
      <div class="big">🥳</div>
      <h1>واای! واقعاً؟! 💖</h1>
      <p class="lead">دلم انقدر خوشحال شده که... خب، بریم سراغ جزئیات:</p>
      <div class="info">
        <div class="info-box">📅 <b>تاریخ:</b> <span id="d-date"></span></div>
        <div class="info-box">🕗 <b>ساعت:</b> <span id="d-time"></span></div>
        <div class="info-box">📍 <b>مکان:</b> <span id="d-place"></span></div>
      </div>
      <p class="lead">اگه همه‌چی اوکیه، پایین رو بزن:</p>
      <button class="btn btn-yes" id="btn-confirm" onclick="confirmDetails(this)">اوکیه! ثبتش کن ✅</button>
    </div>
  </section>

  <section id="screen-final-yes" class="screen">
    <div class="card">
      <div class="big">🌹</div>
      <h1>ثبت شد! 🎉</h1>
      <p class="lead">جوابِ تو برای <span id="boyName4"></span> ارسال شد ✅</p>
      <p class="lead">و من از همین الان برای <b id="d-date2"></b> بی‌قرارم! 💖</p>
      <p class="tiny">می‌بینمت 🌷</p>
    </div>
  </section>

  <section id="screen-sad" class="screen">
    <div class="card">
      <div class="big">🌧️</div>
      <h1>ای بابا... 😔</h1>
      <p class="lead">اشکالی نداره، حرفِ تو حرفه. فقط بگو دقیقاً کجای کاره؟</p>
      <div>
        <button class="btn btn-no" id="btn-hardno" onclick="hardNo(this)">نه قاطع هستم ❌</button>
        <button class="btn btn-yes" id="btn-effort" onclick="wantEffort(this)">با پیشنهاد بهتر شاید 😏</button>
      </div>
    </div>
  </section>

  <section id="screen-hard-no" class="screen">
    <div class="card">
      <div class="big">💔</div>
      <h1>مرسی که صادق بودی</h1>
      <p class="lead">خیالتِ کامل راحت؛ دیگه هیچ‌وقت مزاحمت نمی‌شم.</p>
      <p class="lead">برات آرزوی بهترین‌ها و خوشبختی دارم 🌸</p>
      <p class="tiny">— <span id="boyName2"></span></p>
    </div>
  </section>

  <section id="screen-try-more" class="screen">
    <div class="card">
      <div class="big">😎✨</div>
      <h1>پس هنوز امید هست!</h1>
      <p class="lead">جا زدن تو ذاتِ من نیست!</p>
      <p class="lead">با یه پیشنهادِ بهتر و رویایی‌تر برمی‌گردم... منتظر سوپرایزم باش! 🎁</p>
      <p class="tiny">— <span id="boyName3"></span> 💪</p>
    </div>
  </section>

</div>

<script>
/* ═══════════════════════════════════════
   ✏️ فقط این بخش رو ویرایش کن:
═══════════════════════════════════════ */
const CONFIG = {
  girlName: "نامِ دختر",
  boyName:  "نامِ پسر",
  date:     "جمعه، ۱۵ اسفند ۱۴۰۳",
  time:     "ساعت ۸ شب",
  place:    "کافه/رستوران موردنظر",
  telegramId: "ne_mm7"   // 👈 جواب‌ها به این آیدی تلگرام میرن
};

document.getElementById('girlName1').textContent = CONFIG.girlName;
['boyName1','boyName2','boyName3','boyName4'].forEach(id =>
  document.getElementById(id).textContent = CONFIG.boyName);
document.getElementById('d-date').textContent  = CONFIG.date;
document.getElementById('d-time').textContent  = CONFIG.time;
document.getElementById('d-place').textContent = CONFIG.place;
document.getElementById('d-date2').textContent = CONFIG.date;

const YES_MSG     = `🎉 <b>جواب اومد!</b>\n\n${CONFIG.girlName} دعوت رو <b>قبول کرد</b> و تأیید نهایی هم داد! 💖\n\n📅 تاریخ: ${CONFIG.date}\n🕗 ساعت: ${CONFIG.time}\n📍 مکان: ${CONFIG.place}\n\nهمه‌چی رسمیه! 🌹`;
const HARD_NO_MSG = `💔 <b>جواب اومد...</b>\n\n${CONFIG.girlName} دعوت رو <b>قاطعانه رد کرد</b>. 😔`;
const EFFORT_MSG  = `😏 <b>جواب اومد!</b>\n\n${CONFIG.girlName} گفت: «نه، ولی <b>با پیشنهادِ بهتر</b> شاید!»\n\nیعنی هنوز شانس هست... برو یه برنامه‌ی بهتر بچین! 🔥`;

/* یادآوری ارسال */
const SEND_NOTE = '<br>✈️ توی تلگرامی که باز میشه، فقط دکمه‌ی ارسال رو بزن تا پیام برسه!';
['#screen-final-yes .tiny','#screen-hard-no .tiny','#screen-try-more .tiny'].forEach(sel=>{
  const el = document.querySelector(sel);
  if(el) el.innerHTML += SEND_NOTE;
});

/* ارسال به تلگرام (بدون ربات!) */
function sendTelegram(text){
  const plain = text.replace(/<[^>]+>/g,'');
  window.open(`https://t.me/${CONFIG.telegramId}?text=${encodeURIComponent(plain)}`, '_blank');
}

function showScreen(id){
  document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));
  document.getElementById(id).classList.add('active');
  window.scrollTo({top:0});
}

let opened = false;
function openEnvelope(){
  if(opened) return; opened = true;
  const env = document.getElementById('envelope');
  env.classList.add('open');
  setTimeout(()=> env.querySelector('.flap').style.zIndex = '1', 400);
  setTimeout(()=> showScreen('screen-invite'), 1600);
}

function acceptInvite(){
  burst(26,'💖');
  showScreen('screen-details');
}
function confirmDetails(btn){
  btn.disabled = true;
  btn.textContent = 'در حال ارسال... ⏳';
  sendTelegram(YES_MSG);
  showScreen('screen-final-yes');
  burst(40,'💖');
}

function declineInvite(){
  document.body.classList.add('sad');
  showScreen('screen-sad');
}
function hardNo(btn){
  btn.disabled = true;
  btn.textContent = 'دارم ثبت می‌کنم... ⏳';
  sendTelegram(HARD_NO_MSG);
  showScreen('screen-hard-no');
}
function wantEffort(btn){
  btn.disabled = true;
  btn.textContent = 'دارم ثبت می‌کنم... ⏳';
  sendTelegram(EFFORT_MSG);
  document.body.classList.remove('sad');
  showScreen('screen-try-more');
  burst(20,'✨');
}

function burst(n, emoji='💖'){
  for(let i=0;i<n;i++){
    const h = document.createElement('span');
    h.className = 'burst';
    h.textContent = emoji;
    const angle = Math.random()*Math.PI*2, dist = 90 + Math.random()*160;
    h.style.setProperty('--x', Math.cos(angle)*dist + 'px');
    h.style.setProperty('--y', Math.sin(angle)*dist + 'px');
    h.style.fontSize = (14 + Math.random()*16) + 'px';
    document.body.appendChild(h);
    setTimeout(()=>h.remove(), 1400);
  }
}

const emojis = ['💖','💕','🌸','✨','💗','🌷'];
setInterval(()=>{
  const h = document.createElement('span');
  h.className = 'f-heart';
  h.textContent = emojis[Math.floor(Math.random()*emojis.length)];
  h.style.left = Math.random()*100 + 'vw';
  h.style.fontSize = (12 + Math.random()*18) + 'px';
  h.style.animationDuration = (6 + Math.random()*6) + 's';
  document.getElementById('hearts').appendChild(h);
  setTimeout(()=>h.remove(), 13000);
}, 650);
</script>
</body>
</html>
