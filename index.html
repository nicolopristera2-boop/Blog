<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>LOGBOOK</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Syne:wght@700;800&display=swap" rel="stylesheet">

  <style>
    :root {
      --bg: #0b0f17;
      --card-bg: #131926;
      --border: rgba(255, 255, 255, 0.08);
      --border-hover: rgba(249, 115, 22, 0.4);
      --text: #f8fafc;
      --muted: #94a3b8;
      --accent: #f97316;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: var(--bg);
      color: var(--text);
      font-family: 'Inter', system-ui, sans-serif;
      line-height: 1.5;
      padding-bottom: 5rem;
    }

    .container {
      max-width: 1100px;
      margin: 0 auto;
      padding: 0 1.5rem;
    }

    /* TOP BAR: BRAND A SX, MENU A DX */
    .top-bar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 1.25rem 0;
      border-bottom: 1px solid var(--border);
    }

    .brand {
      font-family: 'Syne', sans-serif;
      font-weight: 800;
      font-size: 1rem;
      letter-spacing: 1px;
      color: var(--text);
      text-decoration: none;
    }
    .brand span { color: var(--accent); }

    /* MENU A TENDINA INFO/PORTFOLIO */
    .menu-container {
      position: relative;
    }

    .menu-trigger {
      display: flex;
      align-items: center;
      gap: 0.5rem;
      background: rgba(255, 255, 255, 0.05);
      border: 1px solid var(--border);
      padding: 0.4rem 0.8rem;
      border-radius: 999px;
      color: var(--text);
      cursor: pointer;
      font-family: inherit;
      font-size: 0.85rem;
      transition: all 0.2s;
    }

    .menu-trigger:hover {
      border-color: var(--accent);
    }

    .avatar {
      width: 22px;
      height: 22px;
      border-radius: 50%;
      background: var(--accent);
      color: #fff;
      font-size: 0.75rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .dropdown {
      position: absolute;
      top: calc(100% + 8px);
      right: 0;
      width: 210px;
      background: #161e2e;
      border: 1px solid var(--border);
      border-radius: 12px;
      padding: 0.4rem;
      box-shadow: 0 10px 30px rgba(0,0,0,0.6);
      display: none;
      z-index: 50;
    }

    .dropdown.show { display: block; }

    .dropdown a {
      display: block;
      padding: 0.6rem 0.8rem;
      color: var(--text);
      text-decoration: none;
      font-size: 0.85rem;
      border-radius: 8px;
      transition: background 0.15s;
    }

    .dropdown a:hover {
      background: rgba(255, 255, 255, 0.08);
      color: var(--accent);
    }

    .dropdown a small {
      display: block;
      color: var(--muted);
      font-size: 0.72rem;
      margin-top: 2px;
    }

    /* HERO CENTRALE */
    .hero {
      text-align: center;
      padding: 3rem 0 2rem;
    }

    .main-title {
      font-family: 'Syne', sans-serif;
      font-size: 2.5rem;
      font-weight: 800;
      letter-spacing: 3px;
      text-transform: uppercase;
      margin-bottom: 0.4rem;
    }

    .subtitle {
      font-size: 0.8rem;
      color: var(--muted);
      letter-spacing: 2px;
      text-transform: uppercase;
    }

    /* FILTRI */
    .filters {
      display: flex;
      justify-content: center;
      gap: 0.5rem;
      flex-wrap: wrap;
      margin-top: 2rem;
    }

    .filter-btn {
      background: transparent;
      border: 1px solid var(--border);
      color: var(--muted);
      padding: 0.4rem 1rem;
      border-radius: 999px;
      font-size: 0.85rem;
      cursor: pointer;
      font-family: inherit;
      transition: all 0.2s;
    }

    .filter-btn:hover {
      color: var(--text);
      border-color: rgba(255, 255, 255, 0.2);
    }

    .filter-btn.active {
      background: var(--text);
      color: var(--bg);
      border-color: var(--text);
      font-weight: 600;
    }

    /* GRIGLIA ARTICOLI */
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 2rem;
      margin-top: 2.5rem;
    }

    .card {
      background: var(--card-bg);
      border: 1px solid var(--border);
      border-radius: 14px;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      transition: transform 0.2s, border-color 0.2s;
    }

    .card:hover {
      transform: translateY(-4px);
      border-color: var(--border-hover);
    }

    .card-media {
      position: relative;
      width: 100%;
      padding-top: 56.25%; /* 16:9 */
      background: #000;
    }

    .card-media iframe, .card-media img {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      border: none;
    }

    .badge {
      position: absolute;
      bottom: 10px;
      right: 10px;
      background: rgba(0, 0, 0, 0.8);
      padding: 0.2rem 0.5rem;
      border-radius: 6px;
      font-size: 0.72rem;
      font-weight: 600;
    }

    .card-body {
      padding: 1.25rem;
      display: flex;
      flex-direction: column;
      flex-grow: 1;
    }

    .card-category {
      color: var(--accent);
      font-size: 0.75rem;
      font-weight: 600;
      text-transform: uppercase;
      margin-bottom: 0.4rem;
    }

    .card-title {
      font-size: 1.15rem;
      font-weight: 600;
      line-height: 1.35;
      margin-bottom: 0.5rem;
    }

    .card-desc {
      font-size: 0.88rem;
      color: var(--muted);
      line-height: 1.5;
      flex-grow: 1;
    }
  </style>
</head>
<body>

  <div class="container">
    
    <!-- LIVELLO 1: Barra superiore con Brand e Menu Esterno -->
    <header class="top-bar">
      <a href="#" class="brand">NICOLÒ<span>.</span></a>

      <div class="menu-container">
        <button class="menu-trigger" id="menuBtn">
          <div class="avatar">N</div>
          <span>Link</span>
          ▾
        </button>
        <div class="dropdown" id="menuDropdown">
          <a href="https://portfolio-tuosito.github.io" target="_blank">
            Portfolio Progetti ↗
            <small>Hardware, CAD & Regia</small>
          </a>
          <a href="https://cv-tuosito.github.io" target="_blank">
            Curriculum Vitae ↗
            <small>Esperienze e Formazione</small>
          </a>
        </div>
      </div>
    </header>

    <!-- LIVELLO 2: Hero centrale con Titolo e Filtri Categoria -->
    <section class="hero">
      <h1 class="main-title">LOGBOOK</h1>
      <p class="subtitle">Tech, Filmmaking & Pensieri</p>

      <div class="filters">
        <button class="filter-btn active" data-cat="all">Tutti</button>
        <button class="filter-btn" data-cat="tech">Tech & Hardware</button>
        <button class="filter-btn" data-cat="cinema">Cinema & Video</button>
        <button class="filter-btn" data-cat="making-of">Making Of</button>
        <button class="filter-btn" data-cat="riflessioni">Riflessioni</button>
      </div>
    </section>

    <!-- GRIGLIA ARTICOLI -->
    <main class="grid">

      <!-- Articolo Video -->
      <article class="card" data-category="making-of">
        <div class="card-media">
          <iframe src="https://www.youtube-nocookie.com/embed/dQw4w9WgXcQ" allowfullscreen></iframe>
          <div class="badge">▶ Video Log</div>
        </div>
        <div class="card-body">
          <span class="card-category">Making Of</span>
          <h2 class="card-title">Color grading cinematografico: illuminazione e post</h2>
          <p class="card-desc">Gestire profili Log, contrasto e resa cromatica per cortometraggi e clip video.</p>
        </div>
      </article>

      <!-- Articolo Tech -->
      <article class="card" data-category="tech">
        <div class="card-media">
          <img src="https://images.unsplash.com/photo-1518770660439-4636190af475?auto=format&fit=crop&w=800&q=80" alt="Circuito elettronico">
          <div class="badge">Devlog</div>
        </div>
        <div class="card-body">
          <span class="card-category">Tech & Hardware</span>
          <h2 class="card-title">Firmware a basso livello e modellazione CAD</h2>
          <p class="card-desc">Dalla programmazione di microcontrollori alla progettazione di componenti 3D su misura.</p>
        </div>
      </article>

    </main>

  </div>

  <script>
    // Menu a tendina
    const btn = document.getElementById('menuBtn');
    const dropdown = document.getElementById('menuDropdown');

    btn.addEventListener('click', (e) => {
      e.stopPropagation();
      dropdown.classList.toggle('show');
    });

    document.addEventListener('click', () => {
      dropdown.classList.remove('show');
    });

    // Filtri categorie
    const filterBtns = document.querySelectorAll('.filter-btn');
    const cards = document.querySelectorAll('.card');

    filterBtns.forEach(b => {
      b.addEventListener('click', () => {
        filterBtns.forEach(x => x.classList.remove('active'));
        b.classList.add('active');

        const cat = b.getAttribute('data-cat');
        cards.forEach(c => {
          if (cat === 'all' || c.getAttribute('data-category') === cat) {
            c.style.display = 'flex';
          } else {
            c.style.display = 'none';
          }
        });
      });
    });
  </script>
</body>
</html>
