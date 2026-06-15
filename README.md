<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Portfolio — Your Name</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;0,900;1,400&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --cream: #f5f0e8;
      --dark: #111008;
      --accent: #c8a96e;
      --accent2: #7c6f5a;
      --text: #2a2416;
      --muted: #8a7e6a;
      --card: #fffdf7;
      --border: rgba(200,169,110,0.2);
    }

    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    html { scroll-behavior: smooth; }

    body {
      background: var(--cream);
      color: var(--text);
      font-family: 'DM Sans', sans-serif;
      font-weight: 300;
      line-height: 1.7;
      overflow-x: hidden;
    }

    /* ── CUSTOM CURSOR ── */
    *, a { cursor: none !important; }
    .cursor {
      position: fixed;
      width: 10px; height: 10px;
      background: var(--accent);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9999;
      transform: translate(-50%,-50%);
      transition: transform 0.1s, width 0.25s, height 0.25s, background 0.25s;
    }
    .cursor-ring {
      position: fixed;
      width: 36px; height: 36px;
      border: 1.5px solid var(--accent);
      border-radius: 50%;
      pointer-events: none;
      z-index: 9998;
      transform: translate(-50%,-50%);
      transition: transform 0.18s ease, width 0.3s, height 0.3s, opacity 0.3s;
      opacity: 0.5;
    }
    .cursor.hover { width: 18px; height: 18px; }
    .cursor-ring.hover { width: 54px; height: 54px; opacity: 0.3; }

    /* ── NAV ── */
    nav {
      position: fixed; top: 0; left: 0; right: 0;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 22px 60px;
      background: rgba(245,240,232,0.85);
      backdrop-filter: blur(12px);
      border-bottom: 1px solid var(--border);
      animation: fadeDown 0.8s ease both;
    }

    @keyframes fadeDown {
      from { opacity:0; transform: translateY(-16px); }
      to   { opacity:1; transform: translateY(0); }
    }

    .logo {
      font-family: 'Playfair Display', serif;
      font-size: 1.3rem;
      font-weight: 700;
      color: var(--dark);
      letter-spacing: 0.02em;
      text-decoration: none;
    }
    .logo span { color: var(--accent); }

    .nav-links {
      display: flex; gap: 36px;
      list-style: none;
    }
    .nav-links a {
      font-size: 0.78rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: var(--muted);
      text-decoration: none;
      font-weight: 500;
      position: relative;
      transition: color 0.2s;
    }
    .nav-links a::after {
      content: '';
      position: absolute;
      bottom: -3px; left: 0;
      width: 0; height: 1px;
      background: var(--accent);
      transition: width 0.3s ease;
    }
    .nav-links a:hover { color: var(--accent); }
    .nav-links a:hover::after { width: 100%; }

    /* ── HERO ── */
    .hero {
      min-height: 100vh;
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      padding: 120px 60px 60px;
      position: relative;
      overflow: hidden;
    }

    .hero::before {
      content: '';
      position: absolute;
      top: -100px; right: -100px;
      width: 600px; height: 600px;
      background: radial-gradient(circle, rgba(200,169,110,0.12) 0%, transparent 70%);
      pointer-events: none;
    }

    .hero-text { animation: fadeUp 1s 0.2s ease both; }

    @keyframes fadeUp {
      from { opacity:0; transform: translateY(30px); }
      to   { opacity:1; transform: translateY(0); }
    }

    .hero-tag {
      font-size: 0.72rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--accent);
      font-weight: 500;
      margin-bottom: 20px;
      display: flex;
      align-items: center;
      gap: 12px;
    }
    .hero-tag::before {
      content: '';
      display: block;
      width: 32px; height: 1px;
      background: var(--accent);
    }

    h1 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.8rem, 6vw, 5rem);
      font-weight: 900;
      line-height: 1.08;
      color: var(--dark);
      margin-bottom: 24px;
    }

    h1 em {
      font-style: italic;
      color: var(--accent);
    }

    .hero-desc {
      font-size: 1rem;
      color: var(--muted);
      max-width: 420px;
      margin-bottom: 40px;
      line-height: 1.8;
    }

    .btn-group { display: flex; gap: 16px; flex-wrap: wrap; }

    .btn-primary {
      background: var(--dark);
      color: var(--cream);
      padding: 14px 32px;
      border-radius: 4px;
      text-decoration: none;
      font-size: 0.8rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      font-weight: 500;
      transition: background 0.25s, transform 0.2s;
      border: none;
    }
    .btn-primary:hover { background: var(--accent); transform: translateY(-2px); }

    .btn-outline {
      background: transparent;
      color: var(--dark);
      padding: 13px 32px;
      border-radius: 4px;
      text-decoration: none;
      font-size: 0.8rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      font-weight: 500;
      border: 1.5px solid rgba(17,16,8,0.25);
      transition: border-color 0.25s, color 0.25s, transform 0.2s;
    }
    .btn-outline:hover { border-color: var(--accent); color: var(--accent); transform: translateY(-2px); }

    /* Hero image side */
    .hero-visual {
      display: flex;
      justify-content: center;
      align-items: center;
      animation: fadeUp 1s 0.4s ease both;
      position: relative;
    }

    .avatar-frame {
      width: clamp(260px, 30vw, 380px);
      height: clamp(320px, 38vw, 460px);
      position: relative;
    }

    .avatar-bg {
      position: absolute;
      inset: 0;
      background: linear-gradient(135deg, var(--accent) 0%, #8a6a3a 100%);
      border-radius: 60% 40% 55% 45% / 50% 50% 50% 50%;
      opacity: 0.18;
      animation: morph 8s ease-in-out infinite;
    }

    @keyframes morph {
      0%,100% { border-radius: 60% 40% 55% 45% / 50% 50% 50% 50%; }
      50%      { border-radius: 40% 60% 45% 55% / 50% 50% 50% 50%; }
    }

    .avatar-placeholder {
      position: absolute;
      inset: 20px;
      background: linear-gradient(160deg, #e8e0d0 0%, #d4c9b0 100%);
      border-radius: 55% 45% 50% 50% / 48% 52% 48% 52%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 12px;
      border: 2px solid rgba(200,169,110,0.3);
      overflow: hidden;
    }

    .avatar-icon {
      width: 90px; height: 90px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent) 0%, #8a6a3a 100%);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 2.4rem;
    }

    .avatar-name-tag {
      font-family: 'Playfair Display', serif;
      font-size: 1rem;
      font-weight: 700;
      color: var(--text);
      letter-spacing: 0.06em;
    }

    .avatar-sub {
      font-size: 0.7rem;
      color: var(--muted);
      letter-spacing: 0.15em;
      text-transform: uppercase;
    }

    .floating-badge {
      position: absolute;
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 8px;
      padding: 10px 16px;
      font-size: 0.72rem;
      font-weight: 500;
      color: var(--text);
      box-shadow: 0 8px 32px rgba(0,0,0,0.08);
      white-space: nowrap;
    }

    .badge-exp { top: 20px; right: -30px; animation: float1 4s ease-in-out infinite; }
    .badge-proj { bottom: 50px; left: -30px; animation: float2 4.5s ease-in-out infinite; }

    @keyframes float1 {
      0%,100% { transform: translateY(0); }
      50% { transform: translateY(-8px); }
    }
    @keyframes float2 {
      0%,100% { transform: translateY(0); }
      50% { transform: translateY(8px); }
    }

    .badge-dot { display: inline-block; width: 7px; height: 7px; border-radius: 50%; background: #4caf78; margin-right: 6px; }

    /* ── SECTION COMMON ── */
    section { padding: 100px 60px; }

    .section-header { margin-bottom: 60px; }

    .section-tag {
      font-size: 0.7rem;
      letter-spacing: 0.22em;
      text-transform: uppercase;
      color: var(--accent);
      font-weight: 500;
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      gap: 10px;
    }
    .section-tag::before {
      content: '';
      display: block;
      width: 24px; height: 1px;
      background: var(--accent);
    }

    h2 {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2rem, 4vw, 3rem);
      font-weight: 900;
      color: var(--dark);
      line-height: 1.15;
    }

    h2 em { font-style: italic; color: var(--accent); }

    /* ── ABOUT ── */
    .about { background: var(--dark); color: var(--cream); }
    .about h2 { color: var(--cream); }
    .about .section-tag { color: var(--accent); }

    .about-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 80px;
      align-items: start;
    }

    .about-text p {
      color: rgba(245,240,232,0.7);
      margin-bottom: 18px;
      font-size: 0.96rem;
    }

    .stats-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 24px;
      margin-top: 40px;
    }

    .stat-item {
      border-top: 1px solid rgba(200,169,110,0.3);
      padding-top: 20px;
    }

    .stat-num {
      font-family: 'Playfair Display', serif;
      font-size: 2.4rem;
      font-weight: 900;
      color: var(--accent);
      line-height: 1;
      margin-bottom: 6px;
    }

    .stat-label {
      font-size: 0.75rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: rgba(245,240,232,0.4);
    }

    /* Skills */
    .skills-list { display: flex; flex-direction: column; gap: 18px; }

    .skill-row { display: flex; flex-direction: column; gap: 6px; }

    .skill-meta {
      display: flex;
      justify-content: space-between;
      font-size: 0.8rem;
      color: rgba(245,240,232,0.6);
    }

    .skill-bar-bg {
      height: 3px;
      background: rgba(255,255,255,0.08);
      border-radius: 2px;
      overflow: hidden;
    }

    .skill-bar {
      height: 100%;
      background: linear-gradient(90deg, var(--accent), #8a6a3a);
      border-radius: 2px;
      width: 0;
      transition: width 1.2s cubic-bezier(0.4,0,0.2,1);
    }

    /* ── PROJECTS ── */
    .projects-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 28px;
    }

    .project-card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 12px;
      overflow: hidden;
      transition: transform 0.3s ease, box-shadow 0.3s ease;
    }

    .project-card:hover {
      transform: translateY(-8px);
      box-shadow: 0 24px 64px rgba(0,0,0,0.1);
    }

    .project-thumb {
      height: 200px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 3rem;
      position: relative;
      overflow: hidden;
    }

    .project-thumb::after {
      content: '';
      position: absolute;
      inset: 0;
      opacity: 0;
      transition: opacity 0.3s;
    }

    .project-card:hover .project-thumb::after { opacity: 1; }

    .p1 { background: linear-gradient(135deg, #1a1a2e, #16213e); }
    .p2 { background: linear-gradient(135deg, #0f2027, #203a43, #2c5364); }
    .p3 { background: linear-gradient(135deg, #1a0a00, #3d1c02); }
    .p4 { background: linear-gradient(135deg, #0a1628, #162040); }
    .p5 { background: linear-gradient(135deg, #0d1b0a, #1a3a12); }
    .p6 { background: linear-gradient(135deg, #1a0a1a, #2d0f2d); }

    .project-body { padding: 24px; }

    .project-tags { display: flex; gap: 8px; flex-wrap: wrap; margin-bottom: 12px; }

    .tag {
      font-size: 0.65rem;
      letter-spacing: 0.1em;
      text-transform: uppercase;
      color: var(--accent);
      background: rgba(200,169,110,0.1);
      border: 1px solid rgba(200,169,110,0.2);
      padding: 3px 10px;
      border-radius: 20px;
      font-weight: 500;
    }

    .project-title {
      font-family: 'Playfair Display', serif;
      font-size: 1.2rem;
      font-weight: 700;
      color: var(--dark);
      margin-bottom: 8px;
    }

    .project-desc {
      font-size: 0.84rem;
      color: var(--muted);
      margin-bottom: 20px;
      line-height: 1.7;
    }

    .project-links { display: flex; gap: 14px; }

    .proj-link {
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      font-weight: 500;
      text-decoration: none;
      color: var(--dark);
      transition: color 0.2s;
      display: flex;
      align-items: center;
      gap: 5px;
    }
    .proj-link:hover { color: var(--accent); }

    /* ── CONTACT ── */
    .contact { background: var(--dark); }
    .contact h2 { color: var(--cream); }
    .contact .section-tag { color: var(--accent); }
    .contact .section-header p { color: rgba(245,240,232,0.5); margin-top: 16px; font-size: 0.95rem; }

    .contact-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 60px;
      align-items: start;
    }

    .contact-info { display: flex; flex-direction: column; gap: 24px; }

    .contact-item {
      display: flex;
      align-items: flex-start;
      gap: 16px;
      padding-bottom: 24px;
      border-bottom: 1px solid rgba(255,255,255,0.06);
    }

    .contact-icon {
      width: 40px; height: 40px;
      background: rgba(200,169,110,0.1);
      border: 1px solid rgba(200,169,110,0.2);
      border-radius: 8px;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1rem;
      flex-shrink: 0;
    }

    .contact-label {
      font-size: 0.68rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: rgba(245,240,232,0.3);
      margin-bottom: 4px;
    }

    .contact-value {
      font-size: 0.9rem;
      color: rgba(245,240,232,0.8);
    }

    /* Form */
    .contact-form { display: flex; flex-direction: column; gap: 16px; }

    .form-group { display: flex; flex-direction: column; gap: 6px; }

    .form-group label {
      font-size: 0.7rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      color: rgba(245,240,232,0.4);
    }

    .form-group input,
    .form-group textarea {
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.08);
      border-radius: 6px;
      padding: 12px 16px;
      color: var(--cream);
      font-family: 'DM Sans', sans-serif;
      font-size: 0.88rem;
      outline: none;
      transition: border-color 0.2s;
      resize: none;
    }

    .form-group input:focus,
    .form-group textarea:focus {
      border-color: rgba(200,169,110,0.5);
    }

    .form-group input::placeholder,
    .form-group textarea::placeholder { color: rgba(245,240,232,0.2); }

    .btn-send {
      background: var(--accent);
      color: var(--dark);
      border: none;
      padding: 14px 32px;
      border-radius: 6px;
      font-family: 'DM Sans', sans-serif;
      font-size: 0.8rem;
      letter-spacing: 0.14em;
      text-transform: uppercase;
      font-weight: 500;
      cursor: none;
      transition: background 0.2s, transform 0.2s;
      align-self: flex-start;
    }
    .btn-send:hover { background: #d4b87a; transform: translateY(-2px); }

    /* ── FOOTER ── */
    footer {
      background: #080804;
      padding: 36px 60px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-top: 1px solid rgba(255,255,255,0.05);
    }

    .footer-copy {
      font-size: 0.75rem;
      color: rgba(245,240,232,0.25);
      letter-spacing: 0.08em;
    }

    .social-links { display: flex; gap: 20px; }
    .social-links a {
      font-size: 0.72rem;
      letter-spacing: 0.12em;
      text-transform: uppercase;
      color: rgba(245,240,232,0.3);
      text-decoration: none;
      transition: color 0.2s;
    }
    .social-links a:hover { color: var(--accent); }

    /* ── SCROLL REVEAL ── */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.7s ease, transform 0.7s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: none;
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      nav { padding: 18px 24px; }
      .nav-links { display: none; }
      .hero { grid-template-columns: 1fr; padding: 100px 24px 60px; text-align: center; }
      .hero-tag { justify-content: center; }
      .hero-desc { margin: 0 auto 40px; }
      .btn-group { justify-content: center; }
      .hero-visual { display: none; }
      section { padding: 70px 24px; }
      .about-grid, .contact-grid { grid-template-columns: 1fr; gap: 40px; }
      footer { flex-direction: column; gap: 16px; text-align: center; }
    }
  </style>
</head>
<body>

<!-- Cursor -->
<div class="cursor" id="cursor"></div>
<div class="cursor-ring" id="cursorRing"></div>

<!-- NAV -->
<nav>
  <a href="#" class="logo">Your<span>.</span>Name</a>
  <ul class="nav-links">
    <li><a href="#about">About</a></li>
    <li><a href="#projects">Projects</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="home">
  <div class="hero-text">
    <div class="hero-tag">Available for work</div>
    <h1>Creative<br/><em>Frontend</em><br/>Developer</h1>
    <p class="hero-desc">I craft elegant, high-performance web experiences that blend beautiful design with clean, purposeful code.</p>
    <div class="btn-group">
      <a href="#projects" class="btn-primary">View My Work</a>
      <a href="#contact" class="btn-outline">Get In Touch</a>
    </div>
  </div>

  <div class="hero-visual">
    <div class="avatar-frame">
      <div class="avatar-bg"></div>
      <div class="avatar-placeholder">
        <div class="avatar-icon">👤</div>
        <div class="avatar-name-tag">Your Name</div>
        <div class="avatar-sub">Developer & Designer</div>
      </div>
      <div class="floating-badge badge-exp">✦ 3+ Years Experience</div>
      <div class="floating-badge badge-proj"><span class="badge-dot"></span>Open to Opportunities</div>
    </div>
  </div>
</section>

<!-- ABOUT -->
<section class="about" id="about">
  <div class="about-grid">
    <div class="about-text reveal">
      <div class="section-tag">About Me</div>
      <h2>Passionate about crafting <em>beautiful</em> things</h2>
      <br/>
      <p>I'm a frontend developer with a deep love for clean interfaces and thoughtful user experiences. I believe great design and great code aren't opposites — they're partners.</p>
      <p>When I'm not pushing pixels, I'm exploring new technologies, contributing to open source, or sketching interface ideas in my notebook.</p>
      <div class="stats-grid">
        <div class="stat-item">
          <div class="stat-num">20+</div>
          <div class="stat-label">Projects Delivered</div>
        </div>
        <div class="stat-item">
          <div class="stat-num">3+</div>
          <div class="stat-label">Years Experience</div>
        </div>
        <div class="stat-item">
          <div class="stat-num">15+</div>
          <div class="stat-label">Happy Clients</div>
        </div>
        <div class="stat-item">
          <div class="stat-num">∞</div>
          <div class="stat-label">Cups of Coffee</div>
        </div>
      </div>
    </div>

    <div class="reveal" style="transition-delay:0.15s">
      <div class="section-tag">Skills</div>
      <div class="skills-list">
        <div class="skill-row">
          <div class="skill-meta"><span>HTML & CSS</span><span>95%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar" data-width="95"></div></div>
        </div>
        <div class="skill-row">
          <div class="skill-meta"><span>JavaScript</span><span>88%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar" data-width="88"></div></div>
        </div>
        <div class="skill-row">
          <div class="skill-meta"><span>React / Vue</span><span>82%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar" data-width="82"></div></div>
        </div>
        <div class="skill-row">
          <div class="skill-meta"><span>UI / UX Design</span><span>78%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar" data-width="78"></div></div>
        </div>
        <div class="skill-row">
          <div class="skill-meta"><span>Node.js</span><span>70%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar" data-width="70"></div></div>
        </div>
        <div class="skill-row">
          <div class="skill-meta"><span>Git & GitHub</span><span>90%</span></div>
          <div class="skill-bar-bg"><div class="skill-bar" data-width="90"></div></div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- PROJECTS -->
<section id="projects">
  <div class="section-header reveal">
    <div class="section-tag">My Work</div>
    <h2>Selected <em>Projects</em></h2>
  </div>

  <div class="projects-grid">
    <div class="project-card reveal">
      <div class="project-thumb p1">⏱️</div>
      <div class="project-body">
        <div class="project-tags"><span class="tag">HTML</span><span class="tag">CSS</span><span class="tag">JS</span></div>
        <div class="project-title">Digital Clock & Stopwatch</div>
        <p class="project-desc">A cyberpunk-themed real-time clock and precision stopwatch with lap tracking and neon glow aesthetics.</p>
        <div class="project-links">
          <a href="#" class="proj-link">↗ Live Demo</a>
          <a href="#" class="proj-link">⌥ GitHub</a>
        </div>
      </div>
    </div>

    <div class="project-card reveal" style="transition-delay:0.1s">
      <div class="project-thumb p2">🛒</div>
      <div class="project-body">
        <div class="project-tags"><span class="tag">React</span><span class="tag">Node</span><span class="tag">MongoDB</span></div>
        <div class="project-title">E-Commerce Platform</div>
        <p class="project-desc">Full-stack shopping app with cart management, authentication, and payment integration.</p>
        <div class="project-links">
          <a href="#" class="proj-link">↗ Live Demo</a>
          <a href="#" class="proj-link">⌥ GitHub</a>
        </div>
      </div>
    </div>

    <div class="project-card reveal" style="transition-delay:0.2s">
      <div class="project-thumb p3">🌤️</div>
      <div class="project-body">
        <div class="project-tags"><span class="tag">JS</span><span class="tag">API</span><span class="tag">CSS</span></div>
        <div class="project-title">Weather Dashboard</div>
        <p class="project-desc">Live weather app fetching real-time data with animated conditions and 7-day forecasts.</p>
        <div class="project-links">
          <a href="#" class="proj-link">↗ Live Demo</a>
          <a href="#" class="proj-link">⌥ GitHub</a>
        </div>
      </div>
    </div>

    <div class="project-card reveal" style="transition-delay:0.05s">
      <div class="project-thumb p4">📋</div>
      <div class="project-body">
        <div class="project-tags"><span class="tag">React</span><span class="tag">Firebase</span></div>
        <div class="project-title">Task Manager App</div>
        <p class="project-desc">Drag-and-drop Kanban board with real-time sync, labels, priorities, and team collaboration.</p>
        <div class="project-links">
          <a href="#" class="proj-link">↗ Live Demo</a>
          <a href="#" class="proj-link">⌥ GitHub</a>
        </div>
      </div>
    </div>

    <div class="project-card reveal" style="transition-delay:0.15s">
      <div class="project-thumb p5">💬</div>
      <div class="project-body">
        <div class="project-tags"><span class="tag">Node</span><span class="tag">Socket.io</span><span class="tag">React</span></div>
        <div class="project-title">Real-Time Chat App</div>
        <p class="project-desc">Instant messaging platform with rooms, emoji reactions, online presence indicators.</p>
        <div class="project-links">
          <a href="#" class="proj-link">↗ Live Demo</a>
          <a href="#" class="proj-link">⌥ GitHub</a>
        </div>
      </div>
    </div>

    <div class="project-card reveal" style="transition-delay:0.25s">
      <div class="project-thumb p6">📊</div>
      <div class="project-body">
        <div class="project-tags"><span class="tag">React</span><span class="tag">D3.js</span><span class="tag">API</span></div>
        <div class="project-title">Analytics Dashboard</div>
        <p class="project-desc">Interactive data visualization dashboard with real-time charts, filters, and exportable reports.</p>
        <div class="project-links">
          <a href="#" class="proj-link">↗ Live Demo</a>
          <a href="#" class="proj-link">⌥ GitHub</a>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- CONTACT -->
<section class="contact" id="contact">
  <div class="section-header reveal">
    <div class="section-tag">Contact</div>
    <h2>Let's <em>work</em> together</h2>
    <p>Have a project in mind? I'd love to hear about it. Send me a message and I'll get back to you.</p>
  </div>

  <div class="contact-grid">
    <div class="contact-info reveal">
      <div class="contact-item">
        <div class="contact-icon">📧</div>
        <div>
          <div class="contact-label">Email</div>
          <div class="contact-value">hello@yourname.com</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">📍</div>
        <div>
          <div class="contact-label">Location</div>
          <div class="contact-value">Bengaluru, India</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">🔗</div>
        <div>
          <div class="contact-label">LinkedIn</div>
          <div class="contact-value">linkedin.com/in/yourname</div>
        </div>
      </div>
      <div class="contact-item">
        <div class="contact-icon">💻</div>
        <div>
          <div class="contact-label">GitHub</div>
          <div class="contact-value">github.com/yourname</div>
        </div>
      </div>
    </div>

    <div class="contact-form reveal" style="transition-delay:0.15s">
      <div class="form-group">
        <label>Your Name</label>
        <input type="text" placeholder="John Doe"/>
      </div>
      <div class="form-group">
        <label>Email Address</label>
        <input type="email" placeholder="john@example.com"/>
      </div>
      <div class="form-group">
        <label>Subject</label>
        <input type="text" placeholder="Project Inquiry"/>
      </div>
      <div class="form-group">
        <label>Message</label>
        <textarea rows="5" placeholder="Tell me about your project..."></textarea>
      </div>
      <button class="btn-send" onclick="sendMsg(this)">Send Message →</button>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-copy">© 2026 Your Name. Crafted with care.</div>
  <div class="social-links">
    <a href="#">GitHub</a>
    <a href="#">LinkedIn</a>
    <a href="#">Twitter</a>
    <a href="#">Dribbble</a>
  </div>
</footer>

<script>
  // ── Cursor ──
  const cursor = document.getElementById('cursor');
  const ring   = document.getElementById('cursorRing');
  let mx = 0, my = 0, rx = 0, ry = 0;

  document.addEventListener('mousemove', e => {
    mx = e.clientX; my = e.clientY;
    cursor.style.left = mx + 'px';
    cursor.style.top  = my + 'px';
  });

  function animRing(){
    rx += (mx - rx) * 0.12;
    ry += (my - ry) * 0.12;
    ring.style.left = rx + 'px';
    ring.style.top  = ry + 'px';
    requestAnimationFrame(animRing);
  }
  animRing();

  document.querySelectorAll('a, button, .project-card').forEach(el => {
    el.addEventListener('mouseenter', () => { cursor.classList.add('hover'); ring.classList.add('hover'); });
    el.addEventListener('mouseleave', () => { cursor.classList.remove('hover'); ring.classList.remove('hover'); });
  });

  // ── Scroll Reveal ──
  const observer = new IntersectionObserver(entries => {
    entries.forEach(e => {
      if(e.isIntersecting){
        e.target.classList.add('visible');
        // Trigger skill bars
        e.target.querySelectorAll('.skill-bar').forEach(bar => {
          bar.style.width = bar.dataset.width + '%';
        });
      }
    });
  }, { threshold: 0.12 });

  document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

  // ── Send message mock ──
  function sendMsg(btn){
    btn.textContent = '✓ Message Sent!';
    btn.style.background = '#4caf78';
    setTimeout(() => {
      btn.textContent = 'Send Message →';
      btn.style.background = '';
    }, 3000);
  }
</script>
</body>
</html>
