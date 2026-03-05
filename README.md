<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Joslin Joseph – GitHub Profile</title>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700;900&family=Rajdhani:wght@300;400;600&family=Share+Tech+Mono&display=swap" rel="stylesheet">
<style>
  :root {
    --crimson: #8B0000;
    --red: #C0000C;
    --bright-red: #FF1A1A;
    --arc: #FF4444;
    --gold: #C9922A;
    --gold-light: #FFD060;
    --bg: #050505;
    --bg2: #0A0000;
    --panel: #0f0303;
    --border: rgba(180,20,20,0.4);
    --glow: rgba(200,0,0,0.6);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: #ddd;
    font-family: 'Rajdhani', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
    position: relative;
  }

  /* === SCANLINES === */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.08) 2px,
      rgba(0,0,0,0.08) 4px
    );
    pointer-events: none;
    z-index: 100;
  }

  /* === CIRCUIT BACKGROUND === */
  .circuit-bg {
    position: fixed;
    inset: 0;
    z-index: 0;
    overflow: hidden;
    opacity: 0.12;
  }
  .circuit-bg svg { width: 100%; height: 100%; }

  /* === PARTICLE FIELD === */
  #particles {
    position: fixed;
    inset: 0;
    z-index: 1;
    pointer-events: none;
  }

  .wrapper {
    position: relative;
    z-index: 10;
    max-width: 860px;
    margin: 0 auto;
    padding: 30px 20px 60px;
  }

  /* === ARC REACTOR HEADER === */
  .hero {
    text-align: center;
    padding: 60px 0 40px;
    position: relative;
  }

  .arc-reactor {
    width: 90px;
    height: 90px;
    margin: 0 auto 30px;
    position: relative;
  }

  .arc-outer {
    width: 90px;
    height: 90px;
    border-radius: 50%;
    border: 2px solid var(--gold);
    position: absolute;
    top: 0; left: 0;
    animation: spin 8s linear infinite;
    box-shadow: 0 0 20px var(--gold), inset 0 0 20px rgba(201,146,42,0.1);
  }

  .arc-middle {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    border: 2px solid var(--arc);
    position: absolute;
    top: 15px; left: 15px;
    animation: spin-rev 5s linear infinite;
    box-shadow: 0 0 15px var(--arc);
  }

  .arc-inner {
    width: 34px;
    height: 34px;
    border-radius: 50%;
    background: radial-gradient(circle, #fff 0%, #88DDFF 20%, #44AAFF 50%, #0044AA 80%);
    position: absolute;
    top: 28px; left: 28px;
    animation: pulse-arc 2s ease-in-out infinite;
    box-shadow: 0 0 30px #44AAFF, 0 0 60px rgba(68,170,255,0.5);
  }

  .arc-dot1, .arc-dot2, .arc-dot3, .arc-dot4 {
    width: 8px; height: 8px;
    background: var(--gold);
    border-radius: 50%;
    position: absolute;
    box-shadow: 0 0 8px var(--gold-light);
  }
  .arc-dot1 { top: -4px; left: 41px; }
  .arc-dot2 { bottom: -4px; left: 41px; }
  .arc-dot3 { left: -4px; top: 41px; }
  .arc-dot4 { right: -4px; top: 41px; }

  @keyframes spin { to { transform: rotate(360deg); } }
  @keyframes spin-rev { to { transform: rotate(-360deg); } }
  @keyframes pulse-arc {
    0%, 100% { box-shadow: 0 0 30px #44AAFF, 0 0 60px rgba(68,170,255,0.5); }
    50% { box-shadow: 0 0 50px #88DDFF, 0 0 100px rgba(68,170,255,0.8); }
  }

  .hero-name {
    font-family: 'Orbitron', monospace;
    font-size: clamp(28px, 5vw, 48px);
    font-weight: 900;
    letter-spacing: 4px;
    background: linear-gradient(135deg, var(--gold-light) 0%, var(--arc) 50%, var(--gold) 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    animation: text-shimmer 3s ease-in-out infinite;
    text-shadow: none;
    filter: drop-shadow(0 0 15px rgba(255,100,100,0.6));
  }

  @keyframes text-shimmer {
    0%, 100% { filter: drop-shadow(0 0 15px rgba(255,100,100,0.6)); }
    50% { filter: drop-shadow(0 0 30px rgba(255,200,50,0.8)); }
  }

  .hero-title {
    font-family: 'Share Tech Mono', monospace;
    font-size: 13px;
    color: var(--gold);
    letter-spacing: 6px;
    margin-top: 8px;
    opacity: 0.85;
    animation: blink-line 4s steps(1) infinite;
  }

  @keyframes blink-line {
    0%, 90%, 100% { opacity: 0.85; }
    92%, 98% { opacity: 0.3; }
  }

  .typing-line {
    font-family: 'Share Tech Mono', monospace;
    font-size: 15px;
    color: var(--arc);
    margin-top: 16px;
    letter-spacing: 2px;
    min-height: 24px;
  }

  .typing-cursor {
    display: inline-block;
    width: 2px;
    height: 16px;
    background: var(--arc);
    margin-left: 3px;
    vertical-align: middle;
    animation: blink 0.7s step-end infinite;
  }
  @keyframes blink { 50% { opacity: 0; } }

  /* === HUD DIVIDER === */
  .hud-divider {
    display: flex;
    align-items: center;
    gap: 12px;
    margin: 30px 0;
    opacity: 0.7;
  }
  .hud-line {
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--red), transparent);
    position: relative;
  }
  .hud-diamond {
    width: 8px; height: 8px;
    background: var(--gold);
    transform: rotate(45deg);
    box-shadow: 0 0 8px var(--gold);
    flex-shrink: 0;
  }

  /* === SECTION PANELS === */
  .section {
    margin-bottom: 32px;
    animation: fade-in 0.6s ease both;
  }

  .panel {
    background: linear-gradient(135deg, rgba(30,0,0,0.7) 0%, rgba(10,0,0,0.9) 100%);
    border: 1px solid var(--border);
    border-radius: 2px;
    padding: 24px;
    position: relative;
    clip-path: polygon(0 0, calc(100% - 16px) 0, 100% 16px, 100% 100%, 16px 100%, 0 calc(100% - 16px));
    box-shadow: 0 0 30px rgba(180,0,0,0.1), inset 0 0 30px rgba(100,0,0,0.05);
    transition: box-shadow 0.3s;
  }

  .panel:hover {
    box-shadow: 0 0 50px rgba(200,0,0,0.2), inset 0 0 30px rgba(100,0,0,0.1);
    border-color: rgba(255,50,50,0.5);
  }

  .panel::before {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--arc), var(--gold), var(--arc), transparent);
    opacity: 0.6;
    animation: scan-line 3s linear infinite;
  }

  @keyframes scan-line {
    0% { opacity: 0.3; }
    50% { opacity: 0.8; }
    100% { opacity: 0.3; }
  }

  .corner-tl, .corner-br {
    position: absolute;
    width: 12px; height: 12px;
  }
  .corner-tl { top: 4px; left: 4px; border-top: 2px solid var(--gold); border-left: 2px solid var(--gold); }
  .corner-br { bottom: 4px; right: 4px; border-bottom: 2px solid var(--gold); border-right: 2px solid var(--gold); }

  .section-label {
    font-family: 'Orbitron', monospace;
    font-size: 11px;
    letter-spacing: 5px;
    color: var(--gold);
    opacity: 0.7;
    margin-bottom: 4px;
    text-transform: uppercase;
  }

  .section-title {
    font-family: 'Orbitron', monospace;
    font-size: 18px;
    font-weight: 700;
    color: var(--arc);
    letter-spacing: 2px;
    margin-bottom: 20px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .section-title::after {
    content: '';
    flex: 1;
    height: 1px;
    background: linear-gradient(90deg, var(--border), transparent);
  }

  /* === ABOUT === */
  .about-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .about-item {
    background: rgba(180,0,0,0.06);
    border: 1px solid rgba(180,0,0,0.2);
    border-left: 3px solid var(--red);
    padding: 10px 14px;
    font-size: 14px;
    color: #ccc;
    letter-spacing: 1px;
    transition: background 0.3s, border-left-color 0.3s;
  }
  .about-item:hover {
    background: rgba(180,0,0,0.12);
    border-left-color: var(--gold);
    color: #fff;
  }
  .about-item span { color: var(--gold); font-weight: 600; }

  /* === SKILLS BADGES === */
  .badge-group {
    margin-bottom: 16px;
  }
  .badge-group-title {
    font-family: 'Share Tech Mono', monospace;
    font-size: 11px;
    color: var(--gold);
    letter-spacing: 3px;
    margin-bottom: 10px;
    opacity: 0.8;
  }
  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  .badge {
    background: linear-gradient(135deg, rgba(100,0,0,0.4), rgba(50,0,0,0.6));
    border: 1px solid rgba(200,0,0,0.4);
    color: #eee;
    font-family: 'Orbitron', monospace;
    font-size: 10px;
    letter-spacing: 1.5px;
    padding: 6px 14px;
    clip-path: polygon(8px 0, 100% 0, calc(100% - 8px) 100%, 0 100%);
    transition: all 0.3s;
    cursor: default;
    position: relative;
    overflow: hidden;
  }

  .badge::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, transparent 40%, rgba(255,200,50,0.1));
    opacity: 0;
    transition: opacity 0.3s;
  }

  .badge:hover {
    background: linear-gradient(135deg, rgba(200,0,0,0.5), rgba(100,0,0,0.8));
    border-color: var(--gold);
    color: var(--gold-light);
    box-shadow: 0 0 15px rgba(200,0,0,0.4);
    transform: translateY(-2px);
  }
  .badge:hover::before { opacity: 1; }

  /* === STATS === */
  .stats-row {
    display: flex;
    gap: 16px;
    flex-wrap: wrap;
  }

  .stat-card {
    flex: 1;
    min-width: 120px;
    background: rgba(100,0,0,0.08);
    border: 1px solid var(--border);
    border-radius: 1px;
    padding: 16px;
    text-align: center;
    position: relative;
    overflow: hidden;
    transition: all 0.3s;
  }

  .stat-card::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    height: 2px;
    background: var(--red);
    transform: scaleX(0);
    transition: transform 0.3s;
    transform-origin: left;
  }
  .stat-card:hover::after { transform: scaleX(1); }
  .stat-card:hover { background: rgba(150,0,0,0.12); }

  .stat-num {
    font-family: 'Orbitron', monospace;
    font-size: 28px;
    font-weight: 900;
    color: var(--arc);
    display: block;
    animation: count-pulse 3s ease-in-out infinite;
  }
  @keyframes count-pulse {
    0%, 100% { text-shadow: 0 0 10px var(--glow); }
    50% { text-shadow: 0 0 25px var(--glow), 0 0 40px rgba(255,0,0,0.3); }
  }
  .stat-label {
    font-family: 'Share Tech Mono', monospace;
    font-size: 10px;
    color: var(--gold);
    letter-spacing: 2px;
    margin-top: 4px;
    opacity: 0.7;
  }

  /* === PROJECTS === */
  .project-list { display: flex; flex-direction: column; gap: 10px; }

  .project-item {
    display: flex;
    align-items: flex-start;
    gap: 14px;
    padding: 12px 16px;
    background: rgba(100,0,0,0.06);
    border-left: 3px solid var(--crimson);
    border-bottom: 1px solid rgba(180,0,0,0.15);
    transition: all 0.3s;
    cursor: default;
  }

  .project-item:hover {
    background: rgba(180,0,0,0.1);
    border-left-color: var(--gold);
    padding-left: 22px;
  }

  .project-icon {
    font-size: 20px;
    flex-shrink: 0;
    filter: drop-shadow(0 0 6px var(--red));
  }

  .project-name {
    font-family: 'Orbitron', monospace;
    font-size: 13px;
    color: var(--arc);
    letter-spacing: 1px;
    margin-bottom: 3px;
  }

  .project-desc {
    font-size: 13px;
    color: #999;
    letter-spacing: 0.5px;
  }

  /* === STATUS BAR === */
  .status-bar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 8px 16px;
    background: rgba(100,0,0,0.1);
    border: 1px solid var(--border);
    font-family: 'Share Tech Mono', monospace;
    font-size: 11px;
    color: var(--gold);
    letter-spacing: 2px;
    margin-bottom: 32px;
    opacity: 0.8;
  }

  .status-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
    background: #00ff88;
    display: inline-block;
    margin-right: 8px;
    box-shadow: 0 0 8px #00ff88;
    animation: pulse-green 2s ease-in-out infinite;
  }
  @keyframes pulse-green {
    0%, 100% { opacity: 1; }
    50% { opacity: 0.3; }
  }

  /* === FOOTER === */
  .footer {
    text-align: center;
    padding: 30px 0 10px;
    font-family: 'Share Tech Mono', monospace;
    font-size: 12px;
    color: rgba(200, 80, 80, 0.5);
    letter-spacing: 3px;
  }

  .footer-quote {
    font-family: 'Orbitron', monospace;
    font-size: 13px;
    color: var(--gold);
    opacity: 0.6;
    margin-bottom: 8px;
    letter-spacing: 2px;
  }

  @keyframes fade-in {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  .section:nth-child(1) { animation-delay: 0.1s; }
  .section:nth-child(2) { animation-delay: 0.2s; }
  .section:nth-child(3) { animation-delay: 0.3s; }
  .section:nth-child(4) { animation-delay: 0.4s; }
  .section:nth-child(5) { animation-delay: 0.5s; }

  /* === RESPONSIVE === */
  @media (max-width: 600px) {
    .about-grid { grid-template-columns: 1fr; }
    .stats-row { flex-direction: column; }
  }
</style>
</head>
<body>

<!-- CIRCUIT BACKGROUND -->
<div class="circuit-bg">
  <svg viewBox="0 0 1200 800" preserveAspectRatio="xMidYMid slice">
    <defs>
      <filter id="glow"><feGaussianBlur stdDeviation="2" result="blur"/><feMerge><feMergeNode in="blur"/><feMergeNode in="SourceGraphic"/></feMerge></filter>
    </defs>
    <g filter="url(#glow)" stroke="#8B0000" stroke-width="1" fill="none">
      <line x1="0" y1="200" x2="300" y2="200"/><line x1="300" y1="200" x2="350" y2="150"/><line x1="350" y1="150" x2="600" y2="150"/>
      <line x1="600" y1="150" x2="650" y2="200"/><line x1="650" y1="200" x2="1200" y2="200"/>
      <line x1="0" y1="500" x2="200" y2="500"/><line x1="200" y1="500" x2="250" y2="450"/><line x1="250" y1="450" x2="500" y2="450"/>
      <line x1="500" y1="450" x2="550" y2="500"/><line x1="550" y1="500" x2="700" y2="500"/><line x1="700" y1="500" x2="750" y2="550"/><line x1="750" y1="550" x2="1200" y2="550"/>
      <line x1="100" y1="0" x2="100" y2="200"/><line x1="400" y1="0" x2="400" y2="150"/><line x1="700" y1="0" x2="700" y2="200"/>
      <line x1="200" y1="800" x2="200" y2="500"/><line x1="500" y1="800" x2="500" y2="450"/><line x1="800" y1="800" x2="800" y2="550"/>
      <circle cx="350" cy="150" r="4" fill="#8B0000"/><circle cx="600" cy="150" r="4" fill="#8B0000"/>
      <circle cx="250" cy="450" r="4" fill="#8B0000"/><circle cx="700" cy="500" r="4" fill="#8B0000"/>
      <rect x="96" y="196" width="8" height="8" fill="#8B0000"/>
      <rect x="396" y="146" width="8" height="8" fill="#8B0000"/>
    </g>
    <g stroke="rgba(201,146,42,0.5)" stroke-width="0.5" fill="none">
      <line x1="1000" y1="0" x2="1000" y2="800"/>
      <line x1="0" y1="700" x2="1200" y2="700"/>
      <circle cx="1000" cy="700" r="20"/>
      <circle cx="1000" cy="700" r="35" stroke-dasharray="5,10"/>
    </g>
  </svg>
</div>

<canvas id="particles"></canvas>

<div class="wrapper">

  <!-- STATUS BAR -->
  <div class="status-bar">
    <span><span class="status-dot"></span>JARVIS ONLINE</span>
    <span>USER: JOSLIN_JOSEPH</span>
    <span>SUIT: MARK_VII</span>
  </div>

  <!-- HERO -->
  <div class="hero section">
    <div class="arc-reactor">
      <div class="arc-outer"></div>
      <div class="arc-middle"></div>
      <div class="arc-inner"></div>
      <div class="arc-dot1"></div>
      <div class="arc-dot2"></div>
      <div class="arc-dot3"></div>
      <div class="arc-dot4"></div>
    </div>

    <h1 class="hero-name">JOSLIN JOSEPH</h1>
    <div class="hero-title">⚡ ELECTRICAL & ELECTRONICS ENGINEER ⚡</div>
    <div class="typing-line" id="typing"></div>
  </div>

  <div class="hud-divider"><div class="hud-line"></div><div class="hud-diamond"></div><div class="hud-line"></div></div>

  <!-- ABOUT -->
  <div class="section">
    <div class="panel">
      <div class="corner-tl"></div><div class="corner-br"></div>
      <div class="section-label">// MODULE_01</div>
      <div class="section-title">⚙ SYSTEM PROFILE</div>
      <div class="about-grid">
        <div class="about-item">🔬 <span>DOMAIN:</span> Embedded Systems</div>
        <div class="about-item">🤖 <span>FIELD:</span> IoT & Robotics</div>
        <div class="about-item">🌾 <span>PROJECT:</span> Smart Agriculture</div>
        <div class="about-item">⚡ <span>FOCUS:</span> Hardware Innovation</div>
        <div class="about-item">🧠 <span>AI EDGE:</span> Embedded AI Devices</div>
        <div class="about-item">🛰 <span>MODE:</span> Builder & Maker</div>
      </div>
    </div>
  </div>

  <!-- TECH STACK -->
  <div class="section">
    <div class="panel">
      <div class="corner-tl"></div><div class="corner-br"></div>
      <div class="section-label">// MODULE_02</div>
      <div class="section-title">🛠 TECH ARSENAL</div>

      <div class="badge-group">
        <div class="badge-group-title">▶ EMBEDDED & HARDWARE</div>
        <div class="badges">
          <div class="badge">EMBEDDED SYS</div>
          <div class="badge">ARDUINO</div>
          <div class="badge">ESP32</div>
          <div class="badge">IoT</div>
          <div class="badge">ROBOTICS</div>
        </div>
      </div>

      <div class="badge-group">
        <div class="badge-group-title">▶ PROGRAMMING</div>
        <div class="badges">
          <div class="badge">PYTHON</div>
          <div class="badge">C</div>
          <div class="badge">HTML</div>
          <div class="badge">CSS</div>
          <div class="badge">JAVASCRIPT</div>
        </div>
      </div>
    </div>
  </div>

  <!-- STATS -->
  <div class="section">
    <div class="panel">
      <div class="corner-tl"></div><div class="corner-br"></div>
      <div class="section-label">// MODULE_03</div>
      <div class="section-title">📊 PERFORMANCE DATA</div>
      <div class="stats-row">
        <div class="stat-card"><span class="stat-num" id="cnt1">0</span><div class="stat-label">COMMITS</div></div>
        <div class="stat-card"><span class="stat-num" id="cnt2">0</span><div class="stat-label">REPOS</div></div>
        <div class="stat-card"><span class="stat-num" id="cnt3">0</span><div class="stat-label">STREAK</div></div>
        <div class="stat-card"><span class="stat-num" id="cnt4">0</span><div class="stat-label">PROJECTS</div></div>
      </div>
      <br>
      <p style="text-align:center;font-family:'Share Tech Mono';font-size:12px;color:#666;letter-spacing:2px;">[ Live stats auto-load via GitHub API in actual README ]</p>
    </div>
  </div>

  <!-- CURRENT BUILDS -->
  <div class="section">
    <div class="panel">
      <div class="corner-tl"></div><div class="corner-br"></div>
      <div class="section-label">// MODULE_04</div>
      <div class="section-title">🚀 ACTIVE MISSIONS</div>
      <div class="project-list">
        <div class="project-item"><div class="project-icon">🤖</div><div><div class="project-name">AUTONOMOUS INSPECTION ROBOT</div><div class="project-desc">Self-navigating inspection unit with real-time sensor fusion</div></div></div>
        <div class="project-item"><div class="project-icon">🌾</div><div><div class="project-name">SMART AGRICULTURE AUTOMATION</div><div class="project-desc">AI-powered soil & crop monitoring with IoT sensor arrays</div></div></div>
        <div class="project-item"><div class="project-icon">🧠</div><div><div class="project-name">EMBEDDED AI EDGE DEVICES</div><div class="project-desc">Running neural inference on microcontrollers at the edge</div></div></div>
      </div>
    </div>
  </div>

  <div class="hud-divider"><div class="hud-line"></div><div class="hud-diamond"></div><div class="hud-line"></div></div>

  <!-- FOOTER -->
  <div class="footer section">
    <div class="footer-quote">"Part genius. Part billionaire. Full engineer."</div>
    ⚡ BUILDING HARDWARE THAT SOLVES REAL-WORLD PROBLEMS ⚡
  </div>

</div>

<script>
  // === PARTICLES ===
  const canvas = document.getElementById('particles');
  const ctx = canvas.getContext('2d');
  canvas.width = window.innerWidth;
  canvas.height = window.innerHeight;

  const particles = Array.from({length: 60}, () => ({
    x: Math.random() * canvas.width,
    y: Math.random() * canvas.height,
    vx: (Math.random() - 0.5) * 0.4,
    vy: (Math.random() - 0.5) * 0.4,
    size: Math.random() * 1.5 + 0.3,
    alpha: Math.random() * 0.4 + 0.1,
    color: Math.random() > 0.7 ? '#C9922A' : '#C0000C'
  }));

  function drawParticles() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    particles.forEach(p => {
      ctx.beginPath();
      ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
      ctx.fillStyle = p.color;
      ctx.globalAlpha = p.alpha;
      ctx.fill();
      p.x += p.vx; p.y += p.vy;
      if (p.x < 0) p.x = canvas.width;
      if (p.x > canvas.width) p.x = 0;
      if (p.y < 0) p.y = canvas.height;
      if (p.y > canvas.height) p.y = 0;
    });
    ctx.globalAlpha = 1;
    requestAnimationFrame(drawParticles);
  }
  drawParticles();

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;
  });

  // === TYPING EFFECT ===
  const lines = [
    'EMBEDDED SYSTEMS DEVELOPER',
    'IoT ARCHITECT',
    'HARDWARE INNOVATOR',
    'SMART AGRICULTURE BUILDER',
    'EDGE AI ENGINEER'
  ];
  let li = 0, ci = 0, deleting = false;
  const el = document.getElementById('typing');

  function type() {
    const cur = lines[li];
    if (!deleting) {
      el.innerHTML = cur.slice(0, ci + 1) + '<span class="typing-cursor"></span>';
      ci++;
      if (ci === cur.length) { deleting = true; setTimeout(type, 2000); return; }
    } else {
      el.innerHTML = cur.slice(0, ci - 1) + '<span class="typing-cursor"></span>';
      ci--;
      if (ci === 0) { deleting = false; li = (li + 1) % lines.length; setTimeout(type, 400); return; }
    }
    setTimeout(type, deleting ? 40 : 70);
  }
  setTimeout(type, 1000);

  // === COUNTER ANIMATION ===
  function animateCount(el, target, dur) {
    let start = 0, startTime = null;
    function step(ts) {
      if (!startTime) startTime = ts;
      const progress = Math.min((ts - startTime) / dur, 1);
      el.textContent = Math.floor(progress * target);
      if (progress < 1) requestAnimationFrame(step);
      else el.textContent = target;
    }
    requestAnimationFrame(step);
  }

  setTimeout(() => {
    animateCount(document.getElementById('cnt1'), 128, 1500);
    animateCount(document.getElementById('cnt2'), 14, 1200);
    animateCount(document.getElementById('cnt3'), 31, 1300);
    animateCount(document.getElementById('cnt4'), 7, 1000);
  }, 800);
</script>

</body>
</html>
