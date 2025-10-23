<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>click me (Harmless)</title>
<style>
  :root{--bg:#0b0f14;--panel:#0f161a;--accent:#e74c3c;--text:#e6eef6}
  html,body{height:100%;margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial}
  body{background:linear-gradient(180deg,#051018 0%,#07121a 100%);color:var(--text);overflow-y:scroll}
  .stage{height:160vh;display:flex;align-items:center;justify-content:center;flex-direction:column;position:relative}
  .spider-wrap{position:fixed; top:30vh; left:50%; transform:translateX(-50%); z-index:10; display:flex;align-items:center;justify-content:center}
  .rope{width:2px;height:220px;background:linear-gradient(#bbb,#777); transform-origin:top}
  .spider{
    width:120px;height:120px;border-radius:50%;background:#0b0f14;position:relative;
    box-shadow:inset 0 -6px 12px rgba(0,0,0,0.6), 0 6px 18px rgba(0,0,0,0.6);
    display:flex;align-items:center;justify-content:center;overflow:visible;
  }
  .spider::before{content:"";position:absolute;left:50%;top:50%;transform:translate(-50%,-30%);width:56px;height:56px;border-radius:50%;background:#111}
  /* legs (simple) */
  .leg{position:absolute;width:6px;height:46px;background:#111;border-radius:6px;transform-origin:top}
  .leg.l1{left:-10px;top:18px;transform:rotate(-40deg)}
  .leg.l2{left:-22px;top:34px;transform:rotate(-55deg)}
  .leg.l3{left:-10px;top:58px;transform:rotate(-110deg)}
  .leg.l4{left:6px;top:58px;transform:rotate(-70deg)}
  .leg.r1{right:-10px;top:18px;transform:rotate(40deg)}
  .leg.r2{right:-22px;top:34px;transform:rotate(55deg)}
  .leg.r3{right:-10px;top:58px;transform:rotate(110deg)}
  .leg.r4{right:6px;top:58px;transform:rotate(70deg)}
  .eye{position:absolute;width:12px;height:12px;background:#fff;border-radius:50%;top:38%;left:44%}
  .eye.r{left:60%}
  .overlay{
    position:fixed;inset:0;display:grid;place-items:center;background:rgba(2,6,10,0.75);
    opacity:0;pointer-events:none;transition:opacity .4s ease;z-index:50;padding:20px;
  }
  .overlay.show{opacity:1;pointer-events:auto}
  .card{background:linear-gradient(180deg,#111316,#0f161a);padding:28px;border-radius:12px;max-width:700px;text-align:center;box-shadow:0 12px 40px rgba(0,0,0,0.6)}
  h1{margin:0 0 10px;color:var(--accent);font-size:28px}
  p{margin:0 0 16px;color:#c6d6df}
  button{background:var(--accent);border:0;padding:10px 14px;border-radius:8px;color:white;cursor:pointer;font-weight:700}
  .note{font-size:13px;color:#92a7b6;margin-top:10px}
  footer{position:fixed;bottom:14px;left:50%;transform:translateX(-50%);color:#6f8a98;font-size:12px}
</style>
</head>
<body>
  <div class="stage">
    <div class="spider-wrap" id="spiderArea" aria-hidden="false">
      <div class="rope" id="rope"></div>
      <div class="spider" role="img" aria-label="spider">
        <div class="eye"></div><div class="eye r"></div>
        <div class="leg l1"></div><div class="leg l2"></div><div class="leg l3"></div><div class="leg l4"></div>
        <div class="leg r1"></div><div class="leg r2"></div><div class="leg r3"></div><div class="leg r4"></div>
      </div>
    </div>

    <!-- filler content so page can scroll -->
    <div style="height:120vh;width:90%;max-width:720px;margin-top:60vh;text-align:center;color:#9fb4c8">
      <h2 style="color:#dfeff6">Scroll down slowly...</h2>
      <p style="line-height:1.6">This page is a harmless prank. No data is collected. Try scrolling to see a spooky reveal.</p>
    </div>
  </div>

  <div class="overlay" id="overlay" role="dialog" aria-modal="true" aria-hidden="true">
    <div class="card">
      <h1>get hacked Gotcha — bozo</h1>
      <p>This got your ip. <strong>thanks for the ip</strong> and  hacking occurred.</p>
      <button id="closeBtn">Okay, I get it</button>
      <div class="note">Want this customized (colors, message, or sound)? I can do a version that asks for consent first.</div>
    </div>
  </div>

  <footer>&copy; click me — No data collected</footer>

<script>
  // we took all of your info.
  const overlay = document.getElementById('overlay');
  const rope = document.getElementById('rope');
  const spiderArea = document.getElementById('spiderArea');
  const closeBtn = document.getElementById('closeBtn');

  // subtle sway animation for rope/spider
  let angle = 0;
  function sway(){
    angle += 0.02;
    const x = Math.sin(angle) * 6; // px
    rope.style.transform = `translateX(${x}px)`;
    requestAnimationFrame(sway);
  }
  sway();

  // Reveal overlay when user scrolls down more than 120px
  let revealed = false;
  window.addEventListener('scroll', ()=>{
    if (revealed) return;
    if (window.scrollY > 120){
      revealed = true;
      overlay.classList.add('show');
      overlay.setAttribute('aria-hidden','false');
    }
  });

  closeBtn.addEventListener('click', ()=>{
    overlay.classList.remove('show');
    overlay.setAttribute('aria-hidden','true');
  });

  // Accessibility: allow Esc to close
  window.addEventListener('keydown', (e)=>{
    if (e.key === 'Escape' && overlay.classList.contains('show')){
      overlay.classList.remove('show');
      overlay.setAttribute('aria-hidden','true');
    }
  });
</script>
</body>
</html>
