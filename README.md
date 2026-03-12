<!DOCTYPE html>

<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>Mohamed Chouaib — Portfolio</title>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600;800&family=Space+Grotesk:wght@300;500;700&display=swap" rel="stylesheet" />
<style>
  :root {
    --orange: #FF6B00;
    --orange-dim: #cc5500;
    --bg: #0A0A0A;
    --surface: #111111;
    --surface2: #1a1a1a;
    --text: #FFFFFF;
    --muted: #888888;
    --border: #222222;
  }

*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

html { scroll-behavior: smooth; }

body {
font-family: ‘Space Grotesk’, sans-serif;
background: var(–bg);
color: var(–text);
overflow-x: hidden;
cursor: none;
}

/* Custom cursor */
.cursor {
position: fixed; top: 0; left: 0; z-index: 9999;
pointer-events: none;
}
.cursor-dot {
width: 8px; height: 8px; background: var(–orange);
border-radius: 50%;
transform: translate(-50%, -50%);
transition: transform 0.1s;
position: absolute;
}
.cursor-ring {
width: 36px; height: 36px;
border: 1.5px solid var(–orange);
border-radius: 50%;
transform: translate(-50%, -50%);
transition: width 0.3s, height 0.3s, opacity 0.3s, transform 0.15s;
position: absolute;
opacity: 0.5;
}
body:hover .cursor-ring { opacity: 0.5; }

/* Noise overlay */
body::before {
content: ‘’;
position: fixed; inset: 0; z-index: 0;
background-image: url(“data:image/svg+xml,%3Csvg viewBox=‘0 0 200 200’ xmlns=‘http://www.w3.org/2000/svg’%3E%3Cfilter id=‘n’%3E%3CfeTurbulence type=‘fractalNoise’ baseFrequency=‘0.9’ numOctaves=‘4’ stitchTiles=‘stitch’/%3E%3C/filter%3E%3Crect width=‘100%25’ height=‘100%25’ filter=‘url(%23n)’ opacity=‘0.03’/%3E%3C/svg%3E”);
pointer-events: none;
}

/* Gradient orbs */
.orb {
position: fixed; border-radius: 50%; filter: blur(120px);
pointer-events: none; z-index: 0; opacity: 0.12;
animation: orbFloat 12s ease-in-out infinite alternate;
}
.orb1 { width: 600px; height: 600px; background: var(–orange); top: -200px; right: -150px; animation-delay: 0s; }
.orb2 { width: 400px; height: 400px; background: #cc3300; bottom: 10%; left: -100px; animation-delay: -6s; }

@keyframes orbFloat {
from { transform: translate(0,0) scale(1); }
to   { transform: translate(30px, 40px) scale(1.1); }
}

/* Layout */
main { position: relative; z-index: 1; max-width: 960px; margin: 0 auto; padding: 0 24px; }

/* HERO */
.hero {
min-height: 100vh;
display: flex; flex-direction: column; justify-content: center; align-items: center;
text-align: center; padding: 80px 0 60px;
}

.hero-badge {
display: inline-flex; align-items: center; gap: 8px;
border: 1px solid #2a2a2a; background: #141414;
padding: 6px 16px; border-radius: 999px;
font-family: ‘JetBrains Mono’, monospace; font-size: 12px;
color: var(–orange); margin-bottom: 32px;
opacity: 0; animation: fadeUp 0.8s 0.2s forwards;
}
.hero-badge .dot {
width: 6px; height: 6px; background: #22c55e; border-radius: 50%;
animation: pulse 2s infinite;
}
@keyframes pulse { 0%,100%{opacity:1;} 50%{opacity:0.3;} }

.hero-name {
font-family: ‘JetBrains Mono’, monospace;
font-size: clamp(52px, 10vw, 96px);
font-weight: 800; line-height: 1;
letter-spacing: -2px;
background: linear-gradient(135deg, #fff 30%, var(–orange) 100%);
-webkit-background-clip: text; -webkit-text-fill-color: transparent;
background-clip: text;
opacity: 0; animation: fadeUp 0.9s 0.4s forwards;
}

.hero-title {
margin-top: 16px;
font-size: 18px; font-weight: 300; color: var(–muted); letter-spacing: 3px;
text-transform: uppercase;
opacity: 0; animation: fadeUp 0.9s 0.6s forwards;
}
.hero-title span { color: var(–orange); font-weight: 600; }

.typewriter-wrap {
margin-top: 32px; height: 36px;
display: flex; justify-content: center; align-items: center;
opacity: 0; animation: fadeUp 0.9s 0.8s forwards;
}
.typewriter {
font-family: ‘JetBrains Mono’, monospace; font-size: 20px; color: var(–orange);
font-weight: 600; border-right: 2px solid var(–orange);
white-space: nowrap; overflow: hidden;
animation: typing 3s steps(40) 1.5s forwards, blink 0.7s step-end infinite;
width: 0;
}
@keyframes typing { to { width: 38ch; } }
@keyframes blink { 50% { border-color: transparent; } }

.hero-cta {
margin-top: 48px; display: flex; gap: 16px; justify-content: center; flex-wrap: wrap;
opacity: 0; animation: fadeUp 0.9s 1s forwards;
}
.btn {
padding: 12px 28px; border-radius: 6px;
font-family: ‘JetBrains Mono’, monospace; font-size: 13px; font-weight: 600;
letter-spacing: 1px; text-decoration: none; cursor: none;
transition: transform 0.2s, box-shadow 0.2s;
}
.btn:hover { transform: translateY(-2px); }
.btn-primary {
background: var(–orange); color: #000;
box-shadow: 0 0 30px rgba(255,107,0,0.3);
}
.btn-primary:hover { box-shadow: 0 0 50px rgba(255,107,0,0.5); }
.btn-outline {
border: 1px solid #333; color: var(–text); background: transparent;
}
.btn-outline:hover { border-color: var(–orange); color: var(–orange); }

@keyframes fadeUp { from { opacity:0; transform:translateY(24px); } to { opacity:1; transform:translateY(0); } }

/* DIVIDER */
.divider {
display: flex; align-items: center; gap: 16px; margin: 80px 0 48px;
opacity: 0; transition: opacity 0.8s, transform 0.8s;
transform: translateY(20px);
}
.divider.visible { opacity: 1; transform: translateY(0); }
.divider-line { flex: 1; height: 1px; background: linear-gradient(90deg, transparent, var(–border)); }
.divider-line.right { background: linear-gradient(270deg, transparent, var(–border)); }
.divider-label {
font-family: ‘JetBrains Mono’, monospace; font-size: 11px;
letter-spacing: 3px; color: var(–orange); text-transform: uppercase;
}

/* ABOUT */
.about-card {
background: var(–surface); border: 1px solid var(–border); border-radius: 12px;
padding: 32px; position: relative; overflow: hidden;
opacity: 0; transition: opacity 0.8s, transform 0.8s; transform: translateY(20px);
}
.about-card.visible { opacity: 1; transform: translateY(0); }
.about-card::before {
content: ‘’;
position: absolute; top: 0; left: 0; right: 0; height: 1px;
background: linear-gradient(90deg, transparent, var(–orange), transparent);
}
.code-block {
font-family: ‘JetBrains Mono’, monospace; font-size: 14px; line-height: 1.8;
}
.code-ln { color: #333; user-select: none; margin-right: 20px; }
.code-key { color: #c792ea; }
.code-str { color: #c3e88d; }
.code-val { color: #82aaff; }
.code-arr { color: var(–orange); }
.code-bool { color: #f78c6c; }
.code-comment { color: #546e7a; font-style: italic; }

/* TECH */
.tech-grid {
display: grid; grid-template-columns: repeat(auto-fill, minmax(90px, 1fr)); gap: 12px;
}
.tech-item {
display: flex; flex-direction: column; align-items: center; justify-content: center;
gap: 8px; padding: 16px 8px;
background: var(–surface); border: 1px solid var(–border); border-radius: 10px;
font-family: ‘JetBrains Mono’, monospace; font-size: 11px; color: var(–muted);
transition: border-color 0.2s, transform 0.2s, color 0.2s;
cursor: none;
opacity: 0; transform: translateY(16px);
transition: opacity 0.5s, transform 0.5s, border-color 0.2s, color 0.2s;
}
.tech-item.visible { opacity: 1; transform: translateY(0); }
.tech-item:hover { border-color: var(–orange); color: var(–orange); transform: translateY(-4px) !important; }
.tech-item .icon { font-size: 28px; }

/* STATS */
.stats-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 16px; }
@media (max-width: 600px) { .stats-grid { grid-template-columns: 1fr; } }

.stat-card {
background: var(–surface); border: 1px solid var(–border); border-radius: 12px;
padding: 24px; position: relative; overflow: hidden;
opacity: 0; transform: translateY(20px); transition: opacity 0.7s, transform 0.7s;
}
.stat-card.visible { opacity: 1; transform: translateY(0); }
.stat-card::after {
content: ‘’; position: absolute; inset: 0;
background: radial-gradient(circle at 80% 20%, rgba(255,107,0,0.05), transparent 70%);
pointer-events: none;
}
.stat-img { width: 100%; border-radius: 8px; display: block; }

/* CONTACT */
.contact-row {
display: flex; gap: 16px; justify-content: center; flex-wrap: wrap;
opacity: 0; transform: translateY(20px); transition: opacity 0.8s, transform 0.8s;
}
.contact-row.visible { opacity: 1; transform: translateY(0); }
.contact-link {
display: flex; align-items: center; gap: 10px;
padding: 14px 24px; border: 1px solid var(–border); border-radius: 8px;
background: var(–surface); color: var(–text); text-decoration: none;
font-family: ‘JetBrains Mono’, monospace; font-size: 13px;
transition: border-color 0.2s, color 0.2s, transform 0.2s, box-shadow 0.2s;
cursor: none;
}
.contact-link:hover {
border-color: var(–orange); color: var(–orange);
transform: translateY(-3px);
box-shadow: 0 8px 24px rgba(255,107,0,0.15);
}

/* FOOTER */
footer {
text-align: center; padding: 60px 0 40px;
font-family: ‘JetBrains Mono’, monospace; font-size: 12px; color: #333;
}
footer span { color: var(–orange); }

/* SCROLL REVEAL base */
.reveal {
opacity: 0; transform: translateY(24px);
transition: opacity 0.8s ease, transform 0.8s ease;
}
.reveal.visible { opacity: 1; transform: translateY(0); }

/* Marquee */
.marquee-wrap { overflow: hidden; margin: 40px 0; mask: linear-gradient(90deg,transparent,black 15%,black 85%,transparent); }
.marquee {
display: flex; gap: 40px; width: max-content;
animation: marqueeScroll 18s linear infinite;
}
.marquee-item {
font-family: ‘JetBrains Mono’, monospace; font-size: 13px; color: #333;
white-space: nowrap; letter-spacing: 2px; text-transform: uppercase;
display: flex; align-items: center; gap: 16px;
}
.marquee-item::after { content:‘●’; color: var(–orange); font-size: 8px; }
@keyframes marqueeScroll { from { transform: translateX(0); } to { transform: translateX(-50%); } }

/* Section labels */
.section-num {
font-family: ‘JetBrains Mono’, monospace; font-size: 11px; color: var(–orange);
letter-spacing: 2px; margin-bottom: 6px;
}
.section-title {
font-size: 36px; font-weight: 700; margin-bottom: 32px;
background: linear-gradient(90deg, #fff, #666);
-webkit-background-clip: text; -webkit-text-fill-color: transparent;
background-clip: text;
}
</style>

</head>
<body>

<div class="cursor"><div class="cursor-dot" id="dot"></div><div class="cursor-ring" id="ring"></div></div>
<div class="orb orb1"></div>
<div class="orb orb2"></div>

<main>

  <!-- HERO -->

  <section class="hero">
    <div class="hero-badge"><span class="dot"></span>Available for opportunities</div>
    <h1 class="hero-name">CHOUAIB</h1>
    <p class="hero-title"><span>Full-Stack</span> · UI/UX · <span>Network Security</span></p>
    <div class="typewriter-wrap">
      <div class="typewriter">Building the Future, One Commit at a Time</div>
    </div>
    <div class="hero-cta">
      <a href="https://m-chouaib.eu.cc" class="btn btn-primary">VIEW PORTFOLIO →</a>
      <a href="mailto:m.chouaib.mohamed@gmail.com" class="btn btn-outline">GET IN TOUCH</a>
    </div>
  </section>

  <!-- MARQUEE -->

  <div class="marquee-wrap">
    <div class="marquee">
      <div class="marquee-item">React</div>
      <div class="marquee-item">Python</div>
      <div class="marquee-item">Java</div>
      <div class="marquee-item">TypeScript</div>
      <div class="marquee-item">MySQL</div>
      <div class="marquee-item">Linux</div>
      <div class="marquee-item">Zabbix</div>
      <div class="marquee-item">Docker</div>
      <div class="marquee-item">Figma</div>
      <div class="marquee-item">Machine Learning</div>
      <div class="marquee-item">DevOps</div>
      <div class="marquee-item">REST API</div>
      <!-- duplicate for seamless loop -->
      <div class="marquee-item">React</div>
      <div class="marquee-item">Python</div>
      <div class="marquee-item">Java</div>
      <div class="marquee-item">TypeScript</div>
      <div class="marquee-item">MySQL</div>
      <div class="marquee-item">Linux</div>
      <div class="marquee-item">Zabbix</div>
      <div class="marquee-item">Docker</div>
      <div class="marquee-item">Figma</div>
      <div class="marquee-item">Machine Learning</div>
      <div class="marquee-item">DevOps</div>
      <div class="marquee-item">REST API</div>
    </div>
  </div>

  <!-- ABOUT -->

  <div class="divider reveal"><div class="divider-line"></div><span class="divider-label">About Me</span><div class="divider-line right"></div></div>

  <div class="about-card reveal">
    <p class="section-num">// 01_ABOUT</p>
    <h2 class="section-title">Who Am I</h2>
    <div class="code-block">
      <div><span class="code-ln">1</span><span class="code-key">const</span> <span style="color:#fff">chouaib</span> = {</div>
      <div><span class="code-ln">2</span>&nbsp;&nbsp;<span class="code-key">location</span>  : <span class="code-str">"Morocco 🇲🇦"</span>,</div>
      <div><span class="code-ln">3</span>&nbsp;&nbsp;<span class="code-key">roles</span>     : <span class="code-arr">[</span><span class="code-str">"Full-Stack Developer"</span>, <span class="code-str">"UI/UX Designer"</span>, <span class="code-str">"NetOps Engineer"</span><span class="code-arr">]</span>,</div>
      <div><span class="code-ln">4</span>&nbsp;&nbsp;<span class="code-key">stack</span>     : <span class="code-arr">[</span><span class="code-str">"React"</span>, <span class="code-str">"Python"</span>, <span class="code-str">"Java"</span>, <span class="code-str">"MySQL"</span>, <span class="code-str">"Linux"</span><span class="code-arr">]</span>,</div>
      <div><span class="code-ln">5</span>&nbsp;&nbsp;<span class="code-key">exploring</span> : <span class="code-arr">[</span><span class="code-str">"Zabbix"</span>, <span class="code-str">"Machine Learning"</span>, <span class="code-str">"DevOps"</span>, <span class="code-str">"Cloud"</span><span class="code-arr">]</span>,</div>
      <div><span class="code-ln">6</span>&nbsp;&nbsp;<span class="code-key">available</span> : <span class="code-bool">true</span>,</div>
      <div><span class="code-ln">7</span>&nbsp;&nbsp;<span class="code-key">motto</span>     : <span class="code-str">"Clean code. Creative solutions. No limits."</span></div>
      <div><span class="code-ln">8</span>};</div>
      <div>&nbsp;</div>
      <div><span class="code-ln">9</span><span class="code-comment">// 💡 I don't just write code — I craft experiences.</span></div>
      <div><span class="code-ln">10</span><span class="code-comment">// 🧠 Obsessed with performance, design, and scalable architecture.</span></div>
      <div><span class="code-ln">11</span><span class="code-comment">// 🌍 Open to collaborations, freelance & exciting new challenges.</span></div>
    </div>
  </div>

  <!-- TECH -->

  <div class="divider reveal"><div class="divider-line"></div><span class="divider-label">Tech Arsenal</span><div class="divider-line right"></div></div>

  <p class="section-num reveal">// 02_STACK</p>
  <h2 class="section-title reveal">Tech Arsenal</h2>

  <div class="tech-grid" id="techGrid">
    <div class="tech-item"><span class="icon">🐍</span>Python</div>
    <div class="tech-item"><span class="icon">☕</span>Java</div>
    <div class="tech-item"><span class="icon">🌐</span>JavaScript</div>
    <div class="tech-item"><span class="icon">🔷</span>TypeScript</div>
    <div class="tech-item"><span class="icon">⚛️</span>React</div>
    <div class="tech-item"><span class="icon">🏗️</span>HTML5</div>
    <div class="tech-item"><span class="icon">🎨</span>CSS3</div>
    <div class="tech-item"><span class="icon">🐧</span>Linux</div>
    <div class="tech-item"><span class="icon">🔧</span>Git</div>
    <div class="tech-item"><span class="icon">🗄️</span>MySQL</div>
    <div class="tech-item"><span class="icon">🐳</span>Docker</div>
    <div class="tech-item"><span class="icon">✏️</span>Figma</div>
    <div class="tech-item"><span class="icon">💻</span>VSCode</div>
    <div class="tech-item"><span class="icon">📡</span>Zabbix</div>
  </div>

  <!-- STATS -->

  <div class="divider reveal"><div class="divider-line"></div><span class="divider-label">GitHub Stats</span><div class="divider-line right"></div></div>

  <p class="section-num reveal">// 03_STATS</p>
  <h2 class="section-title reveal">GitHub Intelligence</h2>

  <div class="stats-grid">
    <div class="stat-card">
      <img class="stat-img" src="https://github-readme-stats.vercel.app/api?username=m-chouaib-0&show_icons=true&hide_border=true&bg_color=111111&title_color=FF6B00&icon_color=FF6B00&text_color=FFFFFF&ring_color=FF6B00&include_all_commits=true&count_private=true" alt="GitHub Stats" loading="lazy" />
    </div>
    <div class="stat-card" style="transition-delay:0.1s">
      <img class="stat-img" src="https://streak-stats.demolab.com?user=m-chouaib-0&hide_border=true&background=111111&ring=FF6B00&fire=FF6B00&currStreakLabel=FF6B00&sideLabels=FFFFFF&dates=888888&currStreakNum=FFFFFF&sideNums=FFFFFF" alt="Streak Stats" loading="lazy" />
    </div>
    <div class="stat-card" style="grid-column: 1/-1; transition-delay:0.2s">
      <img class="stat-img" src="https://github-readme-activity-graph.vercel.app/graph?username=m-chouaib-0&bg_color=111111&color=FF6B00&line=FF6B00&point=FFFFFF&area_color=FF6B00&area=true&hide_border=true&custom_title=Contribution+Graph" alt="Contribution Graph" loading="lazy" />
    </div>
  </div>

  <!-- CONTACT -->

  <div class="divider reveal"><div class="divider-line"></div><span class="divider-label">Connect</span><div class="divider-line right"></div></div>

  <p class="section-num reveal">// 04_CONNECT</p>
  <h2 class="section-title reveal" style="text-align:center">Let's Build Something</h2>

  <div class="contact-row reveal">
    <a href="https://linkedin.com/in/mohamed-chouaib" class="contact-link">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
      LinkedIn
    </a>
    <a href="https://m-chouaib.eu.cc" class="contact-link">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><circle cx="12" cy="12" r="10"/><path d="M2 12h20M12 2a15.3 15.3 0 0 1 4 10 15.3 15.3 0 0 1-4 10 15.3 15.3 0 0 1-4-10 15.3 15.3 0 0 1 4-10z"/></svg>
      Portfolio
    </a>
    <a href="mailto:m.chouaib.mohamed@gmail.com" class="contact-link">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"/><polyline points="22,6 12,13 2,6"/></svg>
      Email Me
    </a>
    <a href="https://github.com/m-chouaib-0" class="contact-link">
      <svg width="18" height="18" viewBox="0 0 24 24" fill="currentColor"><path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/></svg>
      GitHub
    </a>
  </div>

  <!-- FOOTER -->

  <footer>
    <p>🔥 <span>"Clean code. Creative solutions. No limits."</span> 🔥</p>
    <p style="margin-top:8px; font-size:11px;">Built with passion · Morocco 🇲🇦 · © 2025 Mohamed Chouaib</p>
  </footer>

</main>

<script>
  // Smooth cursor
  const dot = document.getElementById('dot');
  const ring = document.getElementById('ring');
  let mx = 0, my = 0, rx = 0, ry = 0;
  document.addEventListener('mousemove', e => { mx = e.clientX; my = e.clientY; dot.style.left = mx + 'px'; dot.style.top = my + 'px'; });
  function animRing() { rx += (mx - rx) * 0.12; ry += (my - ry) * 0.12; ring.style.left = rx + 'px'; ring.style.top = ry + 'px'; requestAnimationFrame(animRing); }
  animRing();

  // Cursor scale on hover
  document.querySelectorAll('a, button, .tech-item').forEach(el => {
    el.addEventListener('mouseenter', () => { ring.style.width = '56px'; ring.style.height = '56px'; ring.style.opacity = '0.8'; });
    el.addEventListener('mouseleave', () => { ring.style.width = '36px'; ring.style.height = '36px'; ring.style.opacity = '0.5'; });
  });

  // Scroll reveal
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => { if (e.isIntersecting) { e.target.classList.add('visible'); } });
  }, { threshold: 0.12 });

  document.querySelectorAll('.reveal, .divider, .about-card, .stat-card, .contact-row').forEach(el => observer.observe(el));

  // Tech items staggered reveal
  const techObs = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if (e.isIntersecting) {
        const items = e.target.querySelectorAll('.tech-item');
        items.forEach((item, i) => {
          setTimeout(() => item.classList.add('visible'), i * 50);
        });
        techObs.unobserve(e.target);
      }
    });
  }, { threshold: 0.1 });
  const grid = document.getElementById('techGrid');
  if (grid) techObs.observe(grid);
</script>

</body>
</html>
