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
nav a{color:var(--muted);text-decoration:none;font-size:.75rem;letter-spacing:.12em;text-transform:uppercase;transition:color .3s}
nav a:hover{color:var(--text)}
.admin-btn{background:none;border:1px solid rgba(201,169,110,.4);color:var(--accent);padding:.4rem 1rem;border-radius:4px;font-size:.72rem;letter-spacing:.1em;text-transform:uppercase;cursor:pointer;transition:all .3s;font-family:'DM Sans',sans-serif}
.admin-btn:hover{background:rgba(201,169,110,.1)}

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
.gallery-badge{display:inline-block;margin-top:.6rem;padding:.2rem .6rem;background:rgba(201,169,110,.12);border:1px solid rgba(201,169,110,.3);color:var(--accent);font-size:.65rem;letter-spacing:.1em;text-transform:uppercase;border-radius:3px}

/* WORK MODAL */
.modal-overlay{display:none;position:fixed;inset:0;z-index:200;background:rgba(5,5,5,.92);backdrop-filter:blur(8px);align-items:center;justify-content:center;padding:2rem}
.modal-overlay.open{display:flex}
.modal{background:var(--surface);border:1px solid rgba(240,236,228,.12);border-radius:12px;max-width:860px;width:100%;max-height:90vh;overflow-y:auto;position:relative;animation:modal-in .3s cubic-bezier(.16,1,.3,1)}
@keyframes modal-in{from{opacity:0;transform:scale(.95) translateY(20px)}to{opacity:1;transform:scale(1) translateY(0)}}
.modal-close{position:absolute;top:1.2rem;right:1.2rem;background:none;border:1px solid var(--border);color:var(--muted);width:32px;height:32px;border-radius:50%;font-size:1rem;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s;z-index:1}
.modal-close:hover{color:var(--text);border-color:rgba(240,236,228,.3)}
.modal-header{padding:2rem 2rem 1.2rem;border-bottom:1px solid var(--border)}
.modal-title{font-family:'Cormorant Garamond',serif;font-size:1.8rem;font-weight:300;margin-bottom:.3rem}
.modal-desc{font-size:.82rem;color:var(--muted);line-height:1.7}
.modal-previews{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;padding:1.5rem 2rem}
.preview-thumb{border-radius:6px;overflow:hidden;border:1px solid var(--border);cursor:pointer}
.preview-thumb:hover{border-color:rgba(201,169,110,.4)}
.preview-thumb img{width:100%;aspect-ratio:4/3;object-fit:cover;display:block;filter:brightness(.85);transition:filter .3s}
.preview-thumb:hover img{filter:brightness(1)}
.preview-num{padding:.5rem .75rem;font-size:.68rem;color:var(--muted)}
.modal-footer{padding:1.5rem 2rem 2rem;border-top:1px solid var(--border);display:flex;align-items:center;justify-content:space-between}
.modal-footer-note{font-size:.78rem;color:var(--muted)}
.btn-view-all{display:inline-flex;align-items:center;gap:.6rem;padding:.7rem 1.6rem;background:var(--accent);color:#0d0d0d;font-family:'DM Sans',sans-serif;font-size:.78rem;letter-spacing:.08em;text-transform:uppercase;text-decoration:none;border-radius:4px;border:none;cursor:pointer;transition:background .3s,transform .2s}
.btn-view-all:hover{background:#d4b57c;transform:translateX(2px)}

/* ADMIN PANEL */
.admin-overlay{display:none;position:fixed;inset:0;z-index:500;background:rgba(0,0,0,.6);backdrop-filter:blur(6px)}
.admin-overlay.open{display:block}
.admin-panel{position:fixed;top:0;right:0;bottom:0;width:min(600px,100vw);z-index:501;background:var(--admin-bg);border-left:1px solid var(--admin-border);overflow-y:auto;transform:translateX(100%);transition:transform .35s cubic-bezier(.16,1,.3,1)}
.admin-panel.open{transform:translateX(0)}
.admin-header{padding:1.5rem 2rem;border-bottom:1px solid var(--admin-border);display:flex;align-items:center;justify-content:space-between;position:sticky;top:0;background:var(--admin-bg);z-index:1}
.admin-header h2{font-family:'Cormorant Garamond',serif;font-size:1.4rem;font-weight:300;letter-spacing:.05em}
.admin-header-actions{display:flex;gap:.75rem;align-items:center}
.btn-dl{display:inline-flex;align-items:center;gap:.5rem;padding:.5rem 1.2rem;background:var(--accent);color:#0d0d0d;border:none;border-radius:4px;font-size:.75rem;font-family:'DM Sans',sans-serif;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;transition:background .3s}
.btn-dl:hover{background:#d4b57c}
.btn-close-admin{background:none;border:1px solid var(--admin-border);color:var(--muted);width:32px;height:32px;border-radius:50%;font-size:1rem;cursor:pointer;display:flex;align-items:center;justify-content:center;transition:all .2s}
.btn-close-admin:hover{color:var(--text)}

.admin-body{padding:1.5rem 2rem 3rem}
.admin-section-title{font-size:.68rem;letter-spacing:.2em;text-transform:uppercase;color:var(--muted);margin:1.5rem 0 .75rem;padding-bottom:.5rem;border-bottom:1px solid var(--admin-border)}

/* work cards in admin */
.work-card-admin{background:var(--admin-surface);border:1px solid var(--admin-border);border-radius:8px;margin-bottom:1rem;overflow:hidden}
.work-card-header{display:flex;align-items:center;justify-content:space-between;padding:.85rem 1rem;cursor:pointer;transition:background .2s}
.work-card-header:hover{background:rgba(255,255,255,.03)}
.work-card-header-left{display:flex;align-items:center;gap:.75rem}
.work-card-header-left img{width:44px;height:34px;object-fit:cover;border-radius:4px;border:1px solid var(--admin-border)}
.work-card-title-sm{font-size:.85rem;letter-spacing:.03em}
.work-card-toggle{font-size:.65rem;color:var(--muted);transition:transform .3s}
.work-card-body{display:none;padding:0 1rem 1rem;border-top:1px solid var(--admin-border)}
.work-card-body.open{display:block}

/* form elements */
.field{margin-top:.9rem}
.field label{display:block;font-size:.68rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:.35rem}
.field input,.field textarea{width:100%;background:rgba(255,255,255,.04);border:1px solid var(--admin-border);color:var(--text);font-family:'DM Sans',sans-serif;font-size:.82rem;padding:.55rem .75rem;border-radius:4px;outline:none;transition:border-color .2s}
.field input:focus,.field textarea:focus{border-color:rgba(201,169,110,.5)}
.field textarea{resize:vertical;min-height:60px;line-height:1.5}
.field-row{display:grid;grid-template-columns:1fr 1fr;gap:.75rem}

/* preview list inside admin */
.preview-list{display:flex;flex-direction:column;gap:.5rem;margin-top:.35rem}
.preview-item{display:flex;align-items:center;gap:.6rem}
.preview-item span{font-size:.7rem;color:var(--muted);white-space:nowrap}
.preview-item input{flex:1}
.preview-item img.prev-thumb{width:36px;height:28px;object-fit:cover;border-radius:3px;border:1px solid var(--admin-border);flex-shrink:0}

.btn-add-preview{background:none;border:1px dashed var(--admin-border);color:var(--muted);width:100%;padding:.45rem;border-radius:4px;font-size:.72rem;cursor:pointer;margin-top:.5rem;transition:all .2s;font-family:'DM Sans',sans-serif}
.btn-add-preview:hover{border-color:rgba(201,169,110,.4);color:var(--accent)}
.btn-remove-preview{background:none;border:none;color:rgba(255,100,100,.5);font-size:.9rem;cursor:pointer;padding:.1rem .3rem;transition:color .2s}
.btn-remove-preview:hover{color:rgba(255,100,100,.9)}

/* add/remove work */
.btn-add-work{width:100%;background:none;border:1px dashed rgba(201,169,110,.3);color:var(--accent);padding:.7rem;border-radius:6px;font-size:.75rem;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;margin-top:.5rem;transition:all .2s;font-family:'DM Sans',sans-serif}
.btn-add-work:hover{background:rgba(201,169,110,.06);border-color:rgba(201,169,110,.5)}
.btn-delete-work{background:none;border:1px solid rgba(255,80,80,.25);color:rgba(255,100,100,.6);padding:.35rem .8rem;border-radius:4px;font-size:.68rem;letter-spacing:.08em;text-transform:uppercase;cursor:pointer;transition:all .2s;font-family:'DM Sans',sans-serif}
.btn-delete-work:hover{background:rgba(255,80,80,.1);color:rgba(255,100,100,.9)}

.toast{position:fixed;bottom:2rem;left:50%;transform:translateX(-50%) translateY(80px);background:var(--accent);color:#0d0d0d;padding:.6rem 1.4rem;border-radius:4px;font-size:.78rem;letter-spacing:.06em;z-index:999;opacity:0;transition:all .4s}
.toast.show{opacity:1;transform:translateX(-50%) translateY(0)}

footer{border-top:1px solid var(--border);padding:2rem 3rem;display:flex;justify-content:space-between;align-items:center;font-size:.72rem;color:var(--muted)}
::-webkit-scrollbar{width:5px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--surface2);border-radius:10px}
</style>
</head>
<body>

<header>
  <a href="#" class="logo">GALLERY</a>
  <nav>
    <a href="#">Works</a>
    <a href="#">Series</a>
    <a href="#">About</a>
    <button class="admin-btn" id="openAdmin">⚙ 管理</button>
  </nav>
</header>

<div class="slider-section">
  <p class="slider-label">— Recent Works</p>
  <div class="rows-wrapper">
    <div class="slider-row" id="row1"></div>
    <div class="slider-row row2" id="row2"></div>
  </div>
</div>

<div class="section-divider"><span>Featured Works</span></div>
<div class="gallery-grid" id="galleryGrid"></div>

<!-- WORK MODAL -->
<div class="modal-overlay" id="modalOverlay">
  <div class="modal">
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
        <svg width="14" height="14" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
      </a>
    </div>
  </div>
</div>

<!-- ADMIN -->
<div class="admin-overlay" id="adminOverlay"></div>
<div class="admin-panel" id="adminPanel">
  <div class="admin-header">
    <h2>管理パネル</h2>
    <div class="admin-header-actions">
      <button class="btn-dl" id="btnDownload">⬇ HTMLをダウンロード</button>
      <button class="btn-close-admin" id="closeAdmin">✕</button>
    </div>
  </div>
  <div class="admin-body">
    <p class="admin-section-title">作品を編集</p>
    <div id="workList"></div>
    <button class="btn-add-work" id="btnAddWork">＋ 作品を追加</button>
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
  {id:1,title:"Twilight No.1",sub:"Digital Illustration · 2024",tag:"Series A",desc:"夕暮れの情景をテーマにしたシリーズ作品。光と影のコントラストを丁寧に描きました。",note:"シリーズ全8枚",url:"https://example.com/series/twilight",thumb:"https://images.unsplash.com/photo-1579546929518-9e396f3cc809?w=600&q=80",previews:["https://images.unsplash.com/photo-1502134249126-9f3755a50d78?w=400&q=80","https://images.unsplash.com/photo-1513151233558-d860c5398176?w=400&q=80","https://images.unsplash.com/photo-1501862700950-18382cd41497?w=400&q=80"]},
  {id:2,title:"Blue Archive Fan Art",sub:"Character Illustration · 2024",tag:"Fan Art",desc:"ブルーアーカイブのキャラクターをオリジナルの構図で描いた作品集。",note:"シリーズ全5枚",url:"https://example.com/series/blue-archive",thumb:"https://images.unsplash.com/photo-1518173946687-a4c8892bbd9f?w=600&q=80",previews:["https://images.unsplash.com/photo-1505506874110-6a7a69069a08?w=400&q=80","https://images.unsplash.com/photo-1528360983277-13d401cdc186?w=400&q=80","https://images.unsplash.com/photo-1470813740244-df37b8c1edcb?w=400&q=80"]},
  {id:3,title:"Monochrome Study",sub:"Concept Art · 2024",tag:"Series B",desc:"モノクロの世界で表現した都市と自然の対比をテーマにした実験的シリーズ。",note:"シリーズ全6枚",url:"https://example.com/series/monochrome",thumb:"https://images.unsplash.com/photo-1524055988636-436cfa46e59e?w=600&q=80",previews:["https://images.unsplash.com/photo-1536184635451-90a0cc3f7e5c?w=400&q=80","https://images.unsplash.com/photo-1555680202-c86f0e12f086?w=400&q=80","https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=400&q=80"]}
];
let nextId = 10;

/* ======== RENDER SITE ======== */
function renderSite(){
  renderSlider();
  renderGallery();
}

function renderSlider(){
  const imgs = WORKS.map(w=>({src:w.thumb,label:w.title,id:w.id}));
  ['row1','row2'].forEach((rowId,ri)=>{
    const el=document.getElementById(rowId);
    el.innerHTML='';
    const all=[...imgs,...imgs];
    all.forEach((_,i)=>{
      const item=imgs[(i+ri*3)%imgs.length];
      const c=document.createElement('div');
      c.className='slide-card';
      c.innerHTML=`<img src="${item.src}" alt="${item.label}" loading="lazy"><div class="slide-card-label">${item.label}</div>`;
      c.onclick=()=>openModal(item.id);
      el.appendChild(c);
    });
  });
}

function renderGallery(){
  const grid=document.getElementById('galleryGrid');
  grid.innerHTML='';
  WORKS.forEach(w=>{
    const d=document.createElement('div');
    d.className='gallery-item';
    d.innerHTML=`<img src="${w.thumb}" alt="${w.title}" loading="lazy"><div class="gallery-info"><div class="gallery-title">${w.title}</div><div class="gallery-sub">${w.sub}</div><span class="gallery-badge">${w.tag}</span></div>`;
    d.onclick=()=>openModal(w.id);
    grid.appendChild(d);
  });
}

/* ======== WORK MODAL ======== */
function openModal(id){
  const w=WORKS.find(x=>x.id===id);
  if(!w)return;
  document.getElementById('modalTitle').textContent=w.title;
  document.getElementById('modalDesc').textContent=w.desc;
  document.getElementById('modalNote').textContent=w.note;
  document.getElementById('modalLink').href=w.url;
  const p=document.getElementById('modalPreviews');
  p.innerHTML='';
  w.previews.forEach((src,i)=>{
    const t=document.createElement('div');
    t.className='preview-thumb';
    t.innerHTML=`<img src="${src}" alt="p${i}" loading="lazy"><div class="preview-num">Page ${i+1} / ${w.previews.length}</div>`;
    p.appendChild(t);
  });
  document.getElementById('modalOverlay').classList.add('open');
  document.body.style.overflow='hidden';
}
document.getElementById('modalClose').onclick=()=>{document.getElementById('modalOverlay').classList.remove('open');document.body.style.overflow='';};
document.getElementById('modalOverlay').onclick=e=>{if(e.target===e.currentTarget){document.getElementById('modalOverlay').classList.remove('open');document.body.style.overflow='';}};

/* ======== ADMIN PANEL ======== */
function openAdmin(){
  document.getElementById('adminOverlay').classList.add('open');
  document.getElementById('adminPanel').classList.add('open');
  document.body.style.overflow='hidden';
  renderAdminList();
}
function closeAdmin(){
  document.getElementById('adminOverlay').classList.remove('open');
  document.getElementById('adminPanel').classList.remove('open');
  document.body.style.overflow='';
}
document.getElementById('openAdmin').onclick=openAdmin;
document.getElementById('closeAdmin').onclick=closeAdmin;
document.getElementById('adminOverlay').onclick=closeAdmin;

function renderAdminList(){
  const list=document.getElementById('workList');
  list.innerHTML='';
  WORKS.forEach(w=>{
    const card=document.createElement('div');
    card.className='work-card-admin';
    card.id=`adminCard_${w.id}`;
    card.innerHTML=buildAdminCard(w);
    list.appendChild(card);
    bindAdminCard(w.id);
  });
}

function buildAdminCard(w){
  const prevInputs=w.previews.map((p,i)=>`
    <div class="preview-item" data-prev-index="${i}">
      <span>${i+1}.</span>
      <img class="prev-thumb" src="${p}" onerror="this.style.opacity=0.2">
      <input type="text" value="${p}" placeholder="画像URL" oninput="updatePreview(${w.id},${i},this.value)">
      <button class="btn-remove-preview" onclick="removePreview(${w.id},${i})">✕</button>
    </div>`).join('');
  return `
    <div class="work-card-header" onclick="toggleCard(${w.id})">
      <div class="work-card-header-left">
        <img src="${w.thumb}" onerror="this.style.opacity=0.2" alt="">
        <span class="work-card-title-sm">${w.title||'無題'}</span>
      </div>
      <div style="display:flex;gap:.6rem;align-items:center">
        <button class="btn-delete-work" onclick="event.stopPropagation();deleteWork(${w.id})">削除</button>
        <span class="work-card-toggle" id="toggle_${w.id}">▼</span>
      </div>
    </div>
    <div class="work-card-body" id="body_${w.id}">
      <div class="field-row" style="margin-top:.9rem">
        <div class="field"><label>タイトル</label><input type="text" value="${w.title}" oninput="updateField(${w.id},'title',this.value)"></div>
        <div class="field"><label>バッジ（タグ）</label><input type="text" value="${w.tag}" oninput="updateField(${w.id},'tag',this.value)"></div>
      </div>
      <div class="field"><label>サブテキスト（種類・年）</label><input type="text" value="${w.sub}" oninput="updateField(${w.id},'sub',this.value)"></div>
      <div class="field"><label>説明文</label><textarea oninput="updateField(${w.id},'desc',this.value)">${w.desc}</textarea></div>
      <div class="field"><label>メモ（枚数など）</label><input type="text" value="${w.note}" oninput="updateField(${w.id},'note',this.value)"></div>
      <div class="field"><label>誘導先URL</label><input type="text" value="${w.url}" placeholder="https://..." oninput="updateField(${w.id},'url',this.value)"></div>
      <div class="field"><label>サムネイル画像URL</label><input type="text" value="${w.thumb}" oninput="updateField(${w.id},'thumb',this.value);refreshThumb(${w.id})"></div>
      <div class="field"><label>続き画像（プレビュー）</label>
        <div class="preview-list" id="prevList_${w.id}">${prevInputs}</div>
        <button class="btn-add-preview" onclick="addPreview(${w.id})">＋ 画像を追加</button>
      </div>
    </div>`;
}

function bindAdminCard(id){}

function toggleCard(id){
  const body=document.getElementById(`body_${id}`);
  const tog=document.getElementById(`toggle_${id}`);
  const open=body.classList.toggle('open');
  tog.textContent=open?'▲':'▼';
}

function updateField(id,field,value){
  const w=WORKS.find(x=>x.id===id);
  if(!w)return;
  w[field]=value;
  if(field==='title'){
    const el=document.querySelector(`#adminCard_${id} .work-card-title-sm`);
    if(el)el.textContent=value||'無題';
  }
  renderSite();
}

function refreshThumb(id){
  const w=WORKS.find(x=>x.id===id);
  const img=document.querySelector(`#adminCard_${id} .work-card-header-left img`);
  if(img&&w)img.src=w.thumb;
}

function updatePreview(id,index,value){
  const w=WORKS.find(x=>x.id===id);
  if(!w)return;
  w.previews[index]=value;
  const pItem=document.querySelector(`#prevList_${id} [data-prev-index="${index}"] .prev-thumb`);
  if(pItem)pItem.src=value;
  renderSite();
}

function addPreview(id){
  const w=WORKS.find(x=>x.id===id);
  if(!w)return;
  w.previews.push('');
  const card=document.getElementById(`adminCard_${id}`);
  const wasOpen=document.getElementById(`body_${id}`).classList.contains('open');
  card.innerHTML=buildAdminCard(w);
  if(wasOpen){document.getElementById(`body_${id}`).classList.add('open');document.getElementById(`toggle_${id}`).textContent='▲';}
  renderSite();
}

function removePreview(id,index){
  const w=WORKS.find(x=>x.id===id);
  if(!w)return;
  w.previews.splice(index,1);
  const card=document.getElementById(`adminCard_${id}`);
  card.innerHTML=buildAdminCard(w);
  document.getElementById(`body_${id}`).classList.add('open');
  document.getElementById(`toggle_${id}`).textContent='▲';
  renderSite();
}

function deleteWork(id){
  if(!confirm('この作品を削除しますか？'))return;
  WORKS=WORKS.filter(w=>w.id!==id);
  renderAdminList();
  renderSite();
}

document.getElementById('btnAddWork').onclick=()=>{
  const w={id:nextId++,title:'新しい作品',sub:'· 2025',tag:'New',desc:'',note:'',url:'https://',thumb:'',previews:['','','']};
  WORKS.push(w);
  renderAdminList();
  renderSite();
  // 追加したカードを開く
  setTimeout(()=>{
    const card=document.getElementById(`adminCard_${w.id}`);
    if(card){card.scrollIntoView({behavior:'smooth',block:'center'});toggleCard(w.id);}
  },100);
};

/* ======== DOWNLOAD ======== */
document.getElementById('btnDownload').onclick=()=>{
  const worksJson=JSON.stringify(WORKS,null,2);
  const html=document.documentElement.outerHTML.replace(
    /let WORKS = \[[\s\S]*?\];/,
    `let WORKS = ${worksJson};`
  );
  const blob=new Blob([html],{type:'text/html'});
  const a=document.createElement('a');
  a.href=URL.createObjectURL(blob);
  a.download='index.html';
  a.click();
  showToast('HTMLをダウンロードしました ✓');
};

function showToast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg;
  t.classList.add('show');
  setTimeout(()=>t.classList.remove('show'),2800);
}

/* ======== INIT ======== */
renderSite();
</script>
</body>
</html>
