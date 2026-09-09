<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Hub & Blog</title>
  <style>
    :root {
      --bg: #0f172a;
      --card-bg: #1e293b;
      --text: #f8fafc;
      --accent: #38bdf8;
      --muted: #94a3b8;
    }
    body {
      margin: 0;
      font-family: system-ui, -apple-system, sans-serif;
      background: var(--bg);
      color: var(--text);
    }
    header {
      position: relative;
      padding: 2.5rem 1.5rem 1rem;
      text-align: center;
      max-width: 1000px;
      margin: auto;
    }
    h1 {
      margin: 0;
      font-size: 2rem;
      letter-spacing: -0.5px;
    }
    /* Menu Icona CV / Portfolio */
    .profile-menu {
      position: absolute;
      right: 1.5rem;
      top: 2.5rem;
    }
    .menu-btn {
      background: var(--card-bg);
      border: 1px solid #334155;
      color: var(--text);
      padding: 0.5rem 0.8rem;
      border-radius: 8px;
      cursor: pointer;
      font-size: 1.1rem;
    }
    .dropdown {
      display: none;
      position: absolute;
      right: 0;
      top: 115%;
      background: var(--card-bg);
      border: 1px solid #334155;
      border-radius: 8px;
      padding: 0.5rem;
      min-width: 140px;
      box-shadow: 0 10px 25px rgba(0,0,0,0.5);
      z-index: 10;
    }
    .dropdown.show { display: flex; flex-direction: column; }
    .dropdown a {
      color: var(--text);
      text-decoration: none;
      padding: 0.5rem 0.8rem;
      border-radius: 4px;
      font-size: 0.9rem;
    }
    .dropdown a:hover { background: #334155; }

    /* Barra Categorie */
    .categories {
      display: flex;
      justify-content: center;
      gap: 0.5rem;
      flex-wrap: wrap;
      margin: 2rem 0;
    }
    .cat-btn {
      background: transparent;
      border: 1px solid #334155;
      color: var(--muted);
      padding: 0.4rem 1rem;
      border-radius: 20px;
      cursor: pointer;
      font-size: 0.9rem;
      transition: all 0.2s;
    }
    .cat-btn:hover, .cat-btn.active {
      background: var(--accent);
      color: #0f172a;
      border-color: var(--accent);
      font-weight: bold;
    }

    /* Griglia Articoli */
    main {
      max-width: 1000px;
      margin: auto;
      padding: 0 1.5rem 3rem;
    }
    .grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
      gap: 1.5rem;
    }
    .card {
      background: var(--card-bg);
      border-radius: 12px;
      overflow: hidden;
      border: 1px solid #334155;
      display: flex;
      flex-direction: column;
    }
    .media-container {
      width: 100%;
      height: 180px;
      background: #000;
      position: relative;
    }
    .media-container iframe, .media-container img {
      width: 100%;
      height: 100%;
      object-fit: cover;
      border: none;
    }
    .card-body {
      padding: 1.25rem;
      flex: 1;
      display: flex;
      flex-direction: column;
    }
    .tag {
      font-size: 0.75rem;
      text-transform: uppercase;
      color: var(--accent);
      font-weight: bold;
      margin-bottom: 0.5rem;
    }
    .card-title {
      font-size: 1.25rem;
      margin: 0 0 0.5rem 0;
    }
    .card-desc {
      font-size: 0.9rem;
      color: var(--muted);
      line-height: 1.5;
      flex: 1;
    }
  </style>
</head>
<body>

  <header>
    <h1>IL MIO HUB</h1>

    <div class="profile-menu">
      <button class="menu-btn" onclick="toggleMenu()">👤</button>
      <div class="dropdown" id="userMenu">
        <a href="https://tuo-sito-portfolio.github.io" target="_blank">Portfolio ↗</a>
        <a href="https://tuo-sito-cv.github.io" target="_blank">Curriculum ↗</a>
      </div>
    </div>

    <!-- Barra Argomenti -->
    <div class="categories">
      <button class="cat-btn active">Tutti</button>
      <button class="cat-btn">Tech & DIY</button>
      <button class="cat-btn">Cinema & Serie</button>
      <button class="cat-btn">Making Of</button>
      <button class="cat-btn">Idee</button>
    </div>
  </header>

  <main>
    <div class="grid">
      
      <!-- Esempio Articolo con Video Embeddato -->
      <article class="card">
        <div class="media-container">
          <!-- Embed YouTube (oppure tag <video> se hai file compressi/hostati) -->
          <iframe src="https://www.youtube-nocookie.com/embed/dQw4w9WgXcQ" allowfullscreen></iframe>
        </div>
        <div class="card-body">
          <span class="tag">Cinema & Video</span>
          <h2 class="card-title">Analisi del color grading e montaggio</h2>
          <p class="card-desc">Dietro le quinte delle riprese, impostazioni della camera e post-produzione.</p>
        </div>
      </article>

      <!-- Esempio Articolo Tech -->
      <article class="card">
        <div class="media-container" style="background:#1e293b; display:flex; align-items:center; justify-content:center;">
          <span style="color:#64748b;">[Immagine Progetto]</span>
        </div>
        <div class="card-body">
          <span class="tag">Tech & DIY</span>
          <h2 class="card-title">Costruire un dispositivo embedded custom</h2>
          <p class="card-desc">Il processo di prototipazione, schema elettrico e firmware in C/C++.</p>
        </div>
      </article>

    </div>
  </main>

  <script>
    function toggleMenu() {
      document.getElementById('userMenu').classList.toggle('show');
    }

    // Chiude il menu se si clicca fuori
    window.onclick = function(event) {
      if (!event.target.matches('.menu-btn')) {
        const dropdown = document.getElementById('userMenu');
        if (dropdown.classList.contains('show')) dropdown.classList.remove('show');
      }
    }
  </script>
</body>
</html>
