<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Hub & Logbook</title>
  
  <!-- Font Google: Inter (corpo) + Syne (titoli display dal look moderno/tech) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Syne:wght@700;800&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #090d14;
      --card-bg: rgba(22, 27, 39, 0.7);
      --card-border: rgba(255, 255, 255, 0.08);
      --card-hover-border: rgba(249, 115, 22, 0.4);
      --text-main: #f1f5f9;
      --text-muted: #94a3b8;
      --accent: #f97316; /* Arancio ambra studio */
      --accent-glow: rgba(249, 115, 22, 0.15);
      --badge-bg: rgba(255, 255, 255, 0.05);
      --transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg);
      /* Sfumatura di fondo sottile per dare profondità */
      background-image: 
        radial-gradient(circle at 50% 0%, rgba(249, 115, 22, 0.08) 0%, transparent 50%),
        radial-gradient(circle at 10% 20%, rgba(56, 189, 248, 0.04) 0%, transparent 40%);
      background-attachment: fixed;
      color: var(--text-main);
      font-family: 'Inter', system-ui, sans-serif;
      line-height: 1.5;
      -webkit-font-smoothing: antialiased;
      padding-bottom: 5rem;
    }

    /* Container centrale */
    .container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 0 1.5rem;
    }

    /* HEADER */
    header {
      padding: 2.5rem 0 1.5rem;
      border-bottom: 1px solid var(--card-border);
      position: sticky;
      top: 0;
      backdrop-filter: blur(16px);
      -webkit-backdrop-filter: blur(16px);
      background: rgba(9, 13, 20, 0.85);
      z-index: 100;
    }

    .nav-wrapper {
      display: grid;
      grid-template-columns: 1fr auto 1fr;
      align-items: center;
    }

    .title-area {
      grid-column: 2;
      text-align: center;
    }

    .brand-title {
      font-family: 'Syne', sans-serif;
      font-size: 1.6rem;
      letter-spacing: -0.5px;
      font-weight: 800;
      background: linear-gradient(180deg, #ffffff 40%, #94a3b8 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      text-transform: uppercase;
    }

    .brand-subtitle {
      font-size: 0.8rem;
      color: var(--text-muted);
      letter-spacing: 1.5px;
      text-transform: uppercase;
      margin-top: -2px;
    }

    /* MENU PROFILO / CV / PORTFOLIO */
    .profile-section {
      grid-column: 3;
      justify-self: end;
      position: relative;
    }

    .profile-btn {
      display: flex;
      align-items: center;
      gap: 0.6rem;
      background: var(--badge-bg);
      border: 1px solid var(--card-border);
      padding: 0.4rem 0.8rem 0.4rem 0.5rem;
      border-radius: 40px;
      color: var(--text-main);
      cursor: pointer;
      font-family: inherit;
      font-size: 0.85rem;
      font-weight: 500;
      transition: var(--transition);
    }

    .profile-btn:hover, .profile-btn[aria-expanded="true"] {
      border-color: var(--accent);
      background: rgba(255, 255, 255, 0.08);
    }

    .avatar-icon {
      width: 28px;
      height: 28px;
      border-radius: 50%;
      background: linear-gradient(135deg, var(--accent), #e11d48);
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 0.75rem;
      font-weight: 700;
      color: #fff;
    }

    .chevron {
      transition: transform 0.2s ease;
      stroke: var(--text-muted);
    }
    .profile-btn[aria-expanded="true"] .chevron {
      transform: rotate(180deg);
    }

    /* Dropdown UI */
    .dropdown {
      position: absolute;
      top: calc(100% + 10px);
      right: 0;
      width: 230px;
      background: #111622;
      border: 1px solid var(--card-border);
      border-radius: 14px;
      padding: 0.5rem;
      box-shadow: 0 20px 35px -10px rgba(0, 0, 0, 0.7);
      opacity: 0;
      visibility: hidden;
      transform: translateY(-8px);
      transition: var(--transition);
    }

    .dropdown.active {
      opacity: 1;
      visibility: visible;
      transform: translateY(0);
    }

    .dropdown-link {
      display: flex;
      flex-direction: column;
      gap: 2px;
      padding: 0.7rem 0.9rem;
      border-radius: 10px;
      text-decoration: none;
      color: var(--text-main);
      font-size: 0.88rem;
      font-weight: 500;
      transition: background 0.15s;
    }

    .dropdown-link span.hint {
      font-size: 0.75rem;
      color: var(--text-muted);
      font-weight: 400;
    }

    .dropdown-link:hover {
      background: rgba(255, 255, 255, 0.06);
    }

    .dropdown-link:hover span.title {
      color: var(--accent);
    }

    /* FILTRI CATEGORIA */
    .filter-bar {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
      padding: 2rem 0 1.5rem;
      overflow-x: auto;
      scrollbar-width: none;
    }
    .filter-bar::-webkit-scrollbar { display: none; }

    .filter-btn {
      background: transparent;
      border: 1px solid var(--card-border);
      color: var(--text-muted);
      padding: 0.45rem 1.1rem;
      border-radius: 30px;
      font-size: 0.85rem;
      font-family: inherit;
      font-weight: 500;
      cursor: pointer;
      white-space: nowrap;
      transition: var(--transition);
    }

    .filter-btn:hover {
      color: var(--text-main);
      border-color: rgba(255, 255, 255, 0.2);
    }

    .filter-btn.active {
      background: var(--text-main);
      color: #090d14;
      border-color: var(--text-main);
      font-weight: 600;
    }

    /* GRIGLIA ARTICOLI */
    .articles-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 1.75rem;
    }

    /* CARD DESIGN */
    .card {
      background: var(--card-bg);
      border: 1px solid var(--card-border);
      border-radius: 16px;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      text-decoration: none;
      color: inherit;
      transition: var(--transition);
      backdrop-filter: blur(8px);
      -webkit-backdrop-filter: blur(8px);
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: var(--card-hover-border);
      box-shadow: 0 12px 30px -10px rgba(0, 0, 0, 0.6), 0 0 20px -5px var(--accent-glow);
    }

    /* Media Wrapper */
    .card-media {
      position: relative;
      width: 100%;
      padding-top: 56.25%; /* Ratio 16:9 cinematografico */
      background: #0f131a;
      overflow: hidden;
    }

    .card-media img, 
    .card-media iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      border: none;
      transition: transform 0.4s ease;
    }

    .card:hover .card-media img {
      transform: scale(1.04);
    }

    /* Badge Tipologia/Durata sopra il Media */
    .media-badge {
      position: absolute;
      bottom: 12px;
      right: 12px;
      background: rgba(0, 0, 0, 0.75);
      backdrop-filter: blur(6px);
      padding: 0.25rem 0.6rem;
      border-radius: 6px;
      font-size: 0.75rem;
      font-weight: 600;
      color: #fff;
      display: flex;
      align-items: center;
      gap: 4px;
      z-index: 2;
    }

    /* Contenuto Card */
    .card-body {
      padding: 1.4rem;
      display: flex;
      flex-direction: column;
      flex-grow: 1;
    }

    .card-meta {
      display: flex;
      align-items: center;
      justify-content: space-between;
      margin-bottom: 0.75rem;
      font-size: 0.8rem;
    }

    .category-tag {
      color: var(--accent);
      font-weight: 600;
      text-transform: uppercase;
      font-size: 0.72rem;
      letter-spacing: 0.5px;
    }

    .card-date {
      color: var(--text-muted);
    }

    .card-title {
      font-size: 1.2rem;
      font-weight: 600;
      margin-bottom: 0.6rem;
      line-height: 1.35;
      color: var(--text-main);
      transition: color 0.15s ease;
    }

    .card:hover .card-title {
      color: var(--accent);
    }

    .card-excerpt {
      font-size: 0.9rem;
      color: var(--text-muted);
      line-height: 1.5;
      margin-bottom: 1.25rem;
      flex-grow: 1;
    }

    .card-footer {
      display: flex;
      align-items: center;
      justify-content: flex-end;
      padding-top: 0.75rem;
      border-top: 1px solid rgba(255, 255, 255, 0.05);
      font-size: 0.8rem;
      color: var(--text-muted);
    }

    .read-more {
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 4px;
      color: var(--text-main);
    }

    /* Responsive */
    @media (max-width: 640px) {
      .nav-wrapper {
        grid-template-columns: 1fr auto;
      }
      .title-area {
        grid-column: 1;
        text-align: left;
      }
      .profile-section {
        grid-column: 2;
      }
      .filter-bar {
        justify-content: flex-start;
      }
    }
  </style>
</head>
<body>

  <!-- HEADER FISSO CON BLUR -->
  <header>
    <div class="container nav-wrapper">
      
      <!-- Spazio vuoto a sinistra per bilanciare la griglia su desktop -->
      <div></div>

      <!-- TITOLO CENTRALE -->
      <div class="title-area">
        <h1 class="brand-title">LOGBOOK</h1>
        <p class="brand-subtitle">Tech, Filmmaking & Pensieri</p>
      </div>

      <!-- MENU PROFILO / CV / PORTFOLIO -->
      <div class="profile-section">
        <button class="profile-btn" id="menuBtn" aria-expanded="false" aria-label="Menu profilo">
          <div class="avatar-icon">N</div>
          <span>Info</span>
          <svg class="chevron" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
            <polyline points="6 9 12 15 18 9"></polyline>
          </svg>
        </button>

        <div class="dropdown" id="dropdownMenu">
          <a href="https://portfolio-url.github.io" target="_blank" rel="noopener" class="dropdown-link">
            <span class="title">Portfolio Progetti ↗</span>
            <span class="hint">Hardware, CAD & Regia</span>
          </a>
          <a href="https://cv-url.github.io" target="_blank" rel="noopener" class="dropdown-link">
            <span class="title">Curriculum Vitae ↗</span>
            <span class="hint">Competenze ed esperienze</span>
          </a>
        </div>
      </div>

    </div>
  </header>

  <div class="container">
    
    <!-- BARRA CATEGORIE FILTRABILE -->
    <nav class="filter-bar" aria-label="Filtra categorie">
      <button class="filter-btn active" data-category="all">Tutti</button>
      <button class="filter-btn" data-category="tech">Tech & Hardware</button>
      <button class="filter-btn" data-category="cinema">Cinema & Analisi</button>
      <button class="filter-btn" data-category="making-of">Making Of</button>
      <button class="filter-btn" data-category="opinioni">Riflessioni</button>
    </nav>

    <!-- GRIGLIA DEGLI ARTICOLI -->
    <main class="articles-grid" id="articlesGrid">

      <!-- Articolo 1: Making Of Video con Embed YouTube -->
      <article class="card" data-category="making-of">
        <div class="card-media">
          <iframe 
            src="https://www.youtube-nocookie.com/embed/dQw4w9WgXcQ" 
            title="Video embed" 
            allowfullscreen 
            loading="lazy">
          </iframe>
          <div class="media-badge">▶ Video Log</div>
        </div>
        <div class="card-body">
          <div class="card-meta">
            <span class="category-tag">Making Of</span>
            <time class="card-date">Marzo 2026</time>
          </div>
          <h2 class="card-title">Color grading cinematografico: illuminazione e post in DaVinci</h2>
          <p class="card-excerpt">Come gestire curve logaritmiche, color palette calde e impostazioni ottiche su mirrorless senza impazzire in timeline.</p>
          <div class="card-footer">
            <span class="read-more">Approfondisci &rarr;</span>
          </div>
        </div>
      </article>

      <!-- Articolo 2: Hardware / Prototipazione -->
      <article class="card" data-category="tech">
        <div class="card-media">
          <img src="https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=700&q=80" alt="Circuito elettronico microcontrollore" loading="lazy">
          <div class="media-badge">Devlog</div>
        </div>
        <div class="card-body">
          <div class="card-meta">
            <span class="category-tag">Tech & Hardware</span>
            <time class="card-date">Febbraio 2026</time>
          </div>
          <h2 class="card-title">Dietro le quinte del firmware: interrupt, bus SPI e FreeCAD</h2>
          <p class="card-excerpt">La cronaca delle nottate passate a debuggare i segnali elettrici e a modellare scocche millimetriche in PLA.</p>
          <div class="card-footer">
            <span class="read-more">Leggi il log &rarr;</span>
          </div>
        </div>
      </article>

      <!-- Articolo 3: Cinema & Serie TV -->
      <article class="card" data-category="cinema">
        <div class="card-media">
          <img src="https://images.unsplash.com/photo-1485846234645-a62644f84728?auto=format&fit=crop&w=700&q=80" alt="Proiettore cinema" loading="lazy">
          <div class="media-badge">7 min read</div>
        </div>
        <div class="card-body">
          <div class="card-meta">
            <span class="category-tag">Cinema & Analisi</span>
            <time class="card-date">Gennaio 2026</time>
          </div>
          <h2 class="card-title">Perché la fotografia di Denis Villeneuve funziona così bene</h2>
          <p class="card-excerpt">Analisi dell'uso della scala monumentale, lenti anamorfiche e sound design nei recenti capolavori di fantascienza.</p>
          <div class="card-footer">
            <span class="read-more">Leggi saggio &rarr;</span>
          </div>
        </div>
      </article>

    </main>
  </div>

  <script>
    // 1. Gestione Dropdown Menu
    const menuBtn = document.getElementById('menuBtn');
    const dropdownMenu = document.getElementById('dropdownMenu');

    menuBtn.addEventListener('click', (e) => {
      e.stopPropagation();
      const isOpen = dropdownMenu.classList.toggle('active');
      menuBtn.setAttribute('aria-expanded', isOpen);
    });

    document.addEventListener('click', (e) => {
      if (!menuBtn.contains(e.target) && !dropdownMenu.contains(e.target)) {
        dropdownMenu.classList.remove('active');
        menuBtn.setAttribute('aria-expanded', 'false');
      }
    });

    // 2. Filtro dinamico per Categoria
    const filterButtons = document.querySelectorAll('.filter-btn');
    const cards = document.querySelectorAll('.articles-grid .card');

    filterButtons.forEach(button => {
      button.addEventListener('click', () => {
        // Toggle classe active
        filterButtons.forEach(btn => btn.classList.remove('active'));
        button.classList.add('active');

        const filter = button.getAttribute('data-category');

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
