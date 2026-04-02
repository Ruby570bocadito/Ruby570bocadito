<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Ruby — Ethical Hacker & Security Researcher</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Share+Tech+Mono&family=Rajdhani:wght@300;400;600;700&family=Orbitron:wght@400;700;900&display=swap" rel="stylesheet">
<style>
  :root {
    --green: #00ff88;
    --cyan: #00e5ff;
    --red: #ff2d55;
    --dark: #020c06;
    --dark2: #050f08;
    --panel: rgba(0,255,136,0.04);
    --border: rgba(0,255,136,0.15);
    --border-bright: rgba(0,255,136,0.5);
    --text: #c8ffd4;
    --muted: #5a8a6a;
    --font-mono: 'Share Tech Mono', monospace;
    --font-body: 'Rajdhani', sans-serif;
    --font-head: 'Orbitron', monospace;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--dark);
    color: var(--text);
    font-family: var(--font-body);
    font-size: 16px;
    line-height: 1.6;
    overflow-x: hidden;
    position: relative;
  }

  /* SCANLINES */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.07) 2px,
      rgba(0,0,0,0.07) 4px
    );
    pointer-events: none;
    z-index: 1000;
  }

  /* GRID BG */
  body::after {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(0,255,136,0.03) 1px, transparent 1px),
      linear-gradient(90deg, rgba(0,255,136,0.03) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    max-width: 900px;
    margin: 0 auto;
    padding: 40px 24px 80px;
    position: relative;
    z-index: 1;
  }

  /* ─── HEADER ─── */
  .header {
    display: grid;
    grid-template-columns: auto 1fr;
    gap: 32px;
    align-items: start;
    margin-bottom: 48px;
    padding-bottom: 32px;
    border-bottom: 1px solid var(--border);
  }

  .avatar-ring {
    width: 120px;
    height: 120px;
    border-radius: 50%;
    border: 2px solid var(--green);
    padding: 4px;
    position: relative;
    flex-shrink: 0;
    box-shadow: 0 0 24px rgba(0,255,136,0.3), inset 0 0 24px rgba(0,255,136,0.05);
    animation: pulse-ring 3s ease-in-out infinite;
  }

  @keyframes pulse-ring {
    0%, 100% { box-shadow: 0 0 24px rgba(0,255,136,0.3), inset 0 0 24px rgba(0,255,136,0.05); }
    50% { box-shadow: 0 0 40px rgba(0,255,136,0.6), inset 0 0 24px rgba(0,255,136,0.1); }
  }

  .avatar-ring img {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    object-fit: cover;
    filter: contrast(1.1) brightness(0.9);
  }

  .avatar-placeholder {
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: linear-gradient(135deg, #051a0b 0%, #0a2a14 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-head);
    font-size: 32px;
    color: var(--green);
    letter-spacing: 2px;
  }

  .online-dot {
    position: absolute;
    bottom: 6px;
    right: 6px;
    width: 14px;
    height: 14px;
    background: var(--green);
    border-radius: 50%;
    border: 2px solid var(--dark);
    animation: blink 2s step-end infinite;
  }
  @keyframes blink { 0%, 100% { opacity: 1; } 50% { opacity: 0.2; } }

  .header-info { padding-top: 8px; }

  .prompt-line {
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--muted);
    margin-bottom: 4px;
    letter-spacing: 0.5px;
  }
  .prompt-line span { color: var(--green); }

  h1 {
    font-family: var(--font-head);
    font-size: clamp(26px, 5vw, 42px);
    font-weight: 900;
    color: #fff;
    letter-spacing: 3px;
    text-transform: uppercase;
    line-height: 1.1;
    margin-bottom: 6px;
    text-shadow: 0 0 30px rgba(0,255,136,0.4);
  }

  h1 .accent { color: var(--green); }

  .tagline {
    font-family: var(--font-mono);
    font-size: 13px;
    color: var(--cyan);
    letter-spacing: 1px;
    margin-bottom: 16px;
  }

  .badges {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
    margin-bottom: 20px;
  }

  .badge {
    display: inline-flex;
    align-items: center;
    gap: 5px;
    padding: 4px 10px;
    border: 1px solid var(--border);
    border-radius: 2px;
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--muted);
    background: var(--panel);
    text-decoration: none;
    transition: all 0.2s;
    letter-spacing: 0.5px;
  }
  .badge:hover { border-color: var(--green); color: var(--green); }
  .badge .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--green); }
  .badge.red .dot { background: var(--red); }
  .badge.cyan .dot { background: var(--cyan); }

  .social-links {
    display: flex;
    flex-wrap: wrap;
    gap: 10px;
  }

  .social-link {
    font-family: var(--font-mono);
    font-size: 12px;
    color: var(--muted);
    text-decoration: none;
    padding: 6px 14px;
    border: 1px solid rgba(0,229,255,0.2);
    border-radius: 2px;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .social-link:hover {
    color: var(--cyan);
    border-color: var(--cyan);
    background: rgba(0,229,255,0.05);
  }
  .social-link .icon { font-size: 14px; }

  /* ─── ABOUT ─── */
  .about {
    background: var(--panel);
    border: 1px solid var(--border);
    border-left: 3px solid var(--green);
    padding: 20px 24px;
    border-radius: 0 4px 4px 0;
    margin-bottom: 48px;
    position: relative;
    overflow: hidden;
  }
  .about::before {
    content: '// WHOAMI';
    position: absolute;
    top: 12px;
    right: 20px;
    font-family: var(--font-mono);
    font-size: 10px;
    color: var(--border-bright);
    letter-spacing: 2px;
  }
  .about p {
    font-size: 16px;
    color: var(--text);
    line-height: 1.8;
    font-weight: 400;
  }
  .about p strong { color: var(--green); font-weight: 600; }
  .about a { color: var(--cyan); text-decoration: none; border-bottom: 1px solid rgba(0,229,255,0.3); }
  .about a:hover { border-bottom-color: var(--cyan); }

  /* ─── SECTION ─── */
  .section-label {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 24px;
  }
  .section-label .line {
    flex: 1;
    height: 1px;
    background: var(--border);
  }
  .section-label h2 {
    font-family: var(--font-head);
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 4px;
    color: var(--green);
    text-transform: uppercase;
    white-space: nowrap;
  }

  section { margin-bottom: 52px; }

  /* ─── SKILLS GRID ─── */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(260px, 1fr));
    gap: 16px;
  }

  .skill-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 18px 20px;
    transition: all 0.25s;
    position: relative;
    overflow: hidden;
  }
  .skill-card::after {
    content: '';
    position: absolute;
    top: 0; left: 0; right: 0;
    height: 1px;
    background: linear-gradient(90deg, transparent, var(--green), transparent);
    opacity: 0;
    transition: opacity 0.25s;
  }
  .skill-card:hover { border-color: var(--border-bright); transform: translateY(-2px); }
  .skill-card:hover::after { opacity: 1; }

  .skill-card-header {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 14px;
  }
  .skill-icon {
    width: 36px;
    height: 36px;
    border-radius: 4px;
    background: rgba(0,255,136,0.1);
    border: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 18px;
  }
  .skill-title {
    font-family: var(--font-head);
    font-size: 13px;
    font-weight: 700;
    letter-spacing: 1px;
    color: #fff;
    text-transform: uppercase;
  }

  .skill-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .skill-tag {
    font-family: var(--font-mono);
    font-size: 11px;
    padding: 3px 8px;
    background: rgba(0,255,136,0.06);
    border: 1px solid rgba(0,255,136,0.12);
    border-radius: 2px;
    color: var(--muted);
  }

  /* ─── PROJECTS ─── */
  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(380px, 1fr));
    gap: 16px;
  }

  .project-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 20px 22px;
    text-decoration: none;
    display: block;
    transition: all 0.25s;
    position: relative;
    overflow: hidden;
  }
  .project-card::before {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    height: 2px;
    width: 0;
    background: var(--green);
    transition: width 0.3s;
  }
  .project-card:hover { border-color: var(--border-bright); }
  .project-card:hover::before { width: 100%; }

  .project-name {
    font-family: var(--font-mono);
    font-size: 13px;
    color: var(--cyan);
    margin-bottom: 6px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .project-name .arrow { color: var(--green); transition: transform 0.2s; }
  .project-card:hover .arrow { transform: translateX(4px); }

  .project-desc {
    font-size: 14px;
    color: var(--muted);
    margin-bottom: 12px;
    line-height: 1.5;
  }
  .project-desc strong { color: var(--green); font-weight: 400; }

  .project-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
  }
  .project-tag {
    font-family: var(--font-mono);
    font-size: 10px;
    padding: 2px 7px;
    border-radius: 2px;
    letter-spacing: 0.5px;
  }
  .project-tag.green { background: rgba(0,255,136,0.1); border: 1px solid rgba(0,255,136,0.2); color: var(--green); }
  .project-tag.cyan { background: rgba(0,229,255,0.08); border: 1px solid rgba(0,229,255,0.2); color: var(--cyan); }
  .project-tag.red { background: rgba(255,45,85,0.08); border: 1px solid rgba(255,45,85,0.2); color: var(--red); }

  /* ─── CERTS ─── */
  .certs-wrapper {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 12px;
  }

  .cert-item {
    display: flex;
    align-items: flex-start;
    gap: 12px;
    padding: 14px 16px;
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 4px;
    transition: border-color 0.2s;
  }
  .cert-item:hover { border-color: var(--border-bright); }

  .cert-bullet {
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background: var(--green);
    margin-top: 6px;
    flex-shrink: 0;
    box-shadow: 0 0 6px var(--green);
  }
  .cert-bullet.cyan { background: var(--cyan); box-shadow: 0 0 6px var(--cyan); }
  .cert-bullet.red { background: var(--red); box-shadow: 0 0 6px var(--red); }

  .cert-text { flex: 1; }
  .cert-name {
    font-size: 14px;
    color: var(--text);
    font-weight: 600;
    line-height: 1.4;
    margin-bottom: 2px;
  }
  .cert-source {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--muted);
  }

  /* ─── STATS ─── */
  .stats-row {
    display: flex;
    flex-wrap: wrap;
    gap: 16px;
    margin-bottom: 32px;
  }
  .stat-card {
    flex: 1;
    min-width: 130px;
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 16px 20px;
    text-align: center;
  }
  .stat-num {
    font-family: var(--font-head);
    font-size: 28px;
    font-weight: 900;
    color: var(--green);
    display: block;
    text-shadow: 0 0 20px rgba(0,255,136,0.5);
  }
  .stat-label {
    font-family: var(--font-mono);
    font-size: 11px;
    color: var(--muted);
    letter-spacing: 1px;
    text-transform: uppercase;
  }

  /* ─── TERMINAL FOOTER ─── */
  .terminal {
    background: #010a04;
    border: 1px solid var(--border);
    border-radius: 4px;
    padding: 20px 24px;
    font-family: var(--font-mono);
    font-size: 13px;
    margin-top: 48px;
  }
  .terminal .t-line { margin-bottom: 6px; color: var(--muted); }
  .terminal .t-line .prompt { color: var(--green); margin-right: 8px; }
  .terminal .t-line .cmd { color: var(--text); }
  .terminal .t-line .output { color: var(--cyan); }
  .terminal .cursor {
    display: inline-block;
    width: 8px;
    height: 14px;
    background: var(--green);
    animation: blink 1s step-end infinite;
    vertical-align: middle;
  }

  /* ─── RESPONSIVE ─── */
  @media (max-width: 600px) {
    .header {
      grid-template-columns: 1fr;
      text-align: center;
    }
    .avatar-ring { margin: 0 auto; }
    .badges, .social-links { justify-content: center; }
    .projects-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>
<div class="wrapper">

  <!-- ══ HEADER ══ -->
  <header class="header">
    <div class="avatar-ring">
      <div class="avatar-placeholder">R</div>
      <span class="online-dot"></span>
    </div>
    <div class="header-info">
      <div class="prompt-line"><span>~/security</span> $ whoami</div>
      <h1>Ruby <span class="accent">_</span></h1>
      <div class="tagline">[ Ethical Hacker · Security Researcher · Python Dev ]</div>
      <div class="badges">
        <span class="badge"><span class="dot"></span>Junior IT</span>
        <span class="badge"><span class="dot red"></span>Pentester</span>
        <span class="badge"><span class="dot cyan"></span>CCNA</span>
        <span class="badge"><span class="dot"></span>Cisco NetAcad</span>
        <span class="badge"><span class="dot"></span>Digitech FP Málaga</span>
        <span class="badge"><span class="dot cyan"></span>AI + Security</span>
      </div>
      <div class="social-links">
        <a href="https://github.com/Ruby570bocadito" class="social-link" target="_blank">
          <span class="icon">⌥</span> GitHub
        </a>
        <a href="https://apuntes-8.gitbook.io/ciber-apuntes/" class="social-link" target="_blank">
          <span class="icon">📖</span> CiberApuntes
        </a>
      </div>
    </div>
  </header>

  <!-- ══ ABOUT ══ -->
  <div class="about">
    <p>
      Estudiante de <strong>Ciberseguridad en Cisco NetAcad</strong> y alumno de <strong>Digitech FP Málaga</strong>,
      apasionado del <strong>ethical hacking</strong>, la seguridad ofensiva y la intersección entre
      <strong>Inteligencia Artificial y Pentesting</strong>. Construyo herramientas reales que combinan
      <strong>LLM · Machine Learning</strong> con técnicas de hacking ético.
      Mantengo una <a href="https://apuntes-8.gitbook.io/ciber-apuntes/" target="_blank">biblioteca documentada de ciberseguridad ofensiva</a>
      — mis propios apuntes, técnicas y recursos para la comunidad.
    </p>
  </div>

  <!-- ══ STATS ══ -->
  <div class="stats-row">
    <div class="stat-card">
      <span class="stat-num">4</span>
      <span class="stat-label">Proyectos activos</span>
    </div>
    <div class="stat-card">
      <span class="stat-num">16+</span>
      <span class="stat-label">Cursos completados</span>
    </div>
    <div class="stat-card">
      <span class="stat-num">3</span>
      <span class="stat-label">Años C++ / gamedev</span>
    </div>
    <div class="stat-card">
      <span class="stat-num">B1</span>
      <span class="stat-label">Inglés certificado</span>
    </div>
  </div>

  <!-- ══ SKILLS ══ -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>// Skills &amp; Arsenal</h2>
      <div class="line"></div>
    </div>
    <div class="skills-grid">
      <div class="skill-card">
        <div class="skill-card-header">
          <div class="skill-icon">🛡</div>
          <div class="skill-title">Offensive Security</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">Pentesting</span>
          <span class="skill-tag">Metasploit</span>
          <span class="skill-tag">Kali Linux</span>
          <span class="skill-tag">Privilege Escalation</span>
          <span class="skill-tag">OSINT</span>
          <span class="skill-tag">Web Hacking</span>
          <span class="skill-tag">WiFi Hacking</span>
          <span class="skill-tag">Social Engineering</span>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-card-header">
          <div class="skill-icon">🤖</div>
          <div class="skill-title">AI + ML Security</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">LLM Integration</span>
          <span class="skill-tag">ML Automation</span>
          <span class="skill-tag">Vibe Hacking</span>
          <span class="skill-tag">AI-Powered Tools</span>
          <span class="skill-tag">Computer Vision</span>
          <span class="skill-tag">Gesture Control</span>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-card-header">
          <div class="skill-icon">🐍</div>
          <div class="skill-title">Programming</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">Python</span>
          <span class="skill-tag">C++</span>
          <span class="skill-tag">Bash / Shell</span>
          <span class="skill-tag">Scripting</span>
          <span class="skill-tag">Automation</span>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-card-header">
          <div class="skill-icon">🌐</div>
          <div class="skill-title">Networking</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">CCNA</span>
          <span class="skill-tag">TCP/IP</span>
          <span class="skill-tag">Network Analysis</span>
          <span class="skill-tag">Cisco IOS</span>
          <span class="skill-tag">Routing &amp; Switching</span>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-card-header">
          <div class="skill-icon">🦠</div>
          <div class="skill-title">Malware &amp; Privacy</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">Malware Analysis</span>
          <span class="skill-tag">Trojans / RAT</span>
          <span class="skill-tag">Android Hacking</span>
          <span class="skill-tag">Deep Web</span>
          <span class="skill-tag">Anonymity &amp; OPSEC</span>
          <span class="skill-tag">Phishing</span>
        </div>
      </div>
      <div class="skill-card">
        <div class="skill-card-header">
          <div class="skill-icon">🧠</div>
          <div class="skill-title">Tools &amp; Platforms</div>
        </div>
        <div class="skill-tags">
          <span class="skill-tag">Linux</span>
          <span class="skill-tag">Kali</span>
          <span class="skill-tag">Burp Suite</span>
          <span class="skill-tag">Nmap</span>
          <span class="skill-tag">ChatGPT + Hacking</span>
          <span class="skill-tag">Git</span>
          <span class="skill-tag">GitBook</span>
        </div>
      </div>
    </div>
  </section>

  <!-- ══ PROJECTS ══ -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>// Proyectos destacados</h2>
      <div class="line"></div>
    </div>
    <div class="projects-grid">
      <a href="https://github.com/Ruby570bocadito/SPECTER-AI-Powered-Offensive-Security-Terminal" class="project-card" target="_blank">
        <div class="project-name">
          SPECTER — AI Offensive Security Terminal
          <span class="arrow">→</span>
        </div>
        <div class="project-desc">
          Terminal ofensiva potenciada con <strong>IA/LLM</strong>. Integra inteligencia artificial en flujos de pentesting para asistencia táctica y automatización de ataques.
        </div>
        <div class="project-tags">
          <span class="project-tag red">Offensive Security</span>
          <span class="project-tag green">Python</span>
          <span class="project-tag cyan">LLM</span>
        </div>
      </a>

      <a href="https://github.com/Ruby570bocadito/Vibe-Hacking-ML-Automation" class="project-card" target="_blank">
        <div class="project-name">
          Vibe Hacking — ML Automation
          <span class="arrow">→</span>
        </div>
        <div class="project-desc">
          Automatización de técnicas de hacking mediante <strong>Machine Learning</strong>. Explora el concepto de "vibe hacking" asistido por IA para pruebas de seguridad.
        </div>
        <div class="project-tags">
          <span class="project-tag green">ML</span>
          <span class="project-tag cyan">Automation</span>
          <span class="project-tag red">Hacking</span>
        </div>
      </a>

      <a href="https://github.com/Ruby570bocadito/Wormy-ML-Network-Worm" class="project-card" target="_blank">
        <div class="project-name">
          Wormy — ML Network Worm
          <span class="arrow">→</span>
        </div>
        <div class="project-desc">
          Investigación sobre propagación de gusanos de red con comportamiento adaptativo mediante <strong>ML</strong>. Proyecto educativo de seguridad ofensiva avanzada.
        </div>
        <div class="project-tags">
          <span class="project-tag red">Network Security</span>
          <span class="project-tag green">Python</span>
          <span class="project-tag cyan">ML Research</span>
        </div>
      </a>

      <a href="https://github.com/Ruby570bocadito/GestureOS-ComputerControl-ML" class="project-card" target="_blank">
        <div class="project-name">
          GestureOS — Computer Control ML
          <span class="arrow">→</span>
        </div>
        <div class="project-desc">
          Control de sistema operativo mediante <strong>reconocimiento de gestos con ML</strong> y visión por computador. Exploración de interfaces alternativas HCI + seguridad.
        </div>
        <div class="project-tags">
          <span class="project-tag cyan">Computer Vision</span>
          <span class="project-tag green">ML</span>
          <span class="project-tag green">Python</span>
        </div>
      </a>
    </div>
  </section>

  <!-- ══ CERTIFICATIONS ══ -->
  <section>
    <div class="section-label">
      <div class="line"></div>
      <h2>// Formación &amp; Certificaciones</h2>
      <div class="line"></div>
    </div>

    <div style="margin-bottom:20px;">
      <div style="font-family:var(--font-mono);font-size:11px;color:var(--muted);letter-spacing:2px;margin-bottom:12px;">— CISCO &amp; ACADEMIAS —</div>
      <div class="certs-wrapper">
        <div class="cert-item">
          <div class="cert-bullet cyan"></div>
          <div class="cert-text">
            <div class="cert-name">CCNA — Cisco Certified Network Associate</div>
            <div class="cert-source">Cisco Networking Academy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet cyan"></div>
          <div class="cert-text">
            <div class="cert-name">Ethical Hacker Certificate</div>
            <div class="cert-source">Cisco NetAcad</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Python Essentials 1</div>
            <div class="cert-source">Cisco Academy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Introducción a la Ciberseguridad</div>
            <div class="cert-source">Cisco Academy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Conceptos Básicos de Redes</div>
            <div class="cert-source">Cisco Academy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Linux Unhatched</div>
            <div class="cert-source">Cisco Academy</div>
          </div>
        </div>
      </div>
    </div>

    <div style="margin-bottom:20px;">
      <div style="font-family:var(--font-mono);font-size:11px;color:var(--muted);letter-spacing:2px;margin-bottom:12px;">— UDEMY —</div>
      <div class="certs-wrapper">
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Máster en Pentesting y Hacking Ético</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético con Kali Linux</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético con Metasploit Framework</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Escalada de Privilegios en Linux</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético a Dispositivos Móviles Android</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético a Redes WiFi</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Curso de Hacking Ético Web — Pentesting</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet red"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético a Redes Sociales</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Anonimato en la Red: Privacidad y Deep Web</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Seguridad Informática desde Cero</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Curso Completo de Hacking Ético — Aprende Todo</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">OSINT para Principiantes</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">ChatGPT para Hacking Ético</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético — Virus, Troyanos, Malware</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético a PC con Malware</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Detectar y Defenderte del Phishing</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Hacking Ético desde Dispositivos Android</div>
            <div class="cert-source">Udemy</div>
          </div>
        </div>
      </div>
    </div>

    <div>
      <div style="font-family:var(--font-mono);font-size:11px;color:var(--muted);letter-spacing:2px;margin-bottom:12px;">— OTROS —</div>
      <div class="certs-wrapper">
        <div class="cert-item">
          <div class="cert-bullet cyan"></div>
          <div class="cert-text">
            <div class="cert-name">Bootcamp Programación Videojuegos — C++ (3 años)</div>
            <div class="cert-source">Evad Kids</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet cyan"></div>
          <div class="cert-text">
            <div class="cert-name">Desarrollo con IA de 0 a Producción</div>
            <div class="cert-source">Brais Moure · mouredev</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet cyan"></div>
          <div class="cert-text">
            <div class="cert-name">Cátedra Lamar IA Edison</div>
            <div class="cert-source">Formación Avanzada</div>
          </div>
        </div>
        <div class="cert-item">
          <div class="cert-bullet"></div>
          <div class="cert-text">
            <div class="cert-name">Cambridge B1 — Inglés Certificado</div>
            <div class="cert-source">Certificación Oficial</div>
          </div>
        </div>
      </div>
    </div>
  </section>

  <!-- ══ TERMINAL ══ -->
  <div class="terminal">
    <div class="t-line"><span class="prompt">ruby@kali:~$</span><span class="cmd"> nmap -sV --script vuln target.htb</span></div>
    <div class="t-line"><span class="output">Starting Nmap — always ethical, always learning.</span></div>
    <div class="t-line"><span class="prompt">ruby@kali:~$</span><span class="cmd"> cat /etc/motd</span></div>
    <div class="t-line"><span class="output">"The quieter you become, the more you are able to hear." — Kali</span></div>
    <div class="t-line"><span class="prompt">ruby@kali:~$</span><span class="cursor"></span></div>
  </div>

</div>
</body>
</html>
