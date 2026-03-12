Nicolas Santos
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>MUSIC ARCHIVE — Biblioteca Biográfica</title>
<link href="https://fonts.googleapis.com/css2?family=Bebas+Neue&family=DM+Serif+Display:ital@0;1&family=DM+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
*, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }
:root {
  --bg: #0e0c0a;
  --panel: #13110e;
  --card: #171410;
  --border: #2a2520;
  --text: #e8e0d4;
  --muted: #6a5f52;
  --accent: #c9a84c;
  --accent2: #e8c87a;
  --px: clamp(16px, 4vw, 48px);
}
html { scroll-behavior: smooth; -webkit-text-size-adjust: 100%; }
body {
  background: var(--bg);
  color: var(--text);
  font-family: 'DM Mono', monospace;
  min-height: 100vh;
  overflow-x: hidden;
}
::-webkit-scrollbar { width: 4px; }
::-webkit-scrollbar-track { background: var(--bg); }
::-webkit-scrollbar-thumb { background: #2a2520; border-radius: 3px; }

/* ── HEADER ── */
header {
  position: sticky; top: 0; z-index: 100;
  background: rgba(14,12,10,0.97);
  backdrop-filter: blur(14px);
  -webkit-backdrop-filter: blur(14px);
  border-bottom: 1px solid var(--border);
}
.header-top {
  padding: 0 var(--px);
  display: flex; align-items: center; gap: 16px;
  height: 56px;
}
.logo {
  font-family: 'Bebas Neue'; font-size: 20px;
  letter-spacing: 4px; color: var(--accent); white-space: nowrap;
  flex-shrink: 0;
}
.logo span { color: var(--muted); font-size: 12px; letter-spacing: 2px; margin-left: 8px; font-family: 'DM Mono'; }
.search-wrap { margin-left: auto; position: relative; flex-shrink: 0; }
.search-input {
  background: var(--panel); border: 1px solid var(--border);
  border-radius: 6px; color: var(--text); font-family: 'DM Mono';
  font-size: 11px; letter-spacing: 1px; padding: 8px 12px 8px 32px;
  outline: none; width: 160px; transition: all 0.25s;
  -webkit-appearance: none;
}
.search-input:focus { border-color: var(--accent); width: 200px; }
.search-icon { position: absolute; left: 10px; top: 50%; transform: translateY(-50%); color: var(--muted); font-size: 14px; pointer-events: none; }

/* filter bar — scrollable row on mobile */
.filter-bar {
  display: flex; gap: 6px;
  padding: 8px var(--px) 10px;
  overflow-x: auto; -webkit-overflow-scrolling: touch;
  scrollbar-width: none;
}
.filter-bar::-webkit-scrollbar { display: none; }
.filter-btn {
  padding: 6px 14px; border-radius: 20px; white-space: nowrap;
  border: 1px solid var(--border); background: transparent;
  color: var(--muted); font-size: 10px; letter-spacing: 2px;
  cursor: pointer; font-family: 'DM Mono'; transition: all 0.2s;
  flex-shrink: 0; -webkit-tap-highlight-color: transparent;
  min-height: 32px;
}
.filter-btn:active, .filter-btn:hover { border-color: var(--accent); color: var(--accent); }
.filter-btn.active { background: var(--accent); border-color: var(--accent); color: #0e0c0a; font-weight: 600; }

/* ── HERO ── */
.hero {
  padding: clamp(36px, 6vw, 80px) var(--px) clamp(32px, 5vw, 60px);
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: clamp(28px, 4vw, 60px);
  align-items: center;
  border-bottom: 1px solid var(--border);
  position: relative; overflow: hidden;
}
.hero::before {
  content: '';
  position: absolute; inset: 0;
  background: radial-gradient(ellipse at 60% 50%, rgba(201,168,76,0.06) 0%, transparent 70%);
  pointer-events: none;
}
.hero-label { font-size: 10px; letter-spacing: 5px; color: var(--muted); margin-bottom: 14px; }
.hero-title {
  font-family: 'Bebas Neue';
  font-size: clamp(52px, 9vw, 110px);
  line-height: 0.9; letter-spacing: 2px;
}
.hero-title em { font-family: 'DM Serif Display'; font-style: italic; color: var(--accent); }
.hero-sub { font-size: 12px; color: var(--muted); line-height: 1.8; margin-top: 18px; letter-spacing: 0.3px; }
.hero-stats { display: flex; gap: clamp(20px, 4vw, 40px); margin-top: 32px; flex-wrap: wrap; }
.stat-num { font-family: 'Bebas Neue'; font-size: clamp(32px, 5vw, 42px); color: var(--accent); letter-spacing: 2px; line-height: 1; }
.stat-label { font-size: 9px; color: var(--muted); letter-spacing: 3px; margin-top: 3px; }

.featured-strip { display: flex; flex-direction: column; gap: 10px; }
.featured-tag { font-size: 9px; letter-spacing: 4px; color: var(--muted); margin-bottom: 4px; }
.feat-card {
  background: var(--panel); border: 1px solid var(--border);
  border-radius: 10px; padding: 14px 16px;
  display: flex; align-items: center; gap: 14px;
  cursor: pointer; transition: all 0.25s;
  text-decoration: none; color: inherit;
  -webkit-tap-highlight-color: transparent;
}
.feat-card:hover, .feat-card:active { border-color: var(--accent); transform: translateX(4px); background: rgba(201,168,76,0.04); }
.feat-avatar { width: 44px; height: 44px; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 18px; flex-shrink: 0; }
.feat-info h3 { font-size: 13px; font-weight: 500; letter-spacing: 0.5px; }
.feat-info p { font-size: 10px; color: var(--muted); margin-top: 2px; letter-spacing: 1px; }
.feat-badge { margin-left: auto; font-size: 9px; letter-spacing: 2px; padding: 4px 10px; border-radius: 20px; white-space: nowrap; flex-shrink: 0; }

/* ── GRID SECTION ── */
.grid-section { padding: clamp(32px, 5vw, 60px) var(--px); }
.section-header { display: flex; align-items: baseline; gap: 16px; margin-bottom: 28px; flex-wrap: wrap; }
.section-title { font-family: 'Bebas Neue'; font-size: clamp(26px, 4vw, 36px); letter-spacing: 3px; }
.section-count { font-size: 11px; color: var(--muted); letter-spacing: 2px; }
.artists-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(min(100%, 340px), 1fr));
  gap: 16px;
}

/* ── ARTIST CARD ── */
.artist-card {
  background: var(--card); border: 1px solid var(--border);
  border-radius: 14px; overflow: hidden; cursor: pointer;
  transition: all 0.3s; position: relative;
  animation: fadeUp 0.4s ease both;
  -webkit-tap-highlight-color: transparent;
}
@media (hover: hover) {
  .artist-card:hover { border-color: rgba(201,168,76,0.4); transform: translateY(-4px); box-shadow: 0 20px 50px rgba(0,0,0,0.5); }
}
.artist-card:active { transform: scale(0.99); }
.card-header {
  padding: 20px 20px 16px;
  display: flex; align-items: center; gap: 16px;
  position: relative;
}
.card-header::after {
  content: ''; position: absolute; bottom: 0; left: 20px; right: 20px;
  height: 1px; background: var(--border);
}
.artist-emoji { font-size: 32px; width: 58px; height: 58px; border-radius: 12px; display: flex; align-items: center; justify-content: center; flex-shrink: 0; }
.artist-meta h2 { font-family: 'Bebas Neue'; font-size: 22px; letter-spacing: 2px; line-height: 1; }
.artist-meta .genre-tag { display: inline-block; font-size: 9px; letter-spacing: 2px; padding: 3px 10px; border-radius: 20px; margin-top: 5px; }
.artist-meta .origin { font-size: 10px; color: var(--muted); margin-top: 4px; letter-spacing: 0.5px; }
.card-body { padding: 16px 20px; }
.bio-text { font-size: 12px; color: #a09080; line-height: 1.8; letter-spacing: 0.2px; }

.sub-section { margin-top: 18px; }
.sub-title { font-size: 9px; letter-spacing: 3px; color: var(--muted); margin-bottom: 10px; padding-bottom: 6px; border-bottom: 1px solid var(--border); }
.songs-list { display: flex; flex-direction: column; gap: 4px; }
.song-item {
  display: flex; align-items: center; gap: 10px;
  padding: 8px 8px; border-radius: 7px;
  font-size: 11px; transition: background 0.2s;
}
.song-item:hover { background: rgba(255,255,255,0.03); }
.song-num { color: var(--muted); width: 16px; font-size: 10px; flex-shrink: 0; }
.song-name { flex: 1; letter-spacing: 0.2px; min-width: 0; overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
.song-year { color: var(--muted); font-size: 10px; flex-shrink: 0; }
.song-dot { width: 6px; height: 6px; border-radius: 50%; flex-shrink: 0; }

.conflicts-list { display: flex; flex-direction: column; gap: 8px; }
.conflict-item { padding: 10px 12px; border-radius: 8px; border-left: 3px solid; }
.conflict-title { font-size: 11px; font-weight: 500; letter-spacing: 0.2px; line-height: 1.4; }
.conflict-desc { font-size: 10px; color: var(--muted); margin-top: 4px; line-height: 1.6; }

.actions-list { display: flex; flex-wrap: wrap; gap: 6px; }
.action-tag {
  font-size: 10px; padding: 5px 10px; border-radius: 20px;
  border: 1px solid var(--border); color: var(--muted); letter-spacing: 0.3px;
  transition: all 0.2s;
}
.action-tag:hover { border-color: var(--accent); color: var(--accent); }

.card-footer {
  padding: 14px 20px;
  display: flex; gap: 16px; align-items: center; flex-wrap: wrap;
  border-top: 1px solid var(--border);
  font-size: 10px; color: var(--muted);
}
.footer-stat span { color: var(--accent); font-family: 'Bebas Neue'; font-size: 17px; margin-right: 3px; }
.ver-mais-btn {
  margin-left: auto;
  padding: 7px 16px; border-radius: 20px;
  font-size: 10px; letter-spacing: 2px;
  cursor: pointer; font-family: 'DM Mono';
  -webkit-tap-highlight-color: transparent;
  min-height: 34px;
}

/* ── MODAL ── */
.modal-overlay {
  display: none; position: fixed; inset: 0; z-index: 500;
  background: rgba(0,0,0,0.88); backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  align-items: flex-start; justify-content: center;
  overflow-y: auto; -webkit-overflow-scrolling: touch;
  padding: clamp(0px, 3vw, 40px) clamp(0px, 2vw, 20px);
}
.modal-overlay.open { display: flex; animation: fadeIn 0.2s ease; }
.modal {
  background: var(--card); border: 1px solid var(--border);
  border-radius: clamp(0px, 2vw, 20px); max-width: 760px; width: 100%;
  overflow: hidden; position: relative;
  animation: slideUp 0.3s ease;
  margin: auto;
}
.modal-hero {
  padding: clamp(20px, 4vw, 40px) clamp(20px, 4vw, 40px) clamp(16px, 3vw, 32px);
  position: relative; overflow: hidden;
}
.modal-close {
  position: absolute; top: 16px; right: 16px;
  background: rgba(255,255,255,0.08); border: 1px solid var(--border);
  color: var(--text); width: 38px; height: 38px; border-radius: 50%;
  cursor: pointer; font-size: 16px; display: flex;
  align-items: center; justify-content: center; transition: all 0.2s;
  font-family: 'DM Mono'; z-index: 10; flex-shrink: 0;
  -webkit-tap-highlight-color: transparent;
}
.modal-close:hover, .modal-close:active { background: rgba(255,255,255,0.15); }
.modal-emoji { font-size: clamp(44px, 8vw, 64px); margin-bottom: 14px; }
.modal-name { font-family: 'Bebas Neue'; font-size: clamp(36px, 7vw, 56px); letter-spacing: 3px; line-height: 0.95; }
.modal-name em { font-family: 'DM Serif Display'; font-style: italic; color: var(--accent); }
.modal-tags { display: flex; gap: 8px; margin-top: 12px; flex-wrap: wrap; align-items: center; }
.modal-body { padding: 0 clamp(20px, 4vw, 40px) clamp(24px, 4vw, 40px); }
.modal-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 28px; margin-top: 24px; }
.modal-section-title { font-family: 'Bebas Neue'; font-size: 18px; letter-spacing: 3px; color: var(--accent); margin-bottom: 14px; }
.timeline { display: flex; flex-direction: column; }
.tl-item { display: flex; gap: 12px; padding-bottom: 18px; position: relative; }
.tl-item::before { content: ''; position: absolute; left: 57px; top: 22px; bottom: 0; width: 1px; background: var(--border); }
.tl-item:last-child::before { display: none; }
.tl-year { font-family: 'Bebas Neue'; font-size: 14px; color: var(--accent); width: 44px; text-align: right; flex-shrink: 0; padding-top: 2px; }
.tl-dot { width: 10px; height: 10px; border-radius: 50%; border: 2px solid var(--accent); background: var(--bg); flex-shrink: 0; margin-top: 4px; }
.tl-content { font-size: 11px; color: #a09080; line-height: 1.7; }
.tl-content strong { color: var(--text); display: block; margin-bottom: 2px; font-size: 12px; }
.awards-grid { display: flex; flex-wrap: wrap; gap: 7px; }
.award-item { background: rgba(201,168,76,0.08); border: 1px solid rgba(201,168,76,0.2); border-radius: 8px; padding: 7px 12px; font-size: 10px; letter-spacing: 0.4px; color: var(--accent2); }

@keyframes fadeUp { from { opacity:0; transform:translateY(20px); } to { opacity:1; transform:translateY(0); } }
@keyframes fadeIn { from { opacity:0; } to { opacity:1; } }
@keyframes slideUp { from { opacity:0; transform:translateY(24px); } to { opacity:1; transform:translateY(0); } }

/* ── TABLET (max 900px) ── */
@media (max-width: 900px) {
  .hero { grid-template-columns: 1fr; }
  .featured-strip { display: none; }
  .modal-grid { grid-template-columns: 1fr; gap: 20px; }
}

/* ── MOBILE (max 600px) ── */
@media (max-width: 600px) {
  :root { --px: 16px; }

  /* header */
  .logo span { display: none; }
  .header-top { height: 52px; }
  .search-input { width: 130px; font-size: 10px; }
  .search-input:focus { width: 155px; }

  /* hero */
  .hero { padding: 32px 16px 28px; }
  .hero-title { font-size: clamp(48px, 14vw, 70px); }
  .hero-sub { font-size: 11px; margin-top: 14px; }
  .hero-stats { gap: 20px; margin-top: 24px; }

  /* grid */
  .grid-section { padding: 24px 16px 40px; }
  .artists-grid { gap: 14px; }

  /* card */
  .card-header { padding: 16px 16px 14px; gap: 14px; }
  .card-header::after { left: 16px; right: 16px; }
  .artist-emoji { width: 52px; height: 52px; font-size: 28px; border-radius: 10px; }
  .card-body { padding: 14px 16px; }
  .card-footer { padding: 12px 16px; gap: 12px; }
  .ver-mais-btn { width: 100%; margin-left: 0; margin-top: 8px; text-align: center; }

  /* modal — full screen bottom sheet feel */
  .modal-overlay { padding: 60px 0 0; align-items: flex-end; }
  .modal {
    border-radius: 20px 20px 0 0;
    max-height: 92vh; overflow-y: auto;
    border-bottom: none;
  }
  .modal-close { top: 14px; right: 14px; width: 36px; height: 36px; font-size: 14px; }
  .modal-name { font-size: clamp(32px, 9vw, 44px); }
  .modal-emoji { font-size: 44px; }
  .modal-grid { grid-template-columns: 1fr; gap: 20px; margin-top: 16px; }

  /* touch targets */
  .filter-btn { min-height: 36px; font-size: 11px; }
  .song-item { padding: 10px 8px; }
  .conflict-item { padding: 12px 12px; }
  .feat-card { padding: 12px 14px; }
}

/* ── VERY SMALL (max 380px) ── */
@media (max-width: 380px) {
  .hero-title { font-size: 44px; }
  .logo { font-size: 17px; letter-spacing: 3px; }
  .search-input { width: 110px; }
  .search-input:focus { width: 130px; }
  .footer-stat { display: none; }
  .footer-stat:first-child { display: block; }
}
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-top">
    <div class="logo">MUSIC ARCHIVE <span>/ BIBLIOTECA</span></div>
    <div class="search-wrap">
      <span class="search-icon">⌕</span>
      <input class="search-input" id="search" placeholder="BUSCAR ARTISTA...">
    </div>
  </div>
  <div class="filter-bar" id="filters">
    <button class="filter-btn active" data-filter="all">TODOS</button>
    <button class="filter-btn" data-filter="hip-hop">HIP-HOP</button>
    <button class="filter-btn" data-filter="pop">POP</button>
    <button class="filter-btn" data-filter="r&b">R&B</button>
    <button class="filter-btn" data-filter="latin">LATIN</button>
  </div>
</header>

<!-- HERO -->
<section class="hero">
  <div>
    <div class="hero-label">◆ ARQUIVO MUSICAL DEFINITIVO</div>
    <h1 class="hero-title">THE<br><em>Greatest</em><br>ARCHIVE</h1>
    <p class="hero-sub">Uma biblioteca biográfica completa dos artistas que definiram a música contemporânea. Músicas icônicas, conflitos históricos, conquistas e legado.</p>
    <div class="hero-stats">
      <div class="stat-item"><div class="stat-num">9</div><div class="stat-label">ARTISTAS</div></div>
      <div class="stat-item"><div class="stat-num">50+</div><div class="stat-label">MÚSICAS</div></div>
      <div class="stat-item"><div class="stat-num">30+</div><div class="stat-label">CONFLITOS</div></div>
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
      { title: "Drake vs. Kendrick Lamar (2024)", desc: "A beef mais épica do rap moderno. Kendrick lançou 'Not Like Us' e 'Euphoria', acusando Drake de pedofilia e falsidade. Drake respondeu com 'Push Ups' e 'Family Matters'. Kendrick venceu amplamente na opinião pública.", color: "#FF6B6B" },
      { title: "Drake vs. Meek Mill (2015)", desc: "Meek acusou Drake de usar ghostwriter. Drake respondeu com 'Charged Up' e 'Back to Back', que recebeu indicação ao Grammy. Um dos beef mais unilaterais da história.", color: "#FF8B94" },
      { title: "Drake vs. Pusha T (2018)", desc: "Pusha revelou que Drake tem um filho secreto (Adonis) na faixa 'The Story of Adidon'. Drake respondeu em 'Duppy Freestyle'. Considerado um dos diss tracks mais eficazes já feitos.", color: "#FFB347" },
    ],
    actions: ["OVO Sound (gravadora)", "NBA Toronto Raptors (embaixador)", "Virginia Black (whisky)", "Série More Life", "Champagne Papi (alter ego)", "Draft pick honorário NBA"],
    timeline: [
      { year: "2006", title: "Início como ator", desc: "Interpretou Jimmy Brooks em Degrassi: The Next Generation" },
      { year: "2009", title: "So Far Gone", desc: "Mixtape que lançou sua carreira musical com 'Best I Ever Had'" },
      { year: "2011", title: "Take Care", desc: "Álbum vencedor do Grammy, consolidou seu domínio no R&B/rap" },
      { year: "2016", title: "Views", desc: "Número 1 em 100 países, quebrando recordes do Spotify" },
      { year: "2023", title: "For All The Dogs", desc: "Lançamento de volta às origens emotivas" },
    ],
    awards: ["Grammy Awards (2x)", "Billboard Music Awards (20+)", "BET Hip-Hop Awards (12+)", "American Music Awards", "Record mais streamado do Spotify (2015-2020)"],
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
      { title: "Kendrick vs. Drake (2024)", desc: "Kendrick desferiu a sequência de diss tracks mais devastadora da história: 'Euphoria' (6 min), 'Meet the Grahams', 'Not Like Us'. Acusações gravíssimas e vitória cultural massiva.", color: "#4ECDC4" },
      { title: "Control Verse (2013)", desc: "No feat de Big Sean, Kendrick declarou que queria 'matar' J. Cole, Big K.R.I.T., Meek Mill e outros. Gerou comoção mas era mais provocação artística que beef real.", color: "#45B7D1" },
      { title: "Drake vs. J. Cole - Escolha de Lado", desc: "Kendrick escolheu ativamente o lado contra Drake após J. Cole pedir trégua, mantendo a pressão com 'Not Like Us' e shows lotados cantando o hit.", color: "#A8E6CF" },
    ],
    actions: ["pgLang (empresa criativa)", "Super Bowl LVIII Halftime Show (2025)", "Pulitzer Prize for Music", "Colaboração Nike", "Curador do Black Panther OST", "Ativismo em Compton"],
    timeline: [
      { year: "2003", title: "Overly Dedicated", desc: "Mixtapes locais em Compton sob o nome K-Dot" },
      { year: "2012", title: "good kid, m.A.A.d city", desc: "Masterpiece conceitual sobre crescer em Compton" },
      { year: "2015", title: "To Pimp a Butterfly", desc: "Obra-prima de jazz, funk e consciência negra" },
      { year: "2017", title: "DAMN.", desc: "Venceu o Prêmio Pulitzer, primeiro rap a fazê-lo" },
      { year: "2022", title: "Mr. Morale & The Big Steppers", desc: "Álbum catártico sobre trauma, terapia e responsabilidade" },
    ],
    awards: ["Grammy Awards (13x)", "Pulitzer Prize for Music (2018)", "BET Hip-Hop Awards (10+)", "MTV Video Music Awards", "Super Bowl LVIII headliner"],
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
      { title: "Tragédia Astroworld (2021)", desc: "No festival Astroworld em Houston, 10 pessoas morreram e centenas ficaram feridas em uma debandada durante seu show. Travis enfrentou mais de 400 ações judiciais. A tragédia redefiniu debates sobre segurança em shows.", color: "#FF6B6B" },
      { title: "Travis vs. Industry (Cancelamento)", desc: "Após Astroworld, foi banido de festivais, perdeu contratos com Nike e outros. Seu comeback com Utopia em 2023 foi cercado de polêmica mas mostrou resiliência.", color: "#FF8B94" },
      { title: "Rival com Drake (amizade)", desc: "Travis e Drake têm uma das alianças mais poderosas do rap, mas há tensão criativa. Rumores de que Travis copiou a estética de Drake circulam há anos.", color: "#FFB347" },
    ],
    actions: ["Cactus Jack Records", "Parceria Nike (Air Jordan Cactus Jack)", "McDonald's Meal (2020)", "PlayStation Ambassador", "Fortnite Astronomical Concert (12M views)", "Utopia Tour (2023)"],
    timeline: [
      { year: "2013", title: "Owl Pharaoh", desc: "Mixtape de estreia com produção de Kanye West e T.I." },
      { year: "2016", title: "Birds in the Trap", desc: "Primeiro álbum #1 no Billboard" },
      { year: "2018", title: "Astroworld", desc: "Obra-prima nostálgica em homenagem a Houston" },
      { year: "2021", title: "Tragédia", desc: "Festival Astroworld vira tragédia com 10 mortes" },
      { year: "2023", title: "Utopia", desc: "Retorno triunfal com colaborações de Beyoncé e outros" },
    ],
    awards: ["Grammy Nominations (5x)", "BET Hip-Hop Awards (4x)", "Billboard Music Awards", "MTV VMA nominations", "Forbes 30 Under 30"],
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
      { title: "Taylor vs. Scooter Braun (2019)", desc: "Scooter Braun adquiriu os masters dos primeiros 6 álbuns de Taylor sem seu consentimento. Taylor iniciou o projeto Taylor's Version, regravando todos os álbuns para recuperar controle criativo.", color: "#C77DFF" },
      { title: "Taylor vs. Kanye West (2009-2016)", desc: "Kanye interrompeu seu discurso no VMA 2009. Anos depois, um vazamento de ligação mostrou Taylor concordando com uma letra polêmica, depois ela negou. Kim Kardashian vazou o áudio.", color: "#9B5DE5" },
      { title: "Taylor vs. Ticketmaster (2022)", desc: "O colapso da venda de ingressos do Eras Tour por falha do Ticketmaster levou Taylor a criticar publicamente a empresa e provocou investigações do Congresso americano.", color: "#F15BB5" },
    ],
    actions: ["Taylor's Version (regravações)", "Eras Tour ($1 bilhão em receita)", "Doações a bancos de alimentos", "Registro de eleitores (300k)", "NYU Doutor Honoris Causa", "Documentário Miss Americana"],
    timeline: [
      { year: "2006", title: "Álbum de estreia", desc: "Primeiro álbum country aos 16 anos pela Big Machine Records" },
      { year: "2012", title: "Red", desc: "Transição para o pop, crítica de amor e perda" },
      { year: "2014", title: "1989", desc: "Pop puro, maior álbum do ano. 5 singles no top 10" },
      { year: "2020", title: "folklore & evermore", desc: "Virada indie folk durante a pandemia, aclamadas pela crítica" },
      { year: "2023", title: "Eras Tour", desc: "Tour mais lucrativa da história da música: $1+ bilhão" },
    ],
    awards: ["Grammy Awards (14x)", "Billboard Music Awards (40+)", "American Music Awards (40+)", "MTV VMAs (14x)", "Time Person of the Year 2023"],
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
      { title: "Comentários sobre gênero e machismo", desc: "Bad Bunny frequentemente desafia normas: usou vestido, pintou unhas, defendeu direitos LGBTQ+. Isso gerou críticas de fãs conservadores mas solidificou seu status como ícone progressista.", color: "#FFE66D" },
      { title: "Recusa de turnê lucrativa", desc: "Em 2021, recusou uma proposta milionária para excluir artistas independentes de sua turnê, priorizando artistas porto-riquenhos e caribenhos menos conhecidos.", color: "#FFC107" },
      { title: "Crítica ao governo de Porto Rico", desc: "Durante as manifestações de 2019 que depuseram o governador Ricardo Rosselló, Bad Bunny foi às ruas e usou sua plataforma como ferramenta política direta.", color: "#FF9800" },
    ],
    actions: ["Campeão de streaming Spotify (3 anos)", "WWE (lutador profissional)", "Ator em Bullet Train e Narcos", "Ativismo em Porto Rico", "Diseño de moda Adidas", "El Apagón (documentário)"],
    timeline: [
      { year: "2016", title: "Diles", desc: "Single viral que o colocou no mapa do trap latino" },
      { year: "2018", title: "X 100pre", desc: "Álbum de estreia revolucionário" },
      { year: "2020", title: "YHLQMDLG", desc: "Álbum gravado em segredo, #1 global imediato" },
      { year: "2022", title: "Un Verano Sin Ti", desc: "Álbum mais streamado da história do Spotify em 2022" },
      { year: "2023", title: "nadie sabe lo que va a pasar mañana", desc: "Trap oscuro e experimental" },
    ],
    awards: ["Grammy Latino (9x)", "Billboard Latin Awards (20+)", "Spotify #1 Global (2020, 2021, 2022)", "MTV VMAs", "American Music Awards (4x)"],
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
      { title: "Acusação de Apropriação Cultural (2018)", desc: "Após o sucesso de Uptown Funk, críticos acusaram Bruno Mars de se apropriar de músicas negras (funk, R&B) sem ser negro. A discussão acendeu debates sobre identidade e crédito cultural na música.", color: "#FF8B94" },
      { title: "Prisão por Posse de Cocaína (2010)", desc: "Antes da fama, Bruno foi preso em Las Vegas por posse de drogas. O incidente foi resolvido e ele usou o episódio para reconstruir sua imagem com disciplina e foco.", color: "#FFB347" },
      { title: "Processo da gravadora", desc: "Conflitos iniciais com a Motown levaram ao cancelamento de seu contrato antes do sucesso. Ele precisou lutar para garantir controle criativo total antes de estourar.", color: "#FFC0CB" },
    ],
    actions: ["Silk Sonic (duo com Anderson .Paak)", "Residência em Las Vegas (maior bilheteria)", "Produtor de outros artistas", "Filmes e comerciais globais", "Ativismo havaiano", "Fundação de instituições de caridade"],
    timeline: [
      { year: "2010", title: "Doo-Wops & Hooligans", desc: "Álbum de estreia com hits instantâneos" },
      { year: "2012", title: "Unorthodox Jukebox", desc: "Experimentação de gêneros: reggae, funk, soul" },
      { year: "2014", title: "Uptown Funk", desc: "Uma das músicas mais vendidas de todos os tempos" },
      { year: "2021", title: "Silk Sonic", desc: "Projeto com Anderson .Paak, 4 Grammys incluindo Record of the Year" },
      { year: "2023", title: "Residência Las Vegas", desc: "Shows esgotados e receita recorde em Las Vegas" },
    ],
    awards: ["Grammy Awards (15x)", "Billboard Music Awards (10+)", "Super Bowl XLVIII Halftime", "American Music Awards (11x)", "MTV VMAs (11x)"],
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
      { title: "Boicote ao Grammy (2021)", desc: "Após ser totalmente ignorado pelo Grammy mesmo com After Hours sendo o álbum mais tocado de 2020 e Blinding Lights quebrando recordes, The Weeknd anunciou boicote à premiação, chamando-a de 'corrupta'.", color: "#74B9FF" },
      { title: "Rompimento com Bella Hadid", desc: "O relacionamento on-and-off com Bella Hadid foi documentado em músicas como 'Call Out My Name'. A exposição pública gerou debate sobre privacidade e uso de relacionamentos como material artístico.", color: "#A29BFE" },
      { title: "Super Bowl sem Grammy", desc: "O paradoxo de se apresentar no Super Bowl LV (2021) como um dos maiores artistas do mundo enquanto era ignorado pelo Grammy evidenciou as falhas do sistema de premiação.", color: "#6C5CE7" },
    ],
    actions: ["XO Records (gravadora)", "Super Bowl LV Halftime Show", "HBO The Idol (série/criador)", "Parceria Puma", "Doação $1M à BLM", "Doação à Etiópia (crise)", "Coleção moda XO"],
    timeline: [
      { year: "2011", title: "Trilogy (mixtapes)", desc: "Três mixtapes anônimas revolucionárias no SoundCloud" },
      { year: "2015", title: "Beauty Behind the Madness", desc: "Primeiro #1 no Billboard 200" },
      { year: "2016", title: "Starboy", desc: "Colaboração com Daft Punk, dominância global" },
      { year: "2020", title: "After Hours", desc: "Era mais coesa de sua carreira, Blinding Lights bate recordes" },
      { year: "2022", title: "Dawn FM", desc: "Álbum conceitual sobre morte e redenção" },
    ],
    awards: ["Grammy Awards (4x)", "Billboard Music Awards (20+)", "American Music Awards (15+)", "Juno Awards (3x)", "MTV VMAs (9x)"],
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
      { title: "Entrada e saída do beef Drake/Kendrick (2024)", desc: "J. Cole entrou com '7 Minute Drill' contra Kendrick, depois se desculpou publicamente na frente de 60.000 pessoas no Dreamville Festival. Ato de humildade raro no rap gerou debate intenso.", color: "#A8E6CF" },
      { title: "J. Cole vs. Lil Pump / SoundCloud Rap", desc: "Cole foi vocal em criticar a onda SoundCloud (Lil Pump, Tekashi 6ix9ine). 'Apparently' e outros tracks incluem indirets a artistas que priorizam estética sobre conteúdo.", color: "#88D8B0" },
      { title: "Experiência na NBA (2023)", desc: "Cole largou a música para jogar basquete profissional no Canadá. Fans e críticos questionar prioridades, mas ele usou o momento para falar sobre perseguir sonhos.", color: "#5CB8A0" },
    ],
    actions: ["Dreamville Records", "Dreamville Festival", "Jogador NBA no Canadá", "Programa habitacional em Fayetteville", "4 Your Eyez Only Foundation", "Colaboração Puma"],
    timeline: [
      { year: "2007", title: "The Come Up", desc: "Mixtape de estreia enquanto morava no sofá em NY" },
      { year: "2013", title: "Born Sinner", desc: "Primeiro #1 no Billboard, debate com Kanye" },
      { year: "2014", title: "2014 Forest Hills Drive", desc: "Álbum sem features, platina sem singles" },
      { year: "2018", title: "KOD", desc: "Álbum sobre vícios e pressão social" },
      { year: "2021", title: "The Off-Season", desc: "Retorno como 'rapper's rapper' aclamado" },
    ],
    awards: ["Grammy Nominations (5x)", "Billboard Music Awards (5x)", "BET Hip-Hop Awards (8x)", "Platinum sem singles (2014 FHD)", "Magna Cum Laude (St. John's Univ.)"],
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
      { title: "Álbum Lemonade e Jay-Z (2016)", desc: "O álbum-visual Lemonade trouxe letras sobre infidelidade que apontavam para Jay-Z. O mundo especulou, o casal ficou em silêncio, e o álbum virou um manifesto sobre traição e perdão.", color: "#F4D03F" },
      { title: "Kanye interrompendo Taylor Swift (2009)", desc: "Beyoncé ficou constrangida quando Kanye subiu ao palco durante o discurso de Taylor Swift no VMA para dizer que 'Single Ladies' merecia vencer. Beyoncé cedeu seu tempo a Taylor depois.", color: "#DAA520" },
      { title: "Renaissance e acusações de plágio", desc: "Faixas do Renaissance geraram acusações de uso não creditado de samples e letras de artistas LGBTQ+ e drag queens. Beyoncé revisou algumas letras após pressão da comunidade.", color: "#B8860B" },
    ],
    actions: ["Parkwood Entertainment", "Ivy Park (moda)", "BeyGOOD (caridade)", "Renaissance World Tour ($580M)", "Coachella 2018 (Beychella)", "Primeiro country de artista negra no #1"],
    timeline: [
      { year: "1997", title: "Destiny's Child", desc: "Grupo se torna um dos mais vendidos da história" },
      { year: "2003", title: "Dangerously in Love", desc: "Álbum solo de estreia, 5 Grammys" },
      { year: "2013", title: "Beyoncé (surpresa)", desc: "Primeiro álbum visual lançado sem aviso prévio" },
      { year: "2016", title: "Lemonade", desc: "Obra-prima política e pessoal" },
      { year: "2023", title: "Renaissance", desc: "32 Grammys no total, mais que qualquer artista na história" },
    ],
    awards: ["Grammy Awards (32x - recorde histórico)", "BET Awards (26x)", "Billboard Music Awards (30+)", "MTV VMAs (26x)", "Time 100 Most Influential"],
    featured: true,
  },
];

// ── FEATURED STRIP ──
const featuredStrip = document.getElementById('featured-strip');
artists.filter(a => a.featured).slice(0, 4).forEach(a => {
  const card = document.createElement('a');
  card.className = 'feat-card';
  card.href = '#';
  card.innerHTML = `
    <div class="feat-avatar" style="background:${a.color}22;border:1px solid ${a.color}44">${a.emoji}</div>
    <div class="feat-info">
      <h3>${a.name}</h3>
      <p>${a.genreLabel}</p>
    </div>
    <div class="feat-badge" style="background:${a.color}22;color:${a.color};border:1px solid ${a.color}44">${a.genre.toUpperCase()}</div>`;
  card.addEventListener('click', e => { e.preventDefault(); openModal(a); });
  featuredStrip.appendChild(card);
});

// ── FILTERS ──
let activeFilter = 'all';
let searchQ = '';
document.querySelectorAll('#filters .filter-btn').forEach(btn => {
  btn.addEventListener('click', () => {
    activeFilter = btn.dataset.filter;
    document.querySelectorAll('#filters .filter-btn').forEach(b => b.classList.remove('active'));
    btn.classList.add('active');
    renderGrid();
  });
});
document.getElementById('search').addEventListener('input', e => { searchQ = e.target.value; renderGrid(); });

// ── GRID ──
function renderGrid() {
  const filtered = artists.filter(a =>
    (activeFilter === 'all' || a.genre === activeFilter) &&
    (a.name.toLowerCase().includes(searchQ.toLowerCase()))
  );
  document.getElementById('count-label').textContent = filtered.length + ' ARTISTAS';
  const grid = document.getElementById('artists-grid');
  grid.innerHTML = '';
  filtered.forEach((a, i) => {
    const card = document.createElement('div');
    card.className = 'artist-card';
    card.style.animationDelay = (i * 0.07) + 's';
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
          <div class="songs-list">${a.songs.map((s, idx) => `
            <div class="song-item">
              <span class="song-num">${idx + 1}</span>
              <div class="song-dot" style="background:${a.color}"></div>
              <span class="song-name">${s.name}</span>
              <span class="song-year">${s.year}</span>
            </div>`).join('')}
          </div>
        </div>

        <div class="sub-section">
          <div class="sub-title">⚡ PRINCIPAIS CONFLITOS</div>
          <div class="conflicts-list">${a.conflicts.map(c => `
            <div class="conflict-item" style="background:${c.color}0d;border-left-color:${c.color}">
              <div class="conflict-title">${c.title}</div>
              <div class="conflict-desc">${c.desc.substring(0, 100)}...</div>
            </div>`).join('')}
          </div>
        </div>

        <div class="sub-section">
          <div class="sub-title">🏆 AÇÕES & ATIVIDADES</div>
          <div class="actions-list">${a.actions.map(ac => `<span class="action-tag">${ac}</span>`).join('')}</div>
        </div>
      </div>
      <div class="card-footer">
        <div class="footer-stat"><span>${a.songs.length}</span> HITS</div>
        <div class="footer-stat"><span>${a.conflicts.length}</span> CONFLITOS</div>
        <div class="footer-stat"><span>${a.awards.length}</span> PRÊMIOS</div>
        <button class="ver-mais-btn" style="background:${a.color}22;border:1px solid ${a.color}44;color:${a.color};" onclick="openModal(artists.find(x=>x.id==='${a.id}'))">VER MAIS →</button>
      </div>`;
    grid.appendChild(card);
  });
}

// ── MODAL ──
function openModal(a) {
  const overlay = document.getElementById('modal-overlay');
  const inner = document.getElementById('modal-inner');
  inner.innerHTML = `
    <div class="modal-hero" style="background:linear-gradient(135deg,${a.color}0f 0%,transparent 60%)">
      <button class="modal-close" onclick="closeModal()">✕</button>
      <div class="modal-emoji">${a.emoji}</div>
      <div class="modal-name">${a.name.split(' ').map((w,i) => i===0 ? w : `<em>${w}</em>`).join(' ')}</div>
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
            ${a.timeline.map(t => `
            <div class="tl-item">
              <div class="tl-year">${t.year}</div>
              <div class="tl-dot"></div>
              <div class="tl-content"><strong>${t.title}</strong>${t.desc}</div>
            </div>`).join('')}
          </div>
        </div>
        <div>
          <div class="modal-section-title">🎵 DISCOGRAFIA</div>
          <div class="songs-list" style="margin-bottom:28px">
            ${a.songs.map((s, idx) => `
            <div class="song-item" style="background:${a.color}08;border-radius:8px">
              <span class="song-num">${idx+1}</span>
              <div class="song-dot" style="background:${a.color}"></div>
              <span class="song-name" style="font-size:12px">${s.name}</span>
              <span class="song-year">${s.year}</span>
            </div>`).join('')}
          </div>
          <div class="modal-section-title">🏆 PRÊMIOS</div>
          <div class="awards-grid">
            ${a.awards.map(aw => `<div class="award-item">${aw}</div>`).join('')}
          </div>
        </div>
      </div>

      <div style="margin-top:32px">
        <div class="modal-section-title">⚡ CONFLITOS & CONTROVÉRSIAS</div>
        <div class="conflicts-list">
          ${a.conflicts.map(c => `
          <div class="conflict-item" style="background:${c.color}0d;border-left-color:${c.color};padding:14px 16px">
            <div class="conflict-title" style="font-size:13px">${c.title}</div>
            <div class="conflict-desc" style="margin-top:6px">${c.desc}</div>
          </div>`).join('')}
        </div>
      </div>

      <div style="margin-top:28px">
        <div class="modal-section-title">🚀 AÇÕES & PROJETOS</div>
        <div class="actions-list">
          ${a.actions.map(ac => `<span class="action-tag" style="font-size:11px;padding:6px 14px">${ac}</span>`).join('')}
        </div>
      </div>
    </div>`;

  overlay.classList.add('open');
  document.body.style.overflow = 'hidden';
}

function closeModal() {
  document.getElementById('modal-overlay').classList.remove('open');
  document.body.style.overflow = '';
}

document.getElementById('modal-overlay').addEventListener('click', function(e) {
  if (e.target === this) closeModal();
});

document.addEventListener('keydown', e => { if (e.key === 'Escape') closeModal(); });

// ── INIT ──
renderGrid();
</script>
</body>
</html>
