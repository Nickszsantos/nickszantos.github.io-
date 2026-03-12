
<html lang="pt-BR">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>MUSIC ARCHIVE — Biblioteca Biográfica</title>
    <link
      href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@400;500&display=swap"
      rel="stylesheet"
    />
    <style>
      *,
      *::before,
      *::after {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
      }
      :root {
        --bg: #0e0c0a;
        --panel: #13110e;
        --card: #171410;
        --border: #2a2520;
        --text: #e8e0d4;
        --muted: #6a5f52;
        --accent: #c9a84c;
        --accent2: #e8c87a;
      }
      html {
        scroll-behavior: smooth;
      }
      body {
        background: var(--bg);
        color: var(--text);
        font-family: "DM Mono", monospace;
        min-height: 100vh;
        cursor: default;
      }
      ::-webkit-scrollbar {
        width: 5px;
      }
      ::-webkit-scrollbar-track {
        background: var(--bg);
      }
      ::-webkit-scrollbar-thumb {
        background: #2a2520;
        border-radius: 3px;
      }

      /* ── HEADER ── */
      header {
        position: sticky;
        top: 0;
        z-index: 100;
        background: rgba(14, 12, 10, 0.96);
        backdrop-filter: blur(12px);
        border-bottom: 1px solid var(--border);
        padding: 0 48px;
        display: flex;
        align-items: center;
        gap: 40px;
        height: 64px;
      }
      .logo {
        font-family: "Bebas Neue";
        font-size: 22px;
        letter-spacing: 4px;
        color: var(--accent);
        white-space: nowrap;
      }
      .logo span {
        color: var(--muted);
        font-size: 14px;
        letter-spacing: 2px;
        margin-left: 10px;
        font-family: "DM Mono";
      }
      .filters {
        display: flex;
        gap: 6px;
        flex-wrap: wrap;
      }
      .filter-btn {
        padding: 5px 14px;
        border-radius: 20px;
        border: 1px solid var(--border);
        background: transparent;
        color: var(--muted);
        font-size: 10px;
        letter-spacing: 2px;
        cursor: pointer;
        font-family: "DM Mono";
        transition: all 0.2s;
      }
      .filter-btn:hover {
        border-color: var(--accent);
        color: var(--accent);
      }
      .filter-btn.active {
        background: var(--accent);
        border-color: var(--accent);
        color: #0e0c0a;
        font-weight: 600;
      }
      .search-wrap {
        margin-left: auto;
        position: relative;
      }
      .search-input {
        background: var(--panel);
        border: 1px solid var(--border);
        border-radius: 6px;
        color: var(--text);
        font-family: "DM Mono";
        font-size: 11px;
        letter-spacing: 1px;
        padding: 8px 14px 8px 34px;
        outline: none;
        width: 200px;
        transition: all 0.2s;
      }
      .search-input:focus {
        border-color: var(--accent);
        width: 260px;
      }
      .search-icon {
        position: absolute;
        left: 11px;
        top: 50%;
        transform: translateY(-50%);
        color: var(--muted);
        font-size: 14px;
        pointer-events: none;
      }

      /* ── HERO ── */
      .hero {
        padding: 80px 48px 60px;
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 60px;
        align-items: center;
        border-bottom: 1px solid var(--border);
        position: relative;
        overflow: hidden;
      }
      .hero::before {
        content: "";
        position: absolute;
        inset: 0;
        background: radial-gradient(
          ellipse at 60% 50%,
          rgba(201, 168, 76, 0.06) 0%,
          transparent 70%
        );
        pointer-events: none;
      }
      .hero-label {
        font-size: 10px;
        letter-spacing: 5px;
        color: var(--muted);
        margin-bottom: 16px;
      }
      .hero-title {
        font-family: "Bebas Neue";
        font-size: clamp(60px, 8vw, 110px);
        line-height: 0.9;
        letter-spacing: 2px;
      }
      .hero-title em {
        font-family: "DM Serif Display";
        font-style: italic;
        color: var(--accent);
      }
      .hero-sub {
        font-size: 12px;
        color: var(--muted);
        line-height: 1.8;
        margin-top: 20px;
        max-width: 440px;
        letter-spacing: 0.5px;
      }
      .hero-stats {
        display: flex;
        gap: 40px;
        margin-top: 40px;
      }
      .stat-item {
      }
      .stat-num {
        font-family: "Bebas Neue";
        font-size: 42px;
        color: var(--accent);
        letter-spacing: 2px;
        line-height: 1;
      }
      .stat-label {
        font-size: 9px;
        color: var(--muted);
        letter-spacing: 3px;
        margin-top: 4px;
      }
      .featured-strip {
        display: flex;
        flex-direction: column;
        gap: 12px;
      }
      .featured-tag {
        font-size: 9px;
        letter-spacing: 4px;
        color: var(--muted);
        margin-bottom: 4px;
      }
      .feat-card {
        background: var(--panel);
        border: 1px solid var(--border);
        border-radius: 10px;
        padding: 16px 20px;
        display: flex;
        align-items: center;
        gap: 16px;
        cursor: pointer;
        transition: all 0.25s;
        text-decoration: none;
        color: inherit;
      }
      .feat-card:hover {
        border-color: var(--accent);
        transform: translateX(6px);
        background: rgba(201, 168, 76, 0.04);
      }
      .feat-avatar {
        width: 48px;
        height: 48px;
        border-radius: 50%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 20px;
        flex-shrink: 0;
      }
      .feat-info h3 {
        font-size: 14px;
        font-weight: 500;
        letter-spacing: 0.5px;
      }
      .feat-info p {
        font-size: 10px;
        color: var(--muted);
        margin-top: 3px;
        letter-spacing: 1px;
      }
      .feat-badge {
        margin-left: auto;
        font-size: 9px;
        letter-spacing: 2px;
        padding: 4px 10px;
        border-radius: 20px;
        white-space: nowrap;
      }

      /* ── GRID ── */
      .grid-section {
        padding: 60px 48px;
      }
      .section-header {
        display: flex;
        align-items: baseline;
        gap: 20px;
        margin-bottom: 36px;
      }
      .section-title {
        font-family: "Bebas Neue";
        font-size: 36px;
        letter-spacing: 3px;
      }
      .section-count {
        font-size: 11px;
        color: var(--muted);
        letter-spacing: 2px;
      }
      .artists-grid {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(340px, 1fr));
        gap: 20px;
      }

      /* ── ARTIST CARD ── */
      .artist-card {
        background: var(--card);
        border: 1px solid var(--border);
        border-radius: 14px;
        overflow: hidden;
        cursor: pointer;
        transition: all 0.3s;
        position: relative;
        animation: fadeUp 0.4s ease both;
      }
      .artist-card:hover {
        border-color: rgba(201, 168, 76, 0.4);
        transform: translateY(-4px);
        box-shadow: 0 20px 50px rgba(0, 0, 0, 0.5);
      }
      .card-header {
        padding: 24px 24px 20px;
        display: flex;
        align-items: center;
        gap: 18px;
        position: relative;
      }
      .card-header::after {
        content: "";
        position: absolute;
        bottom: 0;
        left: 24px;
        right: 24px;
        height: 1px;
        background: var(--border);
      }
      .artist-emoji {
        font-size: 36px;
        width: 64px;
        height: 64px;
        border-radius: 14px;
        display: flex;
        align-items: center;
        justify-content: center;
        flex-shrink: 0;
      }
      .artist-meta h2 {
        font-family: "Bebas Neue";
        font-size: 24px;
        letter-spacing: 2px;
        line-height: 1;
      }
      .artist-meta .genre-tag {
        display: inline-block;
        font-size: 9px;
        letter-spacing: 2px;
        padding: 3px 10px;
        border-radius: 20px;
        margin-top: 6px;
      }
      .artist-meta .origin {
        font-size: 10px;
        color: var(--muted);
        margin-top: 5px;
        letter-spacing: 1px;
      }
      .card-body {
        padding: 20px 24px;
      }
      .bio-text {
        font-size: 12px;
        color: #a09080;
        line-height: 1.8;
        letter-spacing: 0.3px;
      }

      .sub-section {
        margin-top: 20px;
      }
      .sub-title {
        font-size: 9px;
        letter-spacing: 3px;
        color: var(--muted);
        margin-bottom: 10px;
        padding-bottom: 6px;
        border-bottom: 1px solid var(--border);
      }
      .songs-list {
        display: flex;
        flex-direction: column;
        gap: 6px;
      }
      .song-item {
        display: flex;
        align-items: center;
        gap: 10px;
        padding: 8px 10px;
        border-radius: 7px;
        transition: background 0.2s;
        font-size: 11px;
      }
      .song-item:hover {
        background: rgba(255, 255, 255, 0.03);
      }
      .song-num {
        color: var(--muted);
        width: 16px;
        font-size: 10px;
      }
      .song-name {
        flex: 1;
        letter-spacing: 0.3px;
      }
      .song-year {
        color: var(--muted);
        font-size: 10px;
      }
      .song-dot {
        width: 6px;
        height: 6px;
        border-radius: 50%;
        flex-shrink: 0;
      }

      .conflicts-list {
        display: flex;
        flex-direction: column;
        gap: 8px;
      }
      .conflict-item {
        padding: 10px 12px;
        border-radius: 8px;
        border-left: 3px solid;
      }
      .conflict-title {
        font-size: 11px;
        font-weight: 500;
        letter-spacing: 0.3px;
      }
      .conflict-desc {
        font-size: 10px;
        color: var(--muted);
        margin-top: 4px;
        line-height: 1.6;
        letter-spacing: 0.2px;
      }

      .actions-list {
        display: flex;
        flex-wrap: wrap;
        gap: 6px;
      }
      .action-tag {
        font-size: 10px;
        padding: 5px 12px;
        border-radius: 20px;
        border: 1px solid var(--border);
        color: var(--muted);
        letter-spacing: 0.5px;
        transition: all 0.2s;
      }
      .action-tag:hover {
        border-color: var(--accent);
        color: var(--accent);
      }

      .card-footer {
        padding: 16px 24px;
        display: flex;
        gap: 24px;
        align-items: center;
        border-top: 1px solid var(--border);
        font-size: 10px;
        color: var(--muted);
      }
      .footer-stat span {
        color: var(--accent);
        font-family: "Bebas Neue";
        font-size: 18px;
        margin-right: 4px;
      }

      /* ── MODAL ── */
      .modal-overlay {
        display: none;
        position: fixed;
        inset: 0;
        z-index: 500;
        background: rgba(0, 0, 0, 0.85);
        backdrop-filter: blur(8px);
        align-items: flex-start;
        justify-content: center;
        padding: 40px 20px;
        overflow-y: auto;
      }
      .modal-overlay.open {
        display: flex;
        animation: fadeIn 0.2s ease;
      }
      .modal {
        background: var(--card);
        border: 1px solid var(--border);
        border-radius: 20px;
        max-width: 760px;
        width: 100%;
        overflow: hidden;
        position: relative;
        animation: slideUp 0.3s ease;
      }
      .modal-hero {
        padding: 40px 40px 32px;
        position: relative;
        overflow: hidden;
      }
      .modal-close {
        position: absolute;
        top: 20px;
        right: 20px;
        background: rgba(255, 255, 255, 0.07);
        border: 1px solid var(--border);
        color: var(--text);
        width: 36px;
        height: 36px;
        border-radius: 50%;
        cursor: pointer;
        font-size: 16px;
        display: flex;
        align-items: center;
        justify-content: center;
        transition: all 0.2s;
        font-family: "DM Mono";
      }
      .modal-close:hover {
        background: rgba(255, 255, 255, 0.12);
      }
      .modal-emoji {
        font-size: 64px;
        margin-bottom: 16px;
      }
      .modal-name {
        font-family: "Bebas Neue";
        font-size: 56px;
        letter-spacing: 3px;
        line-height: 0.95;
      }
      .modal-name em {
        font-family: "DM Serif Display";
        font-style: italic;
        color: var(--accent);
      }
      .modal-tags {
        display: flex;
        gap: 8px;
        margin-top: 14px;
        flex-wrap: wrap;
      }
      .modal-body {
        padding: 0 40px 40px;
      }
      .modal-grid {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 32px;
        margin-top: 28px;
      }
      .modal-section-title {
        font-family: "Bebas Neue";
        font-size: 18px;
        letter-spacing: 3px;
        color: var(--accent);
        margin-bottom: 14px;
      }
      .timeline {
        display: flex;
        flex-direction: column;
        gap: 0;
      }
      .tl-item {
        display: flex;
        gap: 16px;
        padding-bottom: 20px;
        position: relative;
      }
      .tl-item::before {
        content: "";
        position: absolute;
        left: 31px;
        top: 24px;
        bottom: 0;
        width: 1px;
        background: var(--border);
      }
      .tl-item:last-child::before {
        display: none;
      }
      .tl-year {
        font-family: "Bebas Neue";
        font-size: 15px;
        color: var(--accent);
        width: 46px;
        text-align: right;
        flex-shrink: 0;
        padding-top: 2px;
      }
      .tl-dot {
        width: 10px;
        height: 10px;
        border-radius: 50%;
        border: 2px solid var(--accent);
        background: var(--bg);
        flex-shrink: 0;
        margin-top: 4px;
      }
      .tl-content {
        font-size: 11px;
        color: #a09080;
        line-height: 1.7;
      }
      .tl-content strong {
        color: var(--text);
        display: block;
        margin-bottom: 2px;
        font-size: 12px;
      }
      .awards-grid {
        display: flex;
        flex-wrap: wrap;
        gap: 8px;
      }
      .award-item {
        background: rgba(201, 168, 76, 0.08);
        border: 1px solid rgba(201, 168, 76, 0.2);
        border-radius: 8px;
        padding: 8px 14px;
        font-size: 10px;
        letter-spacing: 0.5px;
        color: var(--accent2);
      }

      @keyframes fadeUp {
        from {
          opacity: 0;
          transform: translateY(20px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }
      @keyframes fadeIn {
        from {
          opacity: 0;
        }
        to {
          opacity: 1;
        }
      }
      @keyframes slideUp {
        from {
          opacity: 0;
          transform: translateY(30px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      /* responsive */
      @media (max-width: 768px) {
        header {
          padding: 0 20px;
          gap: 16px;
        }
        .logo span {
          display: none;
        }
        .hero {
          grid-template-columns: 1fr;
          padding: 40px 20px;
        }
        .featured-strip {
          display: none;
        }
        .grid-section {
          padding: 40px 20px;
        }
        .artists-grid {
          grid-template-columns: 1fr;
        }
        .modal-grid {
          grid-template-columns: 1fr;
        }
        .modal-body {
          padding: 0 24px 32px;
        }
        .modal-hero {
          padding: 28px 24px 24px;
        }
        .modal-name {
          font-size: 40px;
        }
      }
    </style>
  </head>
  <body>
    <!-- HEADER -->
    <header>
      <div class="logo">MUSIC ARCHIVE <span>/ BIBLIOTECA</span></div>
      <div class="filters" id="filters">
        <button class="filter-btn active" data-filter="all">TODOS</button>
        <button class="filter-btn" data-filter="hip-hop">HIP-HOP</button>
        <button class="filter-btn" data-filter="pop">POP</button>
        <button class="filter-btn" data-filter="r&b">R&B</button>
        <button class="filter-btn" data-filter="latin">LATIN</button>
      </div>
      <div class="search-wrap">
        <span class="search-icon">⌕</span>
        <input
          class="search-input"
          id="search"
          placeholder="BUSCAR ARTISTA..."
        />
      </div>
    </header>

    <!-- HERO -->
    <section class="hero">
      <div>
        <div class="hero-label">◆ ARQUIVO MUSICAL DEFINITIVO</div>
        <h1 class="hero-title">THE<br /><em>Greatest</em><br />ARCHIVE</h1>
        <p class="hero-sub">
          Uma biblioteca biográfica completa dos artistas que definiram a música
          contemporânea. Músicas icônicas, conflitos históricos, conquistas e
          legado.
        </p>
        <div class="hero-stats">
          <div class="stat-item">
            <div class="stat-num">9</div>
            <div class="stat-label">ARTISTAS</div>
          </div>
          <div class="stat-item">
            <div class="stat-num">50+</div>
            <div class="stat-label">MÚSICAS</div>
          </div>
          <div class="stat-item">
            <div class="stat-num">30+</div>
            <div class="stat-label">CONFLITOS</div>
          </div>
        </div>
      </div>
      <div>
        <div class="featured-tag">EM DESTAQUE</div>
        <div class="featured-strip" id="featured-strip"></div>
      </div>
    </section>

    <!-- GRID -->
    <section class="grid-section">
      <div class="section-header">
        <div class="section-title">TODOS OS ARTISTAS</div>
        <div class="section-count" id="count-label">9 ARTISTAS</div>
      </div>
      <div class="artists-grid" id="artists-grid"></div>
    </section>

    <!-- MODAL -->
    <div class="modal-overlay" id="modal-overlay">
      <div class="modal" id="modal-inner"></div>
    </div>

    <script>
      const artists = [
        {
          id: "drake",
          name: "Drake",
          emoji: "🦉",
          genre: "hip-hop",
          genreLabel: "HIP-HOP / RAP",
          origin: "Toronto, Canadá · 1986",
          color: "#c9a84c",
          bio: "Aubrey Drake Graham redefiniu o rap com sua vulnerabilidade emocional e versatilidade. Ex-ator de Degrassi, ascendeu ao topo com a mixtape Thank Me Later e se tornou o artista mais streamado da história do Spotify por anos seguidos.",
          songs: [
            { name: "God's Plan", year: "2018" },
            { name: "One Dance", year: "2016" },
            { name: "Hotline Bling", year: "2015" },
            { name: "Started From the Bottom", year: "2013" },
            { name: "HYFR", year: "2012" },
          ],
          conflicts: [
            {
              title: "Drake vs. Kendrick Lamar (2024)",
              desc: "A beef mais épica do rap moderno. Kendrick lançou 'Not Like Us' e 'Euphoria', acusando Drake de pedofilia e falsidade. Drake respondeu com 'Push Ups' e 'Family Matters'. Kendrick venceu amplamente na opinião pública.",
              color: "#FF6B6B",
            },
            {
              title: "Drake vs. Meek Mill (2015)",
              desc: "Meek acusou Drake de usar ghostwriter. Drake respondeu com 'Charged Up' e 'Back to Back', que recebeu indicação ao Grammy. Um dos beef mais unilaterais da história.",
              color: "#FF8B94",
            },
            {
              title: "Drake vs. Pusha T (2018)",
              desc: "Pusha revelou que Drake tem um filho secreto (Adonis) na faixa 'The Story of Adidon'. Drake respondeu em 'Duppy Freestyle'. Considerado um dos diss tracks mais eficazes já feitos.",
              color: "#FFB347",
            },
          ],
          actions: [
            "OVO Sound (gravadora)",
            "NBA Toronto Raptors (embaixador)",
            "Virginia Black (whisky)",
            "Série More Life",
            "Champagne Papi (alter ego)",
            "Draft pick honorário NBA",
          ],
          timeline: [
            {
              year: "2006",
              title: "Início como ator",
              desc: "Interpretou Jimmy Brooks em Degrassi: The Next Generation",
            },
            {
              year: "2009",
              title: "So Far Gone",
              desc: "Mixtape que lançou sua carreira musical com 'Best I Ever Had'",
            },
            {
              year: "2011",
              title: "Take Care",
              desc: "Álbum vencedor do Grammy, consolidou seu domínio no R&B/rap",
            },
            {
              year: "2016",
              title: "Views",
              desc: "Número 1 em 100 países, quebrando recordes do Spotify",
            },
            {
              year: "2023",
              title: "For All The Dogs",
              desc: "Lançamento de volta às origens emotivas",
            },
          ],
          awards: [
            "Grammy Awards (2x)",
            "Billboard Music Awards (20+)",
            "BET Hip-Hop Awards (12+)",
            "American Music Awards",
            "Record mais streamado do Spotify (2015-2020)",
          ],
          featured: true,
        },
        {
          id: "kendrick",
          name: "Kendrick Lamar",
          emoji: "👑",
          genre: "hip-hop",
          genreLabel: "HIP-HOP / CONSCIOUS RAP",
          origin: "Compton, Califórnia · 1987",
          color: "#4ECDC4",
          bio: "Kendrick Duckworth é amplamente considerado o maior rapper vivo. Nascido em Compton, ele transformou experiências de gangues, trauma e fé em arte transcendente. Primeiro rapper a ganhar o Prêmio Pulitzer de Música.",
          songs: [
            { name: "HUMBLE.", year: "2017" },
            { name: "Alright", year: "2015" },
            { name: "Money Trees", year: "2012" },
            { name: "Swimming Pools", year: "2012" },
            { name: "Not Like Us", year: "2024" },
          ],
          conflicts: [
            {
              title: "Kendrick vs. Drake (2024)",
              desc: "Kendrick desferiu a sequência de diss tracks mais devastadora da história: 'Euphoria' (6 min), 'Meet the Grahams', 'Not Like Us'. Acusações gravíssimas e vitória cultural massiva.",
              color: "#4ECDC4",
            },
            {
              title: "Control Verse (2013)",
              desc: "No feat de Big Sean, Kendrick declarou que queria 'matar' J. Cole, Big K.R.I.T., Meek Mill e outros. Gerou comoção mas era mais provocação artística que beef real.",
              color: "#45B7D1",
            },
            {
              title: "Drake vs. J. Cole - Escolha de Lado",
              desc: "Kendrick escolheu ativamente o lado contra Drake após J. Cole pedir trégua, mantendo a pressão com 'Not Like Us' e shows lotados cantando o hit.",
              color: "#A8E6CF",
            },
          ],
          actions: [
            "pgLang (empresa criativa)",
            "Super Bowl LVIII Halftime Show (2025)",
            "Pulitzer Prize for Music",
            "Colaboração Nike",
            "Curador do Black Panther OST",
            "Ativismo em Compton",
          ],
          timeline: [
            {
              year: "2003",
              title: "Overly Dedicated",
              desc: "Mixtapes locais em Compton sob o nome K-Dot",
            },
            {
              year: "2012",
              title: "good kid, m.A.A.d city",
              desc: "Masterpiece conceitual sobre crescer em Compton",
            },
            {
              year: "2015",
              title: "To Pimp a Butterfly",
              desc: "Obra-prima de jazz, funk e consciência negra",
            },
            {
              year: "2017",
              title: "DAMN.",
              desc: "Venceu o Prêmio Pulitzer, primeiro rap a fazê-lo",
            },
            {
              year: "2022",
              title: "Mr. Morale & The Big Steppers",
              desc: "Álbum catártico sobre trauma, terapia e responsabilidade",
            },
          ],
          awards: [
            "Grammy Awards (13x)",
            "Pulitzer Prize for Music (2018)",
            "BET Hip-Hop Awards (10+)",
            "MTV Video Music Awards",
            "Super Bowl LVIII headliner",
          ],
          featured: true,
        },
        {
          id: "travis",
          name: "Travis Scott",
          emoji: "🌵",
          genre: "hip-hop",
          genreLabel: "HIP-HOP / TRAP",
          origin: "Houston, Texas · 1992",
          color: "#FF6B6B",
          bio: "Jacques Bermon Webster II, conhecido como Travis Scott, é o arquiteto do 'rager' — shows caóticos, sonoridade psicodélica e uma estética de videogame. Criador da Cactus Jack Records e do fenômeno Astroworld.",
          songs: [
            { name: "SICKO MODE", year: "2018" },
            { name: "Goosebumps", year: "2016" },
            { name: "Antidote", year: "2015" },
            { name: "HIGHEST IN THE ROOM", year: "2019" },
            { name: "FE!N", year: "2023" },
          ],
          conflicts: [
            {
              title: "Tragédia Astroworld (2021)",
              desc: "No festival Astroworld em Houston, 10 pessoas morreram e centenas ficaram feridas em uma debandada durante seu show. Travis enfrentou mais de 400 ações judiciais. A tragédia redefiniu debates sobre segurança em shows.",
              color: "#FF6B6B",
            },
            {
              title: "Travis vs. Industry (Cancelamento)",
              desc: "Após Astroworld, foi banido de festivais, perdeu contratos com Nike e outros. Seu comeback com Utopia em 2023 foi cercado de polêmica mas mostrou resiliência.",
              color: "#FF8B94",
            },
            {
              title: "Rival com Drake (amizade)",
              desc: "Travis e Drake têm uma das alianças mais poderosas do rap, mas há tensão criativa. Rumores de que Travis copiou a estética de Drake circulam há anos.",
              color: "#FFB347",
            },
          ],
          actions: [
            "Cactus Jack Records",
            "Parceria Nike (Air Jordan Cactus Jack)",
            "McDonald's Meal (2020)",
            "PlayStation Ambassador",
            "Fortnite Astronomical Concert (12M views)",
            "Utopia Tour (2023)",
          ],
          timeline: [
            {
              year: "2013",
              title: "Owl Pharaoh",
              desc: "Mixtape de estreia com produção de Kanye West e T.I.",
            },
            {
              year: "2016",
              title: "Birds in the Trap",
              desc: "Primeiro álbum #1 no Billboard",
            },
            {
              year: "2018",
              title: "Astroworld",
              desc: "Obra-prima nostálgica em homenagem a Houston",
            },
            {
              year: "2021",
              title: "Tragédia",
              desc: "Festival Astroworld vira tragédia com 10 mortes",
            },
            {
              year: "2023",
              title: "Utopia",
              desc: "Retorno triunfal com colaborações de Beyoncé e outros",
            },
          ],
          awards: [
            "Grammy Nominations (5x)",
            "BET Hip-Hop Awards (4x)",
            "Billboard Music Awards",
            "MTV VMA nominations",
            "Forbes 30 Under 30",
          ],
        },
        {
          id: "taylor",
          name: "Taylor Swift",
          emoji: "✨",
          genre: "pop",
          genreLabel: "POP / COUNTRY / INDIE",
          origin: "West Reading, Pennsylvania · 1989",
          color: "#C77DFF",
          bio: "Taylor Alison Swift é a artista mais poderosa do mundo. Com 14 Grammys, recordes históricos de streaming e vendas, e uma base de fãs militante (os Swifties), ela redefiniu o que significa ser uma estrela no século 21.",
          songs: [
            { name: "Anti-Hero", year: "2022" },
            { name: "Shake It Off", year: "2014" },
            { name: "Blank Space", year: "2014" },
            { name: "Love Story", year: "2008" },
            { name: "All Too Well (10 Min)", year: "2021" },
          ],
          conflicts: [
            {
              title: "Taylor vs. Scooter Braun (2019)",
              desc: "Scooter Braun adquiriu os masters dos primeiros 6 álbuns de Taylor sem seu consentimento. Taylor iniciou o projeto Taylor's Version, regravando todos os álbuns para recuperar controle criativo.",
              color: "#C77DFF",
            },
            {
              title: "Taylor vs. Kanye West (2009-2016)",
              desc: "Kanye interrompeu seu discurso no VMA 2009. Anos depois, um vazamento de ligação mostrou Taylor concordando com uma letra polêmica, depois ela negou. Kim Kardashian vazou o áudio.",
              color: "#9B5DE5",
            },
            {
              title: "Taylor vs. Ticketmaster (2022)",
              desc: "O colapso da venda de ingressos do Eras Tour por falha do Ticketmaster levou Taylor a criticar publicamente a empresa e provocou investigações do Congresso americano.",
              color: "#F15BB5",
            },
          ],
          actions: [
            "Taylor's Version (regravações)",
            "Eras Tour ($1 bilhão em receita)",
            "Doações a bancos de alimentos",
            "Registro de eleitores (300k)",
            "NYU Doutor Honoris Causa",
            "Documentário Miss Americana",
          ],
          timeline: [
            {
              year: "2006",
              title: "Álbum de estreia",
              desc: "Primeiro álbum country aos 16 anos pela Big Machine Records",
            },
            {
              year: "2012",
              title: "Red",
              desc: "Transição para o pop, crítica de amor e perda",
            },
            {
              year: "2014",
              title: "1989",
              desc: "Pop puro, maior álbum do ano. 5 singles no top 10",
            },
            {
              year: "2020",
              title: "folklore & evermore",
              desc: "Virada indie folk durante a pandemia, aclamadas pela crítica",
            },
            {
              year: "2023",
              title: "Eras Tour",
              desc: "Tour mais lucrativa da história da música: $1+ bilhão",
            },
          ],
          awards: [
            "Grammy Awards (14x)",
            "Billboard Music Awards (40+)",
            "American Music Awards (40+)",
            "MTV VMAs (14x)",
            "Time Person of the Year 2023",
          ],
          featured: true,
        },
        {
          id: "badbunny",
          name: "Bad Bunny",
          emoji: "🐰",
          genre: "latin",
          genreLabel: "REGGAETON / TRAP LATINO",
          origin: "Vega Baja, Puerto Rico · 1994",
          color: "#FFE66D",
          bio: "Benito Antonio Martínez Ocasio transformou o reggaeton em fenômeno global. Primeiro artista latino a liderar o Spotify Global por 3 anos consecutivos. Desafia normas de gênero e defende causas sociais com a mesma intensidade.",
          songs: [
            { name: "Tití Me Preguntó", year: "2022" },
            { name: "Dakiti", year: "2020" },
            { name: "MIA", year: "2018" },
            { name: "Callaíta", year: "2019" },
            { name: "Moscow Mule", year: "2022" },
          ],
          conflicts: [
            {
              title: "Comentários sobre gênero e machismo",
              desc: "Bad Bunny frequentemente desafia normas: usou vestido, pintou unhas, defendeu direitos LGBTQ+. Isso gerou críticas de fãs conservadores mas solidificou seu status como ícone progressista.",
              color: "#FFE66D",
            },
            {
              title: "Recusa de turnê lucrativa",
              desc: "Em 2021, recusou uma proposta milionária para excluir artistas independentes de sua turnê, priorizando artistas porto-riquenhos e caribenhos menos conhecidos.",
              color: "#FFC107",
            },
            {
              title: "Crítica ao governo de Porto Rico",
              desc: "Durante as manifestações de 2019 que depuseram o governador Ricardo Rosselló, Bad Bunny foi às ruas e usou sua plataforma como ferramenta política direta.",
              color: "#FF9800",
            },
          ],
          actions: [
            "Campeão de streaming Spotify (3 anos)",
            "WWE (lutador profissional)",
            "Ator em Bullet Train e Narcos",
            "Ativismo em Porto Rico",
            "Diseño de moda Adidas",
            "El Apagón (documentário)",
          ],
          timeline: [
            {
              year: "2016",
              title: "Diles",
              desc: "Single viral que o colocou no mapa do trap latino",
            },
            {
              year: "2018",
              title: "X 100pre",
              desc: "Álbum de estreia revolucionário",
            },
            {
              year: "2020",
              title: "YHLQMDLG",
              desc: "Álbum gravado em segredo, #1 global imediato",
            },
            {
              year: "2022",
              title: "Un Verano Sin Ti",
              desc: "Álbum mais streamado da história do Spotify em 2022",
            },
            {
              year: "2023",
              title: "nadie sabe lo que va a pasar mañana",
              desc: "Trap oscuro e experimental",
            },
          ],
          awards: [
            "Grammy Latino (9x)",
            "Billboard Latin Awards (20+)",
            "Spotify #1 Global (2020, 2021, 2022)",
            "MTV VMAs",
            "American Music Awards (4x)",
          ],
        },
        {
          id: "brunomars",
          name: "Bruno Mars",
          emoji: "🌺",
          genre: "r&b",
          genreLabel: "POP / R&B / FUNK",
          origin: "Honolulu, Havaí · 1985",
          color: "#FF8B94",
          bio: "Peter Gene Hernandez, o Bruno Mars, é o entertainer mais completo de sua geração. Com domínio vocal, dança de nível Michael Jackson e produção impecável, ele ressuscitou o funk dos anos 70/80 para audiências modernas.",
          songs: [
            { name: "Uptown Funk", year: "2014" },
            { name: "That's What I Like", year: "2017" },
            { name: "Just the Way You Are", year: "2010" },
            { name: "Grenade", year: "2010" },
            { name: "Leave the Door Open", year: "2021" },
          ],
          conflicts: [
            {
              title: "Acusação de Apropriação Cultural (2018)",
              desc: "Após o sucesso de Uptown Funk, críticos acusaram Bruno Mars de se apropriar de músicas negras (funk, R&B) sem ser negro. A discussão acendeu debates sobre identidade e crédito cultural na música.",
              color: "#FF8B94",
            },
            {
              title: "Prisão por Posse de Cocaína (2010)",
              desc: "Antes da fama, Bruno foi preso em Las Vegas por posse de drogas. O incidente foi resolvido e ele usou o episódio para reconstruir sua imagem com disciplina e foco.",
              color: "#FFB347",
            },
            {
              title: "Processo da gravadora",
              desc: "Conflitos iniciais com a Motown levaram ao cancelamento de seu contrato antes do sucesso. Ele precisou lutar para garantir controle criativo total antes de estourar.",
              color: "#FFC0CB",
            },
          ],
          actions: [
            "Silk Sonic (duo com Anderson .Paak)",
            "Residência em Las Vegas (maior bilheteria)",
            "Produtor de outros artistas",
            "Filmes e comerciais globais",
            "Ativismo havaiano",
            "Fundação de instituições de caridade",
          ],
          timeline: [
            {
              year: "2010",
              title: "Doo-Wops & Hooligans",
              desc: "Álbum de estreia com hits instantâneos",
            },
            {
              year: "2012",
              title: "Unorthodox Jukebox",
              desc: "Experimentação de gêneros: reggae, funk, soul",
            },
            {
              year: "2014",
              title: "Uptown Funk",
              desc: "Uma das músicas mais vendidas de todos os tempos",
            },
            {
              year: "2021",
              title: "Silk Sonic",
              desc: "Projeto com Anderson .Paak, 4 Grammys incluindo Record of the Year",
            },
            {
              year: "2023",
              title: "Residência Las Vegas",
              desc: "Shows esgotados e receita recorde em Las Vegas",
            },
          ],
          awards: [
            "Grammy Awards (15x)",
            "Billboard Music Awards (10+)",
            "Super Bowl XLVIII Halftime",
            "American Music Awards (11x)",
            "MTV VMAs (11x)",
          ],
        },
        {
          id: "weeknd",
          name: "The Weeknd",
          emoji: "🌙",
          genre: "r&b",
          genreLabel: "R&B / POP / DARKWAVE",
          origin: "Toronto, Canadá · 1990",
          color: "#74B9FF",
          bio: "Abel Makkonen Tesfaye construiu um dos personagens mais intrigantes da música moderna. Começou com mixtapes anônimas e evoluiu para um superastro global com estética cinematográfica única — solidão, excesso, redenção.",
          songs: [
            { name: "Blinding Lights", year: "2019" },
            { name: "Save Your Tears", year: "2020" },
            { name: "Starboy", year: "2016" },
            { name: "The Hills", year: "2015" },
            { name: "Can't Feel My Face", year: "2015" },
          ],
          conflicts: [
            {
              title: "Boicote ao Grammy (2021)",
              desc: "Após ser totalmente ignorado pelo Grammy mesmo com After Hours sendo o álbum mais tocado de 2020 e Blinding Lights quebrando recordes, The Weeknd anunciou boicote à premiação, chamando-a de 'corrupta'.",
              color: "#74B9FF",
            },
            {
              title: "Rompimento com Bella Hadid",
              desc: "O relacionamento on-and-off com Bella Hadid foi documentado em músicas como 'Call Out My Name'. A exposição pública gerou debate sobre privacidade e uso de relacionamentos como material artístico.",
              color: "#A29BFE",
            },
            {
              title: "Super Bowl sem Grammy",
              desc: "O paradoxo de se apresentar no Super Bowl LV (2021) como um dos maiores artistas do mundo enquanto era ignorado pelo Grammy evidenciou as falhas do sistema de premiação.",
              color: "#6C5CE7",
            },
          ],
          actions: [
            "XO Records (gravadora)",
            "Super Bowl LV Halftime Show",
            "HBO The Idol (série/criador)",
            "Parceria Puma",
            "Doação $1M à BLM",
            "Doação à Etiópia (crise)",
            "Coleção moda XO",
          ],
          timeline: [
            {
              year: "2011",
              title: "Trilogy (mixtapes)",
              desc: "Três mixtapes anônimas revolucionárias no SoundCloud",
            },
            {
              year: "2015",
              title: "Beauty Behind the Madness",
              desc: "Primeiro #1 no Billboard 200",
            },
            {
              year: "2016",
              title: "Starboy",
              desc: "Colaboração com Daft Punk, dominância global",
            },
            {
              year: "2020",
              title: "After Hours",
              desc: "Era mais coesa de sua carreira, Blinding Lights bate recordes",
            },
            {
              year: "2022",
              title: "Dawn FM",
              desc: "Álbum conceitual sobre morte e redenção",
            },
          ],
          awards: [
            "Grammy Awards (4x)",
            "Billboard Music Awards (20+)",
            "American Music Awards (15+)",
            "Juno Awards (3x)",
            "MTV VMAs (9x)",
          ],
          featured: true,
        },
        {
          id: "jcole",
          name: "J. Cole",
          emoji: "🌿",
          genre: "hip-hop",
          genreLabel: "HIP-HOP / CONSCIOUS RAP",
          origin: "Fayetteville, Carolina do Norte · 1985",
          color: "#A8E6CF",
          bio: "Jermaine Lamarr Cole é o rapper que escolheu a consciência sobre o comercialismo. Formado magna cum laude, fundou a Dreamville Records e construiu uma das carreiras mais consistentes do rap sem depender de features ou polêmicas.",
          songs: [
            { name: "No Role Modelz", year: "2014" },
            { name: "Love Yourz", year: "2014" },
            { name: "MIDDLE CHILD", year: "2019" },
            { name: "G.O.M.D.", year: "2014" },
            { name: "Apparently", year: "2014" },
          ],
          conflicts: [
            {
              title: "Entrada e saída do beef Drake/Kendrick (2024)",
              desc: "J. Cole entrou com '7 Minute Drill' contra Kendrick, depois se desculpou publicamente na frente de 60.000 pessoas no Dreamville Festival. Ato de humildade raro no rap gerou debate intenso.",
              color: "#A8E6CF",
            },
            {
              title: "J. Cole vs. Lil Pump / SoundCloud Rap",
              desc: "Cole foi vocal em criticar a onda SoundCloud (Lil Pump, Tekashi 6ix9ine). 'Apparently' e outros tracks incluem indirets a artistas que priorizam estética sobre conteúdo.",
              color: "#88D8B0",
            },
            {
              title: "Experiência na NBA (2023)",
              desc: "Cole largou a música para jogar basquete profissional no Canadá. Fans e críticos questionar prioridades, mas ele usou o momento para falar sobre perseguir sonhos.",
              color: "#5CB8A0",
            },
          ],
          actions: [
            "Dreamville Records",
            "Dreamville Festival",
            "Jogador NBA no Canadá",
            "Programa habitacional em Fayetteville",
            "4 Your Eyez Only Foundation",
            "Colaboração Puma",
          ],
          timeline: [
            {
              year: "2007",
              title: "The Come Up",
              desc: "Mixtape de estreia enquanto morava no sofá em NY",
            },
            {
              year: "2013",
              title: "Born Sinner",
              desc: "Primeiro #1 no Billboard, debate com Kanye",
            },
            {
              year: "2014",
              title: "2014 Forest Hills Drive",
              desc: "Álbum sem features, platina sem singles",
            },
            {
              year: "2018",
              title: "KOD",
              desc: "Álbum sobre vícios e pressão social",
            },
            {
              year: "2021",
              title: "The Off-Season",
              desc: "Retorno como 'rapper's rapper' aclamado",
            },
          ],
          awards: [
            "Grammy Nominations (5x)",
            "Billboard Music Awards (5x)",
            "BET Hip-Hop Awards (8x)",
            "Platinum sem singles (2014 FHD)",
            "Magna Cum Laude (St. John's Univ.)",
          ],
        },
        {
          id: "beyonce",
          name: "Beyoncé",
          emoji: "💛",
          genre: "pop",
          genreLabel: "POP / R&B / COUNTRY",
          origin: "Houston, Texas · 1981",
          color: "#F4D03F",
          bio: "Beyoncé Giselle Knowles-Carter é a artista mais premiada da história do Grammy. Integrante do Destiny's Child, ela construiu um império solo que vai de R&B a country, desafiando categorias e redefinindo o que significa ser 'Queen Bey'.",
          songs: [
            { name: "Crazy in Love", year: "2003" },
            { name: "Single Ladies", year: "2008" },
            { name: "Lemonade", year: "2016" },
            { name: "Texas Hold 'Em", year: "2024" },
            { name: "Formation", year: "2016" },
          ],
          conflicts: [
            {
              title: "Álbum Lemonade e Jay-Z (2016)",
              desc: "O álbum-visual Lemonade trouxe letras sobre infidelidade que apontavam para Jay-Z. O mundo especulou, o casal ficou em silêncio, e o álbum virou um manifesto sobre traição e perdão.",
              color: "#F4D03F",
            },
            {
              title: "Kanye interrompendo Taylor Swift (2009)",
              desc: "Beyoncé ficou constrangida quando Kanye subiu ao palco durante o discurso de Taylor Swift no VMA para dizer que 'Single Ladies' merecia vencer. Beyoncé cedeu seu tempo a Taylor depois.",
              color: "#DAA520",
            },
            {
              title: "Renaissance e acusações de plágio",
              desc: "Faixas do Renaissance geraram acusações de uso não creditado de samples e letras de artistas LGBTQ+ e drag queens. Beyoncé revisou algumas letras após pressão da comunidade.",
              color: "#B8860B",
            },
          ],
          actions: [
            "Parkwood Entertainment",
            "Ivy Park (moda)",
            "BeyGOOD (caridade)",
            "Renaissance World Tour ($580M)",
            "Coachella 2018 (Beychella)",
            "Primeiro country de artista negra no #1",
          ],
          timeline: [
            {
              year: "1997",
              title: "Destiny's Child",
              desc: "Grupo se torna um dos mais vendidos da história",
            },
            {
              year: "2003",
              title: "Dangerously in Love",
              desc: "Álbum solo de estreia, 5 Grammys",
            },
            {
              year: "2013",
              title: "Beyoncé (surpresa)",
              desc: "Primeiro álbum visual lançado sem aviso prévio",
            },
            {
              year: "2016",
              title: "Lemonade",
              desc: "Obra-prima política e pessoal",
            },
            {
              year: "2023",
              title: "Renaissance",
              desc: "32 Grammys no total, mais que qualquer artista na história",
            },
          ],
          awards: [
            "Grammy Awards (32x - recorde histórico)",
            "BET Awards (26x)",
            "Billboard Music Awards (30+)",
            "MTV VMAs (26x)",
            "Time 100 Most Influential",
          ],
          featured: true,
        },
      ];

      // ── FEATURED STRIP ──
      const featuredStrip = document.getElementById("featured-strip");
      artists
        .filter((a) => a.featured)
        .slice(0, 4)
        .forEach((a) => {
          const card = document.createElement("a");
          card.className = "feat-card";
          card.href = "#";
          card.innerHTML = `
    <div class="feat-avatar" style="background:${a.color}22;border:1px solid ${a.color}44">${a.emoji}</div>
    <div class="feat-info">
      <h3>${a.name}</h3>
      <p>${a.genreLabel}</p>
    </div>
    <div class="feat-badge" style="background:${a.color}22;color:${a.color};border:1px solid ${a.color}44">${a.genre.toUpperCase()}</div>`;
          card.addEventListener("click", (e) => {
            e.preventDefault();
            openModal(a);
          });
          featuredStrip.appendChild(card);
        });

      // ── FILTERS ──
      let activeFilter = "all";
      let searchQ = "";
      document.querySelectorAll(".filter-btn").forEach((btn) => {
        btn.addEventListener("click", () => {
          activeFilter = btn.dataset.filter;
          document
            .querySelectorAll(".filter-btn")
            .forEach((b) => b.classList.remove("active"));
          btn.classList.add("active");
          renderGrid();
        });
      });
      document.getElementById("search").addEventListener("input", (e) => {
        searchQ = e.target.value;
        renderGrid();
      });

      // ── GRID ──
      function renderGrid() {
        const filtered = artists.filter(
          (a) =>
            (activeFilter === "all" || a.genre === activeFilter) &&
            a.name.toLowerCase().includes(searchQ.toLowerCase()),
        );
        document.getElementById("count-label").textContent =
          filtered.length + " ARTISTAS";
        const grid = document.getElementById("artists-grid");
        grid.innerHTML = "";
        filtered.forEach((a, i) => {
          const card = document.createElement("div");
          card.className = "artist-card";
          card.style.animationDelay = i * 0.07 + "s";
          card.innerHTML = `
      <div class="card-header">
        <div class="artist-emoji" style="background:${a.color}18;border:1px solid ${a.color}33">${a.emoji}</div>
        <div class="artist-meta">
          <h2>${a.name}</h2>
          <span class="genre-tag" style="background:${a.color}18;color:${a.color};border:1px solid ${a.color}33">${a.genreLabel}</span>
          <div class="origin">📍 ${a.origin}</div>
        </div>
      </div>
      <div class="card-body">
        <p class="bio-text">${a.bio.substring(0, 160)}...</p>

        <div class="sub-section">
          <div class="sub-title">🎵 MÚSICAS MAIS FAMOSAS</div>
          <div class="songs-list">${a.songs
            .map(
              (s, idx) => `
            <div class="song-item">
              <span class="song-num">${idx + 1}</span>
              <div class="song-dot" style="background:${a.color}"></div>
              <span class="song-name">${s.name}</span>
              <span class="song-year">${s.year}</span>
            </div>`,
            )
            .join("")}
          </div>
        </div>

        <div class="sub-section">
          <div class="sub-title">⚡ PRINCIPAIS CONFLITOS</div>
          <div class="conflicts-list">${a.conflicts
            .map(
              (c) => `
            <div class="conflict-item" style="background:${c.color}0d;border-left-color:${c.color}">
              <div class="conflict-title">${c.title}</div>
              <div class="conflict-desc">${c.desc.substring(0, 100)}...</div>
            </div>`,
            )
            .join("")}
          </div>
        </div>

        <div class="sub-section">
          <div class="sub-title">🏆 AÇÕES & ATIVIDADES</div>
          <div class="actions-list">${a.actions.map((ac) => `<span class="action-tag">${ac}</span>`).join("")}</div>
        </div>
      </div>
      <div class="card-footer">
        <div class="footer-stat"><span>${a.songs.length}</span> HITS</div>
        <div class="footer-stat"><span>${a.conflicts.length}</span> CONFLITOS</div>
        <div class="footer-stat"><span>${a.awards.length}</span> PRÊMIOS</div>
        <button style="margin-left:auto;padding:7px 18px;border-radius:20px;background:${a.color}22;border:1px solid ${a.color}44;color:${a.color};font-size:10px;letter-spacing:2px;cursor:pointer;font-family:'DM Mono'" onclick="openModal(artists.find(x=>x.id==='${a.id}'))">VER MAIS →</button>
      </div>`;
          grid.appendChild(card);
        });
      }

      // ── MODAL ──
      function openModal(a) {
        const overlay = document.getElementById("modal-overlay");
        const inner = document.getElementById("modal-inner");
        inner.innerHTML = `
    <div class="modal-hero" style="background:linear-gradient(135deg,${a.color}0f 0%,transparent 60%)">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div class="modal-emoji">${a.emoji}</div>
      <div class="modal-name">${a.name
        .split(" ")
        .map((w, i) => (i === 0 ? w : `<em>${w}</em>`))
        .join(" ")}</div>
      <div class="modal-tags">
        <span class="genre-tag" style="background:${a.color}22;color:${a.color};border:1px solid ${a.color}44;padding:5px 14px;border-radius:20px;font-size:10px;letter-spacing:2px">${a.genreLabel}</span>
        <span style="color:var(--muted);font-size:11px;padding:5px 0">📍 ${a.origin}</span>
      </div>
      <p style="margin-top:16px;font-size:12px;color:#a09080;line-height:1.8;letter-spacing:0.3px">${a.bio}</p>
    </div>

    <div class="modal-body">
      <div class="modal-grid">
        <div>
          <div class="modal-section-title">⏱ LINHA DO TEMPO</div>
          <div class="timeline">
            ${a.timeline
              .map(
                (t) => `
            <div class="tl-item">
              <div class="tl-year">${t.year}</div>
              <div class="tl-dot"></div>
              <div class="tl-content"><strong>${t.title}</strong>${t.desc}</div>
            </div>`,
              )
              .join("")}
          </div>
        </div>
        <div>
          <div class="modal-section-title">🎵 DISCOGRAFIA</div>
          <div class="songs-list" style="margin-bottom:28px">
            ${a.songs
              .map(
                (s, idx) => `
            <div class="song-item" style="background:${a.color}08;border-radius:8px">
              <span class="song-num">${idx + 1}</span>
              <div class="song-dot" style="background:${a.color}"></div>
              <span class="song-name" style="font-size:12px">${s.name}</span>
              <span class="song-year">${s.year}</span>
            </div>`,
              )
              .join("")}
          </div>
          <div class="modal-section-title">🏆 PRÊMIOS</div>
          <div class="awards-grid">
            ${a.awards.map((aw) => `<div class="award-item">${aw}</div>`).join("")}
          </div>
        </div>
      </div>

      <div style="margin-top:32px">
        <div class="modal-section-title">⚡ CONFLITOS & CONTROVÉRSIAS</div>
        <div class="conflicts-list">
          ${a.conflicts
            .map(
              (c) => `
          <div class="conflict-item" style="background:${c.color}0d;border-left-color:${c.color};padding:14px 16px">
            <div class="conflict-title" style="font-size:13px">${c.title}</div>
            <div class="conflict-desc" style="margin-top:6px">${c.desc}</div>
          </div>`,
            )
            .join("")}
        </div>
      </div>

      <div style="margin-top:28px">
        <div class="modal-section-title">🚀 AÇÕES & PROJETOS</div>
        <div class="actions-list">
          ${a.actions.map((ac) => `<span class="action-tag" style="font-size:11px;padding:6px 14px">${ac}</span>`).join("")}
        </div>
      </div>
    </div>`;

        overlay.classList.add("open");
        document.body.style.overflow = "hidden";
      }

      function closeModal() {
        document.getElementById("modal-overlay").classList.remove("open");
        document.body.style.overflow = "";
      }

      document
        .getElementById("modal-overlay")
        .addEventListener("click", function (e) {
          if (e.target === this) closeModal();
        });

      document.addEventListener("keydown", (e) => {
        if (e.key === "Escape") closeModal();
      });

      // ── INIT ──
      renderGrid();
    </script>
  </body>
</html>
