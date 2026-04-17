<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>BIJU – Biblioteca Jurídica Universitaria</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;600;700&family=Source+Sans+3:wght@300;400;600&display=swap" rel="stylesheet">
<style>
  :root {
    --gold: #C49A2A;
    --gold-light: #E8C96A;
    --navy: #0D1B2A;
    --navy-mid: #1A2E44;
    --cream: #FAF7F2;
    --cream-dark: #F0EAE0;
    --text: #1A1209;
    --text-mid: #4A3F30;
    --text-light: #7A6E60;
    --white: #FFFFFF;
    --border: rgba(196,154,42,0.25);
    --radius: 10px;
    --serif: 'Playfair Display', Georgia, serif;
    --sans: 'Source Sans 3', sans-serif;
  }
  * { margin: 0; padding: 0; box-sizing: border-box; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--cream);
    color: var(--text);
    font-family: var(--sans);
    font-size: 16px;
    line-height: 1.7;
  }

  /* NAV */
  nav {
    position: fixed; top: 0; left: 0; right: 0; z-index: 999;
    background: var(--navy);
    border-bottom: 2px solid var(--gold);
    display: flex; align-items: center; justify-content: space-between;
    padding: 0 2rem; height: 64px;
  }
  .nav-logo {
    font-family: var(--serif); font-size: 1.5rem; font-weight: 700;
    color: var(--gold-light); letter-spacing: 2px;
    text-decoration: none;
  }
  .nav-links { display: flex; gap: 1.5rem; list-style: none; }
  .nav-links a {
    color: #C8C0B0; font-size: 0.85rem; text-decoration: none;
    letter-spacing: 0.5px; transition: color 0.2s; text-transform: uppercase;
  }
  .nav-links a:hover { color: var(--gold-light); }

  /* HERO */
  .hero {
    margin-top: 64px;
    background: linear-gradient(135deg, var(--navy) 0%, #1B3A5C 60%, var(--navy-mid) 100%);
    padding: 5rem 2rem 4rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .hero::before {
    content: '';
    position: absolute; inset: 0;
    background: repeating-linear-gradient(
      45deg,
      transparent,
      transparent 40px,
      rgba(196,154,42,0.04) 40px,
      rgba(196,154,42,0.04) 41px
    );
  }
  .hero-badge {
    display: inline-block;
    border: 1px solid var(--gold);
    color: var(--gold-light);
    font-size: 0.75rem; letter-spacing: 3px; text-transform: uppercase;
    padding: 4px 18px; border-radius: 2px; margin-bottom: 1.5rem;
    position: relative;
  }
  .hero h1 {
    font-family: var(--serif); font-size: clamp(2.4rem, 5vw, 3.8rem);
    color: var(--white); font-weight: 700; line-height: 1.2;
    margin-bottom: 1rem; position: relative;
  }
  .hero h1 span { color: var(--gold-light); }
  .hero p {
    color: #A8B8CC; font-size: 1.1rem; max-width: 560px;
    margin: 0 auto 2.5rem; position: relative;
  }
  .hero-actions { display: flex; gap: 1rem; justify-content: center; flex-wrap: wrap; position: relative; }
  .btn-primary {
    background: var(--gold); color: var(--navy); font-family: var(--sans);
    font-weight: 600; font-size: 0.9rem; letter-spacing: 0.5px;
    padding: 12px 28px; border: none; border-radius: var(--radius);
    cursor: pointer; text-decoration: none; transition: all 0.2s;
  }
  .btn-primary:hover { background: var(--gold-light); transform: translateY(-1px); }
  .btn-outline {
    background: transparent; color: var(--gold-light);
    border: 1.5px solid var(--gold); font-family: var(--sans);
    font-weight: 600; font-size: 0.9rem; letter-spacing: 0.5px;
    padding: 12px 28px; border-radius: var(--radius);
    cursor: pointer; text-decoration: none; transition: all 0.2s;
  }
  .btn-outline:hover { background: rgba(196,154,42,0.12); }

  /* STATS BAR */
  .stats-bar {
    background: var(--navy-mid);
    border-bottom: 1px solid var(--border);
    display: flex; justify-content: center; gap: 0; flex-wrap: wrap;
  }
  .stat-item {
    padding: 1.2rem 2.5rem;
    text-align: center;
    border-right: 1px solid rgba(196,154,42,0.2);
  }
  .stat-item:last-child { border-right: none; }
  .stat-num { font-family: var(--serif); font-size: 1.8rem; color: var(--gold-light); font-weight: 700; }
  .stat-label { font-size: 0.75rem; color: #8898AA; letter-spacing: 0.5px; text-transform: uppercase; }

  /* SECTIONS */
  .section { padding: 4rem 2rem; max-width: 1100px; margin: 0 auto; }
  .section-header { text-align: center; margin-bottom: 3rem; }
  .section-eyebrow {
    display: inline-block; font-size: 0.72rem; letter-spacing: 3px;
    text-transform: uppercase; color: var(--gold); margin-bottom: 0.75rem;
  }
  .section-title {
    font-family: var(--serif); font-size: clamp(1.6rem, 3vw, 2.2rem);
    color: var(--navy); font-weight: 700; line-height: 1.3;
  }
  .section-title::after {
    content: '';
    display: block; width: 50px; height: 3px;
    background: var(--gold); margin: 0.8rem auto 0;
  }

  /* BOOKS GRID */
  .books-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    gap: 1.5rem;
  }
  .book-card {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
    cursor: pointer;
  }
  .book-card:hover { transform: translateY(-4px); box-shadow: 0 12px 30px rgba(13,27,42,0.12); }
  .book-cover {
    height: 200px;
    display: flex; align-items: center; justify-content: center;
    position: relative; overflow: hidden;
    font-size: 3.5rem;
  }
  .book-cover-overlay {
    position: absolute; inset: 0;
    display: flex; align-items: flex-end; padding: 0.75rem;
  }
  .book-tag {
    background: rgba(196,154,42,0.9); color: var(--navy);
    font-size: 0.65rem; letter-spacing: 1px; text-transform: uppercase;
    padding: 2px 8px; border-radius: 2px; font-weight: 600;
  }
  .book-info { padding: 1rem 1rem 1.2rem; }
  .book-title {
    font-family: var(--serif); font-size: 0.95rem; font-weight: 600;
    color: var(--navy); margin-bottom: 0.25rem; line-height: 1.3;
  }
  .book-author { font-size: 0.8rem; color: var(--text-light); margin-bottom: 0.5rem; }
  .book-year { font-size: 0.75rem; color: var(--gold); font-weight: 600; }

  /* CATEGORIES */
  .categories {
    display: flex; flex-wrap: wrap; gap: 0.75rem;
    justify-content: center; margin-bottom: 2.5rem;
  }
  .cat-btn {
    background: var(--white); border: 1.5px solid var(--border);
    color: var(--text-mid); font-family: var(--sans); font-size: 0.82rem;
    padding: 6px 18px; border-radius: 50px; cursor: pointer;
    transition: all 0.2s; font-weight: 600;
  }
  .cat-btn:hover, .cat-btn.active {
    background: var(--gold); border-color: var(--gold); color: var(--navy);
  }

  /* CALIFICACION */
  .score-section {
    background: var(--navy);
    padding: 4rem 2rem;
  }
  .score-grid {
    max-width: 900px; margin: 0 auto;
    display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr));
    gap: 1.5rem;
  }
  .score-card {
    background: rgba(255,255,255,0.06);
    border: 1px solid rgba(196,154,42,0.3);
    border-radius: var(--radius);
    padding: 1.5rem;
    text-align: center;
    transition: background 0.2s;
  }
  .score-card:hover { background: rgba(196,154,42,0.08); }
  .score-icon { font-size: 2rem; margin-bottom: 0.75rem; }
  .score-label { font-size: 0.75rem; letter-spacing: 1.5px; text-transform: uppercase; color: #8898AA; margin-bottom: 0.5rem; }
  .score-value { font-family: var(--serif); font-size: 2.4rem; color: var(--gold-light); font-weight: 700; }
  .score-pts { font-size: 0.75rem; color: #8898AA; }
  .score-total {
    max-width: 900px; margin: 1.5rem auto 0;
    background: rgba(196,154,42,0.15);
    border: 1.5px solid var(--gold);
    border-radius: var(--radius);
    padding: 1.2rem 2rem;
    display: flex; justify-content: space-between; align-items: center;
    flex-wrap: wrap; gap: 1rem;
  }
  .score-total-label { color: var(--gold-light); font-size: 0.85rem; letter-spacing: 1px; text-transform: uppercase; }
  .score-total-value { font-family: var(--serif); font-size: 2rem; color: var(--white); font-weight: 700; }

  /* LEGAL PANELS */
  .legal-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }
  .legal-panel {
    background: var(--white);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
  }
  .legal-header {
    background: var(--navy);
    padding: 1.2rem 1.5rem;
    display: flex; align-items: center; gap: 0.75rem;
  }
  .legal-icon {
    width: 36px; height: 36px; border-radius: 50%;
    background: rgba(196,154,42,0.2);
    display: flex; align-items: center; justify-content: center;
    font-size: 1rem; flex-shrink: 0;
  }
  .legal-panel-title {
    font-family: var(--serif); color: var(--white); font-size: 1rem; font-weight: 600;
  }
  .legal-body { padding: 1.5rem; }
  .legal-body p { font-size: 0.9rem; color: var(--text-mid); margin-bottom: 1rem; line-height: 1.7; }
  .legal-body p:last-child { margin-bottom: 0; }
  .legal-body strong { color: var(--navy); font-weight: 600; }

  /* SEGURIDAD */
  .security-items {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(240px, 1fr));
    gap: 1.5rem;
  }
  .security-item {
    background: var(--white);
    border-left: 4px solid var(--gold);
    border-radius: 0 var(--radius) var(--radius) 0;
    padding: 1.25rem 1.5rem;
    box-shadow: 0 2px 12px rgba(13,27,42,0.06);
  }
  .sec-icon { font-size: 1.6rem; margin-bottom: 0.6rem; }
  .sec-title { font-family: var(--serif); font-size: 1rem; font-weight: 600; color: var(--navy); margin-bottom: 0.4rem; }
  .sec-desc { font-size: 0.85rem; color: var(--text-mid); line-height: 1.6; }

  /* SEARCH */
  .search-bar {
    max-width: 600px; margin: 0 auto 2.5rem;
    position: relative;
  }
  .search-bar input {
    width: 100%;
    padding: 14px 20px 14px 50px;
    border: 2px solid var(--border);
    border-radius: 50px;
    font-family: var(--sans); font-size: 0.95rem;
    background: var(--white);
    color: var(--text);
    outline: none;
    transition: border-color 0.2s;
  }
  .search-bar input:focus { border-color: var(--gold); }
  .search-bar::before {
    content: '🔍';
    position: absolute; left: 18px; top: 50%; transform: translateY(-50%);
    font-size: 1.1rem; pointer-events: none;
  }

  /* FOOTER */
  footer {
    background: var(--navy);
    border-top: 2px solid var(--gold);
    padding: 3rem 2rem 2rem;
    text-align: center;
  }
  footer .footer-logo {
    font-family: var(--serif); font-size: 2rem; color: var(--gold-light);
    font-weight: 700; letter-spacing: 3px; margin-bottom: 0.5rem;
  }
  footer p { color: #6A7A8A; font-size: 0.85rem; margin-bottom: 0.3rem; }
  footer .footer-links { display: flex; justify-content: center; gap: 2rem; margin: 1.5rem 0; flex-wrap: wrap; }
  footer .footer-links a { color: #8898AA; font-size: 0.82rem; text-decoration: none; }
  footer .footer-links a:hover { color: var(--gold-light); }
  footer .footer-copy { font-size: 0.78rem; color: #4A5A6A; margin-top: 1.5rem; }

  /* DIVIDER */
  .divider {
    border: none;
    border-top: 1px solid var(--border);
    max-width: 1100px;
    margin: 0 auto;
  }
  .bg-cream-dark { background: var(--cream-dark); }
  .bg-white { background: var(--white); }

  /* MODAL */
  .modal-overlay {
    position: fixed; inset: 0;
    background: rgba(13,27,42,0.75);
    z-index: 1000;
    display: flex; align-items: center; justify-content: center;
    padding: 1rem;
    opacity: 0; pointer-events: none; transition: opacity 0.3s;
  }
  .modal-overlay.open { opacity: 1; pointer-events: all; }
  .modal {
    background: var(--white); border-radius: 12px;
    max-width: 540px; width: 100%;
    max-height: 80vh; overflow-y: auto;
    padding: 2rem;
    transform: translateY(20px); transition: transform 0.3s;
  }
  .modal-overlay.open .modal { transform: translateY(0); }
  .modal h3 { font-family: var(--serif); font-size: 1.3rem; color: var(--navy); margin-bottom: 1rem; }
  .modal p { font-size: 0.9rem; color: var(--text-mid); margin-bottom: 0.75rem; line-height: 1.7; }
  .modal-close {
    float: right; background: none; border: none;
    font-size: 1.4rem; cursor: pointer; color: var(--text-light);
    margin-left: 1rem;
  }
  .modal-cover-big {
    width: 100%; height: 160px;
    border-radius: 8px; margin-bottom: 1.2rem;
    display: flex; align-items: center; justify-content: center;
    font-size: 5rem;
  }

  @media (max-width: 600px) {
    .nav-links { display: none; }
    .stat-item { padding: 1rem 1.2rem; }
    .score-total { flex-direction: column; text-align: center; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#inicio" class="nav-logo">BIJU</a>
  <ul class="nav-links">
    <li><a href="#catalogo">Catálogo</a></li>
    <li><a href="#calificacion">Evaluación</a></li>
    <li><a href="#seguridad">Seguridad</a></li>
    <li><a href="#privacidad">Legal</a></li>
    <li><a href="#contacto">Contacto</a></li>
  </ul>
</nav>

<!-- HERO -->
<section class="hero" id="inicio">
  <div class="hero-badge">Biblioteca Jurídica Universitaria</div>
  <h1>Derecho al<br><span>Conocimiento</span> Jurídico</h1>
  <p>BIJU reúne las obras fundamentales del derecho para estudiantes, académicos y profesionales del área jurídica.</p>
  <div class="hero-actions">
    <a href="#catalogo" class="btn-primary">Explorar Catálogo</a>
    <a href="#privacidad" class="btn-outline">Aviso de Privacidad</a>
  </div>
</section>

<!-- STATS -->
<div class="stats-bar">
  <div class="stat-item">
    <div class="stat-num">500+</div>
    <div class="stat-label">Títulos jurídicos</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">12</div>
    <div class="stat-label">Áreas del derecho</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">40</div>
    <div class="stat-label">Pts. evaluación total</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">100%</div>
    <div class="stat-label">Acceso seguro</div>
  </div>
</div>

<!-- CATÁLOGO -->
<section id="catalogo" style="padding: 4rem 2rem; background: var(--cream-dark);">
  <div class="section-header">
    <span class="section-eyebrow">Acervo bibliográfico</span>
    <h2 class="section-title">Catálogo Jurídico</h2>
  </div>

  <div class="categories">
    <button class="cat-btn active" onclick="filterBooks('all',this)">Todos</button>
    <button class="cat-btn" onclick="filterBooks('constitucional',this)">Constitucional</button>
    <button class="cat-btn" onclick="filterBooks('penal',this)">Penal</button>
    <button class="cat-btn" onclick="filterBooks('civil',this)">Civil</button>
    <button class="cat-btn" onclick="filterBooks('mercantil',this)">Mercantil</button>
    <button class="cat-btn" onclick="filterBooks('laboral',this)">Laboral</button>
    <button class="cat-btn" onclick="filterBooks('internacional',this)">Internacional</button>
  </div>

  <div class="search-bar">
    <input type="text" placeholder="Buscar libro, autor o tema..." oninput="searchBooks(this.value)">
  </div>

  <div class="books-grid" id="booksGrid" style="max-width: 1100px; margin: 0 auto;">
  </div>
</section>

<!-- EVALUACIÓN / CALIFICACIÓN -->
<section id="calificacion" class="score-section">
  <div class="section-header" style="margin-bottom: 2.5rem;">
    <span class="section-eyebrow" style="color: var(--gold);">Sistema académico</span>
    <h2 class="section-title" style="color: var(--white);">Evaluación del Curso</h2>
  </div>

  <div class="score-grid">
    <div class="score-card">
      <div class="score-icon">📋</div>
      <div class="score-label">Tareas</div>
      <div class="score-value">5</div>
      <div class="score-pts">puntos</div>
    </div>
    <div class="score-card">
      <div class="score-icon">📝</div>
      <div class="score-label">Apuntes</div>
      <div class="score-value">15</div>
      <div class="score-pts">puntos</div>
    </div>
    <div class="score-card">
      <div class="score-icon">📰</div>
      <div class="score-label">Noticia</div>
      <div class="score-value">15</div>
      <div class="score-pts">puntos</div>
    </div>
    <div class="score-card">
      <div class="score-icon">🙋</div>
      <div class="score-label">Participación</div>
      <div class="score-value">5</div>
      <div class="score-pts">puntos + <span style="color: var(--gold-light);">+1 extra</span></div>
    </div>
  </div>

  <div class="score-total">
    <span class="score-total-label">Total de puntos</span>
    <div>
      <span class="score-total-value">40</span>
      <span style="color: #8898AA; font-size: 0.85rem; margin-left: 6px;">pts (+1 participación extra)</span>
    </div>
  </div>
</section>

<!-- MEDIDAS DE SEGURIDAD -->
<section id="seguridad" style="padding: 4rem 2rem; background: var(--cream-dark);">
  <div style="max-width: 1100px; margin: 0 auto;">
    <div class="section-header">
      <span class="section-eyebrow">Ciberseguridad</span>
      <h2 class="section-title">Medidas de Seguridad</h2>
      <p style="color: var(--text-mid); max-width: 560px; margin: 1rem auto 0; font-size: 0.95rem;">
        BIJU implementa protocolos de seguridad informática para proteger la información de todos sus usuarios conforme a la normatividad vigente.
      </p>
    </div>
    <div class="security-items">
      <div class="security-item">
        <div class="sec-icon">🔐</div>
        <div class="sec-title">Cifrado SSL/TLS</div>
        <div class="sec-desc">Toda la comunicación entre el usuario y la plataforma está cifrada mediante protocolos SSL/TLS de 256 bits, garantizando la confidencialidad de los datos.</div>
      </div>
      <div class="security-item">
        <div class="sec-icon">🛡️</div>
        <div class="sec-title">Control de acceso</div>
        <div class="sec-desc">Sistema de autenticación con contraseñas seguras y verificación de identidad. Sesiones con tiempo de expiración automático por inactividad.</div>
      </div>
      <div class="security-item">
        <div class="sec-icon">🔒</div>
        <div class="sec-title">Protección de datos</div>
        <div class="sec-desc">Los datos personales son almacenados de forma segura y protegida, cumpliendo con la Ley Federal de Protección de Datos Personales (LFPDPPP).</div>
      </div>
      <div class="security-item">
        <div class="sec-icon">🧱</div>
        <div class="sec-title">Firewall y monitoreo</div>
        <div class="sec-desc">Sistemas de firewall activos con monitoreo continuo para detectar y prevenir accesos no autorizados, ataques de fuerza bruta y amenazas cibernéticas.</div>
      </div>
      <div class="security-item">
        <div class="sec-icon">💾</div>
        <div class="sec-title">Respaldos periódicos</div>
        <div class="sec-desc">Se realizan copias de seguridad periódicas del acervo y datos de usuarios para garantizar la disponibilidad e integridad de la información.</div>
      </div>
      <div class="security-item">
        <div class="sec-icon">🚨</div>
        <div class="sec-title">Respuesta a incidentes</div>
        <div class="sec-desc">Protocolo de respuesta ante incidentes de seguridad con notificación a usuarios afectados en un plazo no mayor a 72 horas, conforme a la normativa aplicable.</div>
      </div>
    </div>
  </div>
</section>

<!-- AVISO DE PRIVACIDAD Y TÉRMINOS -->
<section id="privacidad" style="padding: 4rem 2rem; background: var(--white);">
  <div style="max-width: 1100px; margin: 0 auto;">
    <div class="section-header">
      <span class="section-eyebrow">Información legal</span>
      <h2 class="section-title">Aviso de Privacidad y Términos</h2>
    </div>
    <div class="legal-grid">

      <!-- Aviso de Privacidad -->
      <div class="legal-panel">
        <div class="legal-header">
          <div class="legal-icon">🔏</div>
          <div class="legal-panel-title">Aviso de Privacidad</div>
        </div>
        <div class="legal-body">
          <p><strong>Responsable:</stron
