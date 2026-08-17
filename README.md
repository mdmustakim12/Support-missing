# Support-missing
Support missing cheekar 
<!DOCTYPE html>
<html lang="bn">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#0b1220">
<title>সাপোর্ট লিস্ট চেকার — কমেন্ট মিসিং ফাইন্ডার</title>
<style>
  :root{
    --bg:#070b16;
    --text:#e8eef7;
    --muted:#8fa1b8;
    --border:rgba(255,255,255,.09);
    --emerald:#34d399;
    --teal:#2dd4bf;
    --cyan:#22d3ee;
    --blue:#60a5fa;
    --violet:#a78bfa;
    --pink:#f472b6;
    --danger:#f87171;
  }
  *{box-sizing:border-box;margin:0;padding:0;}
  html{scroll-behavior:smooth;}
  body{
    font-family:'Inter','Hind Siliguri','Noto Sans Bengali',-apple-system,'Segoe UI',system-ui,sans-serif;
    color:var(--text);
    min-height:100vh;
    padding:20px 16px 40px;
    background:
      radial-gradient(1100px 640px at 8% -12%, rgba(16,185,129,.20), transparent 60%),
      radial-gradient(950px 620px at 100% -5%, rgba(99,102,241,.20), transparent 55%),
      radial-gradient(800px 560px at 50% 115%, rgba(6,182,212,.16), transparent 60%),
      linear-gradient(180deg,#070b16,#0a1122 48%,#070b16);
    background-attachment:fixed;
    position:relative;
  }
  /* floating glow orbs */
  body::before,body::after{
    content:'';position:fixed;border-radius:50%;filter:blur(90px);z-index:0;pointer-events:none;opacity:.35;
  }
  body::before{width:340px;height:340px;background:rgba(52,211,153,.35);top:-90px;left:-90px;animation:drift 16s ease-in-out infinite alternate;}
  body::after{width:300px;height:300px;background:rgba(167,139,250,.30);bottom:-90px;right:-70px;animation:drift 20s ease-in-out infinite alternate-reverse;}
  @keyframes drift{from{transform:translate(0,0) scale(1);}to{transform:translate(46px,32px) scale(1.12);}}

  .wrap{max-width:800px;margin:0 auto;position:relative;z-index:1;}

  header.hero{text-align:center;padding:30px 8px 6px;}
  .logo-badge{
    width:74px;height:74px;margin:0 auto 16px;border-radius:22px;display:grid;place-items:center;font-size:34px;
    background:linear-gradient(135deg,rgba(52,211,153,.16),rgba(34,211,238,.12));
    border:1px solid rgba(52,211,153,.35);
    box-shadow:0 10px 34px rgba(16,185,129,.25), inset 0 1px 0 rgba(255,255,255,.12);
    animation:pop .6s ease;
  }
  @keyframes pop{from{transform:scale(.6);opacity:0;}to{transform:scale(1);opacity:1;}}
  header.hero h1{
    font-size:32px;font-weight:800;letter-spacing:.3px;line-height:1.25;
    background:linear-gradient(90deg,#34d399 0%,#2dd4bf 30%,#22d3ee 62%,#a78bfa 100%);
    -webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;
  }
  header.hero p{color:var(--muted);margin-top:10px;font-size:15px;line-height:1.7;}
  header.hero p b{color:#dbe7f5;}
  .badge-auto{
    display:inline-flex;align-items:center;gap:7px;margin-top:16px;
    background:linear-gradient(135deg,rgba(52,211,153,.14),rgba(45,212,191,.08));
    color:#6ee7b7;border:1px solid rgba(52,211,153,.35);
    padding:7px 16px;border-radius:999px;font-size:13px;font-weight:600;
    box-shadow:0 4px 18px rgba(16,185,129,.15);
  }
  .badge-auto .dot{width:8px;height:8px;border-radius:50%;background:#34d399;box-shadow:0 0 0 0 rgba(52,211,153,.6);animation:pulse 2s infinite;}
  @keyframes pulse{0%{box-shadow:0 0 0 0 rgba(52,211,153,.55);}70%{box-shadow:0 0 0 8px rgba(52,211,153,0);}100%{box-shadow:0 0 0 0 rgba(52,211,153,0);}}

  .card{
    background:linear-gradient(180deg,rgba(255,255,255,.055),rgba(255,255,255,.015));
    border:1px solid var(--border);border-radius:22px;padding:22px;margin-top:18px;
    backdrop-filter:blur(16px);-webkit-backdrop-filter:blur(16px);
    box-shadow:0 14px 40px rgba(0,0,0,.38), inset 0 1px 0 rgba(255,255,255,.06);
    animation:fadeUp .5s ease both;
  }
  @keyframes fadeUp{from{opacity:0;transform:translateY(14px);}to{opacity:1;transform:translateY(0);}}

  .card-head{display:flex;gap:14px;align-items:flex-start;}
  .num{
    flex:0 0 auto;width:40px;height:40px;border-radius:12px;display:grid;place-items:center;
    font-size:19px;font-weight:800;color:#04121a;
    box-shadow:0 8px 20px rgba(0,0,0,.3), inset 0 1px 0 rgba(255,255,255,.5);
  }
  .num.green{background:linear-gradient(135deg,#34d399,#2dd4bf);}
  .num.violet{background:linear-gradient(135deg,#818cf8,#a78bfa);}
  .card h2{font-size:18px;font-weight:700;margin-top:2px;}
  .hint{font-size:13.5px;color:var(--muted);margin-top:5px;line-height:1.7;}
  .hint b{color:#b9c7da;}

  textarea{
    width:100%;min-height:230px;margin-top:14px;
    border:1.5px solid rgba(255,255,255,.12);border-radius:16px;
    padding:14px;font:inherit;font-size:15px;line-height:1.75;resize:vertical;color:#eef4fb;
    background:rgba(2,8,20,.55);
    transition:border-color .2s, box-shadow .2s;
  }
  textarea::placeholder{color:#5c6f88;}
  textarea:focus{outline:none;border-color:rgba(52,211,153,.55);box-shadow:0 0 0 4px rgba(52,211,153,.13);}
  #commentInput{min-height:150px;}
  #commentInput:focus{border-color:rgba(167,139,250,.55);box-shadow:0 0 0 4px rgba(167,139,250,.13);}

  .row{display:flex;align-items:center;justify-content:space-between;margin-top:12px;gap:10px;flex-wrap:wrap;}
  .badge{
    font-size:12.5px;padding:6px 14px;border-radius:999px;font-weight:600;letter-spacing:.2px;
  }
  .badge.g{background:rgba(52,211,153,.12);color:#6ee7b7;border:1px solid rgba(52,211,153,.3);}
  .badge.b{background:rgba(167,139,250,.12);color:#c4b5fd;border:1px solid rgba(167,139,250,.3);}

  button{font:inherit;cursor:pointer;border:none;border-radius:13px;padding:11px 18px;font-weight:700;font-size:14.5px;transition:transform .12s, filter .15s, box-shadow .15s;}
  button:active{transform:scale(.97);}
  .ghost{background:rgba(255,255,255,.05);color:#c6d3e4;border:1px solid rgba(255,255,255,.12);}
  .ghost:hover{background:rgba(255,255,255,.1);}
  .ghost.danger{background:rgba(248,113,113,.14);color:#fca5a5;border-color:rgba(248,113,113,.35);}

  .actions{margin-top:18px;}
  .note-chip{
    display:flex;align-items:center;gap:9px;font-size:13.5px;color:#c4b5fd;
    background:rgba(167,139,250,.08);border:1px solid rgba(167,139,250,.22);
    padding:11px 15px;border-radius:14px;margin-bottom:14px;line-height:1.6;
  }
  .primary{
    background:linear-gradient(135deg,#10b981,#2dd4bf 55%,#0ea5e9);
    color:#04211a;font-size:17px;font-weight:800;padding:16px;width:100%;letter-spacing:.3px;
    box-shadow:0 12px 32px rgba(16,185,129,.35), inset 0 1px 0 rgba(255,255,255,.4);
  }
  .primary:hover{filter:brightness(1.08);transform:translateY(-1px);box-shadow:0 16px 40px rgba(16,185,129,.45), inset 0 1px 0 rgba(255,255,255,.4);}

  .result-head{display:flex;align-items:center;justify-content:space-between;gap:12px;flex-wrap:wrap;}
  .result-head h2{margin:0;}
  .copy{
    background:linear-gradient(135deg,#6366f1,#8b5cf6);
    color:#fff;box-shadow:0 8px 22px rgba(99,102,241,.35);
  }
  .copy:hover{filter:brightness(1.1);}
  .copy.ok{background:linear-gradient(135deg,#10b981,#34d399);color:#04211a;}
  .result-box{
    margin-top:14px;background:rgba(2,8,20,.6);border:1px solid rgba(52,211,153,.22);
    border-left:3px solid #34d399;border-radius:16px;padding:18px;
    font-size:15.5px;line-height:1.9;white-space:pre-wrap;word-break:break-word;user-select:text;
    color:#eaf2fb;max-height:460px;overflow:auto;
  }
  .result-box::-webkit-scrollbar{width:8px;}
  .result-box::-webkit-scrollbar-thumb{background:rgba(52,211,153,.35);border-radius:99px;}
  #resultSummary{
    margin-top:12px;font-size:13.5px;color:#c6d3e4;font-weight:600;
    background:rgba(255,255,255,.04);border:1px solid var(--border);
    padding:9px 14px;border-radius:12px;display:inline-block;
  }
  details{
    margin-top:14px;background:rgba(255,255,255,.03);border:1px dashed rgba(255,255,255,.14);
    border-radius:14px;padding:12px 16px;font-size:14px;
  }
  details summary{cursor:pointer;color:#d3deec;font-weight:700;}
  .matched{margin-top:12px;display:flex;flex-wrap:wrap;gap:8px;}
  .chip{
    background:linear-gradient(135deg,rgba(52,211,153,.14),rgba(45,212,191,.08));
    color:#6ee7b7;border:1px solid rgba(52,211,153,.3);padding:5px 12px;border-radius:999px;font-size:13px;font-weight:600;
  }
  .muted{color:#6b7c94;font-size:13.5px;}

  .hist-item{
    border:1px solid var(--border);border-radius:18px;padding:16px;margin-top:14px;
    background:linear-gradient(180deg,rgba(255,255,255,.045),rgba(255,255,255,.015));
    animation:fadeUp .4s ease both;
  }
  .hist-head{display:flex;justify-content:space-between;align-items:center;gap:10px;flex-wrap:wrap;}
  .hist-title{font-weight:700;color:#e6edf7;font-size:14.5px;}
  .hist-meta{font-size:12px;color:#6b7c94;margin-top:3px;}
  .hist-actions{display:flex;gap:8px;}
  .mini{padding:8px 13px;font-size:13px;border-radius:10px;}
  .mini.del{background:rgba(248,113,113,.13);color:#fca5a5;border:1px solid rgba(248,113,113,.3);}
  .mini.copy{background:rgba(99,102,241,.15);color:#a5b4fc;border:1px solid rgba(99,102,241,.3);}
  .hist-text{
    margin-top:12px;background:rgba(2,8,20,.5);border:1px solid var(--border);border-radius:14px;padding:14px;
    white-space:pre-wrap;word-break:break-word;font-size:14px;line-height:1.8;color:#dbe6f2;
    user-select:text;max-height:280px;overflow:auto;
  }

  #toast{
    position:fixed;left:50%;bottom:26px;transform:translateX(-50%) translateY(20px);
    background:linear-gradient(135deg,#0f172a,#1e293b);color:#e8eef7;padding:12px 22px;border-radius:14px;
    font-size:14px;font-weight:600;opacity:0;pointer-events:none;transition:.28s;z-index:99;
    border:1px solid rgba(52,211,153,.4);box-shadow:0 14px 40px rgba(0,0,0,.5);max-width:92vw;text-align:center;
  }
  #toast.show{opacity:1;transform:translateX(-50%) translateY(0);}

  footer{text-align:center;color:#6b7c94;font-size:12.5px;margin:26px 0 8px;line-height:1.8;}
  .steps{font-size:13.5px;color:#c6d3e4;line-height:2;}
  .steps b{color:#6ee7b7;}
  @media (max-width:520px){header.hero h1{font-size:25px;}}
</style>
</head>
<body>
<div class="wrap">

  <header class="hero">
    <div class="logo-badge">📋</div>
    <h1>সাপোর্ট লিস্ট চেকার</h1>
    <p>সাপোর্ট লিস্টের সাথে কমেন্ট লিস্ট মিলিয়ে দেখুন — <b>কে কমেন্ট করেনি</b>, তা এক ক্লিকে সিরিয়াল করে বের করুন।</p>
    <span class="badge-auto"><span class="dot"></span> অটো-সেভ অন — ব্রাউজার বন্ধ করলেও ডেটা থাকবে</span>
  </header>

  <details class="card" style="padding:16px 20px;">
    <summary style="cursor:pointer;font-weight:700;">📌 কীভাবে ব্যবহার করবেন?</summary>
    <p class="steps" style="margin-top:10px;">
      ১️⃣ <b>১ম বক্সে</b> সাপোর্ট লিস্ট পেস্ট করুন (তারিখ + বার + নামের লিস্ট)।<br>
      ২️⃣ <b>২য় বক্সে</b> কমেন্ট লিস্ট পেস্ট করুন (Link No + যারা কমেন্ট করেছেন তাদের নাম)।<br>
      ৩️⃣ <b>✅ চেক করুন</b> চাপুন → যারা কমেন্ট করেনি তাদের সিরিয়াল লিস্ট পাবেন, সাথে <b>কপি বাটন</b>।
    </p>
  </details>

  <section class="card">
    <div class="card-head">
      <span class="num green">১</span>
      <div>
        <h2>সাপোর্ট লিস্ট পেস্ট করুন</h2>
        <p class="hint">যেমন: <b>📅 তারিখ</b>, <b>📆 বার</b>, তারপর 👇👇👇 এর নিচে <b>1️⃣➤@নাম</b> আকারে নামের লিস্ট।</p>
      </div>
    </div>
    <textarea id="supportInput" placeholder="📅 তারিখ: 04-05-26 ✅&#10;📆 বার: সোমবার ✅&#10;&#10;যারা সাপোর্ট করেছেন তাদের তালিকা ✅&#10;👇👇👇&#10;&#10;1️⃣➤@Rakib Ahamed&#10;2️⃣➤@H.M. Yeasin Khan Tuhin&#10;3️⃣➤@Md Shakil&#10;4️⃣➤@Kobir Khan&#10;5️⃣➤@Rahi Ahmed Rabiul&#10;6️⃣➤@Nil Hasan ..."></textarea>
    <div class="row">
      <span id="supportCount" class="badge g">০ জন নাম</span>
      <button class="ghost" id="clearSupport">🗑 ক্লিয়ার</button>
    </div>
  </section>

  <section class="card">
    <div class="card-head">
      <span class="num violet">২</span>
      <div>
        <h2>কমেন্ট লিস্ট পেস্ট করুন</h2>
        <p class="hint">যেমন: <b>Link- 15</b> লিখে তার নিচে যারা কমেন্ট করেছেন তাদের নাম (যেকোনো ভাষায়)।</p>
      </div>
    </div>
    <textarea id="commentInput" placeholder="Link- 15&#10;&#10;MD Sohan&#10;Siyam Vhai&#10;Sijan AHMED&#10;সুমি আক্তার"></textarea>
    <div class="row">
      <span id="commentCount" class="badge b">০ জন নাম</span>
      <button class="ghost" id="clearComment">🗑 ক্লিয়ার</button>
    </div>
  </section>

  <div class="actions">
    <div class="note-chip">🔍 ফুল-নেম ম্যাচিং — @ এর পরের <b style="margin:0 4px;">সম্পূর্ণ নাম</b> মিললেই ম্যাচ; শুধু <b style="margin:0 4px;">space ও বড়/ছোট হাতের অক্ষর</b> হিসাব করা হয় না।</div>
    <button id="checkBtn" class="primary">✅ চেক করুন</button>
  </div>

  <section class="card" id="resultCard" hidden>
    <div class="result-head">
      <h2>📤 রেজাল্ট</h2>
      <button id="copyResult" class="copy">📋 কপি করুন</button>
    </div>
    <pre id="resultText" class="result-box"></pre>
    <p id="resultSummary"></p>
    <details>
      <summary>✅ যারা ম্যাচ হয়েছে (<span id="matchedCount">0</span> জন) — দেখতে চাপুন</summary>
      <div id="matchedList" class="matched"></div>
    </details>
  </section>

  <section class="card">
    <div class="result-head">
      <h2>📜 আগের রেজাল্ট (সেভ করা)</h2>
      <button class="ghost" id="clearAll">🗑 সব মুছে ফেলুন</button>
    </div>
    <p class="hint" style="margin-top:8px;">প্রতিবার চেক করার রেজাল্ট এখানে জমা থাকবে। মুছে না ফেলা পর্যন্ত দিনের পর দিন সেভ থাকবে — প্রতিটা রেজাল্টের সাথে আলাদা কপি বাটন আছে।</p>
    <div id="history" class="history"></div>
  </section>

  <footer>
    💾 সব ডেটা শুধু এই ব্রাউজারে (localStorage) সেভ হয় — অন্য কেউ দেখতে পাবে না।<br>
    রেজাল্ট টেক্সট সিলেক্ট করে ম্যানুয়ালি কপিও করতে পারবেন।
  </footer>
</div>

<div id="toast"></div>

<script>
/* ============================================================
   Pure helper functions (DOM-নির্ভর নয়)
============================================================ */
function toLatinDigits(s){
  return String(s).replace(/[০-৯]/g, function(d){ return String('০১২৩৪৫৬৭৮৯'.indexOf(d)); });
}

/* নাম নরমালাইজ করা: @ বাদ, ডট/কমা বাদ, ইমোজি বাদ, বড়-ছোট হাতের অক্ষর এক করা
   (শুধু পরিষ্কার করার জন্য — ম্যাচিং হয় সম্পূর্ণ নামের সমতার ভিত্তিতে) */
function normalizeName(raw){
  let s = String(raw == null ? '' : raw).trim();
  s = s.replace(/^[@➤\s]+/, '');
  s = s.replace(/[.\u0964\u09F7,،;]/g, ' ');
  s = s.replace(/\.{2,}|…/g, ' ');
  s = s.replace(/[^\p{L}\p{N}\s]/gu, ' ');
  s = s.replace(/\s+/g, ' ').trim().toLowerCase();
  return s;
}

var EMOJI_RANGE = '\\u{1F000}-\\u{1FAFF}\\u{2600}-\\u{27BF}\\u{2B00}-\\u{2BFF}\\u{FE0F}\\u{200D}\\u{20E3}\\u{2190}-\\u{21FF}\\u{25A0}-\\u{25FF}';
var RE_EMOJI_ANY  = new RegExp('[' + EMOJI_RANGE + ']', 'gu');
var RE_EMOJI_ONLY = new RegExp('^[' + EMOJI_RANGE + '\\s]+$', 'u');

/* ডিসপ্লের জন্য নাম পরিষ্কার (শুরু/শেষের ইমোজি, ডট, ড্যাশ বাদ) — @ রাখা হয় */
function cleanDisplayName(s){
  let t = String(s || '').trim();
  t = t.replace(/^[\s➤]+/, '');
  t = t.replace(RE_EMOJI_ANY, '').trim();
  t = t.replace(/\.{2,}|…/g, '').trim();
  t = t.replace(/^[-–—•*]\s*/, '').trim();
  return t;
}

function dedupe(arr){
  var seen = new Set(), out = [];
  for (var i = 0; i < arr.length; i++){
    if (!seen.has(arr[i].norm)){ seen.add(arr[i].norm); out.push(arr[i]); }
  }
  return out;
}

function pick(text, re){
  var m = String(text || '').match(re);
  if (!m) return null;
  var v = m[1].trim();
  v = v.replace(RE_EMOJI_ANY, '').trim();
  v = v.replace(/\s+/g, ' ').trim();
  return v || null;
}

/* ১ম বক্স: তারিখ, বার ও নামের লিস্ট পার্স করা */
function parseSupport(text){
  var names = [];
  var date = pick(text, /তারিখ\s*[:：]\s*([^\n]+)/);
  var day  = pick(text, /বার\s*[:：]\s*([^\n]+)/);
  var lines = String(text || '').split(/\r?\n/);
  var started = false;
  for (var i = 0; i < lines.length; i++){
    var t = lines[i].trim();
    if (!t) continue;
    if (/[👇👉🔻]/.test(t)) continue;               // ডেকোরেশন/হেডার লাইন
    if (RE_EMOJI_ONLY.test(t)) continue;            // শুধু ইমোজির লাইন
    var name = null;
    if (t.indexOf('➤') !== -1){
      name = t.split('➤').pop();
    } else {
      var t2 = t.replace(RE_EMOJI_ANY, '').replace(/^[\s➤]+/, '').trim();
      if (t2.charAt(0) === '@'){
        name = t2;
      } else if (/^\d+\s*[.)]\s*/.test(t2)){
        name = t2.replace(/^\d+\s*[.)]\s*/, '');
      } else if (started && /[\p{L}\p{N}]/u.test(t2)){
        name = t2;                                   // লিস্ট শুরু হওয়ার পরের প্লেইন নাম
      } else {
        continue;
      }
    }
    name = cleanDisplayName(name);
    var norm = normalizeName(name);
    if (!norm) continue;
    names.push({ raw: name, norm: norm });
    started = true;
  }
  return { names: dedupe(names), date: date, day: day };
}

/* ২য় বক্স থেকে Link No বের করা */
function extractLinkNo(text){
  var t = String(text || '');
  var m = t.match(/link\s*[-–—_:=\s]*(?:no\.?\s*)?[-–—_:=\s]*([0-9০-৯]+)/i)
       || t.match(/link\s*[-–—_:=\s]*([0-9০-৯]+)/i)
       || t.match(/(?:লিংক|লিংকে)\s*[-–—_:=\s]*(?:no\.?\s*)?[-–—_:=\s]*([0-9০-৯]+)/i)
       || t.match(/link[^0-9০-৯\n]{0,15}([0-9০-৯]+)/i);
  return m ? toLatinDigits(m[1]) : null;
}

/* ২য় বক্স: কমেন্ট লিস্ট পার্স করা */
function parseComment(text){
  var linkNo = extractLinkNo(text);
  var names = [];
  var lines = String(text || '').split(/\r?\n/);
  for (var i = 0; i < lines.length; i++){
    var t = lines[i].trim();
    if (!t) continue;
    if (/[👇👉🔻]/.test(t)) continue;
    if (RE_EMOJI_ONLY.test(t)) continue;
    if (/^link\b/i.test(t) || /^লিংক\b/i.test(t)) continue;   // লিংক হেডার লাইন
    var t2 = t.replace(RE_EMOJI_ANY, '').replace(/^[\s➤]+/, '').trim();
    if (!t2) continue;
    if (/^link\b/i.test(t2) || /^লিংক\b/i.test(t2)) continue;
    if (/^(যারা|যাঁরা|নিচে|নীচে|নিচের|নীচের)/.test(t2) && /(কমেন্ট|লিস্ট|তালিকা)/.test(t2)) continue;
    t2 = t2.replace(/^\d+\s*[.)]\s*/, '').trim();
    var name = cleanDisplayName(t2);
    var norm = normalizeName(name);
    if (!norm) continue;
    names.push({ raw: name, norm: norm });
  }
  return { linkNo: linkNo, names: dedupe(names) };
}

/* ফুল-নেম ম্যাচিং: সম্পূর্ণ নাম মিললেই ম্যাচ।
   বড়/ছোট হাতের অক্ষর ও space হিসাব করা হয় না (ডট/কমা আগেই বাদ পড়ে) */
function isMatched(sNorm, cNorms){
  if (!sNorm) return false;
  var key = sNorm.replace(/\s+/g, '');
  for (var i = 0; i < cNorms.length; i++){
    if (cNorms[i] && cNorms[i].replace(/\s+/g, '') === key) return true;
  }
  return false;
}

/* আউটপুট টেক্সট তৈরি */
function buildResultText(linkNo, missing){
  if (!missing.length) return '🎉 সবাই কমেন্ট করেছেন — কেউ মিসিং নেই!';
  var head = linkNo ? ('Link No ' + linkNo + ' তে যাঁরা কমেন্ট করে নাই 👇') : 'যাঁরা কমেন্ট করে নাই 👇';
  var lines = [head, '', 'মোট: ' + missing.length + ' জন', ''];
  for (var i = 0; i < missing.length; i++){
    lines.push((i + 1) + '. ' + missing[i].raw);
  }
  return lines.join('\n');
}

function buildTitle(support, linkNo){
  var parts = [];
  if (support.date) parts.push('📅 ' + support.date);
  if (support.day) parts.push(support.day);
  if (linkNo) parts.push('Link No ' + linkNo);
  return parts.join(' · ') || 'রেজাল্ট';
}

if (typeof module !== 'undefined') {
  module.exports = {
    normalizeName: normalizeName, parseSupport: parseSupport, parseComment: parseComment,
    extractLinkNo: extractLinkNo, isMatched: isMatched, buildResultText: buildResultText,
    buildTitle: buildTitle
  };
}

/* ============================================================
   DOM wiring (ব্রাউজারে চলবে)
============================================================ */
if (typeof document !== 'undefined' && document.getElementById) {
  var $ = function(id){ return document.getElementById(id); };
  var supportInput = $('supportInput');
  var commentInput = $('commentInput');
  var supportCount = $('supportCount');
  var commentCount = $('commentCount');
  var checkBtn = $('checkBtn');
  var resultCard = $('resultCard');
  var resultText = $('resultText');
  var resultSummary = $('resultSummary');
  var copyResult = $('copyResult');
  var matchedCount = $('matchedCount');
  var matchedList = $('matchedList');
  var historyBox = $('history');
  var clearSupport = $('clearSupport');
  var clearComment = $('cle
