<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GALLERY — Works by Kanato</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300&family=DM+Sans:wght@300;400&display=swap" rel="stylesheet">
<style>
  :root {
    --bg: #0d0d0d;
    --surface: #161616;
    --surface2: #1f1f1f;
    --text: #f0ece4;
    --muted: #888880;
    --accent: #c9a96e;
    --accent2: #8ba89c;
    --border: rgba(240,236,228,0.08);
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-weight: 300;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ── HEADER ── */
  header {
    position: fixed;
    top: 0; left: 0; right: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1.5rem 3rem;
    background: linear-gradient(to bottom, rgba(13,13,13,0.95) 0%, transparent 100%);
  }

  .logo {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.5rem;
    font-weight: 300;
    letter-spacing: 0.15em;
    color: var(--text);
    text-decoration: none;
  }

  nav {
    display: flex;
    gap: 2.5rem;
    align-items: center;
  }

  nav a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.75rem;
    letter-spacing: 0.12em;
    text-transform: uppercase;
    transition: color 0.3s;
  }
  nav a:hover { color: var(--text); }

  /* ── SLIDER SECTION ── */
  .slider-section {
    padding-top: 80px;
  }

  .slider-label {
    padding: 1.5rem 3rem 1rem;
    font-size: 0.68rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
  }

  /* Row wrapper: two rows stacked */
  .rows-wrapper {
    display: flex;
    flex-direction: column;
    gap: 1rem;
    overflow: hidden;
    padding-bottom: 0.5rem;
  }

  .slider-row {
    display: flex;
    gap: 1rem;
    width: max-content;
    animation: slide-left 28s linear infinite;
  }

  .slider-row.row2 {
    animation: slide-left 36s linear infinite;
    animation-direction: reverse;
  }

  @keyframes slide-left {
    0%   { transform: translateX(0); }
    100% { transform: translateX(-50%); }
  }

  .rows-wrapper:hover .slider-row { animation-play-state: paused; }

  .slide-card {
    flex-shrink: 0;
    width: 260px;
    height: 170px;
    border-radius: 6px;
    overflow: hidden;
    cursor: pointer;
    position: relative;
    border: 1px solid var(--border);
    transition: border-color 0.3s;
  }

  .slide-card:hover { border-color: rgba(201,169,110,0.4); }

  .slide-card img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
    filter: brightness(0.85);
  }

  .slide-card:hover img {
    transform: scale(1.05);
    filter: brightness(1);
  }

  .slide-card-label {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    padding: 2rem 1rem 0.75rem;
    background: linear-gradient(to top, rgba(0,0,0,0.7) 0%, transparent 100%);
    font-size: 0.72rem;
    letter-spacing: 0.08em;
    opacity: 0;
    transition: opacity 0.3s;
  }
  .slide-card:hover .slide-card-label { opacity: 1; }

  /* ── DIVIDER ── */
  .section-divider {
    display: flex;
    align-items: center;
    gap: 1.5rem;
    padding: 3rem 3rem 2rem;
  }

  .section-divider span {
    font-size: 0.68rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--muted);
    white-space: nowrap;
  }

  .section-divider::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ── FIXED GALLERY ── */
  .gallery-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 1.5rem;
    padding: 0 3rem 6rem;
  }

  .gallery-item {
    cursor: pointer;
    position: relative;
    border-radius: 8px;
    overflow: hidden;
    border: 1px solid var(--border);
    background: var(--surface);
    transition: border-color 0.3s, transform 0.3s;
  }

  .gallery-item:hover {
    border-color: rgba(201,169,110,0.35);
    transform: translateY(-4px);
  }

  .gallery-item img {
    width: 100%;
    aspect-ratio: 4/3;
    object-fit: cover;
    display: block;
    filter: brightness(0.9);
    transition: filter 0.4s;
  }

  .gallery-item:hover img { filter: brightness(1); }

  .gallery-info {
    padding: 1rem 1.1rem 1.2rem;
  }

  .gallery-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.15rem;
    font-weight: 300;
    margin-bottom: 0.3rem;
    color: var(--text);
  }

  .gallery-sub {
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.06em;
  }

  .gallery-badge {
    display: inline-block;
    margin-top: 0.6rem;
    padding: 0.2rem 0.6rem;
    background: rgba(201,169,110,0.12);
    border: 1px solid rgba(201,169,110,0.3);
    color: var(--accent);
    font-size: 0.65rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    border-radius: 3px;
  }

  /* ── MODAL ── */
  .modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    z-index: 200;
    background: rgba(5,5,5,0.92);
    backdrop-filter: blur(8px);
    align-items: center;
    justify-content: center;
    padding: 2rem;
  }

  .modal-overlay.open { display: flex; }

  .modal {
    background: var(--surface);
    border: 1px solid rgba(240,236,228,0.12);
    border-radius: 12px;
    max-width: 860px;
    width: 100%;
    max-height: 90vh;
    overflow-y: auto;
    position: relative;
    animation: modal-in 0.3s cubic-bezier(0.16,1,0.3,1);
  }

  @keyframes modal-in {
    from { opacity: 0; transform: scale(0.95) translateY(20px); }
    to   { opacity: 1; transform: scale(1)   translateY(0); }
  }

  .modal-close {
    position: absolute;
    top: 1.2rem; right: 1.2rem;
    background: none;
    border: 1px solid var(--border);
    color: var(--muted);
    width: 32px; height: 32px;
    border-radius: 50%;
    font-size: 1rem;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    transition: all 0.2s;
    z-index: 1;
  }
  .modal-close:hover { color: var(--text); border-color: rgba(240,236,228,0.3); }

  .modal-header {
    padding: 2rem 2rem 1.2rem;
    border-bottom: 1px solid var(--border);
  }

  .modal-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.8rem;
    font-weight: 300;
    margin-bottom: 0.3rem;
  }

  .modal-desc {
    font-size: 0.82rem;
    color: var(--muted);
    line-height: 1.7;
  }

  .modal-previews {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
    padding: 1.5rem 2rem;
  }

  .preview-thumb {
    border-radius: 6px;
    overflow: hidden;
    border: 1px solid var(--border);
    transition: border-color 0.3s;
    cursor: pointer;
  }
  .preview-thumb:hover { border-color: rgba(201,169,110,0.4); }

  .preview-thumb img {
    width: 100%;
    aspect-ratio: 4/3;
    object-fit: cover;
    display: block;
    filter: brightness(0.85);
    transition: filter 0.3s;
  }
  .preview-thumb:hover img { filter: brightness(1); }

  .preview-num {
    padding: 0.5rem 0.75rem;
    font-size: 0.68rem;
    color: var(--muted);
    letter-spacing: 0.06em;
  }

  .modal-footer {
    padding: 1.5rem 2rem 2rem;
    border-top: 1px solid var(--border);
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  .modal-footer-note {
    font-size: 0.78rem;
    color: var(--muted);
  }

  .btn-view-all {
    display: inline-flex;
    align-items: center;
    gap: 0.6rem;
    padding: 0.7rem 1.6rem;
    background: var(--accent);
    color: #0d0d0d;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.78rem;
    font-weight: 400;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    text-decoration: none;
    border-radius: 4px;
    border: none;
    cursor: pointer;
    transition: background 0.3s, transform 0.2s;
  }
  .btn-view-all:hover { background: #d4b57c; transform: translateX(2px); }
  .btn-view-all svg { width: 14px; height: 14px; }

  /* ── FOOTER ── */
  footer {
    border-top: 1px solid var(--border);
    padding: 2rem 3rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    font-size: 0.72rem;
    color: var(--muted);
    letter-spacing: 0.06em;
  }

  /* scrollbar */
  ::-webkit-scrollbar { width: 5px; }
  ::-webkit-scrollbar-track { background: var(--bg); }
  ::-webkit-scrollbar-thumb { background: var(--surface2); border-radius: 10px; }
</style>
</head>
<body>

<header>
  <a href="#" class="logo">GALLERY</a>
  <nav>
    <a href="#">Works</a>
    <a href="#">Series</a>
    <a href="#">About</a>
    <a href="#">Contact</a>
  </nav>
</header>

<!-- AUTO SLIDER -->
<div class="slider-section">
  <p class="slider-label">— Recent Works</p>

  <div class="rows-wrapper">

    <!-- Row 1 (duplicated for seamless loop) -->
    <div class="slider-row" id="row1">
      <!-- duplicated inside by JS -->
    </div>

    <!-- Row 2 -->
    <div class="slider-row row2" id="row2">
    </div>

  </div>
</div>

<!-- FIXED GALLERY -->
<div class="section-divider"><span>Featured Works</span></div>

<div class="gallery-grid" id="galleryGrid"></div>

<!-- MODAL -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal" id="modal">
    <button class="modal-close" id="modalClose">✕</button>
    <div class="modal-header">
      <h2 class="modal-title" id="modalTitle"></h2>
      <p class="modal-desc" id="modalDesc"></p>
    </div>
    <div class="modal-previews" id="modalPreviews"></div>
    <div class="modal-footer">
      <span class="modal-footer-note" id="modalNote"></span>
      <a class="btn-view-all" id="modalLink" href="#" target="_blank">
        View Full Series
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
          <path d="M5 12h14M12 5l7 7-7 7"/>
        </svg>
      </a>
    </div>
  </div>
</div>

<footer>
  <span>© 2025 Kanato — All rights reserved</span>
  <span>Made with care ✦</span>
</footer>

<script>
/* ── DATA ── */
/* 実際の画像URLをここに入れてください */
const WORKS = [
  {
    id: 1,
    title: "Twilight No.1",
    sub: "Digital Illustration · 2024",
    tag: "Series A",
    desc: "夕暮れの情景をテーマにしたシリーズ作品。光と影のコントラストを丁寧に描きました。",
    note: "シリーズ全8枚 — 外部サイトで閲覧できます",
    url: "https://example.com/series/twilight",
    thumb: "https://images.unsplash.com/photo-1579546929518-9e396f3cc809?w=600&q=80",
    previews: [
      "https://images.unsplash.com/photo-1502134249126-9f3755a50d78?w=400&q=80",
      "https://images.unsplash.com/photo-1513151233558-d860c5398176?w=400&q=80",
      "https://images.unsplash.com/photo-1501862700950-18382cd41497?w=400&q=80"
    ]
  },
  {
    id: 2,
    title: "Blue Archive Fan Art",
    sub: "Character Illustration · 2024",
    tag: "Fan Art",
    desc: "ブルーアーカイブのキャラクターをオリジナルの構図で描いた作品集。",
    note: "シリーズ全5枚 — 外部サイトで閲覧できます",
    url: "https://example.com/series/blue-archive",
    thumb: "https://images.unsplash.com/photo-1518173946687-a4c8892bbd9f?w=600&q=80",
    previews: [
      "https://images.unsplash.com/photo-1505506874110-6a7a69069a08?w=400&q=80",
      "https://images.unsplash.com/photo-1528360983277-13d401cdc186?w=400&q=80",
      "https://images.unsplash.com/photo-1470813740244-df37b8c1edcb?w=400&q=80"
    ]
  },
  {
    id: 3,
    title: "Monochrome Study",
    sub: "Concept Art · 2024",
    tag: "Series B",
    desc: "モノクロの世界で表現した都市と自然の対比をテーマにした実験的シリーズ。",
    note: "シリーズ全6枚 — 外部サイトで閲覧できます",
    url: "https://example.com/series/monochrome",
    thumb: "https://images.unsplash.com/photo-1524055988636-436cfa46e59e?w=600&q=80",
    previews: [
      "https://images.unsplash.com/photo-1536184635451-90a0cc3f7e5c?w=400&q=80",
      "https://images.unsplash.com/photo-1555680202-c86f0e12f086?w=400&q=80",
      "https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=400&q=80"
    ]
  },
  {
    id: 4,
    title: "Neon Dreams",
    sub: "Digital Art · 2025",
    tag: "New Work",
    desc: "サイバーパンク的な世界観をベースに、夜の都市の光を幻想的に描いたシリーズ。",
    note: "シリーズ全10枚 — 外部サイトで閲覧できます",
    url: "https://example.com/series/neon",
    thumb: "https://images.unsplash.com/photo-1558618666-fcd25c85cd64?w=600&q=80",
    previews: [
      "https://images.unsplash.com/photo-1519608487953-e999c86e7455?w=400&q=80",
      "https://images.unsplash.com/photo-1482160549825-59d1b23cb208?w=400&q=80",
      "https://images.unsplash.com/photo-1542831371-d531d36971e6?w=400&q=80"
    ]
  },
  {
    id: 5,
    title: "Spring Petals",
    sub: "Illustration · 2025",
    tag: "Series C",
    desc: "春をテーマにしたやわらかい色彩のイラストシリーズ。桜と女の子たち。",
    note: "シリーズ全7枚 — 外部サイトで閲覧できます",
    url: "https://example.com/series/spring",
    thumb: "https://images.unsplash.com/photo-1490750967868-88df5691cc02?w=600&q=80",
    previews: [
      "https://images.unsplash.com/photo-1462275646964-a0e3386b89fa?w=400&q=80",
      "https://images.unsplash.com/photo-1441974231531-c6227db76b6e?w=400&q=80",
      "https://images.unsplash.com/photo-1506905925346-21bda4d32df4?w=400&q=80"
    ]
  },
  {
    id: 6,
    title: "Portrait Study",
    sub: "Character Design · 2025",
    tag: "New Work",
    desc: "オリジナルキャラクターのポートレート研究。さまざまな表情と光源で描いた習作集。",
    note: "シリーズ全12枚 — 外部サイトで閲覧できます",
    url: "https://example.com/series/portrait",
    thumb: "https://images.unsplash.com/photo-1520975954732-35dd22299614?w=600&q=80",
    previews: [
      "https://images.unsplash.com/photo-1531746020798-e6953c6e8e04?w=400&q=80",
      "https://images.unsplash.com/photo-1544005313-94ddf0286df2?w=400&q=80",
      "https://images.unsplash.com/photo-1567532939604-b6b5b0db2604?w=400&q=80"
    ]
  }
];

/* ── SLIDER ── */
const sliderImages = WORKS.map(w => ({ src: w.thumb, label: w.title, id: w.id }));

function buildSliderRow(el, items, offset = 0) {
  const all = [...items, ...items]; // duplicate for seamless loop
  all.forEach((item, i) => {
    const idx = (i + offset) % items.length;
    const card = document.createElement('div');
    card.className = 'slide-card';
    card.innerHTML = `
      <img src="${items[idx].src}" alt="${items[idx].label}" loading="lazy">
      <div class="slide-card-label">${items[idx].label}</div>
    `;
    card.addEventListener('click', () => openModal(items[idx].id));
    el.appendChild(card);
  });
}

buildSliderRow(document.getElementById('row1'), sliderImages, 0);
buildSliderRow(document.getElementById('row2'), sliderImages, 3);

/* ── GALLERY ── */
const grid = document.getElementById('galleryGrid');
WORKS.forEach(w => {
  const item = document.createElement('div');
  item.className = 'gallery-item';
  item.innerHTML = `
    <img src="${w.thumb}" alt="${w.title}" loading="lazy">
    <div class="gallery-info">
      <div class="gallery-title">${w.title}</div>
      <div class="gallery-sub">${w.sub}</div>
      <span class="gallery-badge">${w.tag}</span>
    </div>
  `;
  item.addEventListener('click', () => openModal(w.id));
  grid.appendChild(item);
});

/* ── MODAL ── */
function openModal(id) {
  const work = WORKS.find(w => w.id === id);
  if (!work) return;

  document.getElementById('modalTitle').textContent = work.title;
  document.getElementById('modalDesc').textContent = work.desc;
  document.getElementById('modalNote').textContent = work.note;
  document.getElementById('modalLink').href = work.url;

  const previews = document.getElementById('modalPreviews');
  previews.innerHTML = '';
  work.previews.forEach((src, i) => {
    const thumb = document.createElement('div');
    thumb.className = 'preview-thumb';
    thumb.innerHTML = `
      <img src="${src}" alt="Preview ${i+1}" loading="lazy">
      <div class="preview-num">Page ${i+1} / ${work.previews.length}</div>
    `;
    previews.appendChild(thumb);
  });

  document.getElementById('modalOverlay').classList.add('open');
  document.body.style.overflow = 'hidden';
}

function closeModal() {
  document.getElementById('modalOverlay').classList.remove('open');
  document.body.style.overflow = '';
}

document.getElementById('modalClose').addEventListener('click', closeModal);
document.getElementById('modalOverlay').addEventListener('click', e => {
  if (e.target === e.currentTarget) closeModal();
});
document.addEventListener('keydown', e => { if (e.key === 'Escape') closeModal(); });
</script>
</body>
</html>
