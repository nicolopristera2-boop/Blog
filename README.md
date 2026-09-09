<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LOGBOOK — Tech, Video & Notes</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Syne:wght@700;800&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #0b0f17;
      --card-bg: rgba(18, 24, 38, 0.75);
      --card-border: rgba(255, 255, 255, 0.07);
      --card-border-hover: rgba(249, 115, 22, 0.45);
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
      --accent: #f97316;
      --accent-glow: rgba(249, 115, 22, 0.15);
      --badge-bg: rgba(15, 23, 42, 0.85);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg);
      background-image: 
        radial-gradient(ellipse 60% 40% at 50% 0%, rgba(249, 115, 22, 0.07), transparent 70%),
        radial-gradient(circle at 100% 100%, rgba(56, 189, 248, 0.03), transparent 50%);
      background-attachment: fixed;
      color: var(--text-main);
      font-family: 'Inter', system-ui, sans-serif;
      line-height: 1.5;
      padding-bottom: 5rem;
    }

    .container {
      max-width: 1120px;
      margin: 0 auto;
      padding: 0 1.5rem;
    }

    /* HEADER */
    header {
      position: sticky;
      top: 0;
      z-index: 100;
      backdrop-filter: blur(20px);
      -webkit-backdrop-filter: blur(20px);
      background: rgba(11, 15, 23, 0.82);
      border-bottom: 1px solid var(--card-border);
      padding: 1rem 0;
    }

    .nav-bar {
      display: grid;
      grid-template-columns: 1fr auto 1fr;
      align-items: center;
    }

    .brand-mark {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 0.95rem;
      letter-spacing: 1px;
      color: var(--text-muted);
      text-decoration: none;
      transition: color 0.2s;
    }
    .brand-mark:hover { color: var(--text-main); }
    .brand-mark span { color: var(--accent); }

    .title-center {
      text-align: center;
    }

    .site-title {
      font-family: 'Syne', sans-serif;
      font-size: 1.5rem;
      font-weight: 800;
      letter-spacing: 2px;
      text-transform: uppercase;
      background: linear-gradient(180deg, #ffffff 30%, #94a3b8 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    .site-tagline {
      font-size: 0.72rem;
      color: var(--text-muted);
      letter-spacing: 2px;
      text-transform: uppercase;
      margin-top: 2px;
    }

    /* MENU PROFILO (CV / PORTFOLIO) */
    .profile-wrap {
      justify-self: end;
      position: relative;
    }

    .profile-toggle {
      display: flex;
      align-items: center;
      gap: 0.55rem;
      background: rgba(255, 255, 255, 0.04);
      border: 1px solid var(--card-border);
      padding: 0.35rem 0.75rem 0.35rem 0.4rem;
      border-radius: 999px;
      color: var(--text-main);
      cursor: pointer;
      font-family: inherit;
      font-size: 0.85rem;
      font-weight: 500;
      transition: all 0.2s ease;
    }

    .profile-toggle:hover, .profile-toggle[aria-expanded="true"] {
      border-color: var(--accent);
      background: rgba(255, 255, 255, 0.07);
    }

    .avatar-badge {
      width: 26px;
      height: 26px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent), #e11d48);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.75rem;
      font-weight: 700;
      color: #fff;
    }

    .dropdown-box {
      position: absolute;
      top: calc(100% + 8px);
      right: 0;
      width: 230px;
      background: #111726;
      border: 1px solid var(--card-border);
      border-radius: 12px;
      padding: 0.4rem;
      box-shadow: 0 16px 36px rgba(0, 0, 0, 0.55);
      opacity: 0;
      visibility: hidden;
      transform: translateY(-6px);
      transition: all 0.2s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .dropdown-box.open {
      opacity: 1;
      visibility: visible;
      transform: translateY(0);
    }

    .dropdown-item {
      display: flex;
      flex-direction: column;
      gap: 2px;
      padding: 0.65rem 0.85rem;
      border-radius: 8px;
      text-decoration: none;
      color: var(--text-main);
      font-size: 0.85rem;
      font-weight: 500;
      transition: background 0.15s;
    }

    .dropdown-item .subtext {
      font-size: 0.72rem;
      color: var(--text-muted);
      font-weight: 400;
    }

    .dropdown-item:hover {
      background: rgba(255, 255, 255, 0.05);
    }
    .dropdown-item:hover .item-title {
      color: var(--accent);
    }

    /* FILTRI CATEGORIE */
    .filter-wrapper {
      display: flex;
      justify-content: center;
      gap: 0.5rem;
      padding: 2.2rem 0 1.8rem;
      overflow-x: auto;
      scrollbar-width: none;
    }
    .filter-wrapper::-webkit-scrollbar { display: none; }

    .filter-btn {
      background: rgba(255, 255, 255, 0.03);
      border: 1px solid var(--card-border);
      color: var(--text-muted);
      padding: 0.4rem 1rem;
      border-radius: 999px;
      font-size: 0.82rem;
      font-family: inherit;
      font-weight: 500;
      cursor: pointer;
      white-space: nowrap;
      transition: all 0.2s ease;
    }

    .filter-btn:hover {
      color: var(--text-main);
      border-color: rgba(255, 255, 255, 0.2);
    }

    .filter-btn.active {
      background: var(--text-main);
      color: #0b0f17;
      border-color: var(--text-main);
      font-weight: 600;
    }

    /* GRIGLIA ARTICOLI */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(330px, 1fr));
      gap: 1.75rem;
    }

    /* CARD DESIGN */
    .card {
      background: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 14px;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      text-decoration: none;
      color: inherit;
      transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: var(--card-border-hover);
      box-shadow: 0 14px 30px rgba(0, 0, 0, 0.5), 0 0 25px var(--accent-glow);
    }

    .card-cover {
      position: relative;
      width: 100%;
      padding-top: 56.25%; /* 16:9 */
      background: #070a0e;
      overflow: hidden;
    }

    .card-cover iframe,
    .card-cover img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      border: none;
      transition: transform 0.4s ease;
    }

    .card:hover .card-cover img {
      transform: scale(1.03);
    }

    .tag-badge {
      position: absolute;
      bottom: 10px;
      right: 10px;
      background: var(--badge-bg);
      backdrop-filter: blur(8px);
      border: 1px solid rgba(255, 255, 255, 0.1);
      padding: 0.22rem 0.55rem;
      border-radius: 6px;
      font-size: 0.72rem;
      font-weight: 600;
      color: var(--text-main);
      z-index: 2;
    }

    .card-content {
      padding: 1.3rem;
      display: flex;
      flex-direction: column;
      flex-grow: 1;
    }

    .meta-line {
      display: flex;
      justify-content: space-between;
      font-size: 0.75rem;
      margin-bottom: 0.6rem;
    }

    .cat-name {
      color: var(--accent);
      font-weight: 600;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .post-date {
      color: var(--text-muted);
    }

    .post-title {
      font-size: 1.15rem;
      font-weight: 600;
      line-height: 1.4;
      margin-bottom: 0.55rem;
      color: var(--text-main);
      transition: color 0.15s;
    }

    .card:hover .post-title {
      color: var(--accent);
    }

    .post-excerpt {
      font-size: 0.88rem;
      color: var(--text-muted);
      line-height: 1.5;
      margin-bottom: 1.2rem;
      flex-grow: 1;
    }

    .card-action {
      font-size: 0.8rem;
      font-weight: 500;
      color: var(--text-main);
      display: flex;
      align-items: center;
      gap: 4px;
      padding-top: 0.7rem;
      border-top: 1px solid rgba(255, 255, 255, 0.05);
    }

    @media (max-width: 640px) {
      .site-title { font-size: 1.25rem; }
      .site-tagline { display: none; }
      .brand-mark { display: none; }
      .nav-bar { grid-template-columns: 1fr auto; }
      .title-center { text-align: left; }
      .filter-wrapper { justify-content: flex-start; }
    }
  </style>
</head>
<body>

  <!-- HEADER -->
  <header>
    <div class="container nav-bar">
      <!-- Monogramma/Brand a sinistra -->
      <a href="#" class="brand-mark">PRISTERÀ<span>.</span></a>

      <!-- Titolo centrale -->
      <div class="title-center">
        <h1 class="site-title">LOGBOOK</h1>
        <p class="site-tagline">Tech, Filmmaking & Pensieri</p>
      </div>

      <!-- Menu Profilo a destra -->
      <div class="profile-wrap">
        <button class="profile-toggle" id="menuBtn" aria-expanded="false" aria-label="Apri menu">
          <div class="avatar-badge">N</div>
          <span>Info</span>
          <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <polyline points="6 9 12 15 18 9"></polyline>
          </svg>
        </button>

        <div class="dropdown-box" id="menuBox">
          <a href="https://portfolio-url.github.io" target="_blank" rel="noopener" class="dropdown-item">
            <span class="item-title">Portfolio ↗</span>
            <span class="subtext">Progetti Tech & Video</span>
          </a>
          <a href="https://cv-url.github.io" target="_blank" rel="noopener" class="dropdown-item">
            <span class="item-title">Curriculum Vitae ↗</span>
            <span class="subtext">Esperienze & Competenze</span>
          </a>
        </div>
      </div>
    </div>
  </header>

  <!-- CONTENITORE PRINCIPALE -->
  <div class="container">
    
    <!-- BARRA CATEGORIE -->
    <nav class="filter-wrapper" aria-label="Filtri articoli">
      <button class="filter-btn active" data-filter="all">Tutti</button>
      <button class="filter-btn" data-filter="tech">Tech & Hardware</button>
      <button class="filter-btn" data-filter="cinema">Cinema & Video</button>
      <button class="filter-btn" data-filter="making-of">Making Of</button>
      <button class="filter-btn" data-filter="riflessioni">Riflessioni</button>
    </nav>

    <!-- GRIGLIA DEGLI ARTICOLI -->
    <main class="grid" id="postsGrid">

      <!-- Card 1: Video / Making Of -->
      <article class="card" data-category="making-of">
        <div class="card-cover">
          <iframe 
            src="https://www.youtube-nocookie.com/embed/dQw4w9WgXcQ" 
            title="Video embed" 
            allowfullscreen 
            loading="lazy">
          </iframe>
          <div class="tag-badge">▶ Video Log</div>
        </div>
        <div class="card-content">
          <div class="meta-line">
            <span class="cat-name">Making Of</span>
            <span class="post-date">Marzo 2026</span>
          </div>
          <h2 class="post-title">Color grading cinematografico: illuminazione e post in DaVinci</h2>
          <p class="post-excerpt">Gestire profili Log, curve di contrasto calibrate e resa cromatica per cortometraggi e clip video.</p>
          <div class="card-action">Guarda e leggi &rarr;</div>
        </div>
      </article>

      <!-- Card 2: Tech / Prototipazione -->
      <article class="card" data-category="tech">
        <div class="card-cover">
          <img src="https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=800&q=80" alt="Circuito stampato" loading="lazy">
          <div class="tag-badge">Devlog</div>
        </div>
        <div class="card-content">
          <div class="meta-line">
            <span class="cat-name">Tech & Hardware</span>
            <span class="post-date">Febbraio 2026</span>
          </div>
          <h2 class="post-title">Dietro le quinte del firmware: interrupt, bus SPI e FreeCAD</h2>
          <p class="post-excerpt">Progettazione integrata tra modellazione scocche millimetriche in PLA e codice a basso livello.</p>
          <div class="card-action">Leggi l'articolo &rarr;</div>
        </div>
      </article>

      <!-- Card 3: Cinema / Opinione -->
      <article class="card" data-category="cinema">
        <div class="card-cover">
          <img src="https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=800&q=80" alt="Proiettore cinematografico" loading="lazy">
          <div class="tag-badge">Analisi</div>
        </div>
        <div class="card-content">
          <div class="meta-line">
            <span class="cat-name">Cinema & Video</span>
            <span class="post-date">Gennaio 2026</span>
          </div>
          <h2 class="post-title">Composizione dell'inquadratura e lenti anamorfiche nel cinema sci-fi</h2>
          <p class="post-excerpt">Perché la scala visiva monumentale e la gestione delle luci pratiche cambiano completamente l'immersione nello spettatore.</p>
          <div class="card-action">Leggi saggio &rarr;</div>
        </div>
      </article>

    </main>
  </div>

  <script>
    // Toggle menu profilo
    const menuBtn = document.getElementById('menuBtn');
    const menuBox = document.getElementById('menuBox');

    menuBtn.addEventListener('click', (e) => {
      e.stopPropagation();
      const open = menuBox.classList.toggle('open');
      menuBtn.setAttribute('aria-expanded', open);
    });

    document.addEventListener('click', (e) => {
      if (!menuBtn.contains(e.target) && !menuBox.contains(e.target)) {
        menuBox.classList.remove('open');
        menuBtn.setAttribute('aria-expanded', 'false');
      }
    });

    // Filtro categorie live
    const filterBtns = document.querySelectorAll('.filter-btn');
    const cards = document.querySelectorAll('.grid .card');

    filterBtns.forEach(btn => {
      btn.addEventListener('click', () => {
        filterBtns.forEach(b => b.classList.remove('active'));
        btn.classList.add('active');

        const filter = btn.getAttribute('data-filter');
        cards.forEach(card => {
          if (filter === 'all' || card.getAttribute('data-category') === filter) {
            card.style.display = 'flex';
          } else {
            card.style.display = 'none';
          }
        });
      });
    });
  </script>
</body>
</html>
