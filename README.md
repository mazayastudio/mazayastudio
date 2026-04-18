
<style>
@import url('https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@300;400;700&family=DM+Mono:wght@400;500&display=swap');

#brut-wrap { background:#0a0a0a; color:#f0f0f0; font-family:'DM Mono',monospace; padding:2rem; box-sizing:border-box; }

@keyframes scanline {
  0% { transform: translateY(-100%) }
  100% { transform: translateY(100vh) }
}
@keyframes glitch1 {
  0%,95%,100% { clip-path: none; transform: none }
  96% { clip-path: polygon(0 20%, 100% 20%, 100% 25%, 0 25%); transform: translate(-4px, 0) }
  97% { clip-path: polygon(0 60%, 100% 60%, 100% 65%, 0 65%); transform: translate(4px, 0) }
  98% { clip-path: polygon(0 40%, 100% 40%, 100% 42%, 0 42%); transform: translate(-2px, 0) }
  99% { clip-path: none; transform: translate(2px, 0) }
}
@keyframes glitch2 {
  0%,95%,100% { clip-path: none; transform: none; opacity:0 }
  96% { clip-path: polygon(0 30%, 100% 30%, 100% 35%, 0 35%); transform: translate(6px, 0); opacity:1; color:#ff2d2d }
  98% { clip-path: polygon(0 70%, 100% 70%, 100% 75%, 0 75%); transform: translate(-6px, 0); opacity:1; color:#00ffcc }
  99% { opacity:0 }
}
@keyframes blink { 0%,49%{opacity:1} 50%,100%{opacity:0} }
@keyframes revealUp { from{opacity:0;transform:translateY(40px)} to{opacity:1;transform:translateY(0)} }
@keyframes tickerX { from{transform:translateX(0)} to{transform:translateX(-50%)} }
@keyframes barIn { from{transform:scaleX(0)} to{transform:scaleX(1)} }
@keyframes dotPulse { 0%,100%{opacity:1;transform:scale(1)} 50%{opacity:0.3;transform:scale(0.7)} }
@keyframes borderSpin {
  0%{border-top-color:#ff2d2d;border-right-color:#0a0a0a;border-bottom-color:#0a0a0a;border-left-color:#0a0a0a}
  25%{border-top-color:#0a0a0a;border-right-color:#ff2d2d;border-bottom-color:#0a0a0a;border-left-color:#0a0a0a}
  50%{border-top-color:#0a0a0a;border-right-color:#0a0a0a;border-bottom-color:#ff2d2d;border-left-color:#0a0a0a}
  75%{border-top-color:#0a0a0a;border-right-color:#0a0a0a;border-bottom-color:#0a0a0a;border-left-color:#ff2d2d}
  100%{border-top-color:#ff2d2d;border-right-color:#0a0a0a;border-bottom-color:#0a0a0a;border-left-color:#0a0a0a}
}

.glitch-main { position:relative; font-family:'Space Grotesk',sans-serif; font-size:52px; font-weight:700; letter-spacing:-2px; line-height:1; color:#f0f0f0; animation: glitch1 8s infinite; }
.glitch-ghost { position:absolute; top:0;left:0; font-family:'Space Grotesk',sans-serif; font-size:52px; font-weight:700; letter-spacing:-2px; line-height:1; color:#f0f0f0; animation: glitch2 8s infinite; pointer-events:none; }
.cursor { display:inline-block; width:3px; height:52px; background:#ff2d2d; vertical-align:middle; animation: blink 0.8s step-end infinite; margin-left:4px; }

.section-label { font-size:9px; letter-spacing:4px; color:#555; text-transform:uppercase; margin-bottom:4px; }
.red { color:#ff2d2d; }
.mono { font-family:'DM Mono',monospace; }

.ticker-wrap { overflow:hidden; border-top:1px solid #222; border-bottom:1px solid #222; padding:8px 0; margin:24px 0; }
.ticker { display:flex; gap:48px; animation: tickerX 18s linear infinite; white-space:nowrap; }
.ticker-item { font-size:11px; letter-spacing:2px; color:#444; text-transform:uppercase; }
.ticker-item span { color:#ff2d2d; margin-right:8px; }

.skill-row { display:grid; grid-template-columns:120px 1fr 36px; align-items:center; gap:12px; margin-bottom:10px; }
.skill-name { font-size:11px; letter-spacing:1px; color:#888; }
.skill-track { height:2px; background:#1a1a1a; overflow:hidden; }
.skill-fill { height:100%; background:#ff2d2d; transform-origin:left; animation: barIn 1.2s cubic-bezier(.77,0,.175,1) both; }
.skill-pct { font-size:11px; color:#444; text-align:right; }

.stat-grid { display:grid; grid-template-columns:1fr 1fr; gap:2px; margin:24px 0; }
.stat-cell { background:#111; padding:16px; position:relative; overflow:hidden; }
.stat-cell::before { content:''; position:absolute; top:0;left:0;right:0; height:1px; background:#ff2d2d; transform:scaleX(0); transform-origin:left; transition:transform 0.4s; }
.stat-cell:hover::before { transform:scaleX(1); }
.stat-n { font-family:'Space Grotesk',sans-serif; font-size:36px; font-weight:700; color:#f0f0f0; line-height:1; }
.stat-l { font-size:9px; letter-spacing:3px; color:#444; margin-top:4px; text-transform:uppercase; }

.stack-grid { display:flex; flex-wrap:wrap; gap:2px; margin-top:12px; }
.stack-tag { font-size:10px; letter-spacing:1.5px; padding:5px 10px; border:1px solid #1e1e1e; color:#555; text-transform:uppercase; transition:all 0.2s; cursor:default; }
.stack-tag:hover { border-color:#ff2d2d; color:#ff2d2d; }

.avail-dot { display:inline-block; width:6px; height:6px; background:#00ffcc; border-radius:50%; animation: dotPulse 2s ease-in-out infinite; margin-right:6px; }
.spin-border { width:60px; height:60px; border:2px solid #0a0a0a; border-radius:50%; animation: borderSpin 2s linear infinite; display:flex; align-items:center; justify-content:center; }
.spin-inner { font-family:'Space Grotesk',sans-serif; font-size:14px; font-weight:700; color:#f0f0f0; }

.r1 { animation: revealUp 0.7s ease 0.1s both; }
.r2 { animation: revealUp 0.7s ease 0.25s both; }
.r3 { animation: revealUp 0.7s ease 0.4s both; }
.r4 { animation: revealUp 0.7s ease 0.55s both; }
.r5 { animation: revealUp 0.7s ease 0.7s both; }
.r6 { animation: revealUp 0.7s ease 0.85s both; }

hr.brut { border:none; border-top:1px solid #1a1a1a; margin:24px 0; }
</style>

<div id="brut-wrap">

  <div class="r1" style="display:flex;justify-content:space-between;align-items:center;margin-bottom:32px;">
    <div>
      <div class="section-label">developer / bandung / indonesia</div>
      <div style="position:relative;display:inline-block;">
        <div class="glitch-main">SAYUDHA<span class="cursor"></span></div>
        <div class="glitch-ghost">SAYUDHA</div>
      </div>
      <div style="font-family:'Space Grotesk',sans-serif;font-size:14px;color:#444;letter-spacing:3px;margin-top:8px;">FULL-STACK &nbsp;/&nbsp; CREATIVE CODER</div>
    </div>
    <div style="text-align:right;">
      <div class="spin-border">
        <div class="spin-inner">MZ</div>
      </div>
      <div style="font-size:9px;letter-spacing:2px;color:#333;margin-top:8px;">MAZAYA.STUDIO</div>
    </div>
  </div>

  <div class="r2">
    <div class="ticker-wrap">
      <div class="ticker">
        <div class="ticker-item"><span>*</span>REACT</div>
        <div class="ticker-item"><span>*</span>THREE.JS</div>
        <div class="ticker-item"><span>*</span>SHOPIFY</div>
        <div class="ticker-item"><span>*</span>NODE.JS</div>
        <div class="ticker-item"><span>*</span>VUE</div>
        <div class="ticker-item"><span>*</span>SASS</div>
        <div class="ticker-item"><span>*</span>FIGMA</div>
        <div class="ticker-item"><span>*</span>WEBFLOW</div>
        <div class="ticker-item"><span>*</span>REACT</div>
        <div class="ticker-item"><span>*</span>THREE.JS</div>
        <div class="ticker-item"><span>*</span>SHOPIFY</div>
        <div class="ticker-item"><span>*</span>NODE.JS</div>
        <div class="ticker-item"><span>*</span>VUE</div>
        <div class="ticker-item"><span>*</span>SASS</div>
        <div class="ticker-item"><span>*</span>FIGMA</div>
        <div class="ticker-item"><span>*</span>WEBFLOW</div>
      </div>
    </div>
  </div>

  <div class="r3" style="display:grid;grid-template-columns:1fr 1fr;gap:32px;margin-bottom:24px;">
    <div>
      <div class="section-label">about</div>
      <div style="font-size:12px;color:#555;line-height:1.8;margin-top:8px;">
        Building at the intersection of<br>
        <span style="color:#f0f0f0;">engineering</span> and <span style="color:#ff2d2d;">design</span>.<br>
        Founder of Mazaya Studio.<br>
        Shopify D2C + Creative Web.<br>
        <br>
        <span class="avail-dot"></span><span style="font-size:9px;letter-spacing:2px;color:#00ffcc;">OPEN TO WORK</span>
      </div>
    </div>
    <div>
      <div class="section-label">proficiency</div>
      <div style="margin-top:12px;">
        <div class="skill-row"><div class="skill-name">JavaScript</div><div class="skill-track"><div class="skill-fill" style="width:92%;animation-delay:0.6s"></div></div><div class="skill-pct">92</div></div>
        <div class="skill-row"><div class="skill-name">React</div><div class="skill-track"><div class="skill-fill" style="width:88%;animation-delay:0.75s"></div></div><div class="skill-pct">88</div></div>
        <div class="skill-row"><div class="skill-name">Three.js</div><div class="skill-track"><div class="skill-fill" style="width:75%;animation-delay:0.9s"></div></div><div class="skill-pct">75</div></div>
        <div class="skill-row"><div class="skill-name">Shopify</div><div class="skill-track"><div class="skill-fill" style="width:82%;animation-delay:1.05s"></div></div><div class="skill-pct">82</div></div>
        <div class="skill-row"><div class="skill-name">UI/UX</div><div class="skill-track"><div class="skill-fill" style="width:85%;animation-delay:1.2s"></div></div><div class="skill-pct">85</div></div>
      </div>
    </div>
  </div>

  <div class="r4 stat-grid">
    <div class="stat-cell"><div class="stat-n">3<span class="red">+</span></div><div class="stat-l">years active</div></div>
    <div class="stat-cell"><div class="stat-n">15<span class="red">+</span></div><div class="stat-l">tech stack</div></div>
    <div class="stat-cell" style="grid-column:1/-1;background:#0d0d0d;display:flex;gap:32px;align-items:center;">
      <div><div class="stat-n" style="font-size:24px;">mazaya.studio@outlook.com</div><div class="stat-l">primary contact</div></div>
      <div style="margin-left:auto;text-align:right;">
        <div style="font-size:9px;letter-spacing:3px;color:#333;margin-bottom:4px;">LINKEDIN</div>
        <div style="font-size:11px;color:#555;">sayudha-lukita-wibisana</div>
      </div>
    </div>
  </div>

  <hr class="brut r5">

  <div class="r6">
    <div class="section-label">full stack</div>
    <div class="stack-grid">
      <div class="stack-tag">JavaScript</div>
      <div class="stack-tag">TypeScript</div>
      <div class="stack-tag">React</div>
      <div class="stack-tag">Vue</div>
      <div class="stack-tag">Node.js</div>
      <div class="stack-tag">Three.js</div>
      <div class="stack-tag">Shopify</div>
      <div class="stack-tag">Webflow</div>
      <div class="stack-tag">Sass</div>
      <div class="stack-tag">Webpack</div>
      <div class="stack-tag">Figma</div>
      <div class="stack-tag">Linux</div>
      <div class="stack-tag">Git</div>
    </div>
  </div>

</div>
