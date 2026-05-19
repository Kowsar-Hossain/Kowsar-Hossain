<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Kowsar Hossain — Full Stack Developer</title>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #090d13;
    --surface: #0f1520;
    --card: #131c2a;
    --border: #1e2d40;
    --accent: #00e5ff;
    --accent2: #7c5cfc;
    --accent3: #ff6b6b;
    --text: #e8edf5;
    --muted: #6b7f96;
    --glow: rgba(0,229,255,0.18);
    --glow2: rgba(124,92,252,0.15);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── NOISE OVERLAY ── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    pointer-events: none; z-index: 0; opacity: 0.5;
  }

  /* ── GRID ── */
  .page {
    display: grid;
    grid-template-columns: 1fr 1fr;
    min-height: 100vh;
    position: relative;
    z-index: 1;
  }

  /* ═══════════════════════════
     LEFT SIDE
  ═══════════════════════════ */
  .left {
    padding: 60px 48px 60px 56px;
    display: flex;
    flex-direction: column;
    gap: 40px;
    position: relative;
    overflow: hidden;
  }

  .left::after {
    content: '';
    position: absolute;
    right: 0; top: 0; bottom: 0;
    width: 1px;
    background: linear-gradient(to bottom, transparent, var(--border) 20%, var(--border) 80%, transparent);
  }

  /* STATUS BADGE */
  .badge {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,229,255,0.07);
    border: 1px solid rgba(0,229,255,0.2);
    border-radius: 100px;
    padding: 6px 14px;
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    color: var(--accent);
    width: fit-content;
    animation: fadeSlideIn 0.6s ease forwards;
  }
  .badge-dot {
    width: 7px; height: 7px;
    border-radius: 50%;
    background: var(--accent);
    box-shadow: 0 0 8px var(--accent);
    animation: pulse 2s ease infinite;
  }

  /* HERO TEXT */
  .hero-text { animation: fadeSlideIn 0.7s 0.1s ease both; }
  .hero-text h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(2.4rem, 4vw, 3.6rem);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -0.03em;
  }
  .hero-text h1 span {
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .role-line {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-top: 14px;
    font-family: 'Space Mono', monospace;
    font-size: 13px;
    color: var(--muted);
  }
  .role-line::before {
    content: '';
    flex: 0 0 32px;
    height: 1px;
    background: var(--accent);
    opacity: 0.5;
  }

  /* BIO */
  .bio {
    font-size: 15px;
    line-height: 1.75;
    color: #a0b0c5;
    animation: fadeSlideIn 0.7s 0.2s ease both;
  }

  /* SKILLS */
  .skills-section { animation: fadeSlideIn 0.7s 0.3s ease both; }
  .section-label {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    letter-spacing: 0.2em;
    color: var(--muted);
    text-transform: uppercase;
    margin-bottom: 16px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  .skill-group { margin-bottom: 20px; }
  .skill-group-title {
    font-size: 11px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    margin-bottom: 10px;
    opacity: 0.7;
  }
  .skill-pills {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }
  .pill {
    display: flex;
    align-items: center;
    gap: 6px;
    padding: 5px 12px;
    border-radius: 6px;
    background: var(--card);
    border: 1px solid var(--border);
    font-size: 12px;
    font-weight: 500;
    color: var(--text);
    transition: all 0.25s;
    cursor: default;
  }
  .pill:hover {
    border-color: var(--accent);
    background: rgba(0,229,255,0.05);
    transform: translateY(-2px);
    box-shadow: 0 4px 16px rgba(0,229,255,0.1);
  }
  .pill-dot {
    width: 6px; height: 6px;
    border-radius: 50%;
  }

  /* SOCIAL */
  .socials {
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    animation: fadeSlideIn 0.7s 0.4s ease both;
  }
  .social-btn {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 9px 16px;
    border-radius: 8px;
    border: 1px solid var(--border);
    background: var(--card);
    color: var(--text);
    text-decoration: none;
    font-size: 12px;
    font-family: 'Space Mono', monospace;
    transition: all 0.25s;
  }
  .social-btn:hover {
    border-color: var(--accent2);
    background: rgba(124,92,252,0.08);
    transform: translateY(-2px);
    box-shadow: 0 6px 20px rgba(124,92,252,0.15);
    color: #fff;
  }
  .social-btn svg { flex-shrink: 0; }

  /* ═══════════════════════════
     RIGHT SIDE
  ═══════════════════════════ */
  .right {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    background: radial-gradient(ellipse 60% 60% at 60% 40%, rgba(124,92,252,0.08) 0%, transparent 70%);
  }

  /* BG GLOW BLOBS */
  .blob {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
  }
  .blob-1 {
    width: 380px; height: 380px;
    background: radial-gradient(circle, rgba(0,229,255,0.15), transparent 70%);
    top: -60px; right: -60px;
    animation: floatBlob 9s ease-in-out infinite;
  }
  .blob-2 {
    width: 300px; height: 300px;
    background: radial-gradient(circle, rgba(124,92,252,0.18), transparent 70%);
    bottom: -40px; left: -40px;
    animation: floatBlob 11s 2s ease-in-out infinite reverse;
  }
  .blob-3 {
    width: 200px; height: 200px;
    background: radial-gradient(circle, rgba(255,107,107,0.1), transparent 70%);
    top: 50%; right: 30px;
    animation: floatBlob 7s 1s ease-in-out infinite;
  }

  /* CANVAS PARTICLE RING */
  #canvas-ring {
    position: absolute;
    inset: 0;
    width: 100%; height: 100%;
    pointer-events: none;
  }

  /* CENTRAL CARD */
  .center-card {
    position: relative;
    z-index: 2;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 28px;
    padding: 44px 36px;
    animation: fadeIn 1s 0.4s ease both;
  }

  /* AVATAR */
  .avatar-wrap {
    position: relative;
    width: 120px; height: 120px;
  }
  .avatar-ring {
    position: absolute; inset: -6px;
    border-radius: 50%;
    background: conic-gradient(var(--accent), var(--accent2), var(--accent3), var(--accent));
    animation: spinRing 5s linear infinite;
  }
  .avatar-ring::before {
    content: '';
    position: absolute; inset: 3px;
    border-radius: 50%;
    background: var(--bg);
  }
  .avatar-inner {
    position: absolute; inset: 0;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent2), var(--accent));
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: 'Syne', sans-serif;
    font-size: 38px;
    font-weight: 800;
    color: #fff;
    letter-spacing: -2px;
    z-index: 1;
  }

  /* STATS GRID */
  .stats-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
    width: 100%;
    max-width: 300px;
  }
  .stat-card {
    background: rgba(255,255,255,0.03);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 16px;
    text-align: center;
    transition: all 0.3s;
    position: relative;
    overflow: hidden;
  }
  .stat-card::before {
    content: '';
    position: absolute;
    inset: 0;
    background: linear-gradient(135deg, transparent, rgba(0,229,255,0.04));
    opacity: 0;
    transition: opacity 0.3s;
  }
  .stat-card:hover::before { opacity: 1; }
  .stat-card:hover {
    border-color: rgba(0,229,255,0.3);
    transform: translateY(-3px);
    box-shadow: 0 8px 30px rgba(0,229,255,0.08);
  }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 26px;
    font-weight: 800;
    background: linear-gradient(135deg, var(--accent), var(--accent2));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
    display: block;
  }
  .stat-label {
    font-size: 10px;
    color: var(--muted);
    font-family: 'Space Mono', monospace;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-top: 2px;
  }

  /* ACTIVITY BARS */
  .activity-section {
    width: 100%;
    max-width: 300px;
  }
  .activity-title {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.18em;
    margin-bottom: 12px;
  }
  .activity-bars {
    display: flex;
    gap: 4px;
    align-items: flex-end;
    height: 56px;
  }
  .bar {
    flex: 1;
    border-radius: 3px 3px 0 0;
    background: var(--border);
    position: relative;
    transition: background 0.3s;
    overflow: hidden;
  }
  .bar::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0; right: 0;
    border-radius: 3px 3px 0 0;
    background: linear-gradient(to top, var(--accent), var(--accent2));
    animation: barGrow 1.2s ease both;
    transform-origin: bottom;
  }
  .bar:nth-child(1)::after { height: 35%; animation-delay: 0.1s; }
  .bar:nth-child(2)::after { height: 55%; animation-delay: 0.15s; }
  .bar:nth-child(3)::after { height: 70%; animation-delay: 0.2s; }
  .bar:nth-child(4)::after { height: 45%; animation-delay: 0.25s; }
  .bar:nth-child(5)::after { height: 85%; animation-delay: 0.3s; }
  .bar:nth-child(6)::after { height: 60%; animation-delay: 0.35s; }
  .bar:nth-child(7)::after { height: 95%; animation-delay: 0.4s; }
  .bar:nth-child(8)::after { height: 50%; animation-delay: 0.45s; }
  .bar:nth-child(9)::after { height: 75%; animation-delay: 0.5s; }
  .bar:nth-child(10)::after { height: 40%; animation-delay: 0.55s; }
  .bar:nth-child(11)::after { height: 65%; animation-delay: 0.6s; }
  .bar:nth-child(12)::after { height: 90%; animation-delay: 0.65s; }

  /* CURRENTLY WORKING */
  .work-chip {
    display: flex;
    align-items: center;
    gap: 10px;
    background: rgba(0,229,255,0.05);
    border: 1px solid rgba(0,229,255,0.15);
    border-radius: 10px;
    padding: 12px 16px;
    width: 100%;
    max-width: 300px;
  }
  .work-chip-icon {
    width: 32px; height: 32px;
    border-radius: 8px;
    background: linear-gradient(135deg, var(--accent2), var(--accent));
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
  }
  .work-chip-text { flex: 1; }
  .work-chip-label {
    font-size: 9px;
    font-family: 'Space Mono', monospace;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 0.1em;
  }
  .work-chip-value {
    font-size: 13px;
    font-weight: 500;
    color: var(--text);
    margin-top: 2px;
  }

  /* ── KEYFRAMES ── */
  @keyframes fadeSlideIn {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes fadeIn {
    from { opacity: 0; }
    to   { opacity: 1; }
  }
  @keyframes pulse {
    0%, 100% { box-shadow: 0 0 0 0 rgba(0,229,255,0.5); }
    50%       { box-shadow: 0 0 0 6px rgba(0,229,255,0); }
  }
  @keyframes spinRing {
    to { transform: rotate(360deg); }
  }
  @keyframes floatBlob {
    0%, 100% { transform: translate(0, 0) scale(1); }
    33%       { transform: translate(-20px, 20px) scale(1.05); }
    66%       { transform: translate(15px, -15px) scale(0.95); }
  }
  @keyframes barGrow {
    from { transform: scaleY(0); }
    to   { transform: scaleY(1); }
  }
  @keyframes orbiting {
    to { transform: rotate(360deg); }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 900px) {
    .page { grid-template-columns: 1fr; }
    .left { padding: 40px 28px; }
    .left::after { display: none; }
    .right { min-height: 500px; padding: 40px 20px; }
  }
  @media (max-width: 520px) {
    .hero-text h1 { font-size: 2rem; }
    .left { padding: 32px 20px; }
    .socials { gap: 8px; }
    .social-btn { padding: 7px 12px; font-size: 11px; }
  }
</style>
</head>
<body>

<div class="page">

  <!-- ═══════════ LEFT ═══════════ -->
  <section class="left">

    <div class="badge">
      <span class="badge-dot"></span>
      Available for opportunities
    </div>

    <div class="hero-text">
      <h1>Kowsar<br><span>Hossain</span></h1>
      <p class="role-line">Full Stack Developer &amp; Problem Solver</p>
    </div>

    <p class="bio">
      Crafting end-to-end web experiences with clean code and creative thinking.
      Passionate about building scalable applications — from pixel-perfect UIs
      to robust backend architectures. Active Codeforces competitive programmer.
    </p>

    <!-- SKILLS -->
    <div class="skills-section">
      <div class="section-label">Tech Stack</div>

      <div class="skill-group">
        <div class="skill-group-title">Languages</div>
        <div class="skill-pills">
          <span class="pill"><span class="pill-dot" style="background:#f7df1e;"></span>JavaScript</span>
          <span class="pill"><span class="pill-dot" style="background:#00599c;"></span>C++</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title">Frontend</div>
        <div class="skill-pills">
          <span class="pill"><span class="pill-dot" style="background:#e34f26;"></span>HTML5</span>
          <span class="pill"><span class="pill-dot" style="background:#1572b6;"></span>CSS3</span>
          <span class="pill"><span class="pill-dot" style="background:#06b6d4;"></span>Tailwind</span>
          <span class="pill"><span class="pill-dot" style="background:#61dafb;"></span>React</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title">Backend &amp; Database</div>
        <div class="skill-pills">
          <span class="pill"><span class="pill-dot" style="background:#339933;"></span>Node.js</span>
          <span class="pill"><span class="pill-dot" style="background:#fff;"></span>Express</span>
          <span class="pill"><span class="pill-dot" style="background:#47a248;"></span>MongoDB</span>
          <span class="pill"><span class="pill-dot" style="background:#4479a1;"></span>MySQL</span>
        </div>
      </div>

      <div class="skill-group">
        <div class="skill-group-title">Tools</div>
        <div class="skill-pills">
          <span class="pill"><span class="pill-dot" style="background:#f05033;"></span>Git</span>
          <span class="pill"><span class="pill-dot" style="background:#fff;"></span>GitHub</span>
          <span class="pill"><span class="pill-dot" style="background:#ffca28;"></span>Firebase</span>
          <span class="pill"><span class="pill-dot" style="background:#fff;"></span>JWT</span>
          <span class="pill"><span class="pill-dot" style="background:#ff6c37;"></span>Postman</span>
          <span class="pill"><span class="pill-dot" style="background:#0078d4;"></span>VS Code</span>
        </div>
      </div>
    </div>

    <!-- SOCIALS -->
    <div class="socials">
      <a class="social-btn" href="https://www.facebook.com/profile.php?id=100063684969448" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z"/></svg>
        Facebook
      </a>
      <a class="social-btn" href="https://www.linkedin.com/in/md-kowsar-hossain-476bb4266/" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
        LinkedIn
      </a>
      <a class="social-btn" href="https://stackoverflow.com/users/21478943/md-kowsar-hossain" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M15.725 0l-1.72 1.277 6.39 8.588 1.716-1.277L15.725 0zm-3.94 3.418l-1.369 1.644 8.225 6.85 1.369-1.644-8.225-6.85zm-3.15 4.465l-.905 1.94 9.702 4.517.904-1.94-9.701-4.517zm-1.85 4.86l-.44 2.093 10.473 2.201.44-2.092-10.473-2.203zM1.89 15.47V24h19.19v-8.53h-2.133v6.397H4.021v-6.396H1.89zm4.265 2.133v2.13h10.66v-2.13H6.154Z"/></svg>
        Stack Overflow
      </a>
      <a class="social-btn" href="https://web.telegram.org/a/" target="_blank">
        <svg width="14" height="14" viewBox="0 0 24 24" fill="currentColor"><path d="M11.944 0A12 12 0 0 0 0 12a12 12 0 0 0 12 12 12 12 0 0 0 12-12A12 12 0 0 0 12 0a12 12 0 0 0-.056 0zm4.962 7.224c.1-.002.321.023.465.14a.506.506 0 0 1 .171.325c.016.093.036.306.02.472-.18 1.898-.962 6.502-1.36 8.627-.168.9-.499 1.201-.82 1.23-.696.065-1.225-.46-1.9-.902-1.056-.693-1.653-1.124-2.678-1.8-1.185-.78-.417-1.21.258-1.91.177-.184 3.247-2.977 3.307-3.23.007-.032.014-.15-.056-.212s-.174-.041-.249-.024c-.106.024-1.793 1.14-5.061 3.345-.48.33-.913.49-1.302.48-.428-.008-1.252-.241-1.865-.44-.752-.245-1.349-.374-1.297-.789.027-.216.325-.437.893-.663 3.498-1.524 5.83-2.529 6.998-3.014 3.332-1.386 4.025-1.627 4.476-1.635z"/></svg>
        Telegram
      </a>
    </div>

  </section>

  <!-- ═══════════ RIGHT ═══════════ -->
  <section class="right">
    <div class="blob blob-1"></div>
    <div class="blob blob-2"></div>
    <div class="blob blob-3"></div>

    <canvas id="canvas-ring"></canvas>

    <div class="center-card">

      <!-- Avatar -->
      <div class="avatar-wrap">
        <div class="avatar-ring"></div>
        <div class="avatar-inner">KH</div>
      </div>

      <!-- Stats -->
      <div class="stats-grid">
        <div class="stat-card">
          <span class="stat-num" id="cnt-projects">0</span>
          <span class="stat-label">Projects</span>
        </div>
        <div class="stat-card">
          <span class="stat-num" id="cnt-cf">0</span>
          <span class="stat-label">CF Solved</span>
        </div>
        <div class="stat-card">
          <span class="stat-num" id="cnt-tech">0</span>
          <span class="stat-label">Technologies</span>
        </div>
        <div class="stat-card">
          <span class="stat-num" id="cnt-commits">0</span>
          <span class="stat-label">Commits</span>
        </div>
      </div>

      <!-- Activity Bars -->
      <div class="activity-section">
        <div class="activity-title">Weekly Activity</div>
        <div class="activity-bars">
          <div class="bar"></div><div class="bar"></div><div class="bar"></div>
          <div class="bar"></div><div class="bar"></div><div class="bar"></div>
          <div class="bar"></div><div class="bar"></div><div class="bar"></div>
          <div class="bar"></div><div class="bar"></div><div class="bar"></div>
        </div>
      </div>

      <!-- Currently Working -->
      <div class="work-chip">
        <div class="work-chip-icon">
          <svg width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="#fff" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polyline points="16 18 22 12 16 6"/><polyline points="8 6 2 12 8 18"/></svg>
        </div>
        <div class="work-chip-text">
          <div class="work-chip-label">Currently Building</div>
          <div class="work-chip-value">Web Application Projects</div>
        </div>
      </div>

    </div>
  </section>

</div>

<script>
/* ── COUNTER ANIMATION ── */
function animateCount(id, target, suffix = '') {
  const el = document.getElementById(id);
  const duration = 1600;
  const start = performance.now();
  const update = (now) => {
    const t = Math.min((now - start) / duration, 1);
    const ease = 1 - Math.pow(1 - t, 3);
    el.textContent = Math.round(ease * target) + suffix;
    if (t < 1) requestAnimationFrame(update);
  };
  requestAnimationFrame(update);
}

window.addEventListener('load', () => {
  setTimeout(() => {
    animateCount('cnt-projects', 18, '+');
    animateCount('cnt-cf', 350, '+');
    animateCount('cnt-tech', 14, '+');
    animateCount('cnt-commits', 800, '+');
  }, 600);
});

/* ── CANVAS PARTICLE FIELD ── */
const canvas = document.getElementById('canvas-ring');
const ctx = canvas.getContext('2d');

let W, H, particles = [], mouse = { x: null, y: null };

function resize() {
  const rect = canvas.parentElement.getBoundingClientRect();
  W = canvas.width = rect.width;
  H = canvas.height = rect.height;
  initParticles();
}

function initParticles() {
  particles = [];
  const count = Math.min(80, Math.floor((W * H) / 9000));
  for (let i = 0; i < count; i++) {
    particles.push({
      x: Math.random() * W,
      y: Math.random() * H,
      r: Math.random() * 1.6 + 0.4,
      vx: (Math.random() - 0.5) * 0.4,
      vy: (Math.random() - 0.5) * 0.4,
      opacity: Math.random() * 0.5 + 0.1,
    });
  }
}

function drawParticles() {
  ctx.clearRect(0, 0, W, H);
  // Draw connecting lines
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const dx = particles[i].x - particles[j].x;
      const dy = particles[i].y - particles[j].y;
      const dist = Math.sqrt(dx * dx + dy * dy);
      if (dist < 100) {
        ctx.beginPath();
        ctx.strokeStyle = `rgba(0,229,255,${0.08 * (1 - dist / 100)})`;
        ctx.lineWidth = 0.6;
        ctx.moveTo(particles[i].x, particles[i].y);
        ctx.lineTo(particles[j].x, particles[j].y);
        ctx.stroke();
      }
    }
    // Draw dots
    ctx.beginPath();
    ctx.arc(particles[i].x, particles[i].y, particles[i].r, 0, Math.PI * 2);
    ctx.fillStyle = `rgba(124,92,252,${particles[i].opacity})`;
    ctx.fill();
  }

  // Mouse glow
  if (mouse.x !== null) {
    const grd = ctx.createRadialGradient(mouse.x, mouse.y, 0, mouse.x, mouse.y, 90);
    grd.addColorStop(0, 'rgba(0,229,255,0.08)');
    grd.addColorStop(1, 'rgba(0,229,255,0)');
    ctx.fillStyle = grd;
    ctx.beginPath();
    ctx.arc(mouse.x, mouse.y, 90, 0, Math.PI * 2);
    ctx.fill();
  }
}

function updateParticles() {
  for (const p of particles) {
    p.x += p.vx;
    p.y += p.vy;
    if (p.x < 0) p.x = W;
    if (p.x > W) p.x = 0;
    if (p.y < 0) p.y = H;
    if (p.y > H) p.y = 0;

    // Attract slightly to mouse
    if (mouse.x !== null) {
      const dx = mouse.x - p.x;
      const dy = mouse.y - p.y;
      const d = Math.sqrt(dx * dx + dy * dy);
      if (d < 150) {
        p.vx += dx / d * 0.012;
        p.vy += dy / d * 0.012;
      }
    }
    // Dampen velocity
    p.vx *= 0.99;
    p.vy *= 0.99;
  }
}

function loop() {
  updateParticles();
  drawParticles();
  requestAnimationFrame(loop);
}

canvas.parentElement.addEventListener('mousemove', e => {
  const rect = canvas.getBoundingClientRect();
  mouse.x = e.clientX - rect.left;
  mouse.y = e.clientY - rect.top;
});
canvas.parentElement.addEventListener('mouseleave', () => {
  mouse.x = null; mouse.y = null;
});

window.addEventListener('resize', resize);
resize();
loop();
</script>
</body>
</html>
