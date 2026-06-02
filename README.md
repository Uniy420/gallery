<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>GALLERY — Works by Kanato</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;1,300&family=DM+Sans:wght@300;400&display=swap" rel="stylesheet">
<style>
:root{--bg:#0d0d0d;--surface:#161616;--surface2:#1f1f1f;--text:#f0ece4;--muted:#888880;--accent:#c9a96e;--border:rgba(240,236,228,0.08);--admin-bg:#111;--admin-surface:#1a1a1a;--admin-border:rgba(255,255,255,0.1)}
*{margin:0;padding:0;box-sizing:border-box}
body{background:var(--bg);color:var(--text);font-family:'DM Sans',sans-serif;font-weight:300;min-height:100vh;overflow-x:hidden}

/* HEADER */
header{position:fixed;top:0;left:0;right:0;z-index:100;display:flex;align-items:center;justify-content:space-between;padding:1.4rem 3rem;background:linear-gradient(to bottom,rgba(13,13,13,0.95),transparent)}
.logo{font-family:'Cormorant Garamond',serif;font-size:1.5rem;font-weight:300;letter-spacing:.15em;color:var(--text);text-decoration:none}
nav{display:flex;gap:2rem;align-items:center}
nav a{color:var(--muted);text-decoration:none;font-size:.75rem;letter-spacing:.12em;text-transform:uppercase;transition:color .3s;cursor:pointer;background:none;border:none;font-family:'DM Sans',sans-serif}
nav a:hover,nav a.active{color:var(--text)}
.admin-btn{background:none;border:1px solid rgba(201,169,110,.4);color:var(--accent);padding:.4rem 1rem;border-radius:4px;font-size:.72rem;letter-spacing:.1em;text-transform:uppercase;cursor:pointer;transition:all .3s;font-family:'DM Sans',sans-serif}
.admin-btn:hover{background:rgba(201,169,110,.1)}

/* PAGE VIEWS */
.page{display:none}.page.active{display:block}

/* SLIDER */
.slider-section{padding-top:80px}
.slider-label{padding:1.5rem 3rem 1rem;font-size:.68rem;letter-spacing:.2em;text-transform:uppercase;color:var(--muted)}
.rows-wrapper{display:flex;flex-direction:column;gap:1rem;overflow:hidden;padding-bottom:.5rem}
.slider-row{display:flex;gap:1rem;width:max-content;animation:slide-left 28s linear infinite}
.slider-row.row2{animation-duration:36s;animation-direction:reverse}
@keyframes slide-left{0%{transform:translateX(0)}100%{transform:translateX(-50%)}}
.rows-wrapper:hover .slider-row{animation-play-state:paused}
.slide-card{flex-shrink:0;width:260px;height:170px;border-radius:6px;overflow:hidden;cursor:pointer;position:relative;border:1px solid var(--border);transition:border-color .3s}
.slide-card:hover{border-color:rgba(201,169,110,.4)}
.slide-card img{width:100%;height:100%;object-fit:cover;transition:transform .5s ease;filter:brightness(.85)}
.slide-card:hover img{transform:scale(1.05);filter:brightness(1)}
.slide-card-label{position:absolute;bottom:0;left:0;right:0;padding:2rem 1rem .75rem;background:linear-gradient(to top,rgba(0,0,0,.7),transparent);font-size:.72rem;letter-spacing:.08em;opacity:0;transition:opacity .3s}
.slide-card:hover .slide-card-label{opacity:1}

/* DIVIDER */
.section-divider{display:flex;align-items:center;gap:1.5rem;padding:3rem 3rem 2rem}
.section-divider span{font-size:.68rem;letter-spacing:.2em;text-transform:uppercase;color:var(--muted);white-space:nowrap}
.section-divider::after{content:'';flex:1;height:1px;background:var(--border)}

/* GALLERY */
.gallery-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:1.5rem;padding:0 3rem 6rem}
.gallery-item{cursor:pointer;border-radius:8px;overflow:hidden;border:1px solid var(--border);background:var(--surface);transition:border-color .3s,transform .3s}
.gallery-item:hover{border-color:rgba(201,169,110,.35);transform:translateY(-4px)}
.gallery-item img{width:100%;aspect-ratio:4/3;object-fit:cover;display:block;filter:brightness(.9);transition:filter .4s}
.gallery-item:hover img{filter:brightness(1)}
.gallery-info{padding:1rem 1.1rem 1.2rem}
.gallery-title{font-family:'Cormorant Garamond',serif;font-size:1.15rem;font-weight:300;margin-bottom:.3rem}
.gallery-sub{font-size:.72rem;color:var(--muted);letter-spacing:.06em}
.gallery-tags{display:flex;flex-wrap:wrap;gap:.4rem;margin-top:.6rem}
.gallery-badge{display:inline-block;padding:.2rem .6rem;background:rgba(201,169,110,.12);border:1px solid rgba(201,169,110,.3);color:var(--accent);font-size:.65rem;letter-spacing:.1em;text-transform:uppercase;border-radius:3px}

/* SERIES PAGE */
#seriesPage{padding-top:100px;padding-bottom:6rem}
.series-page-title{font-family:'Cormorant Garamond',serif;font-size:2rem;font-weight:300;letter-spacing:.08em;padding:0 3rem 2rem}
.year-section{margin-bottom:3rem}
.year-heading{font-size:.68rem;letter-spacing:.25em;text-transform:uppercase;color:var(--muted);padding:.5rem 3rem 1.2rem;border-bottom:1px solid var(--border);margin:0 0 1.5rem}
.month-group{margin-bottom:2rem;padding:0 3rem}
.month-label{font-size:.72rem;letter-spacing:.15em;text-transform:uppercase;color:var(--accent);margin-bottom:1rem;display:flex;align-items:center;gap:.75rem}
.month-label::after{content:'';flex:1;height:1px;background:rgba(201,169,110,.15)}
.month-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:1rem}
.month-card{cursor:pointer;border-radius:6px;overflow:hidden;border:1px solid var(--border);background:var(--surface);transition:border-color .3s,transform .3s}
.month-card:hover{border-color:rgba(201,169,110,.35);transform:translateY(-3px)}
.month-card img{width:100%;aspect-ratio:3/2;object-fit:cover;display:block;filter:brightness(.85);transition:filter .4s}
.month-card:hover img{filter:brightness(1)}
.month-card-info{padding:.7rem .85rem .85rem}
.month-card-title{font-family:'Cormorant Garamond',serif;font-size:1rem;font-weight:300;margin-bottom:.25rem}
.month-card-tags{display:flex;flex-wrap:wrap;gap:.3rem;margin-top:.4rem}
.month-card-badge{display:inline-block;padding:.15rem .45rem;background:rgba(201,169,110,.1);border:1px solid rgba(201,169,110,.25);color:var(--accent);font-size:.6rem;letter-spacing:.08em;text-transform:uppercase;border-radius:2px}

/* WORK MODAL */
.modal-overlay{display:none;position:fixed;inset:0;z-index:200;background:rgba(5,5,5,.92);backdrop-filter:blur(8px);align-items:center;justify-content:center;padding:1.5rem}
.modal-overlay.open{display:flex}
.modal{background:var(--surface);border:1px solid rgba(240,236,228,.12);border-radius:12px;max-width:780px;width:100%;max-height:92vh;overflow-y:auto;position:relative;animation:modal-in .3s cubic-bezier(.16,1,.3,1)}
@keyframes modal-in{from{opacity:0;transform:scale(.95) translateY(20px)}to{opacity:1;transform:scale(1) translateY(0)}}
.modal-close{position:absolute;top:1rem;right:1rem;background:rgba(0,0,0,.5);border:1px solid var(--border);color:var(--muted);width:32px;height:32px;border-radius:50%;font-size:1rem;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;z-index:10}
.modal-close:hover{color:var(--text);border-color:rgba(240,236,228,.3)}
.modal-header{padding:1.5rem 1.5rem 1rem;border-bottom:1px solid var(--border)}
.modal-title{font-family:'Cormorant Garamond',serif;font-size:1.6rem;font-weight:300;margin-bottom:.25rem}
.modal-desc{font-size:.8rem;color:var(--muted);line-height:1.7;margin-top:.3rem}
.modal-tags{display:flex;flex-wrap:wrap;gap:.4rem;margin-top:.6rem}

/* Preview thumbnails grid — fit image naturally */
.modal-previews{display:flex;flex-direction:column;gap:.75rem;padding:1.2rem 1.5rem}
.preview-thumb{border-radius:6px;overflow:hidden;border:1px solid var(--border);cursor:pointer;transition:border-color .3s;background:rgba(0,0,0,.3)}
.preview-thumb:hover{border-color:rgba(201,169,110,.4)}
.preview-thumb img{width:100%;height:auto;display:block;max-height:420px;object-fit:contain;filter:brightness(.9);transition:filter .3s}
.preview-thumb:hover img{filter:brightness(1)}
.preview-num{padding:.45rem .75rem;font-size:.65rem;color:var(--muted)}

.modal-footer{padding:1.2rem 1.5rem 1.5rem;border-top:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;gap:1rem}
.modal-footer-note{font-size:.75rem;color:var(--muted)}
.btn-view-all{display:inline-flex;align-items:center;gap:.6rem;padding:.65rem 1.4rem;background:var(--accent);color:#0d0d0d;font-family:'DM Sans',sans-serif;font-size:.76rem;letter-spacing:.08em;text-transform:uppercase;text-decoration:none;border-radius:4px;border:none;cursor:pointer;transition:background .3s,transform .2s;white-space:nowrap}
.btn-view-all:hover{background:#d4b57c;transform:translateX(2px)}

/* LIGHTBOX */
.lightbox{display:none;position:fixed;inset:0;z-index:300;background:rgba(0,0,0,.96);align-items:center;justify-content:center}
.lightbox.open{display:flex}
.lightbox-img{max-width:90vw;max-height:90vh;object-fit:contain;border-radius:4px;animation:lb-in .25s ease}
@keyframes lb-in{from{opacity:0;transform:scale(.97)}to{opacity:1;transform:scale(1)}}
.lightbox-close{position:absolute;top:1.2rem;right:1.5rem;background:none;border:none;color:rgba(255,255,255,.5);font-size:1.8rem;cursor:pointer;transition:color .2s}
.lightbox-close:hover{color:#fff}
.lightbox-nav{position:absolute;top:50%;transform:translateY(-50%);background:rgba(255,255,255,.08);border:1px solid rgba(255,255,255,.15);color:rgba(255,255,255,.7);width:44px;height:44px;border-radius:50%;font-size:1.1rem;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s}
.lightbox-nav:hover{background:rgba(255,255,255,.15);color:#fff}
.lightbox-prev{left:1.5rem}
.lightbox-next{right:1.5rem}
.lightbox-counter{position:absolute;bottom:1.5rem;left:50%;transform:translateX(-50%);font-size:.72rem;color:rgba(255,255,255,.4);letter-spacing:.1em}

/* PASSWORD MODAL */
.pw-overlay{display:none;position:fixed;inset:0;z-index:600;background:rgba(0,0,0,.85);backdrop-filter:blur(10px);align-items:center;justify-content:center}
.pw-overlay.open{display:flex}
.pw-box{background:var(--admin-bg);border:1px solid var(--admin-border);border-radius:12px;padding:2.5rem;width:min(380px,90vw);text-align:center}
.pw-title{font-family:'Cormorant Garamond',serif;font-size:1.5rem;font-weight:300;margin-bottom:.4rem;letter-spacing:.05em}
.pw-sub{font-size:.75rem;color:var(--muted);margin-bottom:1.5rem}
.pw-input{width:100%;background:rgba(255,255,255,.05);border:1px solid var(--admin-border);color:var(--text);font-family:'DM Sans',sans-serif;font-size:.9rem;padding:.65rem 1rem;border-radius:6px;outline:none;text-align:center;letter-spacing:.15em;transition:border-color .2s;margin-bottom:.75rem}
.pw-input:focus{border-color:rgba(201,169,110,.5)}
.pw-error{font-size:.72rem;color:rgba(255,100,100,.8);margin-bottom:.75rem;min-height:1em}
.pw-btn{width:100%;padding:.65rem;background:var(--accent);color:#0d0d0d;border:none;border-radius:6px;font-family:'DM Sans',sans-serif;font-size:.8rem;letter-spacing:.1em;text-transform:uppercase;cursor:pointer;transition:background .3s}
.pw-btn:hover{background:#d4b57c}

/* ADMIN PANEL */
.admin-overlay{display:none;position:fixed;inset:0;z-index:500;background:rgba(0,0,0,.6);backdrop-filter:blur(6px)}
.admin-overlay.open{display:block}
.admin-panel{position:fixed;top:0;right:0;bottom:0;width:min(640px,100vw);z-index:501;background:var(--admin-bg);border-left:1px solid var(--admin-border);overflow-y:auto;transform:translateX(100%);transition:transform .35s cubic-bezier(.16,1,.3,1)}
.admin-panel.open{transform:translateX(0)}
.admin-header{padding:1.2rem 1.5rem;border-bottom:1px solid var(--admin-border);display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;background:var(--admin-bg);z-index:1}
.admin-header h2{font-family:'Cormorant Garamond',serif;font-size:1.3rem;font-weight:300;letter-spacing:.05em}
.admin-header-actions{display:flex;gap:.6rem;align-items:center}
.btn-dl{display:inline-flex;align-items:center;gap:.4rem;padding:.45rem 1rem;background:var(--accent);color:#0d0d0d;border:none;border-radius:4px;font-size:.72rem;font-family:'DM Sans',sans-serif;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;transition:background .3s}
.btn-dl:hover{background:#d4b57c}
.btn-close-admin{background:none;border:1px solid var(--admin-border);color:var(--muted);width:30px;height:30px;border-radius:50%;font-size:.9rem;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s}
.btn-close-admin:hover{color:var(--text)}

/* Admin tabs */
.admin-tabs{display:flex;border-bottom:1px solid var(--admin-border);padding:0 1.5rem}
.admin-tab{background:none;border:none;border-bottom:2px solid transparent;color:var(--muted);font-family:'DM Sans',sans-serif;font-size:.72rem;letter-spacing:.1em;text-transform:uppercase;padding:.75rem .5rem;cursor:pointer;transition:all .2s;margin-bottom:-1px}
.admin-tab.active{color:var(--accent);border-bottom-color:var(--accent)}
.admin-tab-content{display:none;padding:1.2rem 1.5rem 3rem}
.admin-tab-content.active{display:block}

.admin-section-title{font-size:.65rem;letter-spacing:.2em;text-transform:uppercase;color:var(--muted);margin:1.2rem 0 .65rem;padding-bottom:.4rem;border-bottom:1px solid var(--admin-border)}
.field{margin-top:.85rem}
.field label{display:block;font-size:.65rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:.3rem}
.field input,.field textarea,.field select{width:100%;background:rgba(255,255,255,.04);border:1px solid var(--admin-border);color:var(--text);font-family:'DM Sans',sans-serif;font-size:.82rem;padding:.5rem .7rem;border-radius:4px;outline:none;transition:border-color .2s}
.field input:focus,.field textarea:focus,.field select:focus{border-color:rgba(201,169,110,.5)}
.field textarea{resize:vertical;min-height:55px;line-height:1.5}
.field select option{background:#1a1a1a}
.field-row{display:grid;grid-template-columns:1fr 1fr;gap:.7rem}
.field-row3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:.5rem}

/* Tags in admin */
.tags-row{display:flex;gap:.5rem}
.tags-row input{flex:1}

/* preview list */
.preview-list{display:flex;flex-direction:column;gap:.5rem;margin-top:.35rem}
.preview-item{display:flex;align-items:center;gap:.5rem}
.preview-item span{font-size:.68rem;color:var(--muted);white-space:nowrap;min-width:18px}
.preview-item input{flex:1}
.preview-item img.prev-thumb{width:34px;height:26px;object-fit:cover;border-radius:3px;border:1px solid var(--admin-border);flex-shrink:0}
.btn-add-preview{background:none;border:1px dashed var(--admin-border);color:var(--muted);width:100%;padding:.4rem;border-radius:4px;font-size:.7rem;cursor:pointer;margin-top:.45rem;transition:all .2s;font-family:'DM Sans',sans-serif}
.btn-add-preview:hover{border-color:rgba(201,169,110,.4);color:var(--accent)}
.btn-remove-preview{background:none;border:none;color:rgba(255,100,100,.45);font-size:.85rem;cursor:pointer;padding:.1rem .25rem;transition:color .2s;flex-shrink:0}
.btn-remove-preview:hover{color:rgba(255,100,100,.9)}

/* work cards */
.work-card-admin{background:var(--admin-surface);border:1px solid var(--admin-border);border-radius:8px;margin-bottom:.85rem;overflow:hidden}
.work-card-header{display:flex;align-items:center;justify-content:space-between;padding:.75rem .9rem;cursor:pointer;transition:background .2s}
.work-card-header:hover{background:rgba(255,255,255,.03)}
.work-card-header-left{display:flex;align-items:center;gap:.65rem}
.work-card-header-left img{width:40px;height:30px;object-fit:cover;border-radius:3px;border:1px solid var(--admin-border)}
.work-card-title-sm{font-size:.82rem;letter-spacing:.03em}
.work-card-toggle{font-size:.6rem;color:var(--muted)}
.work-card-body{display:none;padding:0 .9rem .9rem;border-top:1px solid var(--admin-border)}
.work-card-body.open{display:block}
.btn-add-work{width:100%;background:none;border:1px dashed rgba(201,169,110,.3);color:var(--accent);padding:.65rem;border-radius:6px;font-size:.72rem;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;margin-top:.5rem;transition:all .2s;font-family:'DM Sans',sans-serif}
.btn-add-work:hover{background:rgba(201,169,110,.06);border-color:rgba(201,169,110,.5)}
.btn-delete-work{background:none;border:1px solid rgba(255,80,80,.25);color:rgba(255,100,100,.6);padding:.3rem .7rem;border-radius:4px;font-size:.65rem;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;transition:all .2s;font-family:'DM Sans',sans-serif}
.btn-delete-work:hover{background:rgba(255,80,80,.1);color:rgba(255,100,100,.9)}

/* Display settings */
.radio-group{display:flex;flex-direction:column;gap:.5rem;margin-top:.4rem}
.radio-label{display:flex;align-items:center;gap:.6rem;font-size:.8rem;cursor:pointer;color:var(--text)}
.radio-label input[type=radio]{accent-color:var(--accent)}
.color-preview{width:24px;height:24px;border-radius:4px;border:1px solid var(--admin-border);flex-shrink:0;display:inline-block;vertical-align:middle;margin-left:.4rem}

.toast{position:fixed;bottom:2rem;left:50%;transform:translateX(-50%) translateY(80px);background:var(--accent);color:#0d0d0d;padding:.55rem 1.3rem;border-radius:4px;font-size:.76rem;letter-spacing:.06em;z-index:999;opacity:0;transition:all .4s}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}
footer{border-top:1px solid var(--border);padding:1.8rem 3rem;display:flex;justify-content:space-between;align-items:center;font-size:.72rem;color:var(--muted)}
::-webkit-scrollbar{width:5px}::-webkit-scrollbar-track{background:var(--bg)}::-webkit-scrollbar-thumb{background:var(--surface2);border-radius:10px}
</style>
</head>
<body>

<header>
  <a href="#" class="logo" onclick="showPage('home');return false">GALLERY</a>
  <nav>
    <a onclick="showPage('series')" id="navSeries">Series</a>
    <button class="admin-btn" id="openAdmin">⚙ 管理</button>
  </nav>
</header>

<!-- HOME PAGE -->
<div id="homePage" class="page active">
  <div class="slider-section" id="sliderSection">
    <p class="slider-label" id="sliderLabel">— Recent Works</p>
    <div class="rows-wrapper" id="rowsWrapper">
      <div class="slider-row" id="row1"></div>
      <div class="slider-row row2" id="row2"></div>
    </div>
  </div>
  <div class="section-divider" id="featuredDivider"><span>Featured Works</span></div>
  <div class="gallery-grid" id="galleryGrid"></div>
</div>

<!-- SERIES PAGE -->
<div id="seriesPage" class="page">
  <h1 class="series-page-title">Series</h1>
  <div id="seriesContent"></div>
</div>

<!-- WORK MODAL -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal" id="modal">
    <button class="modal-close" id="modalClose">✕</button>
    <div class="modal-header">
      <h2 class="modal-title" id="modalTitle"></h2>
      <p class="modal-desc" id="modalDesc"></p>
      <div class="modal-tags" id="modalTags"></div>
    </div>
    <div class="modal-previews" id="modalPreviews"></div>
    <div class="modal-footer">
      <span class="modal-footer-note" id="modalNote"></span>
      <a class="btn-view-all" id="modalLink" href="#" target="_blank">
        View Full Series
        <svg width="13" height="13" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
      </a>
    </div>
  </div>
</div>

<!-- LIGHTBOX -->
<div class="lightbox" id="lightbox">
  <button class="lightbox-close" id="lbClose">✕</button>
  <button class="lightbox-nav lightbox-prev" id="lbPrev">&#8592;</button>
  <img class="lightbox-img" id="lbImg" src="" alt="">
  <button class="lightbox-nav lightbox-next" id="lbNext">&#8594;</button>
  <div class="lightbox-counter" id="lbCounter"></div>
</div>

<!-- PASSWORD MODAL -->
<div class="pw-overlay" id="pwOverlay">
  <div class="pw-box">
    <div class="pw-title">管理パネル</div>
    <div class="pw-sub">パスワードを入力してください</div>
    <input class="pw-input" type="password" id="pwInput" placeholder="••••••••••" maxlength="30">
    <div class="pw-error" id="pwError"></div>
    <button class="pw-btn" id="pwBtn">Enter</button>
  </div>
</div>

<!-- ADMIN PANEL -->
<div class="admin-overlay" id="adminOverlay"></div>
<div class="admin-panel" id="adminPanel">
  <div class="admin-header">
    <h2>管理パネル</h2>
    <div class="admin-header-actions">
      <button class="btn-dl" id="btnDownload">⬇ DL</button>
      <button class="btn-close-admin" id="closeAdmin">✕</button>
    </div>
  </div>
  <div class="admin-tabs">
    <button class="admin-tab active" data-tab="works">作品管理</button>
    <button class="admin-tab" data-tab="display">表示設定</button>
  </div>
  <!-- WORKS TAB -->
  <div class="admin-tab-content active" id="tabWorks">
    <p class="admin-section-title">作品を編集</p>
    <div id="workList"></div>
    <button class="btn-add-work" id="btnAddWork">＋ 作品を追加</button>
  </div>
  <!-- DISPLAY TAB -->
  <div class="admin-tab-content" id="tabDisplay">
    <p class="admin-section-title">ホーム画面スライダー</p>
    <div class="field">
      <label>スライダー表示設定</label>
      <div class="radio-group">
        <label class="radio-label"><input type="radio" name="sliderMode" value="both" checked> 両方表示（Recent + Featured）</label>
        <label class="radio-label"><input type="radio" name="sliderMode" value="recent"> Recent Worksのみ</label>
        <label class="radio-label"><input type="radio" name="sliderMode" value="featured"> Featured Worksのみ</label>
        <label class="radio-label"><input type="radio" name="sliderMode" value="none"> 非表示</label>
      </div>
    </div>
    <p class="admin-section-title" style="margin-top:1.5rem">サイト背景色</p>
    <div class="field">
      <label>背景カラー</label>
      <div style="display:flex;align-items:center;gap:.75rem">
        <input type="color" id="bgColorPicker" value="#0d0d0d" style="width:44px;height:32px;padding:2px;border-radius:4px;cursor:pointer;background:none;border:1px solid var(--admin-border)">
        <input type="text" id="bgColorText" value="#0d0d0d" placeholder="#0d0d0d" style="max-width:120px">
        <button onclick="applyBgColor()" style="padding:.4rem .9rem;background:var(--accent);color:#0d0d0d;border:none;border-radius:4px;font-size:.72rem;cursor:pointer;font-family:'DM Sans',sans-serif">適用</button>
      </div>
    </div>
  </div>
</div>

<footer>
  <span>© 2025 Kanato — All rights reserved</span>
  <span>Made with care ✦</span>
</footer>
<div class="toast" id="toast"></div>

<script>
/* ======== DATA ======== */
let WORKS = [
  {"id":11,"title":"ダイヤの秘めた想い","sub":"Diamond's Secret Feelings","tags":["New","ウマ娘",""],"desc":"","note":"","url":"https://www.patreon.com/posts/daiyanomi-i-159734941?utm_medium=clipboard_copy&utm_source=copyLink&utm_campaign=postshare_creator&utm_content=join_link","thumb":"https://pbs.twimg.com/media/HJuxK0ZaAAAAsyA?format=jpg&name=medium","year":2025,"month":5,"previews":["https://pbs.twimg.com/media/HJuxK0da8AAVO9W?format=jpg&name=medium","https://pbs.twimg.com/media/HJuxK0gasAAmNgk?format=jpg&name=medium","https://pbs.twimg.com/media/HJuxK0eaUAAypgu?format=jpg&name=medium"]},
  {"id":12,"title":"オグリキャップ","sub":"· 2025","tags":["New","ウマ娘",""],"desc":"","note":"","url":"https://","thumb":"https://pbs.twimg.com/media/HJux5y7aEAAYANY?format=jpg&name=4096x4096","year":2025,"month":5,"previews":["https://pbs.twimg.com/media/HJux5y2bQAAKGo4?format=jpg&name=4096x4096","https://pbs.twimg.com/media/HJux5yxbkAAe3i4?format=jpg&name=4096x4096","https://pbs.twimg.com/media/HJux5y1awAA8TxL?format=jpg&name=4096x4096"]},
  {"id":13,"title":"メジロマックイーン","sub":"· 2025","tags":["New","ウマ娘",""],"desc":"","note":"","url":"https://","thumb":"https://pbs.twimg.com/media/HJuyRpUaUAAufcg?format=jpg&name=4096x4096","year":2025,"month":5,"previews":["https://pbs.twimg.com/media/HJuyRdyaoAE_kkU?format=jpg&name=4096x4096","https://pbs.twimg.com/media/HJuyVCpa0AEp01D?format=jpg&name=4096x4096",""]}
];
let nextId = 20;
let SETTINGS = {sliderMode:'both', bgColor:'#0d0d0d'};

/* ======== PAGE NAV ======== */
function showPage(p){
  document.querySelectorAll('.page').forEach(el=>el.classList.remove('active'));
  document.querySelectorAll('nav a').forEach(el=>el.classList.remove('active'));
  if(p==='home'){document.getElementById('homePage').classList.add('active');}
  else if(p==='series'){document.getElementById('seriesPage').classList.add('active');renderSeries();document.getElementById('navSeries').classList.add('active');}
}

/* ======== RENDER SITE ======== */
function renderSite(){applySettings();renderSlider();renderGallery();}

function applySettings(){
  const m=SETTINGS.sliderMode;
  const sec=document.getElementById('sliderSection');
  const fd=document.getElementById('featuredDivider');
  const gg=document.getElementById('galleryGrid');
  // slider label
  if(m==='both'){
    sec.style.display='';
    document.getElementById('sliderLabel').textContent='— Recent Works';
    fd.style.display='';gg.style.display='';
  } else if(m==='recent'){
    sec.style.display='';
    document.getElementById('sliderLabel').textContent='— Recent Works';
    fd.style.display='none';gg.style.display='none';
  } else if(m==='featured'){
    sec.style.display='none';
    fd.style.display='';gg.style.display='';
  } else {
    sec.style.display='none';fd.style.display='none';gg.style.display='none';
  }
  document.body.style.background=SETTINGS.bgColor;
  document.documentElement.style.setProperty('--bg',SETTINGS.bgColor);
  // sync radio
  document.querySelectorAll('input[name=sliderMode]').forEach(r=>{r.checked=(r.value===m);});
  document.getElementById('bgColorPicker').value=SETTINGS.bgColor;
  document.getElementById('bgColorText').value=SETTINGS.bgColor;
}

function applyBgColor(){
  const v=document.getElementById('bgColorText').value.trim();
  SETTINGS.bgColor=v;applySettings();showToast('背景色を変更しました ✓');
}
document.getElementById('bgColorPicker').addEventListener('input',function(){
  document.getElementById('bgColorText').value=this.value;
  SETTINGS.bgColor=this.value;applySettings();
});
document.querySelectorAll('input[name=sliderMode]').forEach(r=>{
  r.addEventListener('change',function(){SETTINGS.sliderMode=this.value;applySettings();});
});

function renderSlider(){
  const imgs=WORKS.map(w=>({src:w.thumb,label:w.title,id:w.id}));
  ['row1','row2'].forEach((rowId,ri)=>{
    const el=document.getElementById(rowId);el.innerHTML='';
    if(!imgs.length)return;
    const all=[...imgs,...imgs];
    all.forEach((_,i)=>{
      const item=imgs[(i+ri*2)%imgs.length];
      const c=document.createElement('div');c.className='slide-card';
      c.innerHTML=`<img src="${item.src}" alt="${item.label}" loading="lazy"><div class="slide-card-label">${item.label}</div>`;
      c.onclick=()=>openModal(item.id);el.appendChild(c);
    });
  });
}

function renderGallery(){
  const grid=document.getElementById('galleryGrid');grid.innerHTML='';
  WORKS.forEach(w=>{
    const d=document.createElement('div');d.className='gallery-item';
    const tagsHtml=(w.tags||[]).filter(t=>t).map(t=>`<span class="gallery-badge">${t}</span>`).join('');
    d.innerHTML=`<img src="${w.thumb}" alt="${w.title}" loading="lazy"><div class="gallery-info"><div class="gallery-title">${w.title}</div><div class="gallery-sub">${w.sub||''}</div><div class="gallery-tags">${tagsHtml}</div></div>`;
    d.onclick=()=>openModal(w.id);grid.appendChild(d);
  });
}

/* ======== SERIES PAGE ======== */
function renderSeries(){
  const cont=document.getElementById('seriesContent');cont.innerHTML='';
  // group by year then month
  const byYear={};
  WORKS.forEach(w=>{
    const y=w.year||2025,mo=w.month||1;
    if(!byYear[y])byYear[y]={};
    if(!byYear[y][mo])byYear[y][mo]=[];
    byYear[y][mo].push(w);
  });
  const months=['','1月','2月','3月','4月','5月','6月','7月','8月','9月','10月','11月','12月'];
  Object.keys(byYear).sort((a,b)=>b-a).forEach(y=>{
    const ySec=document.createElement('div');ySec.className='year-section';
    ySec.innerHTML=`<div class="year-heading">${y}</div>`;
    const moData=byYear[y];
    Object.keys(moData).sort((a,b)=>b-a).forEach(mo=>{
      const grp=document.createElement('div');grp.className='month-group';
      grp.innerHTML=`<div class="month-label">${months[mo]||mo+'月'}</div>`;
      const mg=document.createElement('div');mg.className='month-grid';
      moData[mo].forEach(w=>{
        const c=document.createElement('div');c.className='month-card';
        const tagsHtml=(w.tags||[]).filter(t=>t).map(t=>`<span class="month-card-badge">${t}</span>`).join('');
        c.innerHTML=`<img src="${w.thumb}" alt="${w.title}" loading="lazy"><div class="month-card-info"><div class="month-card-title">${w.title}</div><div class="month-card-tags">${tagsHtml}</div></div>`;
        c.onclick=()=>openModal(w.id);
        mg.appendChild(c);
      });
      grp.appendChild(mg);ySec.appendChild(grp);
    });
    cont.appendChild(ySec);
  });
}

/* ======== WORK MODAL ======== */
let currentWorkPreviews=[];
function openModal(id){
  const w=WORKS.find(x=>x.id===id);if(!w)return;
  document.getElementById('modalTitle').textContent=w.title;
  document.getElementById('modalDesc').textContent=w.desc||'';
  document.getElementById('modalNote').textContent=w.note||'';
  document.getElementById('modalLink').href=w.url||'#';
  const tagsEl=document.getElementById('modalTags');
  tagsEl.innerHTML=(w.tags||[]).filter(t=>t).map(t=>`<span class="gallery-badge">${t}</span>`).join('');
  const p=document.getElementById('modalPreviews');p.innerHTML='';
  const validPreviews=(w.previews||[]).filter(s=>s);
  currentWorkPreviews=validPreviews;
  validPreviews.forEach((src,i)=>{
    const t=document.createElement('div');t.className='preview-thumb';
    t.innerHTML=`<img src="${src}" alt="p${i}" loading="lazy"><div class="preview-num">${i+1} / ${validPreviews.length}</div>`;
    t.querySelector('img').onclick=()=>openLightbox(validPreviews,i);
    p.appendChild(t);
  });
  document.getElementById('modalOverlay').classList.add('open');
  document.body.style.overflow='hidden';
}
document.getElementById('modalClose').onclick=closeModal;
document.getElementById('modalOverlay').onclick=e=>{if(e.target===e.currentTarget)closeModal();};
function closeModal(){document.getElementById('modalOverlay').classList.remove('open');document.body.style.overflow='';}

/* ======== LIGHTBOX ======== */
let lbImages=[],lbIndex=0;
function openLightbox(imgs,idx){
  lbImages=imgs;lbIndex=idx;
  updateLightbox();
  document.getElementById('lightbox').classList.add('open');
}
function updateLightbox(){
  document.getElementById('lbImg').src=lbImages[lbIndex];
  document.getElementById('lbCounter').textContent=`${lbIndex+1} / ${lbImages.length}`;
  document.getElementById('lbPrev').style.opacity=lbIndex>0?'1':'0.3';
  document.getElementById('lbNext').style.opacity=lbIndex<lbImages.length-1?'1':'0.3';
}
document.getElementById('lbClose').onclick=()=>document.getElementById('lightbox').classList.remove('open');
document.getElementById('lbPrev').onclick=()=>{if(lbIndex>0){lbIndex--;updateLightbox();}};
document.getElementById('lbNext').onclick=()=>{if(lbIndex<lbImages.length-1){lbIndex++;updateLightbox();}};
document.getElementById('lightbox').onclick=e=>{if(e.target===e.currentTarget)e.currentTarget.classList.remove('open');};
document.addEventListener('keydown',e=>{
  if(document.getElementById('lightbox').classList.contains('open')){
    if(e.key==='ArrowLeft'&&lbIndex>0){lbIndex--;updateLightbox();}
    if(e.key==='ArrowRight'&&lbIndex<lbImages.length-1){lbIndex++;updateLightbox();}
    if(e.key==='Escape')document.getElementById('lightbox').classList.remove('open');
  } else if(e.key==='Escape')closeModal();
});

/* ======== PASSWORD ======== */
const ADMIN_PW='BENz196619';
let adminUnlocked=false;
document.getElementById('openAdmin').onclick=()=>{
  if(adminUnlocked){openAdminPanel();}else{document.getElementById('pwOverlay').classList.add('open');document.getElementById('pwInput').value='';document.getElementById('pwError').textContent='';}
};
document.getElementById('pwBtn').onclick=checkPw;
document.getElementById('pwInput').addEventListener('keydown',e=>{if(e.key==='Enter')checkPw();});
function checkPw(){
  const v=document.getElementById('pwInput').value;
  if(v===ADMIN_PW){adminUnlocked=true;document.getElementById('pwOverlay').classList.remove('open');openAdminPanel();}
  else{document.getElementById('pwError').textContent='パスワードが違います';document.getElementById('pwInput').value='';}
}

/* ======== ADMIN PANEL ======== */
function openAdminPanel(){
  document.getElementById('adminOverlay').classList.add('open');
  document.getElementById('adminPanel').classList.add('open');
  document.body.style.overflow='hidden';
  renderAdminList();
  // sync display tab
  document.querySelectorAll('input[name=sliderMode]').forEach(r=>{r.checked=(r.value===SETTINGS.sliderMode);});
  document.getElementById('bgColorPicker').value=SETTINGS.bgColor;
  document.getElementById('bgColorText').value=SETTINGS.bgColor;
}
function closeAdmin(){
  document.getElementById('adminOverlay').classList.remove('open');
  document.getElementById('adminPanel').classList.remove('open');
  document.body.style.overflow='';
}
document.getElementById('closeAdmin').onclick=closeAdmin;
document.getElementById('adminOverlay').onclick=closeAdmin;

// Admin tabs
document.querySelectorAll('.admin-tab').forEach(tab=>{
  tab.onclick=function(){
    document.querySelectorAll('.admin-tab').forEach(t=>t.classList.remove('active'));
    document.querySelectorAll('.admin-tab-content').forEach(t=>t.classList.remove('active'));
    this.classList.add('active');
    document.getElementById('tab'+this.dataset.tab.charAt(0).toUpperCase()+this.dataset.tab.slice(1)).classList.add('active');
  };
});

function renderAdminList(){
  const list=document.getElementById('workList');list.innerHTML='';
  WORKS.forEach(w=>{
    const card=document.createElement('div');card.className='work-card-admin';card.id=`adminCard_${w.id}`;
    card.innerHTML=buildAdminCard(w);list.appendChild(card);
  });
}

function buildAdminCard(w){
  const tags=w.tags||['','',''];
  const prevInputs=(w.previews||[]).map((p,i)=>`
    <div class="preview-item" data-prev-index="${i}">
      <span>${i+1}.</span>
      <img class="prev-thumb" src="${p}" onerror="this.style.opacity=0.2">
      <input type="text" value="${p.replace(/"/g,'&quot;')}" placeholder="画像URL" oninput="updatePreview(${w.id},${i},this.value)">
      <button class="btn-remove-preview" onclick="removePreview(${w.id},${i})">✕</button>
    </div>`).join('');
  const mo=w.month||1,yr=w.year||2025;
  return `
    <div class="work-card-header" onclick="toggleCard(${w.id})">
      <div class="work-card-header-left">
        <img src="${w.thumb}" onerror="this.style.opacity=0.2" alt="">
        <span class="work-card-title-sm">${w.title||'無題'}</span>
      </div>
      <div style="display:flex;gap:.5rem;align-items:center">
        <button class="btn-delete-work" onclick="event.stopPropagation();deleteWork(${w.id})">削除</button>
        <span class="work-card-toggle" id="toggle_${w.id}">▼</span>
      </div>
    </div>
    <div class="work-card-body" id="body_${w.id}">
      <div class="field-row" style="margin-top:.85rem">
        <div class="field"><label>タイトル</label><input type="text" value="${w.title.replace(/"/g,'&quot;')}" oninput="updateField(${w.id},'title',this.value)"></div>
        <div class="field"><label>サブテキスト</label><input type="text" value="${(w.sub||'').replace(/"/g,'&quot;')}" oninput="updateField(${w.id},'sub',this.value)"></div>
      </div>
      <div class="field">
        <label>タグ（最大3つ）</label>
        <div class="field-row3">
          <input type="text" value="${(tags[0]||'').replace(/"/g,'&quot;')}" placeholder="タグ1" oninput="updateTag(${w.id},0,this.value)">
          <input type="text" value="${(tags[1]||'').replace(/"/g,'&quot;')}" placeholder="タグ2" oninput="updateTag(${w.id},1,this.value)">
          <input type="text" value="${(tags[2]||'').replace(/"/g,'&quot;')}" placeholder="タグ3" oninput="updateTag(${w.id},2,this.value)">
        </div>
      </div>
      <div class="field"><label>説明文</label><textarea oninput="updateField(${w.id},'desc',this.value)">${w.desc||''}</textarea></div>
      <div class="field"><label>メモ（枚数など）</label><input type="text" value="${(w.note||'').replace(/"/g,'&quot;')}" oninput="updateField(${w.id},'note',this.value)"></div>
      <div class="field-row">
        <div class="field"><label>投稿年</label><input type="number" value="${yr}" min="2000" max="2099" oninput="updateField(${w.id},'year',parseInt(this.value)||2025)"></div>
        <div class="field"><label>投稿月</label>
          <select onchange="updateField(${w.id},'month',parseInt(this.value))">
            ${[1,2,3,4,5,6,7,8,9,10,11,12].map(m=>`<option value="${m}"${m===mo?' selected':''}>${m}月</option>`).join('')}
          </select>
        </div>
      </div>
      <div class="field"><label>誘導先URL</label><input type="text" value="${(w.url||'').replace(/"/g,'&quot;')}" placeholder="https://..." oninput="updateField(${w.id},'url',this.value)"></div>
      <div class="field"><label>サムネイル画像URL</label><input type="text" value="${(w.thumb||'').replace(/"/g,'&quot;')}" oninput="updateField(${w.id},'thumb',this.value);refreshThumb(${w.id})"></div>
      <div class="field"><label>続き画像（タップで拡大・← →で移動）</label>
        <div class="preview-list" id="prevList_${w.id}">${prevInputs}</div>
        <button class="btn-add-preview" onclick="addPreview(${w.id})">＋ 画像を追加</button>
      </div>
    </div>`;
}

function toggleCard(id){
  const body=document.getElementById(`body_${id}`);
  const tog=document.getElementById(`toggle_${id}`);
  const open=body.classList.toggle('open');
  tog.textContent=open?'▲':'▼';
}
function updateField(id,field,value){
  const w=WORKS.find(x=>x.id===id);if(!w)return;
  w[field]=value;
  if(field==='title'){const el=document.querySelector(`#adminCard_${id} .work-card-title-sm`);if(el)el.textContent=value||'無題';}
  renderSite();if(document.getElementById('seriesPage').classList.contains('active'))renderSeries();
}
function updateTag(id,idx,value){
  const w=WORKS.find(x=>x.id===id);if(!w)return;
  if(!w.tags)w.tags=['','',''];
  w.tags[idx]=value;renderSite();if(document.getElementById('seriesPage').classList.contains('active'))renderSeries();
}
function refreshThumb(id){
  const w=WORKS.find(x=>x.id===id);
  const img=document.querySelector(`#adminCard_${id} .work-card-header-left img`);
  if(img&&w)img.src=w.thumb;
}
function updatePreview(id,index,value){
  const w=WORKS.find(x=>x.id===id);if(!w)return;
  w.previews[index]=value;
  const pItem=document.querySelector(`#prevList_${id} [data-prev-index="${index}"] .prev-thumb`);
  if(pItem)pItem.src=value;
}
function addPreview(id){
  const w=WORKS.find(x=>x.id===id);if(!w)return;
  w.previews.push('');
  const card=document.getElementById(`adminCard_${id}`);
  const wasOpen=document.getElementById(`body_${id}`).classList.contains('open');
  card.innerHTML=buildAdminCard(w);
  if(wasOpen){document.getElementById(`body_${id}`).classList.add('open');document.getElementById(`toggle_${id}`).textContent='▲';}
}
function removePreview(id,index){
  const w=WORKS.find(x=>x.id===id);if(!w)return;
  w.previews.splice(index,1);
  const card=document.getElementById(`adminCard_${id}`);
  card.innerHTML=buildAdminCard(w);
  document.getElementById(`body_${id}`).classList.add('open');
  document.getElementById(`toggle_${id}`).textContent='▲';
}
function deleteWork(id){
  if(!confirm('この作品を削除しますか？'))return;
  WORKS=WORKS.filter(w=>w.id!==id);renderAdminList();renderSite();
  if(document.getElementById('seriesPage').classList.contains('active'))renderSeries();
}
document.getElementById('btnAddWork').onclick=()=>{
  const w={id:nextId++,title:'新しい作品',sub:'· 2025',tags:['','',''],desc:'',note:'',url:'https://',thumb:'',year:2025,month:new Date().getMonth()+1,previews:['','','']};
  WORKS.push(w);renderAdminList();renderSite();
  setTimeout(()=>{const c=document.getElementById(`adminCard_${w.id}`);if(c){c.scrollIntoView({behavior:'smooth',block:'center'});toggleCard(w.id);}},100);
};

/* ======== DOWNLOAD ======== */
document.getElementById('btnDownload').onclick=()=>{
  const worksJson=JSON.stringify(WORKS,null,2);
  const settingsJson=JSON.stringify(SETTINGS);
  let html=document.documentElement.outerHTML;
  html=html.replace(/let WORKS = \[[\s\S]*?\];/,`let WORKS = ${worksJson};`);
  html=html.replace(/let SETTINGS = \{[\s\S]*?\};/,`let SETTINGS = ${settingsJson};`);
  const blob=new Blob([html],{type:'text/html'});
  const a=document.createElement('a');a.href=URL.createObjectURL(blob);a.download='index.html';a.click();
  showToast('HTMLをダウンロードしました ✓');
};

function showToast(msg){
  const t=document.getElementById('toast');t.textContent=msg;t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2800);
}

/* ======== INIT ======== */
renderSite();
</script>
</body>
</html>
