<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>读书笔记 · Reading Notes</title>
<link rel="icon" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24'%3E%3Cpath fill='%23e8572a' d='M12 0c1.3 7 4.4 10.1 12 12-7.6 1.9-10.7 5-12 12-1.3-7-4.4-10.1-12-12C7.6 10.1 10.7 7 12 0z'/%3E%3C/svg%3E">
<script src="https://cdn.tailwindcss.com"></script>
<script>
tailwind.config = {
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        cream:  '#f5f0e1',
        charcoal: '#3d3d3d',
        burnt:  '#e8572a',
        teal2:  '#2a6e5e',
        gold:   '#c4a35a',
        night:  '#2d2d2d',
        ncard:  '#383838',
        ntext:  '#e8e3d3',
        nborder:'#555555'
      },
      boxShadow: {
        mcm: '4px 4px 0 0 var(--sh)',
        'mcm-sm': '2px 2px 0 0 var(--sh)',
        'mcm-lg': '6px 6px 0 0 var(--sh)'
      }
    }
  }
}
</script>
<style>
  :root { --sh: #3d3d3d; }
  .dark { --sh: #555555; }

  html, body { height: 100%; }
  body {
    font-family: ui-sans-serif, system-ui, "Helvetica Neue", Arial, "PingFang SC", "Microsoft YaHei", "Noto Sans SC", sans-serif;
    background: #f5f0e1;
    color: #3d3d3d;
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
  }
  .dark body { background: #2d2d2d; color: #e8e3d3; }

  ::selection { background: #e8572a; color: #f5f0e1; }

  /* ---------- 按钮：复古机械按键 ---------- */
  .btn {
    display: inline-flex; align-items: center; justify-content: center; gap: 6px;
    font-weight: 600; letter-spacing: 0.08em; text-transform: uppercase;
    border-radius: 0.5rem; border: 2px solid #3d3d3d;
    box-shadow: 3px 3px 0 0 var(--sh);
    transition: transform 200ms ease, box-shadow 200ms ease, background-color 200ms ease, color 200ms ease, border-color 200ms ease;
    cursor: pointer; user-select: none; white-space: nowrap;
  }
  .btn:active { transform: translateY(2px); box-shadow: none !important; }
  .btn:focus-visible { outline: 2px dashed #e8572a; outline-offset: 2px; }
  .btn-primary { background: #e8572a; color: #f5f0e1; }
  .btn-primary:hover { background: #d14a20; }
  .btn-secondary { background: transparent; color: #3d3d3d; }
  .btn-secondary:hover { background: rgba(61,61,61,0.08); }
  .dark .btn-secondary { color: #e8e3d3; border-color: #555555; }
  .dark .btn-secondary:hover { background: rgba(232,227,211,0.08); }
  .btn-danger { background: transparent; color: #e8572a; border-color: #e8572a; box-shadow: 3px 3px 0 0 rgba(232,87,42,0.45); }
  .btn-danger:hover { background: rgba(232,87,42,0.1); }
  .dark .btn-primary { border-color: #555555; }
  .btn-sm { font-size: 0.7rem; padding: 4px 10px; }
  .btn-md { font-size: 0.8rem; padding: 8px 16px; }

  /* ---------- 卡片 ---------- */
  .card {
    border-radius: 0.75rem; border: 2px solid #3d3d3d;
    background: #f5f0e1; padding: 20px;
    box-shadow: 4px 4px 0 0 var(--sh);
    transition: transform 200ms ease, box-shadow 200ms ease, background-color 200ms ease;
    cursor: pointer;
  }
  .card:hover { transform: translateY(-2px); box-shadow: 8px 8px 0 0 var(--sh); }
  .card:focus-visible { outline: 2px dashed #e8572a; outline-offset: 2px; }
  .dark .card { background: #383838; border-color: #555555; }

  /* ---------- 输入框 ---------- */
  .field {
    border-radius: 0.5rem; border: 2px solid rgba(61,61,61,0.35);
    background: #ffffff; color: #3d3d3d;
    padding: 8px 12px; width: 100%;
    transition: border-color 200ms ease, background-color 200ms ease;
  }
  .field:focus { border-color: #e8572a; outline: none; }
  .field::placeholder { color: rgba(61,61,61,0.4); }
  .dark .field { background: #383838; color: #e8e3d3; border-color: rgba(85,85,85,0.8); }
  .dark .field::placeholder { color: rgba(232,227,211,0.35); }

  /* ---------- 标签 chip：星芒反光 ---------- */
  .chip {
    display: inline-flex; align-items: center; gap: 4px;
    border-radius: 999px; border: 2px solid #2a6e5e;
    padding: 2px 10px; font-size: 0.72rem; font-weight: 600;
    color: #2a6e5e; background: transparent; cursor: pointer;
    transition: background-color 200ms ease, color 200ms ease, border-color 200ms ease;
  }
  .chip:hover { background: rgba(42,110,94,0.12); }
  .chip:focus-visible { outline: 2px dashed #e8572a; outline-offset: 2px; }
  .chip .spark { color: #c4a35a; transition: transform 200ms ease, color 200ms ease; }
  .chip:hover .spark { transform: rotate(90deg) scale(1.2); color: #9a7c33; }
  .chip.active { background: #e8572a; border-color: #e8572a; color: #f5f0e1; }
  .chip.active .spark { color: #f5f0e1; }
  .dark .chip { color: #7fbfae; border-color: #2a6e5e; }
  .dark .chip:hover { background: rgba(42,110,94,0.25); }
  .chip-static { cursor: default; }

  /* ---------- 分类条目 ---------- */
  .cat-item {
    display: flex; align-items: center; gap: 8px;
    padding: 8px 10px; border-radius: 0.5rem; cursor: pointer;
    transition: background-color 150ms ease, color 150ms ease;
    position: relative;
  }
  .cat-item:hover { background: rgba(61,61,61,0.07); }
  .dark .cat-item:hover { background: rgba(232,227,211,0.07); }
  .cat-item:focus-visible { outline: 2px dashed #e8572a; outline-offset: 2px; }
  .cat-item.active { background: #e8572a; color: #f5f0e1; }
  .cat-item.active .cat-name { color: #f5f0e1; }
  .cat-item.active .chev, .cat-item.active .more { color: #f5f0e1; }
  .cat-item.active:hover { background: #d14a20; }
  .more-btn { opacity: 0; transition: opacity 150ms ease; }
  .cat-item:hover .more-btn, .cat-item:focus-within .more-btn { opacity: 1; }

  /* ---------- 几何分隔线 ---------- */
  .geo-divider { display: flex; align-items: center; gap: 8px; }
  .geo-divider .blk { height: 8px; display: inline-block; }

  /* ---------- 有机曲线容器（空状态） ---------- */
  .organic {
    border-radius: 58% 42% 55% 45% / 48% 55% 45% 52%;
  }

  /* ---------- 淡入淡出 ---------- */
  @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }
  .fade-in { animation: fadeIn 200ms ease both; }

  /* ---------- 抽屉（移动端） ---------- */
  #scrim { transition: opacity 200ms ease; }
  @media (max-width: 1023px) {
    #sidebar, #tagbar { transition: transform 200ms ease; }
    #sidebar {
      position: fixed; left: 0; top: 0; bottom: 0; z-index: 40;
      transform: translateX(-105%);
      box-shadow: 6px 0 0 0 var(--sh);
    }
    #tagbar {
      position: fixed; right: 0; top: 0; bottom: 0; z-index: 40;
      transform: translateX(105%);
      box-shadow: -6px 0 0 0 var(--sh);
    }
    #sidebar.open, #tagbar.open { transform: none; }
  }

  /* ---------- 面包屑 ---------- */
  .crumb-sep { color: #c4a35a; font-weight: 700; }

  /* ---------- 滚动条 ---------- */
  ::-webkit-scrollbar { width: 10px; height: 10px; }
  ::-webkit-scrollbar-thumb { background: rgba(61,61,61,0.3); border-radius: 8px; border: 2px solid transparent; background-clip: content-box; }
  .dark ::-webkit-scrollbar-thumb { background: rgba(232,227,211,0.25); background-clip: content-box; }
  ::-webkit-scrollbar-track { background: transparent; }

  /* ---------- 无障碍：减少动效 ---------- */
  @media (prefers-reduced-motion: reduce) {
    *, *::before, *::after {
      transition-duration: 0.01ms !important;
      animation-duration: 0.01ms !important;
      animation-iteration-count: 1 !important;
    }
    .card:hover, .btn:active { transform: none !important; }
    .chip:hover .spark { transform: none !important; }
  }
</style>
</head>
<body>

<div id="app" class="flex h-full overflow-hidden">

  <!-- ═══════════ 左侧：分类栏 ═══════════ -->
  <aside id="sidebar" class="w-[248px] shrink-0 h-full overflow-y-auto border-r-2 border-charcoal dark:border-nborder bg-cream dark:bg-night flex flex-col">
    <div class="p-5 pb-3">
      <div class="flex items-center justify-between">
        <h1 class="text-base font-bold tracking-widest uppercase flex items-center gap-2 text-charcoal dark:text-ntext">
          <svg class="w-5 h-5 text-burnt" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M12 0c1.3 7 4.4 10.1 12 12-7.6 1.9-10.7 5-12 12-1.3-7-4.4-10.1-12-12C7.6 10.1 10.7 7 12 0z"/></svg>
          读书笔记
        </h1>
        <div class="flex items-center gap-1">
          <button class="btn btn-secondary btn-sm !shadow-none !border-transparent" data-action="toggle-dark" aria-label="切换夜间模式" title="夜间模式">
            <span id="darkIcon">☀</span>
          </button>
          <button class="btn btn-secondary btn-sm !shadow-none !border-transparent" data-action="open-settings" aria-label="设置" title="设置">
            <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><circle cx="12" cy="12" r="3"/><path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 1 1-2.83 2.83l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 1 1-4 0v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 1 1-2.83-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 1 1 0-4h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 1 1 2.83-2.83l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 1 1 4 0v.09a1.65 1.65 0 0 0 1 1.51 1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 1 1 2.83 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 1 1 0 4h-.09a1.65 1.65 0 0 0-1.51 1z"/></svg>
          </button>
        </div>
      </div>
      <div class="geo-divider mt-3" aria-hidden="true">
        <span class="blk w-8 bg-burnt"></span><span class="blk w-4 bg-teal2"></span><span class="blk w-2 bg-gold"></span>
        <span class="flex-1 h-[2px] bg-charcoal/20 dark:bg-nborder"></span>
      </div>
    </div>

    <div class="px-5 pb-3">
      <button class="btn btn-primary btn-md w-full" data-action="add-book">＋ 添加新书</button>
    </div>

    <nav class="flex-1 px-3 pb-6" aria-label="分类列表">
      <div class="cat-item text-sm font-semibold" data-action="select-root" tabindex="0" id="rootItem">
        <svg class="w-4 h-4 text-gold shrink-0" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true"><path d="M4 4h7v7H4zM13 4h7v4h-7zM13 10h7v10h-7zM4 13h7v7H4z"/></svg>
        <span class="cat-name">全部笔记</span>
        <span class="ml-auto text-xs opacity-60" id="rootCount">0</span>
      </div>
      <div id="bookTree"></div>
    </nav>
  </aside>

  <!-- ═══════════ 中间：内容区 ═══════════ -->
  <main id="main" class="flex-1 min-w-0 h-full overflow-y-auto bg-cream dark:bg-night"></main>

  <!-- ═══════════ 右侧：标签栏 ═══════════ -->
  <aside id="tagbar" class="w-[208px] shrink-0 h-full overflow-y-auto border-l-2 border-charcoal dark:border-nborder bg-cream dark:bg-night flex flex-col">
    <div class="p-5 pb-3">
      <h2 class="text-sm font-bold tracking-widest uppercase text-charcoal dark:text-ntext">标签</h2>
      <div class="geo-divider mt-3" aria-hidden="true">
        <span class="blk w-6 bg-gold"></span><span class="blk w-3 bg-burnt"></span>
        <span class="flex-1 h-[2px] bg-charcoal/20 dark:bg-nborder"></span>
      </div>
    </div>
    <div class="px-4 pb-3">
      <button class="btn btn-secondary btn-sm w-full" data-action="new-tag">＋ 新建标签</button>
    </div>
    <div id="tagList" class="px-4 pb-6 flex flex-col gap-1"></div>
  </aside>
</div>

<!-- 移动端抽屉遮罩 -->
<div id="scrim" class="fixed inset-0 z-30 bg-charcoal/40 hidden opacity-0" data-action="close-drawer"></div>

<!-- 右键/长按菜单 -->
<div id="ctxMenu" class="fixed z-50 hidden min-w-[160px] rounded-lg border-2 border-charcoal dark:border-nborder bg-cream dark:bg-ncard shadow-mcm p-1 fade-in"></div>

<!-- 弹窗容器（对话框 / 设置面板） -->
<div id="modalWrap" class="fixed inset-0 z-50 hidden items-center justify-center p-4 bg-charcoal/40"></div>

<!-- Toast -->
<div id="toast" class="fixed z-[60] left-1/2 -translate-x-1/2 bottom-8 hidden rounded-lg border-2 border-charcoal dark:border-nborder bg-burnt text-cream px-5 py-3 text-sm font-semibold shadow-mcm fade-in"></div>

<!-- 隐藏的导入文件框 -->
<input type="file" id="importFile" accept="application/json,.json" class="hidden">

<script>
/* ═══════════════════════════ 数据层 ═══════════════════════════ */
const LS_KEY = 'mcm-reading-notes-v1';
const ACCENTS = ['#e8572a', '#2a6e5e', '#c4a35a'];
const SORT_MODES = ['updated-desc', 'created-desc', 'updated-asc', 'created-asc'];
const SORT_LABELS = {
  'updated-desc': '修改时间 ↓', 'updated-asc': '修改时间 ↑',
  'created-desc': '创建时间 ↓', 'created-asc': '创建时间 ↑'
};

const uid = () => Date.now().toString(36) + Math.random().toString(36).slice(2, 7);
const esc = s => String(s ?? '').replace(/[&<>"']/g, c => ({ '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#39;' }[c]));

function defaultState() {
  return {
    version: 1,
    books: [],   // {id, name, color, expanded, children:[{id,name}]}
    notes: [],   // {id, bookId, catId, title, body, tags:[tagId], created, updated}
    tags: [],    // {id, name}
    prefs: { sort: 'updated-desc', dark: false, followSystem: false }
  };
}

function loadState() {
  try {
    const raw = localStorage.getItem(LS_KEY);
    if (!raw) return defaultState();
    const s = JSON.parse(raw);
    if (!Array.isArray(s.books) || !Array.isArray(s.notes) || !Array.isArray(s.tags)) return defaultState();
    s.prefs = Object.assign({ sort: 'updated-desc', dark: false, followSystem: false }, s.prefs || {});
    return s;
  } catch (e) { return defaultState(); }
}

let state = loadState();
let ui = {
  view: 'list',          // 'list' | 'detail'
  bookId: null, catId: null,
  noteId: null, editing: false, isNew: false, snapshot: null,
  search: '', activeTags: [],
  sort: state.prefs.sort || 'updated-desc',
  drawer: null,          // null | 'left' | 'right'
  suppressClick: false
};

function persist() { localStorage.setItem(LS_KEY, JSON.stringify(state)); }

/* 防抖工具 */
function debounce(fn, ms) { let t; return (...a) => { clearTimeout(t); t = setTimeout(() => fn(...a), ms); }; }
const debouncedPersist = debounce(persist, 500);

/* ═══════════════════════════ 查询工具 ═══════════════════════════ */
const bookById = id => state.books.find(b => b.id === id);
const subById = (book, id) => (book && book.children) ? book.children.find(c => c.id === id) : undefined;
const tagById = id => state.tags.find(t => t.id === id);
const noteById = id => state.notes.find(n => n.id === id);

function currentScope() {
  // 返回当前作用域内的笔记数组
  let ns = state.notes;
  if (ui.bookId) {
    ns = ns.filter(n => n.bookId === ui.bookId);
    if (ui.catId) ns = ns.filter(n => n.catId === ui.catId);
  }
  return ns;
}

function visibleNotes() {
  let ns = currentScope();
  const q = ui.search.trim().toLowerCase();
  if (q) ns = ns.filter(n => (n.title || '').toLowerCase().includes(q) || (n.body || '').toLowerCase().includes(q));
  if (ui.activeTags.length) ns = ns.filter(n => ui.activeTags.every(t => (n.tags || []).includes(t)));
  const [field, dir] = ui.sort.split('-');
  ns = [...ns].sort((a, b) => (a[field] - b[field]) * (dir === 'asc' ? 1 : -1));
  return ns;
}

function tagGlobalCount(tagId) { return state.notes.filter(n => (n.tags || []).includes(tagId)).length; }
function tagScopeCount(tagId) { return currentScope().filter(n => (n.tags || []).includes(tagId)).length; }

function fmt(ts) {
  if (!ts) return '';
  const d = new Date(ts);
  const p = n => String(n).padStart(2, '0');
  return `${d.getFullYear()}/${p(d.getMonth() + 1)}/${p(d.getDate())} ${p(d.getHours())}:${p(d.getMinutes())}`;
}

/* ═══════════════════════════ 装饰元素 ═══════════════════════════ */
function star(cls, color) {
  return `<svg class="${cls}" viewBox="0 0 24 24" fill="${color || 'currentColor'}" aria-hidden="true"><path d="M12 0c1.3 7 4.4 10.1 12 12-7.6 1.9-10.7 5-12 12-1.3-7-4.4-10.1-12-12C7.6 10.1 10.7 7 12 0z"/></svg>`;
}
function chev(open) {
  return `<svg class="chev w-3 h-3 shrink-0 transition-transform duration-200 ${open ? 'rotate-90' : ''}" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="3" aria-hidden="true"><path d="M9 5l7 7-7 7"/></svg>`;
}

/* ═══════════════════════════ 渲染：侧栏 ═══════════════════════════ */
function renderSidebar() {
  document.getElementById('rootCount').textContent = state.notes.length;
  document.getElementById('rootItem').classList.toggle('active', !ui.bookId);

  const tree = document.getElementById('bookTree');
  if (!state.books.length) {
    tree.innerHTML = `<p class="px-4 py-6 text-xs text-charcoal/50 dark:text-ntext/50 leading-relaxed">还没有书籍。<br>点击上方「添加新书」开始整理你的阅读笔记。</p>`;
    return;
  }
  tree.innerHTML = state.books.map(b => {
    const active = ui.bookId === b.id && !ui.catId;
    const subs = (b.expanded && b.children.length) ? b.children.map(c => {
      const cActive = ui.bookId === b.id && ui.catId === c.id;
      return `
      <div class="cat-item ${cActive ? 'active' : ''} pl-10 text-sm text-charcoal dark:text-ntext" tabindex="0"
           data-action="select-cat" data-book-id="${b.id}" data-cat-id="${c.id}" data-cat-item data-type="cat">
        <span class="w-1.5 h-1.5 rounded-full shrink-0" style="background:${ACCENTS[b.color % 3]}"></span>
        <span class="cat-name truncate">${esc(c.name)}</span>
        <span class="ml-auto text-[10px] opacity-60">${state.notes.filter(n => n.bookId === b.id && n.catId === c.id).length}</span>
        <button class="more-btn text-xs px-1 opacity-60" data-action="cat-menu" data-book-id="${b.id}" data-cat-id="${c.id}" data-type="cat" aria-label="子分类操作">⋯</button>
      </div>`;
    }).join('') : '';
    return `
    <div>
      <div class="cat-item ${active ? 'active' : ''} text-sm font-semibold text-charcoal dark:text-ntext" tabindex="0"
           data-action="select-book" data-book-id="${b.id}" data-cat-item data-type="book">
        <button class="shrink-0 p-0.5 rounded ${b.children.length ? '' : 'invisible'}" data-action="toggle-expand" data-book-id="${b.id}" aria-label="展开/折叠">${chev(!!b.expanded)}</button>
        <span class="w-1.5 h-5 rounded-sm shrink-0" style="background:${ACCENTS[b.color % 3]}"></span>
        <span class="cat-name truncate">${esc(b.name)}</span>
        <span class="ml-auto text-[10px] opacity-60">${state.notes.filter(n => n.bookId === b.id).length}</span>
        <button class="more-btn more text-xs px-1 opacity-60" data-action="cat-menu" data-book-id="${b.id}" data-type="book" aria-label="书籍操作">⋯</button>
      </div>
      <div class="ml-4">${subs}</div>
    </div>`;
  }).join('');
}

/* ═══════════════════════════ 渲染：标签栏 ═══════════════════════════ */
function renderTagbar() {
  const wrap = document.getElementById('tagList');
  if (!state.tags.length) {
    wrap.innerHTML = `<p class="px-1 py-6 text-xs text-charcoal/50 dark:text-ntext/50 leading-relaxed">还没有标签。编辑笔记时可添加标签，或点击上方「新建标签」。</p>`;
    return;
  }
  const tags = [...state.tags].sort((a, b) => tagGlobalCount(b.id) - tagGlobalCount(a.id) || a.name.localeCompare(b.name, 'zh'));
  wrap.innerHTML = tags.map(t => {
    const on = ui.activeTags.includes(t.id);
    return `
    <button class="chip !justify-between w-full ${on ? 'active' : ''}" data-action="toggle-tag-filter" data-tag-id="${t.id}"
            aria-pressed="${on}" title="${on ? '点击取消筛选' : '点击筛选'}">
      <span class="flex items-center gap-1 truncate">${star('w-2.5 h-2.5 spark', 'currentColor')}${esc(t.name)}</span>
      <span class="text-[10px] font-bold px-1">${tagScopeCount(t.id)}</span>
    </button>`;
  }).join('');
}

/* ═══════════════════════════ 渲染：内容区（列表） ═══════════════════════════ */
function breadcrumbHTML() {
  const b = ui.bookId ? bookById(ui.bookId) : null;
  const c = b && ui.catId ? subById(b, ui.catId) : null;
  return `
  <nav class="flex items-center gap-2 text-xs font-semibold tracking-wide uppercase min-w-0" aria-label="面包屑">
    <button class="hover:text-burnt transition-colors ${!b ? 'text-burnt' : ''}" data-action="select-root">全部笔记</button>
    ${b ? `<span class="crumb-sep">›</span>
      <button class="hover:text-burnt transition-colors truncate ${b && !c ? 'text-burnt' : ''}" data-action="select-book" data-book-id="${b.id}">${esc(b.name)}</button>` : ''}
    ${c ? `<span class="crumb-sep">›</span><span class="text-burnt truncate">${esc(c.name)}</span>` : ''}
  </nav>`;
}

function emptyStateHTML() {
  if (!state.books.length) {
    return `
    <div class="flex flex-col items-center justify-center py-24 fade-in">
      <div class="organic w-56 h-44 flex items-center justify-center border-2 border-charcoal/20 dark:border-nborder/40">
        ${star('w-14 h-14 text-gold', 'currentColor')}
      </div>
      <h3 class="mt-6 text-lg font-bold tracking-widest uppercase">还没有书籍</h3>
      <p class="mt-2 text-sm text-charcoal/60 dark:text-ntext/60">先添加一本书，再为它记录读书笔记。</p>
      <button class="btn btn-primary btn-md mt-6" data-action="add-book">＋ 添加新书</button>
    </div>`;
  }
  const hasFilter = ui.search.trim() || ui.activeTags.length;
  if (hasFilter) {
    return `
    <div class="flex flex-col items-center justify-center py-24 fade-in">
      <div class="organic w-56 h-44 flex items-center justify-center border-2 border-charcoal/20 dark:border-nborder/40">
        <svg class="w-12 h-12 text-burnt" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><circle cx="11" cy="11" r="7"/><path d="M21 21l-4.35-4.35"/></svg>
      </div>
      <h3 class="mt-6 text-lg font-bold tracking-widest uppercase">没有找到匹配的笔记</h3>
      <p class="mt-2 text-sm text-charcoal/60 dark:text-ntext/60">换个关键词试试，或清除当前筛选条件。</p>
      <div class="flex gap-3 mt-6">
        ${ui.search.trim() ? `<button class="btn btn-secondary btn-md" data-action="clear-search">清除搜索</button>` : ''}
        ${ui.activeTags.length ? `<button class="btn btn-secondary btn-md" data-action="clear-tag-filters">清除标签筛选</button>` : ''}
      </div>
    </div>`;
  }
  return `
  <div class="flex flex-col items-center justify-center py-24 fade-in">
    <div class="organic w-56 h-44 flex items-center justify-center border-2 border-charcoal/20 dark:border-nborder/40">
      <svg class="w-12 h-12 text-teal2" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M4 19.5A2.5 2.5 0 0 1 6.5 17H20"/><path d="M6.5 2H20v20H6.5A2.5 2.5 0 0 1 4 19.5v-15A2.5 2.5 0 0 1 6.5 2z"/></svg>
    </div>
    <h3 class="mt-6 text-lg font-bold tracking-widest uppercase">这里还没有笔记</h3>
    <p class="mt-2 text-sm text-charcoal/60 dark:text-ntext/60">记录你的第一条阅读想法吧。</p>
    <button class="btn btn-primary btn-md mt-6" data-action="new-note">＋ 新建笔记</button>
  </div>`;
}

function noteCardHTML(n) {
  const b = bookById(n.bookId);
  const c = b && n.catId ? subById(b, n.catId) : null;
  const tags = (n.tags || []).map(tid => tagById(tid)).filter(Boolean);
  const preview = (n.body || '').replace(/\s+/g, ' ').trim() || '（暂无正文）';
  return `
  <article class="card flex flex-col gap-3" tabindex="0" data-action="open-note" data-note-id="${n.id}" role="button" aria-label="打开笔记 ${esc(n.title)}">
    <h3 class="font-bold tracking-wide text-base leading-snug line-clamp-2">${esc(n.title || '无标题笔记')}</h3>
    <p class="text-sm text-charcoal/70 dark:text-ntext/70 line-clamp-2 leading-relaxed">${esc(preview)}</p>
    <div class="flex flex-wrap gap-1.5 mt-auto">
      ${tags.map(t => `<span class="chip chip-static !py-0 !text-[10px]">${star('w-2 h-2 spark', 'currentColor')}${esc(t.name)}</span>`).join('')}
    </div>
    <div class="flex items-center gap-2 text-[11px] text-charcoal/50 dark:text-ntext/50 pt-2 border-t-2 border-dashed border-charcoal/15 dark:border-nborder/40">
      <span class="truncate">${b ? esc(b.name) : ''}${c ? ' › ' + esc(c.name) : ''}</span>
      <span class="ml-auto shrink-0">${fmt(n.updated)}</span>
    </div>
  </article>`;
}

function listHTML() {
  const notes = visibleNotes();
  const grid = notes.length
    ? `<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 fade-in">${notes.map(noteCardHTML).join('')}</div>`
    : emptyStateHTML();

  return `
  <div class="sticky top-0 z-10 bg-cream dark:bg-night border-b-2 border-charcoal/10 dark:border-nborder/40 px-4 md:px-8 pt-4 pb-4">
    <div class="flex items-center gap-2 md:gap-3">
      <button class="btn btn-secondary btn-sm lg:hidden" data-action="open-drawer-left" aria-label="打开分类栏">☰</button>
      <div class="relative flex-1 max-w-md">
        <svg class="w-4 h-4 absolute left-3 top-1/2 -translate-y-1/2 text-charcoal/40 dark:text-ntext/40 pointer-events-none" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><circle cx="11" cy="11" r="7"/><path d="M21 21l-4.35-4.35"/></svg>
        <input id="searchInput" type="search" class="field !pl-9" placeholder="搜索笔记标题或正文…" value="${esc(ui.search)}" aria-label="全文搜索">
      </div>
      <button class="btn btn-secondary btn-sm" data-action="sort-cycle" title="切换排序方式">⇅ ${SORT_LABELS[ui.sort]}</button>
      <button class="btn btn-primary btn-sm" data-action="new-note">＋ 新建笔记</button>
      <button class="btn btn-secondary btn-sm lg:hidden" data-action="open-drawer-right" aria-label="打开标签栏">
        <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M20.59 13.41l-7.17 7.17a2 2 0 0 1-2.83 0L2 12V2h10l8.59 8.59a2 2 0 0 1 0 2.82z"/><circle cx="7" cy="7" r="1.5" fill="currentColor"/></svg>
      </button>
    </div>
    <div class="mt-3 flex items-center justify-between flex-wrap gap-2">
      ${breadcrumbHTML()}
      <span class="text-[11px] text-charcoal/50 dark:text-ntext/50">${visibleNotes().length} 条笔记</span>
    </div>
  </div>
  <div id="gridArea" class="px-4 md:px-8 py-6">${grid}</div>`;
}

/* ═══════════════════════════ 渲染：详情页 ═══════════════════════════ */
function detailReadHTML(n) {
  const tags = (n.tags || []).map(tid => tagById(tid)).filter(Boolean);
  return `
  <div class="sticky top-0 z-10 bg-cream dark:bg-night border-b-2 border-charcoal/10 dark:border-nborder/40 px-4 md:px-8 py-4">
    <div class="flex items-center gap-3 max-w-[720px] mx-auto">
      <button class="btn btn-secondary btn-sm" data-action="back" aria-label="返回列表">← 返回</button>
      <span class="flex-1"></span>
      <button class="btn btn-secondary btn-sm" data-action="edit-note" data-note-id="${n.id}">✎ 编辑</button>
      <button class="btn btn-danger btn-sm" data-action="delete-note" data-note-id="${n.id}">删除</button>
    </div>
  </div>
  <div class="px-4 md:px-8 py-8 fade-in">
    <article class="max-w-[680px] mx-auto">
      <div class="geo-divider mb-6" aria-hidden="true">
        <span class="blk w-10 bg-burnt"></span><span class="blk w-5 bg-teal2"></span><span class="blk w-2.5 bg-gold"></span>
        <span class="flex-1 h-[2px] bg-charcoal/20 dark:bg-nborder"></span>
      </div>
      <h2 class="text-2xl md:text-3xl font-bold tracking-wide leading-tight">${esc(n.title || '无标题笔记')}</h2>
      <div class="flex flex-wrap items-center gap-2 mt-4">
        ${tags.length ? tags.map(t => `<span class="chip chip-static">${star('w-2.5 h-2.5 spark', 'currentColor')}${esc(t.name)}</span>`).join('')
                      : '<span class="text-xs text-charcoal/50 dark:text-ntext/50">暂无标签</span>'}
      </div>
      <p class="mt-3 text-xs text-charcoal/50 dark:text-ntext/50">创建于 ${fmt(n.created)} · 修改于 ${fmt(n.updated)}</p>
      <div class="geo-divider my-6" aria-hidden="true">
        <span class="blk w-2 bg-gold"></span><span class="flex-1 h-[2px] bg-charcoal/20 dark:bg-nborder"></span>
      </div>
      <div class="whitespace-pre-wrap text-base leading-[1.6] md:text-[17px]">${esc(n.body || '（暂无正文）')}</div>
    </article>
  </div>`;
}

function detailEditHTML(n) {
  const tagBoxes = state.tags.map(t => {
    const on = (n.tags || []).includes(t.id);
    return `
    <button type="button" class="chip ${on ? 'active' : ''}" data-action="editor-toggle-tag" data-tag-id="${t.id}" aria-pressed="${on}">
      ${star('w-2.5 h-2.5 spark', 'currentColor')}${esc(t.name)}
    </button>`;
  }).join('');
  return `
  <div class="sticky top-0 z-10 bg-cream dark:bg-night border-b-2 border-charcoal/10 dark:border-nborder/40 px-4 md:px-8 py-4">
    <div class="flex items-center gap-3 max-w-[720px] mx-auto">
      <button class="btn btn-secondary btn-sm" data-action="cancel-edit" data-note-id="${n.id}">← 取消</button>
      <span class="flex-1 text-xs font-bold tracking-widest uppercase text-burnt">编辑模式</span>
      <button class="btn btn-primary btn-sm" data-action="save-note" data-note-id="${n.id}">✓ 保存并返回</button>
    </div>
  </div>
  <div class="px-4 md:px-8 py-8 fade-in">
    <form id="editorForm" class="max-w-[680px] mx-auto flex flex-col gap-5" onsubmit="return false">
      <div>
        <label for="edTitle" class="block text-xs font-bold tracking-widest uppercase mb-2">标题</label>
        <input id="edTitle" class="field text-lg font-bold" type="text" value="${esc(n.title)}" placeholder="笔记标题…" maxlength="120" autocomplete="off">
      </div>
      <div>
        <label for="edBody" class="block text-xs font-bold tracking-widest uppercase mb-2">正文</label>
        <textarea id="edBody" class="field min-h-[260px] leading-relaxed resize-y" placeholder="写下你的阅读笔记…（输入会自动保存草稿）">${esc(n.body)}</textarea>
      </div>
      <div>
        <div class="flex items-center justify-between mb-2">
          <label class="text-xs font-bold tracking-widest uppercase">标签</label>
          <button type="button" class="btn btn-secondary btn-sm !shadow-none" data-action="editor-new-tag">＋ 新标签</button>
        </div>
        <div class="flex flex-wrap gap-2">${tagBoxes || '<span class="text-xs text-charcoal/50 dark:text-ntext/50">还没有可选标签，点击「新标签」创建。</span>'}</div>
      </div>
    </form>
  </div>`;
}

function renderMain() {
  const el = document.getElementById('main');
  if (ui.view === 'detail') {
    const n = noteById(ui.noteId);
    if (!n) { ui.view = 'list'; ui.noteId = null; ui.editing = false; }
    else {
      el.innerHTML = ui.editing ? detailEditHTML(n) : detailReadHTML(n);
      if (ui.editing) {
        const ti = document.getElementById('edTitle');
        const bo = document.getElementById('edBody');
        if (ti) { ti.focus(); ti.setSelectionRange(ti.value.length, ti.value.length); }
        const onInput = () => { n.title = ti ? ti.value : n.title; n.body = bo ? bo.value : n.body; debouncedPersist(); };
        if (ti) ti.addEventListener('input', onInput);
        if (bo) bo.addEventListener('input', onInput);
      }
      return;
    }
  }
  el.innerHTML = listHTML();
  const si = document.getElementById('searchInput');
  if (si) si.addEventListener('input', () => {
    ui.search = si.value;
    const notes = visibleNotes();
    document.getElementById('gridArea').innerHTML = notes.length
      ? `<div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 fade-in">${notes.map(noteCardHTML).join('')}</div>`
      : emptyStateHTML();
  });
}

function render() {
  renderSidebar();
  renderTagbar();
  renderMain();
  persist();
}

/* ═══════════════════════════ 夜间模式 ═══════════════════════════ */
const sysDark = window.matchMedia ? window.matchMedia('(prefers-color-scheme: dark)') : null;
function applyDark() {
  const dark = state.prefs.followSystem ? (sysDark && sysDark.matches) : state.prefs.dark;
  document.documentElement.classList.toggle('dark', !!dark);
  const icon = document.getElementById('darkIcon');
  if (icon) icon.textContent = dark ? '☾' : '☀';
}
if (sysDark) sysDark.addEventListener('change', () => { if (state.prefs.followSystem) applyDark(); });

/* ═══════════════════════════ 对话框系统 ═══════════════════════════ */
function dialog({ title, desc = '', fields = [], okText = '确定', danger = false }) {
  return new Promise(resolve => {
    const wrap = document.getElementById('modalWrap');
    const fieldHTML = fields.map(f => {
      if (f.type === 'select') {
        return `<div>
          <label class="block text-xs font-bold tracking-widest uppercase mb-2">${esc(f.label)}</label>
          <select class="field dialog-field" data-name="${esc(f.name)}">
            ${f.options.map(o => `<option value="${esc(o.value)}" ${o.value === f.value ? 'selected' : ''}>${esc(o.label)}</option>`).join('')}
          </select></div>`;
      }
      if (f.type === 'checkbox') {
        return `<label class="flex items-center gap-3 text-sm cursor-pointer">
          <input type="checkbox" class="dialog-field w-5 h-5 accent-[#e8572a]" data-name="${esc(f.name)}" ${f.value ? 'checked' : ''}>
          <span>${esc(f.label)}</span></label>`;
      }
      return `<div>
        <label class="block text-xs font-bold tracking-widest uppercase mb-2">${esc(f.label)}</label>
        <input type="text" class="field dialog-field" data-name="${esc(f.name)}" value="${esc(f.value || '')}" placeholder="${esc(f.placeholder || '')}" autocomplete="off">
      </div>`;
    }).join('');

    wrap.innerHTML = `
    <div class="modal-card w-full max-w-md rounded-xl border-2 border-charcoal dark:border-nborder bg-cream dark:bg-ncard shadow-mcm-lg p-6 md:p-8 fade-in" role="dialog" aria-modal="true" aria-label="${esc(title)}">
      <h3 class="text-lg font-bold tracking-widest uppercase">${esc(title)}</h3>
      ${desc ? `<p class="mt-2 text-sm text-charcoal/70 dark:text-ntext/70 leading-relaxed">${desc}</p>` : ''}
      <div class="mt-5 flex flex-col gap-4">${fieldHTML}</div>
      <div class="mt-8 flex justify-end gap-3">
        <button class="btn btn-secondary btn-md" data-dlg="cancel">取消</button>
        <button class="btn ${danger ? 'btn-danger' : 'btn-primary'} btn-md" data-dlg="ok">${esc(okText)}</button>
      </div>
    </div>`;
    wrap.classList.remove('hidden');
    wrap.classList.add('flex');
    const card = wrap.querySelector('.modal-card');

    const close = val => {
      wrap.classList.add('hidden'); wrap.classList.remove('flex'); wrap.innerHTML = '';
      document.removeEventListener('keydown', onKey);
      resolve(val);
    };
    const collect = () => {
      const out = {};
      wrap.querySelectorAll('.dialog-field').forEach(el => {
        out[el.dataset.name] = el.type === 'checkbox' ? el.checked : el.value;
      });
      return out;
    };
    const onKey = e => {
      if (e.key === 'Escape') close(null);
      if (e.key === 'Enter' && fields.length) close(collect());
    };
    document.addEventListener('keydown', onKey);
    wrap.onclick = e => { if (e.target === wrap) close(null); };
    card.querySelectorAll('[data-dlg]').forEach(btn => {
      btn.onclick = e => { e.stopPropagation(); close(btn.dataset.dlg === 'ok' ? collect() : null); };
    });
    const first = wrap.querySelector('.dialog-field');
    if (first) first.focus();
  });
}

const mcmPrompt = (title, value = '') => dialog({ title, fields: [{ type: 'text', name: 'v', value }] }).then(r => r ? r.v : null);
const mcmConfirm = (title, desc, okText = '删除') => dialog({ title, desc, okText, danger: true }).then(r => r !== null);

function toast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.remove('hidden');
  clearTimeout(t._timer);
  t._timer = setTimeout(() => t.classList.add('hidden'), 2200);
}

/* ═══════════════════════════ 右键 / 长按菜单 ═══════════════════════════ */
const ctxEl = document.getElementById('ctxMenu');
function showCtx(x, y, items) {
  ctxEl.innerHTML = items.map(it => `
    <button class="w-full text-left px-4 py-2 rounded-md text-sm font-semibold transition-colors
      ${it.danger ? 'text-burnt hover:bg-burnt/10' : 'text-charcoal dark:text-ntext hover:bg-charcoal/10 dark:hover:bg-ntext/10'}"
      data-ctx="${esc(it.action)}" ${it.bookId ? `data-book-id="${it.bookId}"` : ''} ${it.catId ? `data-cat-id="${it.catId}"` : ''}>
      ${esc(it.label)}
    </button>`).join('');
  ctxEl.classList.remove('hidden');
  const r = ctxEl.getBoundingClientRect();
  const px = Math.min(x, window.innerWidth - r.width - 8);
  const py = Math.min(y, window.innerHeight - r.height - 8);
  ctxEl.style.left = px + 'px';
  ctxEl.style.top = py + 'px';
}
function hideCtx() { ctxEl.classList.add('hidden'); }
ctxEl.addEventListener('click', e => {
  const b = e.target.closest('[data-ctx]');
  if (!b) return;
  hideCtx();
  const act = b.dataset.ctx;
  const p = { bookId: b.dataset.bookId, catId: b.dataset.catId };
  if (act === 'rename-book') renameBook(p.bookId);
  else if (act === 'delete-book') deleteBook(p.bookId);
  else if (act === 'add-subcat') addSubcat(p.bookId);
  else if (act === 'rename-cat') renameCat(p.bookId, p.catId);
  else if (act === 'delete-cat') deleteCat(p.bookId, p.catId);
});
document.addEventListener('click', e => { if (!e.target.closest('#ctxMenu')) hideCtx(); });
document.addEventListener('scroll', hideCtx, true);

/* 右键菜单 */
document.getElementById('bookTree').addEventListener('contextmenu', e => {
  const item = e.target.closest('[data-cat-item]');
  if (!item) return;
  e.preventDefault();
  const { type, bookId, catId } = item.dataset;
  const items = type === 'book'
    ? [
        { label: '✎ 重命名书籍', action: 'rename-book', bookId },
        { label: '＋ 添加子分类', action: 'add-subcat', bookId },
        { label: '✕ 删除书籍', action: 'delete-book', bookId, danger: true }
      ]
    : [
        { label: '✎ 重命名子分类', action: 'rename-cat', bookId, catId },
        { label: '✕ 删除子分类', action: 'delete-cat', bookId, catId, danger: true }
      ];
  showCtx(e.clientX, e.clientY, items);
});

/* 长按菜单（移动端） */
let lpTimer = null, lpPoint = null;
document.getElementById('bookTree').addEventListener('touchstart', e => {
  const item = e.target.closest('[data-cat-item]');
  if (!item) return;
  const t = e.touches[0];
  lpPoint = { x: t.clientX, y: t.clientY, type: item.dataset.type, bookId: item.dataset.bookId, catId: item.dataset.catId };
  lpTimer = setTimeout(() => {
    ui.suppressClick = true;
    setTimeout(() => { ui.suppressClick = false; }, 400);
    const items = lpPoint.type === 'book'
      ? [
          { label: '✎ 重命名书籍', action: 'rename-book', bookId: lpPoint.bookId },
          { label: '＋ 添加子分类', action: 'add-subcat', bookId: lpPoint.bookId },
          { label: '✕ 删除书籍', action: 'delete-book', bookId: lpPoint.bookId, danger: true }
        ]
      : [
          { label: '✎ 重命名子分类', action: 'rename-cat', bookId: lpPoint.bookId, catId: lpPoint.catId },
          { label: '✕ 删除子分类', action: 'delete-cat', bookId: lpPoint.bookId, catId: lpPoint.catId, danger: true }
        ];
    showCtx(lpPoint.x, lpPoint.y, items);
    if (navigator.vibrate) navigator.vibrate(10);
  }, 550);
}, { passive: true });
['touchmove', 'touchend', 'touchcancel'].forEach(ev =>
  document.getElementById('bookTree').addEventListener(ev, () => { clearTimeout(lpTimer); }, { passive: true })
);

/* ═══════════════════════════ 分类 CRUD ═══════════════════════════ */
async function addBook() {
  const name = await mcmPrompt('添加新书', '');
  if (name === null) return;
  const n = name.trim();
  if (!n) return toast('书籍名称不能为空');
  state.books.push({ id: uid(), name: n, color: state.books.length % 3, expanded: true, children: [] });
  render();
  toast(`已添加《${n}》`);
}
async function renameBook(id) {
  const b = bookById(id);
  if (!b) return;
  const name = await mcmPrompt('重命名书籍', b.name);
  if (name === null) return;
  const n = name.trim();
  if (!n) return toast('书籍名称不能为空');
  b.name = n;
  render();
}
async function deleteBook(id) {
  const b = bookById(id);
  if (!b) return;
  const count = state.notes.filter(n => n.bookId === id).length;
  const ok = await mcmConfirm('删除书籍', `将删除《${b.name}》及其全部 ${count} 条笔记与子分类，此操作不可撤销。`);
  if (!ok) return;
  state.books = state.books.filter(x => x.id !== id);
  state.notes = state.notes.filter(n => n.bookId !== id);
  if (ui.bookId === id) { ui.bookId = null; ui.catId = null; }
  render();
  toast('书籍已删除');
}
async function addSubcat(bookId) {
  const b = bookById(bookId);
  if (!b) return;
  const name = await mcmPrompt(`为《${b.name}》添加子分类`, '');
  if (name === null) return;
  const n = name.trim();
  if (!n) return toast('子分类名称不能为空');
  b.children.push({ id: uid(), name: n });
  b.expanded = true;
  render();
}
async function renameCat(bookId, catId) {
  const b = bookById(bookId);
  const c = b && subById(b, catId);
  if (!c) return;
  const name = await mcmPrompt('重命名子分类', c.name);
  if (name === null) return;
  const n = name.trim();
  if (!n) return toast('子分类名称不能为空');
  c.name = n;
  render();
}
async function deleteCat(bookId, catId) {
  const b = bookById(bookId);
  const c = b && subById(b, catId);
  if (!c) return;
  const count = state.notes.filter(n => n.bookId === bookId && n.catId === catId).length;
  const ok = await mcmConfirm('删除子分类', `将删除「${c.name}」及其下 ${count} 条笔记，此操作不可撤销。`);
  if (!ok) return;
  b.children = b.children.filter(x => x.id !== catId);
  state.notes = state.notes.filter(n => !(n.bookId === bookId && n.catId === catId));
  if (ui.catId === catId) ui.catId = null;
  render();
  toast('子分类已删除');
}

/* ═══════════════════════════ 标签 CRUD ═══════════════════════════ */
async function createTag(prefill = '') {
  const name = await mcmPrompt('新建标签', prefill);
  if (name === null) return null;
  const n = name.trim();
  if (!n) { toast('标签名称不能为空'); return null; }
  if (state.tags.some(t => t.name === n)) { toast('该标签已存在'); return state.tags.find(t => t.name === n).id; }
  const t = { id: uid(), name: n };
  state.tags.push(t);
  render();
  return t.id;
}
async function renameTag(id) {
  const t = tagById(id);
  if (!t) return;
  const name = await mcmPrompt('重命名标签', t.name);
  if (name === null) return;
  const n = name.trim();
  if (!n) return toast('标签名称不能为空');
  t.name = n;
  render();
}
async function deleteTag(id) {
  const t = tagById(id);
  if (!t) return;
  const count = tagGlobalCount(id);
  const ok = await mcmConfirm('删除标签', `将删除标签「${t.name}」，并从 ${count} 条笔记中移除该标签。`);
  if (!ok) return;
  state.tags = state.tags.filter(x => x.id !== id);
  state.notes.forEach(n => { n.tags = (n.tags || []).filter(x => x !== id); });
  ui.activeTags = ui.activeTags.filter(x => x !== id);
  render();
  toast('标签已删除');
}
async function mergeTag(id) {
  const src = tagById(id);
  if (!src) return;
  const others = state.tags.filter(t => t.id !== id);
  if (!others.length) return toast('没有其他标签可合并');
  const r = await dialog({
    title: '合并标签',
    desc: `将「${src.name}」合并到下面的标签中：所有使用「${src.name}」的笔记将改用目标标签，源标签随之删除。`,
    fields: [{ type: 'select', name: 'target', label: '目标标签', options: others.map(t => ({ value: t.id, label: t.name })) }],
    okText: '合并'
  });
  if (!r) return;
  const dst = tagById(r.target);
  if (!dst) return;
  state.notes.forEach(n => {
    if ((n.tags || []).includes(id)) {
      n.tags = n.tags.filter(x => x !== id);
      if (!n.tags.includes(dst.id)) n.tags.push(dst.id);
    }
  });
  state.tags = state.tags.filter(t => t.id !== id);
  ui.activeTags = ui.activeTags.filter(x => x !== id).map(x => x === id ? dst.id : x);
  render();
  toast(`已将「${src.name}」合并到「${dst.name}」`);
}

/* ═══════════════════════════ 笔记 CRUD ═══════════════════════════ */
function newNote() {
  let bookId = ui.bookId, catId = ui.catId;
  if (!bookId) {
    if (!state.books.length) { toast('请先添加一本书'); return; }
    bookId = state.books[0].id; catId = null;
  }
  const now = Date.now();
  const n = { id: uid(), bookId, catId, title: '', body: '', tags: [], created: now, updated: now };
  state.notes.push(n);
  ui.noteId = n.id; ui.view = 'detail'; ui.editing = true; ui.isNew = true; ui.snapshot = null;
  ui.search = ''; ui.activeTags = [];
  renderMain(); renderTagbar();
}
function openNote(id) {
  ui.noteId = id; ui.view = 'detail'; ui.editing = false; ui.isNew = false; ui.snapshot = null;
  renderMain();
}
function startEdit(id) {
  const n = noteById(id);
  if (!n) return;
  ui.editing = true; ui.isNew = false;
  ui.snapshot = JSON.parse(JSON.stringify(n));
  renderMain();
}
async function deleteNote(id) {
  const n = noteById(id);
  if (!n) return;
  const ok = await mcmConfirm('删除笔记', `确定删除笔记「${n.title || '无标题笔记'}」吗？此操作不可撤销。`);
  if (!ok) return;
  state.notes = state.notes.filter(x => x.id !== id);
  ui.view = 'list'; ui.noteId = null; ui.editing = false;
  render();
  toast('笔记已删除');
}
function saveNote(id) {
  const n = noteById(id);
  if (!n) return;
  const ti = document.getElementById('edTitle');
  const bo = document.getElementById('edBody');
  if (ti) n.title = ti.value.trim();
  if (bo) n.body = bo.value;
  if (!n.title) n.title = '无标题笔记';
  n.updated = Date.now();
  ui.editing = false; ui.isNew = false; ui.snapshot = null;
  persist();
  ui.view = 'list'; ui.noteId = null;
  render();
  toast('笔记已保存');
}
function cancelEdit(id) {
  const n = noteById(id);
  if (!n) { ui.editing = false; ui.view = 'list'; renderMain(); return; }
  if (ui.isNew) {
    state.notes = state.notes.filter(x => x.id !== id);
    ui.view = 'list'; ui.editing = false; ui.isNew = false; ui.noteId = null;
    persist(); render();
    return;
  }
  if (ui.snapshot) Object.assign(n, ui.snapshot);
  ui.editing = false; ui.snapshot = null;
  persist(); renderMain();
}

/* ═══════════════════════════ 数据管理 ═══════════════════════════ */
function exportData() {
  const blob = new Blob([JSON.stringify(state, null, 2)], { type: 'application/json' });
  const a = document.createElement('a');
  const d = new Date();
  const p = x => String(x).padStart(2, '0');
  a.href = URL.createObjectURL(blob);
  a.download = `reading-notes-backup-${d.getFullYear()}${p(d.getMonth() + 1)}${p(d.getDate())}.json`;
  a.click();
  URL.revokeObjectURL(a.href);
  toast('已导出 JSON 备份');
}
async function importData(file) {
  try {
    const text = await file.text();
    const data = JSON.parse(text);
    if (!Array.isArray(data.books) || !Array.isArray(data.notes) || !Array.isArray(data.tags)) throw new Error('格式不符');
    const ok = await mcmConfirm('导入备份', '导入将覆盖当前全部数据（书籍、子分类、笔记、标签），确定继续吗？', '导入');
    if (!ok) return;
    state = {
      version: 1,
      books: data.books, notes: data.notes, tags: data.tags,
      prefs: Object.assign({ sort: 'updated-desc', dark: false, followSystem: false }, data.prefs || {})
    };
    ui.bookId = null; ui.catId = null; ui.view = 'list'; ui.noteId = null; ui.editing = false;
    ui.activeTags = []; ui.search = ''; ui.sort = state.prefs.sort;
    applyDark();
    render();
    toast('数据导入成功');
  } catch (e) {
    toast('导入失败：文件不是有效的备份 JSON');
  }
}
async function clearAll() {
  const ok = await mcmConfirm('清空数据', '将删除全部书籍、子分类、笔记与标签（保留外观偏好），此操作不可撤销！', '全部清空');
  if (!ok) return;
  const prefs = state.prefs;
  state = defaultState();
  state.prefs = prefs;
  ui.bookId = null; ui.catId = null; ui.view = 'list'; ui.noteId = null;
  ui.editing = false; ui.activeTags = []; ui.search = '';
  render();
  toast('数据已清空');
}
document.getElementById('importFile').addEventListener('change', e => {
  const f = e.target.files[0];
  if (f) importData(f);
  e.target.value = '';
});

/* ═══════════════════════════ 设置面板 ═══════════════════════════ */
let settingsTab = 'cats';
const TABS = [
  { id: 'cats', label: '分类管理' }, { id: 'tags', label: '标签管理' },
  { id: 'data', label: '数据管理' }, { id: 'prefs', label: '偏好设置' }
];

function settingsCatsHTML() {
  if (!state.books.length) return `<p class="text-sm text-charcoal/60 dark:text-ntext/60 py-4">还没有书籍。</p>`;
  return state.books.map(b => `
    <div class="border-2 border-charcoal/15 dark:border-nborder/50 rounded-lg p-3">
      <div class="flex items-center gap-2">
        <span class="w-1.5 h-5 rounded-sm shrink-0" style="background:${ACCENTS[b.color % 3]}"></span>
        <span class="font-bold text-sm truncate">${esc(b.name)}</span>
        <span class="text-[10px] opacity-50">${state.notes.filter(n => n.bookId === b.id).length} 笔记</span>
        <span class="flex-1"></span>
        <button class="btn btn-secondary btn-sm !shadow-none" data-action="st-rename-book" data-book-id="${b.id}">重命名</button>
        <button class="btn btn-secondary btn-sm !shadow-none" data-action="st-add-subcat" data-book-id="${b.id}">＋ 子分类</button>
        <button class="btn btn-danger btn-sm !shadow-none" data-action="st-delete-book" data-book-id="${b.id}">删除</button>
      </div>
      ${b.children.length ? `<div class="mt-2 ml-4 flex flex-col gap-1">${b.children.map(c => `
        <div class="flex items-center gap-2 text-sm">
          <span class="w-1.5 h-1.5 rounded-full shrink-0" style="background:${ACCENTS[b.color % 3]}"></span>
          <span class="truncate">${esc(c.name)}</span>
          <span class="text-[10px] opacity-50">${state.notes.filter(n => n.bookId === b.id && n.catId === c.id).length}</span>
          <span class="flex-1"></span>
          <button class="btn btn-secondary btn-sm !shadow-none" data-action="st-rename-cat" data-book-id="${b.id}" data-cat-id="${c.id}">重命名</button>
          <button class="btn btn-danger btn-sm !shadow-none" data-action="st-delete-cat" data-book-id="${b.id}" data-cat-id="${c.id}">删除</button>
        </div>`).join('')}</div>` : ''}
    </div>`).join('');
}

function settingsTagsHTML() {
  if (!state.tags.length) return `<p class="text-sm text-charcoal/60 dark:text-ntext/60 py-4">还没有标签。</p>`;
  return state.tags.map(t => `
    <div class="flex items-center gap-2 border-2 border-charcoal/15 dark:border-nborder/50 rounded-lg p-3">
      ${star('w-3 h-3 text-gold shrink-0', 'currentColor')}
      <span class="font-semibold text-sm truncate">${esc(t.name)}</span>
      <span class="text-[10px] opacity-50">${tagGlobalCount(t.id)} 次使用</span>
      <span class="flex-1"></span>
      <button class="btn btn-secondary btn-sm !shadow-none" data-action="st-rename-tag" data-tag-id="${t.id}">重命名</button>
      <button class="btn btn-secondary btn-sm !shadow-none" data-action="st-merge-tag" data-tag-id="${t.id}">合并</button>
      <button class="btn btn-danger btn-sm !shadow-none" data-action="st-delete-tag" data-tag-id="${t.id}">删除</button>
    </div>`).join('');
}

function settingsDataHTML() {
  return `
  <div class="flex flex-col gap-5">
    <div class="border-2 border-charcoal/15 dark:border-nborder/50 rounded-lg p-4">
      <h4 class="text-xs font-bold tracking-widest uppercase mb-1">导出备份</h4>
      <p class="text-sm text-charcoal/60 dark:text-ntext/60 mb-3">将全部数据导出为 JSON 文件，保存到本地。</p>
      <button class="btn btn-primary btn-md" data-action="st-export">⬇ 导出 JSON</button>
    </div>
    <div class="border-2 border-charcoal/15 dark:border-nborder/50 rounded-lg p-4">
      <h4 class="text-xs font-bold tracking-widest uppercase mb-1">导入恢复</h4>
      <p class="text-sm text-charcoal/60 dark:text-ntext/60 mb-3">从之前导出的 JSON 备份文件恢复，导入会覆盖当前数据。</p>
      <button class="btn btn-secondary btn-md" data-action="st-import">⬆ 选择文件导入</button>
    </div>
    <div class="border-2 border-burnt/50 rounded-lg p-4">
      <h4 class="text-xs font-bold tracking-widest uppercase text-burnt mb-1">清空数据</h4>
      <p class="text-sm text-charcoal/60 dark:text-ntext/60 mb-3">删除全部书籍、子分类、笔记与标签，不可撤销。</p>
      <button class="btn btn-danger btn-md" data-action="st-clear">✕ 清空全部数据</button>
    </div>
  </div>`;
}

function settingsPrefsHTML() {
  return `
  <div class="flex flex-col gap-5">
    <div>
      <label class="block text-xs font-bold tracking-widest uppercase mb-2">默认排序方式</label>
      <select id="prefSort" class="field">
        ${SORT_MODES.map(m => `<option value="${m}" ${state.prefs.sort === m ? 'selected' : ''}>${SORT_LABELS[m]}</option>`).join('')}
      </select>
    </div>
    <label class="flex items-center gap-3 text-sm cursor-pointer">
      <input type="checkbox" id="prefFollow" class="w-5 h-5 accent-[#e8572a]" ${state.prefs.followSystem ? 'checked' : ''}>
      <span>夜间模式跟随系统外观</span>
    </label>
    <p class="text-xs text-charcoal/50 dark:text-ntext/50 leading-relaxed">开启后，夜间模式将自动跟随操作系统的深浅色设置；手动切换按钮会关闭此选项。</p>
  </div>`;
}

function openSettings() {
  const wrap = document.getElementById('modalWrap');
  wrap.innerHTML = `
  <div class="modal-card w-full max-w-2xl max-h-[85vh] overflow-hidden flex flex-col rounded-xl border-2 border-charcoal dark:border-nborder bg-cream dark:bg-ncard shadow-mcm-lg fade-in" role="dialog" aria-modal="true" aria-label="设置">
    <div class="flex items-center justify-between p-5 md:p-6 border-b-2 border-charcoal/10 dark:border-nborder/40">
      <h3 class="text-lg font-bold tracking-widest uppercase">设置</h3>
      <button class="btn btn-secondary btn-sm" data-action="st-close" aria-label="关闭设置">✕</button>
    </div>
    <div class="flex gap-1 px-5 md:px-6 pt-4 border-b-2 border-charcoal/10 dark:border-nborder/40 overflow-x-auto" role="tablist">
      ${TABS.map(t => `<button class="tab-btn px-4 py-2 text-sm font-bold tracking-wide rounded-t-lg whitespace-nowrap transition-colors ${settingsTab === t.id ? 'text-burnt border-b-4 border-burnt' : 'text-charcoal/60 dark:text-ntext/60 hover:text-charcoal dark:hover:text-ntext'}" data-action="st-tab" data-tab="${t.id}" role="tab" aria-selected="${settingsTab === t.id}">${t.label}</button>`).join('')}
    </div>
    <div id="stBody" class="p-5 md:p-6 overflow-y-auto flex-1"></div>
  </div>`;
  wrap.classList.remove('hidden');
  wrap.classList.add('flex');
  wrap.onclick = e => { if (e.target === wrap) closeSettings(); };
  renderSettingsBody();
}
function closeSettings() {
  const wrap = document.getElementById('modalWrap');
  wrap.classList.add('hidden'); wrap.classList.remove('flex'); wrap.innerHTML = '';
}
function renderSettingsBody() {
  const body = document.getElementById('stBody');
  if (!body) return;
  if (settingsTab === 'cats') body.innerHTML = `
    <div class="flex flex-col gap-3">
      <button class="btn btn-primary btn-md self-start" data-action="st-add-book">＋ 添加新书</button>
      ${settingsCatsHTML()}
    </div>`;
  else if (settingsTab === 'tags') body.innerHTML = `
    <div class="flex flex-col gap-3">
      <button class="btn btn-primary btn-md self-start" data-action="st-new-tag">＋ 新建标签</button>
      ${settingsTagsHTML()}
    </div>`;
  else if (settingsTab === 'data') body.innerHTML = settingsDataHTML();
  else {
    body.innerHTML = settingsPrefsHTML();
    const sel = document.getElementById('prefSort');
    const chk = document.getElementById('prefFollow');
    sel.addEventListener('change', () => { state.prefs.sort = sel.value; ui.sort = sel.value; persist(); renderMain(); });
    chk.addEventListener('change', () => { state.prefs.followSystem = chk.checked; persist(); applyDark(); });
  }
}

/* ═══════════════════════════ 移动端抽屉 ═══════════════════════════ */
const scrim = document.getElementById('scrim');
function openDrawer(side) {
  ui.drawer = side;
  const el = side === 'left' ? document.getElementById('sidebar') : document.getElementById('tagbar');
  el.classList.add('open');
  el.style.transform = 'none';
  scrim.classList.remove('hidden');
  requestAnimationFrame(() => scrim.classList.remove('opacity-0'));
}
function closeDrawer() {
  if (!ui.drawer) return;
  const el = ui.drawer === 'left' ? document.getElementById('sidebar') : document.getElementById('tagbar');
  el.classList.remove('open');
  el.style.transform = '';
  scrim.classList.add('opacity-0');
  setTimeout(() => scrim.classList.add('hidden'), 200);
  ui.drawer = null;
}
/* 移动端抽屉样式（JS 注入媒体查询类不可行，直接在 resize 时处理布局切换） */
function handleResize() {
  if (window.innerWidth >= 1024) {
    closeDrawer();
    document.getElementById('sidebar').style.transform = '';
    document.getElementById('tagbar').style.transform = '';
  }
}
window.addEventListener('resize', handleResize);

/* ═══════════════════════════ 事件分发 ═══════════════════════════ */
const ACTIONS = {
  'select-root': () => { ui.bookId = null; ui.catId = null; ui.view = 'list'; closeDrawer(); render(); },
  'select-book': t => {
    if (ui.suppressClick) return;
    ui.bookId = t.dataset.bookId; ui.catId = null; ui.view = 'list'; closeDrawer(); render();
  },
  'select-cat': t => {
    if (ui.suppressClick) return;
    ui.bookId = t.dataset.bookId; ui.catId = t.dataset.catId; ui.view = 'list'; closeDrawer(); render();
  },
  'toggle-expand': t => {
    const b = bookById(t.dataset.bookId);
    if (b) { b.expanded = !b.expanded; persist(); renderSidebar(); }
  },
  'add-book': () => addBook(),
  'cat-menu': (t, e) => {
    e.stopPropagation();
    const r = t.getBoundingClientRect();
    const type = t.dataset.type;
    const items = type === 'book'
      ? [
          { label: '✎ 重命名书籍', action: 'rename-book', bookId: t.dataset.bookId },
          { label: '＋ 添加子分类', action: 'add-subcat', bookId: t.dataset.bookId },
          { label: '✕ 删除书籍', action: 'delete-book', bookId: t.dataset.bookId, danger: true }
        ]
      : [
          { label: '✎ 重命名子分类', action: 'rename-cat', bookId: t.dataset.bookId, catId: t.dataset.catId },
          { label: '✕ 删除子分类', action: 'delete-cat', bookId: t.dataset.bookId, catId: t.dataset.catId, danger: true }
        ];
    showCtx(r.left + r.width / 2, r.bottom + 4, items);
  },
  'toggle-dark': () => {
    state.prefs.followSystem = false;
    state.prefs.dark = !document.documentElement.classList.contains('dark');
    persist(); applyDark();
  },
  'open-settings': () => { closeDrawer(); openSettings(); },
  'new-note': () => newNote(),
  'open-note': t => { if (!ui.suppressClick) openNote(t.dataset.noteId); },
  'sort-cycle': () => {
    const i = SORT_MODES.indexOf(ui.sort);
    ui.sort = SORT_MODES[(i + 1) % SORT_MODES.length];
    renderMain();
  },
  'clear-search': () => { ui.search = ''; renderMain(); },
  'clear-tag-filters': () => { ui.activeTags = []; render(); },
  'new-tag': () => createTag(),
  'toggle-tag-filter': t => {
    const id = t.dataset.tagId;
    const i = ui.activeTags.indexOf(id);
    if (i >= 0) ui.activeTags.splice(i, 1); else ui.activeTags.push(id);
    ui.view = 'list';
    render();
  },
  'back': () => { ui.view = 'list'; ui.noteId = null; ui.editing = false; renderMain(); },
  'edit-note': t => startEdit(t.dataset.noteId),
  'delete-note': t => deleteNote(t.dataset.noteId),
  'save-note': t => saveNote(t.dataset.noteId),
  'cancel-edit': t => cancelEdit(t.dataset.noteId),
  'editor-toggle-tag': t => {
    const n = noteById(ui.noteId);
    if (!n) return;
    const id = t.dataset.tagId;
    n.tags = n.tags || [];
    const i = n.tags.indexOf(id);
    if (i >= 0) n.tags.splice(i, 1); else n.tags.push(id);
    t.classList.toggle('active', n.tags.includes(id));
    t.setAttribute('aria-pressed', n.tags.includes(id));
    debouncedPersist();
  },
  'editor-new-tag': async () => {
    const id = await createTag();
    if (!id) return;
    const n = noteById(ui.noteId);
    if (n && !(n.tags || []).includes(id)) { n.tags.push(id); persist(); }
    renderMain();
  },
  'open-drawer-left': () => openDrawer('left'),
  'open-drawer-right': () => openDrawer('right'),
  'close-drawer': () => closeDrawer(),

  /* ── 设置面板动作 ── */
  'st-close': () => closeSettings(),
  'st-tab': t => { settingsTab = t.dataset.tab; openSettings(); },
  'st-add-book': () => addBook(),
  'st-rename-book': t => renameBook(t.dataset.bookId),
  'st-delete-book': t => deleteBook(t.dataset.bookId),
  'st-add-subcat': t => addSubcat(t.dataset.bookId),
  'st-rename-cat': t => renameCat(t.dataset.bookId, t.dataset.catId),
  'st-delete-cat': t => deleteCat(t.dataset.bookId, t.dataset.catId),
  'st-new-tag': () => createTag(),
  'st-rename-tag': t => renameTag(t.dataset.tagId),
  'st-merge-tag': t => mergeTag(t.dataset.tagId),
  'st-delete-tag': t => deleteTag(t.dataset.tagId),
  'st-export': () => exportData(),
  'st-import': () => document.getElementById('importFile').click(),
  'st-clear': () => clearAll()
};

document.addEventListener('click', e => {
  const t = e.target.closest('[data-action]');
  if (!t) return;
  const fn = ACTIONS[t.dataset.action];
  if (fn) { e.stopPropagation(); fn(t, e); }
});

/* 键盘：Enter 打开聚焦的分类/卡片，Escape 关闭浮层 */
document.addEventListener('keydown', e => {
  if (e.key === 'Escape') { hideCtx(); closeDrawer(); }
  if (e.key === 'Enter') {
    const t = e.target.closest && e.target.closest('.cat-item[data-action], .card[data-action]');
    if (t && e.target === t) { e.preventDefault(); const fn = ACTIONS[t.dataset.action]; if (fn) fn(t, e); }
  }
});

/* ═══════════════════════════ 启动 ═══════════════════════════ */
applyDark();
render();
</script>
</body>
</html>
