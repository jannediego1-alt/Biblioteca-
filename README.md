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
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <a href="#inicio" class="nav-logo">BIJU</a>
  <ul class="nav-links">
    <li><a href="#catalogo">Catálogo</a></li>
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
  <div style="max-width: 900px; margin: 0 auto;">
    <div class="section-header">
      <span class="section-eyebrow">Información legal</span>
      <h2 class="section-title">Documentos Legales</h2>
      <p style="color: var(--text-mid); max-width: 560px; margin: 1rem auto 0; font-size: 0.95rem;">
        Consulta nuestros documentos legales vigentes. Haz clic en cada tarjeta para leer el documento completo.
      </p>
    </div>

    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr)); gap: 1.5rem;">

      <!-- Card Aviso de Privacidad -->
      <div onclick="openLegal('privacidad')" style="background: var(--white); border: 1.5px solid var(--border); border-radius: var(--radius); overflow: hidden; cursor: pointer; transition: transform 0.2s, box-shadow 0.2s;" onmouseover="this.style.transform='translateY(-4px)';this.style.boxShadow='0 12px 30px rgba(13,27,42,0.10)'" onmouseout="this.style.transform='';this.style.boxShadow=''">
        <div style="background: var(--navy); padding: 2rem; text-align: center;">
          <div style="font-size: 3rem; margin-bottom: 0.5rem;">🔏</div>
          <div style="font-family: var(--serif); color: var(--white); font-size: 1.1rem; font-weight: 600;">Aviso de Privacidad</div>
          <div style="font-size: 0.75rem; color: var(--gold-light); letter-spacing: 1px; margin-top: 0.3rem;">LFPDPPP</div>
        </div>
        <div style="padding: 1.25rem 1.5rem;">
          <p style="font-size: 0.85rem; color: var(--text-mid); margin-bottom: 1rem; line-height: 1.6;">Conoce cómo BIJU recopila, usa y protege tus datos personales conforme a la legislación mexicana vigente.</p>
          <div style="display: flex; justify-content: space-between; align-items: center;">
            <span style="font-size: 0.75rem; color: var(--text-light);">Última actualización: 2026</span>
            <span style="background: var(--gold); color: var(--navy); font-size: 0.75rem; font-weight: 700; padding: 4px 14px; border-radius: 50px;">Ver documento →</span>
          </div>
        </div>
      </div>

      <!-- Card Términos y Condiciones -->
      <div onclick="openLegal('terminos')" style="background: var(--white); border: 1.5px solid var(--border); border-radius: var(--radius); overflow: hidden; cursor: pointer; transition: transform 0.2s, box-shadow 0.2s;" onmouseover="this.style.transform='translateY(-4px)';this.style.boxShadow='0 12px 30px rgba(13,27,42,0.10)'" onmouseout="this.style.transform='';this.style.boxShadow=''">
        <div style="background: var(--navy-mid); padding: 2rem; text-align: center;">
          <div style="font-size: 3rem; margin-bottom: 0.5rem;">📜</div>
          <div style="font-family: var(--serif); color: var(--white); font-size: 1.1rem; font-weight: 600;">Términos y Condiciones</div>
          <div style="font-size: 0.75rem; color: var(--gold-light); letter-spacing: 1px; margin-top: 0.3rem;">Uso de la plataforma</div>
        </div>
        <div style="padding: 1.25rem 1.5rem;">
          <p style="font-size: 0.85rem; color: var(--text-mid); margin-bottom: 1rem; line-height: 1.6;">Reglas de uso de la plataforma, derechos y obligaciones de los usuarios, préstamos digitales y legislación aplicable.</p>
          <div style="display: flex; justify-content: space-between; align-items: center;">
            <span style="font-size: 0.75rem; color: var(--text-light);">Última actualización: 2026</span>
            <span style="background: var(--gold); color: var(--navy); font-size: 0.75rem; font-weight: 700; padding: 4px 14px; border-radius: 50px;">Ver documento →</span>
          </div>
        </div>
      </div>

      <!-- Card Ciberseguridad -->
      <div onclick="document.getElementById('seguridad').scrollIntoView({behavior:'smooth'})" style="background: var(--white); border: 1.5px solid var(--border); border-radius: var(--radius); overflow: hidden; cursor: pointer; transition: transform 0.2s, box-shadow 0.2s;" onmouseover="this.style.transform='translateY(-4px)';this.style.boxShadow='0 12px 30px rgba(13,27,42,0.10)'" onmouseout="this.style.transform='';this.style.boxShadow=''">
        <div style="background: #0D3040; padding: 2rem; text-align: center;">
          <div style="font-size: 3rem; margin-bottom: 0.5rem;">🛡️</div>
          <div style="font-family: var(--serif); color: var(--white); font-size: 1.1rem; font-weight: 600;">Medidas de Seguridad</div>
          <div style="font-size: 0.75rem; color: var(--gold-light); letter-spacing: 1px; margin-top: 0.3rem;">Ciberseguridad</div>
        </div>
        <div style="padding: 1.25rem 1.5rem;">
          <p style="font-size: 0.85rem; color: var(--text-mid); margin-bottom: 1rem; line-height: 1.6;">Protocolos de cifrado, control de acceso, firewall y respuesta ante incidentes que protegen tu información.</p>
          <div style="display: flex; justify-content: space-between; align-items: center;">
            <span style="font-size: 0.75rem; color: var(--text-light);">SSL/TLS · Firewall · ARCO</span>
            <span style="background: var(--gold); color: var(--navy); font-size: 0.75rem; font-weight: 700; padding: 4px 14px; border-radius: 50px;">Ver sección →</span>
          </div>
        </div>
      </div>

    </div>
  </div>
</section>

<!-- MODALES LEGALES -->
<div class="modal-overlay" id="legalModal" onclick="closeLegalModal(event)">
  <div class="modal" id="legalModalContent" style="max-width: 680px;"></div>
</div>

<!-- CONTACTO -->
<section id="contacto" style="padding: 4rem 2rem; background: var(--cream-dark);">
  <div style="max-width: 700px; margin: 0 auto; text-align: center;">
    <div class="section-header">
      <span class="section-eyebrow">Comunícate con nosotros</span>
      <h2 class="section-title">Contacto</h2>
    </div>
    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(180px, 1fr)); gap: 1.5rem; text-align: left; margin-top: 2rem;">
      <div style="background: var(--white); border: 1px solid var(--border); border-radius: var(--radius); padding: 1.2rem;">
        <div style="font-size: 1.5rem; margin-bottom: 0.5rem;">📧</div>
        <div style="font-size: 0.78rem; color: var(--text-light); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 0.25rem;">Correo general</div>
        <div style="font-size: 0.9rem; color: var(--navy); font-weight: 600;">contacto@biju.edu.mx</div>
      </div>
      <div style="background: var(--white); border: 1px solid var(--border); border-radius: var(--radius); padding: 1.2rem;">
        <div style="font-size: 1.5rem; margin-bottom: 0.5rem;">🔏</div>
        <div style="font-size: 0.78rem; color: var(--text-light); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 0.25rem;">Privacidad</div>
        <div style="font-size: 0.9rem; color: var(--navy); font-weight: 600;">privacidad@biju.edu.mx</div>
      </div>
      <div style="background: var(--white); border: 1px solid var(--border); border-radius: var(--radius); padding: 1.2rem;">
        <div style="font-size: 1.5rem; margin-bottom: 0.5rem;">🚨</div>
        <div style="font-size: 0.78rem; color: var(--text-light); text-transform: uppercase; letter-spacing: 1px; margin-bottom: 0.25rem;">Seguridad</div>
        <div style="font-size: 0.9rem; color: var(--navy); font-weight: 600;">seguridad@biju.edu.mx</div>
      </div>
    </div>
  </div>
</section>

<!-- FOOTER -->
<footer>
  <div class="footer-logo">BIJU</div>
  <p>Biblioteca Jurídica Universitaria</p>
  <div class="footer-links">
    <a href="#catalogo">Catálogo</a>
    <a href="#seguridad">Ciberseguridad</a>
    <a href="#privacidad">Aviso de Privacidad</a>
    <a href="#privacidad">Términos y Condiciones</a>
    <a href="#contacto">Contacto</a>
  </div>
  <div class="footer-copy">© 2026 BIJU – Biblioteca Jurídica Universitaria. Todos los derechos reservados. | México</div>
</footer>

<!-- MODAL -->
<div class="modal-overlay" id="bookModal" onclick="closeModal(event)">
  <div class="modal" id="modalContent"></div>
</div>

<script>
const books = [
  { id:1, emoji:'⚖️', title:'Constitución Política de los Estados Unidos Mexicanos', author:'Congreso de la Unión', year:'2024', cat:'constitucional', color:'#1A2E44', desc:'Texto constitucional vigente con sus más de 700 artículos que establecen la organización política y los derechos fundamentales de México.' },
  { id:2, emoji:'📖', title:'Teoría del Derecho', author:'Manuel Atienza', year:'2018', cat:'constitucional', color:'#2D4A6A', desc:'Obra fundamental sobre los conceptos básicos del derecho, la norma jurídica y la metodología del pensamiento jurídico moderno.' },
  { id:3, emoji:'🔨', title:'Código Penal Federal', author:'Diario Oficial de la Federación', year:'2023', cat:'penal', color:'#4A1B0C', desc:'Compilación actualizada del Código Penal Federal mexicano con todas las reformas vigentes y notas explicativas.' },
  { id:4, emoji:'🧾', title:'Derecho Civil. Parte General', author:'Rafael Rojina Villegas', year:'2020', cat:'civil', color:'#0D3B2E', desc:'Clásico del derecho civil mexicano que abarca personas, familia, bienes y obligaciones en el sistema jurídico nacional.' },
  { id:5, emoji:'🏢', title:'Ley General de Sociedades Mercantiles', author:'Cámara de Diputados', year:'2023', cat:'mercantil', color:'#2A1A00', desc:'Texto completo y actualizado de la LGSM con comentarios sobre tipos societarios, asambleas y responsabilidades.' },
  { id:6, emoji:'👷', title:'Ley Federal del Trabajo', author:'Secretaría del Trabajo', year:'2024', cat:'laboral', color:'#1A2E44', desc:'Compilación integral de la LFT con las más recientes reformas en materia laboral, sindical y de seguridad social.' },
  { id:7, emoji:'🌍', title:'Derecho Internacional Público', author:'César Sepúlveda', year:'2019', cat:'internacional', color:'#0D3B4A', desc:'Referencia esencial sobre los principios del derecho internacional, tratados, organismos y relaciones entre estados soberanos.' },
  { id:8, emoji:'👨‍⚖️', title:'El Juicio de Amparo', author:'Ignacio Burgoa Orihuela', year:'2020', cat:'constitucional', color:'#1A0D2E', desc:'La obra definitiva sobre el amparo mexicano. Estudia sus fundamentos constitucionales, procedencia, efectos y jurisprudencia.' },
  { id:9, emoji:'💼', title:'Derecho Mercantil Mexicano', author:'Felipe de J. Tena', year:'2021', cat:'mercantil', color:'#2A1A00', desc:'Análisis clásico del régimen jurídico del comercio en México: comerciantes, actos de comercio, contratos y títulos de crédito.' },
  { id:10, emoji:'🏛️', title:'Derecho Administrativo', author:'Gabino Fraga', year:'2022', cat:'constitucional', color:'#2D4A6A', desc:'Estudio sistemático del derecho administrativo mexicano: organización del Estado, acto administrativo y responsabilidad pública.' },
  { id:11, emoji:'⚡', title:'Criminología y Derecho Penal', author:'Luis Rodríguez Manzanera', year:'2021', cat:'penal', color:'#4A1B0C', desc:'Análisis interdisciplinario sobre la conducta delictiva, la victimología y las políticas criminológicas contemporáneas.' },
  { id:12, emoji:'📋', title:'Contratos Civiles', author:'Ernesto Gutiérrez y González', year:'2020', cat:'civil', color:'#0D3B2E', desc:'Tratado detallado sobre la teoría general del contrato, clasificación, efectos y los contratos típicos del derecho civil mexicano.' },
];

let activeFilter = 'all';
let searchQuery = '';

function renderBooks() {
  const grid = document.getElementById('booksGrid');
  const filtered = books.filter(b => {
    const matchCat = activeFilter === 'all' || b.cat === activeFilter;
    const matchSearch = !searchQuery || b.title.toLowerCase().includes(searchQuery.toLowerCase()) || b.author.toLowerCase().includes(searchQuery.toLowerCase());
    return matchCat && matchSearch;
  });
  grid.innerHTML = filtered.map(b => `
    <div class="book-card" onclick="openBook(${b.id})">
      <div class="book-cover" style="background: ${b.color};">
        <span style="font-size: 3.5rem;">${b.emoji}</span>
        <div class="book-cover-overlay">
          <span class="book-tag">${b.cat.charAt(0).toUpperCase()+b.cat.slice(1)}</span>
        </div>
      </div>
      <div class="book-info">
        <div class="book-title">${b.title}</div>
        <div class="book-author">${b.author}</div>
        <div class="book-year">${b.year}</div>
      </div>
    </div>
  `).join('');
}

function filterBooks(cat, btn) {
  activeFilter = cat;
  document.querySelectorAll('.cat-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderBooks();
}

function searchBooks(val) {
  searchQuery = val;
  renderBooks();
}

function openBook(id) {
  const b = books.find(x => x.id === id);
  if (!b) return;
  document.getElementById('modalContent').innerHTML = `
    <button class="modal-close" onclick="document.getElementById('bookModal').classList.remove('open')">✕</button>
    <div class="modal-cover-big" style="background: ${b.color}; font-size: 5rem;">${b.emoji}</div>
    <h3>${b.title}</h3>
    <p><strong>Autor / Fuente:</strong> ${b.author}</p>
    <p><strong>Año de edición:</strong> ${b.year}</p>
    <p><strong>Área jurídica:</strong> ${b.cat.charAt(0).toUpperCase()+b.cat.slice(1)}</p>
    <p>${b.desc}</p>
    <button class="btn-primary" style="margin-top: 1rem; width: 100%;" onclick="document.getElementById('bookModal').classList.remove('open')">Cerrar</button>
  `;
  document.getElementById('bookModal').classList.add('open');
}

function closeModal(e) {
  if (e.target.id === 'bookModal') document.getElementById('bookModal').classList.remove('open');
}

renderBooks();

const legalDocs = {
  privacidad: {
    icon: '🔏',
    title: 'Aviso de Privacidad',
    subtitle: 'Biblioteca Jurídica Universitaria BIJU — Versión 2026',
    sections: [
      { heading: 'I. Identidad y domicilio del Responsable', body: 'Biblioteca Jurídica Universitaria BIJU (en adelante "BIJU"), con domicilio en la República Mexicana, es responsable del tratamiento de los datos personales que usted proporcione, de conformidad con lo establecido en la Ley Federal de Protección de Datos Personales en Posesión de los Particulares (LFPDPPP) y su Reglamento.' },
      { heading: 'II. Datos personales recabados', body: 'BIJU recaba los siguientes datos personales: nombre completo, correo electrónico institucional, número de matrícula o cédula profesional, área o rama de estudio jurídico, y dirección IP de acceso. No se recaban datos personales sensibles según la definición del artículo 3, fracción VI de la LFPDPPP.' },
      { heading: 'III. Finalidades del tratamiento', body: 'Los datos personales serán utilizados para las siguientes finalidades primarias: (a) gestionar el registro y acceso al catálogo bibliográfico; (b) administrar el sistema de préstamos digitales y físicos; (c) generar estadísticas de uso interno de forma anonimizada. Finalidades secundarias: (d) enviar notificaciones sobre nuevas adquisiciones bibliográficas y eventos académicos; (e) mejorar los servicios de la plataforma.' },
      { heading: 'IV. Transferencia de datos', body: 'BIJU no transferirá sus datos personales a terceros sin su consentimiento previo, salvo en los casos previstos en el artículo 37 de la LFPDPPP: (i) cuando sea requerido por autoridad competente mediante orden judicial o administrativa; (ii) cuando sea necesario para el cumplimiento de una obligación legal; (iii) cuando la transferencia sea precisa para el mantenimiento o cumplimiento de la relación jurídica entre el titular y BIJU.' },
      { heading: 'V. Derechos ARCO', body: 'De conformidad con los artículos 28 al 35 de la LFPDPPP, usted tiene derecho a: Acceder a sus datos personales en posesión de BIJU; Rectificar sus datos cuando sean inexactos o incompletos; Cancelar sus datos cuando considere que no están siendo tratados conforme a la ley; Oponerse al tratamiento de sus datos para finalidades específicas. Para ejercer sus derechos ARCO, envíe una solicitud a: privacidad@biju.edu.mx, indicando su nombre completo, matrícula y el derecho que desea ejercer. BIJU responderá en un plazo máximo de 20 días hábiles.' },
      { heading: 'VI. Mecanismo para revocar el consentimiento', body: 'Usted podrá revocar el consentimiento otorgado para el tratamiento de sus datos personales en cualquier momento, mediante solicitud escrita enviada a privacidad@biju.edu.mx. La revocación del consentimiento puede implicar la imposibilidad de continuar prestando los servicios de la plataforma.' },
      { heading: 'VII. Uso de cookies y tecnologías similares', body: 'La plataforma BIJU utiliza cookies de sesión estrictamente necesarias para el funcionamiento del sistema de autenticación. No se utilizan cookies de rastreo publicitario ni se comparte información de navegación con redes publicitarias de terceros.' },
      { heading: 'VIII. Cambios al aviso de privacidad', body: 'BIJU se reserva el derecho de modificar el presente Aviso de Privacidad. Cualquier cambio será publicado en esta plataforma con un mínimo de 30 días de anticipación a su entrada en vigor. El uso continuo de la plataforma después de dicha notificación constituirá su aceptación de los cambios.' },
      { heading: 'IX. Autoridad supervisora', body: 'Si usted considera que su derecho a la protección de datos personales ha sido vulnerado, puede acudir ante el Instituto Nacional de Transparencia, Acceso a la Información y Protección de Datos Personales (INAI), www.inai.org.mx.' },
    ]
  },
  terminos: {
    icon: '📜',
    title: 'Términos y Condiciones de Uso',
    subtitle: 'Biblioteca Jurídica Universitaria BIJU — Versión 2026',
    sections: [
      { heading: '1. Aceptación de los términos', body: 'Al registrarse y utilizar la plataforma BIJU, el usuario declara haber leído, entendido y aceptado en su totalidad los presentes Términos y Condiciones. Si no está de acuerdo con alguno de ellos, deberá abstenerse de utilizar la plataforma.' },
      { heading: '2. Objeto y finalidad', body: 'BIJU es una biblioteca jurídica universitaria de acceso restringido cuyo objeto es proporcionar acceso a material bibliográfico jurídico con fines exclusivamente académicos, de investigación y de formación profesional. Queda expresamente prohibido cualquier uso comercial del contenido disponible en la plataforma.' },
      { heading: '3. Registro y credenciales de acceso', body: 'El acceso a BIJU requiere registro previo con datos verídicos. El usuario es el único responsable de mantener la confidencialidad de su nombre de usuario y contraseña. Está estrictamente prohibido compartir credenciales de acceso entre distintos usuarios. Ante cualquier uso no autorizado de su cuenta, el usuario deberá notificar de inmediato a contacto@biju.edu.mx.' },
      { heading: '4. Propiedad intelectual', body: 'Todo el contenido bibliográfico disponible en la plataforma — incluyendo textos, compilaciones, bases de datos y materiales digitalizados — está sujeto a derechos de autor conforme a la Ley Federal del Derecho de Autor (LFDA). Su reproducción total o parcial, distribución, comunicación pública, transformación o cualquier otra forma de explotación sin autorización expresa del titular de los derechos constituye una infracción susceptible de responsabilidad civil y penal.' },
      { heading: '5. Sistema de préstamos digitales', body: 'Cada usuario registrado podrá tener activos hasta cinco (5) títulos en préstamo de forma simultánea. El periodo de préstamo es de catorce (14) días naturales, renovable en una sola ocasión por igual período. El incumplimiento en la devolución oportuna podrá resultar en la suspensión temporal del servicio de préstamos.' },
      { heading: '6. Conductas prohibidas', body: 'Se prohíbe expresamente: (a) intentar acceder a sistemas o bases de datos de BIJU sin autorización; (b) realizar ingeniería inversa, descompilar o desensamblar cualquier componente de la plataforma; (c) introducir virus, malware o cualquier código malicioso; (d) utilizar la plataforma para actividades ilícitas; (e) recolectar datos de otros usuarios sin su consentimiento.' },
      { heading: '7. Limitación de responsabilidad', body: 'BIJU no garantiza la disponibilidad ininterrumpida del servicio. La plataforma se proporciona "tal cual" y BIJU no será responsable por daños directos, indirectos, incidentales o consecuentes derivados del uso o imposibilidad de uso de la plataforma, salvo en los casos en que la legislación mexicana no permita dicha limitación.' },
      { heading: '8. Sanciones y terminación', body: 'El incumplimiento de cualquiera de los presentes términos faculta a BIJU para suspender o cancelar el acceso del usuario a la plataforma de forma inmediata y sin previo aviso, sin perjuicio de las acciones legales civiles y penales que pudieran corresponder conforme a la legislación mexicana aplicable.' },
      { heading: '9. Legislación aplicable y jurisdicción', body: 'Los presentes Términos y Condiciones se rigen e interpretan conforme a las leyes de los Estados Unidos Mexicanos. Para cualquier controversia derivada de su interpretación o cumplimiento, las partes se someten expresamente a la jurisdicción de los Tribunales competentes de la Ciudad de México, renunciando a cualquier otro fuero que pudiera corresponderles.' },
      { heading: '10. Modificaciones', body: 'BIJU se reserva el derecho de modificar los presentes Términos y Condiciones en cualquier momento. Las modificaciones serán notificadas a través de la plataforma con al menos quince (15) días naturales de anticipación. El uso continuo de la plataforma tras dicho plazo implica la aceptación de las nuevas condiciones.' },
    ]
  }
};

function openLegal(tipo) {
  const doc = legalDocs[tipo];
  if (!doc) return;
  const sectionsHTML = doc.sections.map(s => `
    <div style="margin-bottom: 1.4rem; padding-bottom: 1.4rem; border-bottom: 1px solid rgba(196,154,42,0.15);">
      <div style="font-family: var(--serif); font-size: 0.95rem; font-weight: 600; color: var(--navy); margin-bottom: 0.5rem;">${s.heading}</div>
      <p style="font-size: 0.875rem; color: var(--text-mid); line-height: 1.75; margin: 0;">${s.body}</p>
    </div>
  `).join('');
  document.getElementById('legalModalContent').innerHTML = `
    <div style="display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 1.5rem;">
      <div>
        <div style="font-size: 2rem; margin-bottom: 0.4rem;">${doc.icon}</div>
        <h3 style="font-family: var(--serif); font-size: 1.3rem; color: var(--navy); margin: 0 0 0.2rem;">${doc.title}</h3>
        <div style="font-size: 0.75rem; color: var(--text-light); letter-spacing: 0.5px;">${doc.subtitle}</div>
      </div>
      <button class="modal-close" onclick="document.getElementById('legalModal').classList.remove('open')" style="font-size: 1.2rem; color: var(--text-light); background: none; border: none; cursor: pointer; padding: 4px 8px;">✕</button>
    </div>
    <div style="background: rgba(196,154,42,0.08); border-left: 3px solid var(--gold); border-radius: 0 6px 6px 0; padding: 0.75rem 1rem; margin-bottom: 1.5rem; font-size: 0.8rem; color: var(--text-mid);">
      Este documento tiene carácter informativo y forma parte del marco legal de BIJU conforme a la legislación mexicana vigente.
    </div>
    ${sectionsHTML}
    <button class="btn-primary" style="width: 100%; margin-top: 0.5rem;" onclick="document.getElementById('legalModal').classList.remove('open')">Cerrar documento</button>
  `;
  document.getElementById('legalModal').classList.add('open');
}

function closeLegalModal(e) {
  if (e.target.id === 'legalModal') document.getElementById('legalModal').classList.remove('open');
}
</script>
</body>
</html>
