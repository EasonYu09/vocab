[114NTU_vocab.html](https://github.com/user-attachments/files/27852476/114NTU_vocab.html)
# vocab<!DOCTYPE html>
<html lang="zh-TW">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>114 台大英文 A｜單字複習系統</title>
<style>
/* ===== DESIGN TOKENS ===== */
:root {
  --bg: #0d1117;
  --bg2: #161b22;
  --bg3: #21262d;
  --surface: #1c2128;
  --border: #30363d;
  --border-glow: rgba(88,166,255,0.3);
  --text: #e6edf3;
  --text-muted: #8b949e;
  --text-dim: #484f58;
  --accent: #58a6ff;
  --accent2: #bc8cff;
  --accent3: #3fb950;
  --danger: #f85149;
  --warn: #d29922;
  --card-flip: 0.5s;
  --radius: 14px;
  --radius-sm: 8px;
  --shadow: 0 8px 32px rgba(0,0,0,0.5);
  --shadow-lg: 0 16px 64px rgba(0,0,0,0.6);
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  font-family: 'Segoe UI', 'PingFang TC', 'Microsoft JhengHei', sans-serif;
  background: var(--bg);
  color: var(--text);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ===== LAYOUT ===== */
.app { display: flex; min-height: 100vh; }

/* ===== SIDEBAR NAV ===== */
.sidebar {
  width: 220px;
  min-height: 100vh;
  background: var(--bg2);
  border-right: 1px solid var(--border);
  display: flex;
  flex-direction: column;
  position: fixed;
  top: 0; left: 0;
  z-index: 100;
  transition: transform .3s;
}
.sidebar-logo {
  padding: 24px 20px 16px;
  border-bottom: 1px solid var(--border);
}
.sidebar-logo h1 {
  font-size: 15px; font-weight: 700;
  color: var(--accent);
  letter-spacing: .5px;
  line-height: 1.4;
}
.sidebar-logo p { font-size: 11px; color: var(--text-muted); margin-top: 2px; }

.nav-list { list-style: none; padding: 12px 0; flex: 1; }
.nav-item {
  display: flex; align-items: center; gap: 10px;
  padding: 10px 20px;
  cursor: pointer;
  font-size: 14px;
  color: var(--text-muted);
  border-left: 3px solid transparent;
  transition: all .2s;
}
.nav-item:hover { color: var(--text); background: var(--bg3); }
.nav-item.active {
  color: var(--accent);
  border-left-color: var(--accent);
  background: rgba(88,166,255,0.08);
}
.nav-icon { font-size: 18px; width: 24px; text-align: center; }

.sidebar-stats {
  padding: 16px 20px;
  border-top: 1px solid var(--border);
  font-size: 12px;
  color: var(--text-muted);
}
.stat-row { display: flex; justify-content: space-between; margin-bottom: 6px; }
.stat-val { color: var(--accent3); font-weight: 700; }

/* ===== MAIN ===== */
.main {
  margin-left: 220px;
  flex: 1;
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

.topbar {
  padding: 16px 32px;
  border-bottom: 1px solid var(--border);
  display: flex;
  align-items: center;
  justify-content: space-between;
  background: var(--bg2);
  position: sticky; top: 0; z-index: 50;
}
.topbar-title { font-size: 18px; font-weight: 700; }
.topbar-badges { display: flex; gap: 8px; }
.badge {
  padding: 3px 10px;
  border-radius: 20px;
  font-size: 11px;
  font-weight: 600;
  border: 1px solid;
}
.badge-blue { border-color: var(--accent); color: var(--accent); background: rgba(88,166,255,0.1); }
.badge-purple { border-color: var(--accent2); color: var(--accent2); background: rgba(188,140,255,0.1); }
.badge-green { border-color: var(--accent3); color: var(--accent3); background: rgba(63,185,80,0.1); }

.content { padding: 32px; flex: 1; }
.panel { display: none; }
.panel.active { display: block; }

/* ===== CARDS GENERAL ===== */
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 24px;
  box-shadow: var(--shadow);
}

/* ===== FLASHCARD ===== */
.fc-controls-top {
  display: flex; align-items: center; gap: 12px;
  margin-bottom: 24px; flex-wrap: wrap;
}
.fc-progress {
  font-size: 13px; color: var(--text-muted);
  margin-left: auto;
}
.fc-progress span { color: var(--accent); font-weight: 700; }

.fc-scene {
  width: 100%; max-width: 640px;
  margin: 0 auto 28px;
  height: 320px;
  perspective: 1200px;
  cursor: pointer;
}
.fc-card {
  width: 100%; height: 100%;
  position: relative;
  transform-style: preserve-3d;
  transition: transform var(--card-flip) cubic-bezier(.4,0,.2,1);
}
.fc-card.flipped { transform: rotateY(180deg); }
.fc-face {
  position: absolute;
  width: 100%; height: 100%;
  backface-visibility: hidden;
  border-radius: var(--radius);
  display: flex; flex-direction: column;
  align-items: center; justify-content: center;
  padding: 32px;
  border: 1px solid var(--border);
  background: var(--bg2);
  box-shadow: var(--shadow-lg);
}
.fc-front {
  background: linear-gradient(135deg, var(--bg2) 0%, #1a2332 100%);
  border-color: var(--border-glow);
}
.fc-back { transform: rotateY(180deg); background: var(--bg3); }

.fc-word {
  font-size: 42px; font-weight: 800;
  color: var(--text); letter-spacing: -1px;
  text-align: center; margin-bottom: 8px;
}
.fc-pos {
  font-size: 13px; color: var(--accent);
  background: rgba(88,166,255,0.1);
  padding: 3px 12px; border-radius: 20px;
  margin-bottom: 16px;
}
.fc-level {
  position: absolute; top: 16px; right: 16px;
}
.fc-hint { font-size: 12px; color: var(--text-dim); margin-top: 16px; }

.fc-meaning { font-size: 26px; font-weight: 700; color: var(--text); margin-bottom: 16px; text-align: center; }
.fc-example {
  font-size: 14px; color: var(--text-muted); text-align: center;
  font-style: italic; line-height: 1.6; margin-bottom: 6px;
}
.fc-translation { font-size: 13px; color: var(--text-dim); text-align: center; }

.fc-controls-bot {
  display: flex; justify-content: center; align-items: center;
  gap: 12px; flex-wrap: wrap;
}

.fc-audio-row {
  display: flex; justify-content: center; gap: 10px; margin-bottom: 12px;
}

/* ===== BUTTONS ===== */
.btn {
  display: inline-flex; align-items: center; gap: 6px;
  padding: 8px 18px;
  border-radius: var(--radius-sm);
  font-size: 14px; font-weight: 600;
  cursor: pointer; border: 1px solid;
  transition: all .18s;
  user-select: none;
}
.btn:active { transform: scale(.97); }
.btn-primary {
  background: var(--accent); color: #0d1117;
  border-color: var(--accent);
}
.btn-primary:hover { background: #79b8ff; }
.btn-outline {
  background: transparent; color: var(--text);
  border-color: var(--border);
}
.btn-outline:hover { border-color: var(--accent); color: var(--accent); background: rgba(88,166,255,0.06); }
.btn-ghost {
  background: transparent; color: var(--text-muted);
  border-color: transparent; padding: 8px 12px;
}
.btn-ghost:hover { color: var(--text); background: var(--bg3); }
.btn-green {
  background: var(--accent3); color: #0d1117;
  border-color: var(--accent3);
}
.btn-green:hover { background: #56d364; }
.btn-red {
  background: var(--danger); color: #fff;
  border-color: var(--danger);
}
.btn-red:hover { background: #ff6a6a; }
.btn-purple {
  background: var(--accent2); color: #0d1117;
  border-color: var(--accent2);
}
.btn-sm { padding: 5px 12px; font-size: 12px; }
.btn:disabled { opacity: .4; cursor: not-allowed; }

/* ===== FILL-IN-THE-BLANK ===== */
.quiz-header {
  display: flex; gap: 16px; margin-bottom: 24px; flex-wrap: wrap;
}
.quiz-stat {
  background: var(--bg3); border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 10px 20px; text-align: center;
}
.quiz-stat-label { font-size: 11px; color: var(--text-muted); }
.quiz-stat-val { font-size: 22px; font-weight: 800; color: var(--accent); }

.quiz-card { max-width: 640px; }
.quiz-prompt {
  font-size: 20px; line-height: 1.7;
  color: var(--text); margin-bottom: 20px;
  background: var(--bg3);
  border-radius: var(--radius-sm);
  padding: 20px 24px;
  border: 1px solid var(--border);
}
.blank {
  display: inline-block;
  min-width: 120px; border-bottom: 3px solid var(--accent);
  color: var(--accent); font-weight: 800;
  text-align: center; padding: 0 4px;
}
.quiz-translation {
  font-size: 13px; color: var(--text-muted);
  margin-bottom: 20px; padding-left: 4px;
}
.quiz-input-row { display: flex; gap: 10px; margin-bottom: 16px; }
.quiz-input {
  flex: 1;
  background: var(--bg3); border: 1px solid var(--border);
  color: var(--text); border-radius: var(--radius-sm);
  padding: 10px 16px; font-size: 16px;
  outline: none; transition: border .2s;
  font-family: inherit;
}
.quiz-input:focus { border-color: var(--accent); }
.quiz-input.correct { border-color: var(--accent3); background: rgba(63,185,80,.08); }
.quiz-input.wrong { border-color: var(--danger); background: rgba(248,81,73,.08); }

.quiz-feedback {
  padding: 14px 18px;
  border-radius: var(--radius-sm);
  font-size: 14px; margin-bottom: 16px;
  display: none;
}
.quiz-feedback.show { display: block; }
.quiz-feedback.correct { background: rgba(63,185,80,.1); border: 1px solid var(--accent3); color: var(--accent3); }
.quiz-feedback.wrong { background: rgba(248,81,73,.1); border: 1px solid var(--danger); color: var(--danger); }

/* ===== MATCH GAME ===== */
.match-header { display: flex; gap: 12px; margin-bottom: 20px; flex-wrap: wrap; align-items: center; }
.match-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 12px;
  max-width: 700px;
}
.match-col { display: flex; flex-direction: column; gap: 10px; }
.match-item {
  background: var(--bg3); border: 1px solid var(--border);
  border-radius: var(--radius-sm);
  padding: 12px 16px;
  cursor: pointer; font-size: 14px;
  transition: all .18s;
  min-height: 52px;
  display: flex; align-items: center;
  user-select: none;
}
.match-item:hover:not(.matched):not(.disabled) {
  border-color: var(--accent); background: rgba(88,166,255,0.06);
}
.match-item.selected { border-color: var(--accent2); background: rgba(188,140,255,.1); color: var(--accent2); }
.match-item.matched { border-color: var(--accent3); background: rgba(63,185,80,.08); color: var(--accent3); opacity: .7; cursor: default; }
.match-item.error { border-color: var(--danger); background: rgba(248,81,73,.08); animation: shake .3s; }
@keyframes shake { 0%,100%{transform:translateX(0)} 25%{transform:translateX(-6px)} 75%{transform:translateX(6px)} }

/* ===== SLEEP TIMER ===== */
.sleep-layout { display: grid; grid-template-columns: 1fr 1fr; gap: 24px; max-width: 800px; }
.sleep-display {
  grid-column: 1 / -1;
  background: var(--bg2);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 32px;
  text-align: center;
}
.sleep-timer {
  font-size: 72px; font-weight: 900;
  color: var(--accent);
  font-variant-numeric: tabular-nums;
  letter-spacing: -2px;
  line-height: 1;
  margin-bottom: 12px;
  font-family: 'Courier New', monospace;
}
.sleep-now-word { font-size: 18px; color: var(--text-muted); margin-bottom: 4px; }
.sleep-now-meaning { font-size: 14px; color: var(--text-dim); }
.sleep-progress-bar {
  width: 100%; height: 4px;
  background: var(--border);
  border-radius: 2px; margin-top: 20px; overflow: hidden;
}
.sleep-progress-fill {
  height: 100%; background: var(--accent);
  border-radius: 2px; transition: width 1s linear;
}

.sleep-config label { display: block; font-size: 13px; color: var(--text-muted); margin-bottom: 6px; }
.sleep-config select, .sleep-config input[type=number], .sleep-config input[type=range] {
  width: 100%;
  background: var(--bg3); border: 1px solid var(--border);
  color: var(--text); border-radius: var(--radius-sm);
  padding: 8px 12px; font-size: 14px; font-family: inherit;
  outline: none; margin-bottom: 14px;
}
.sleep-config select:focus, .sleep-config input:focus { border-color: var(--accent); }
.sleep-btn-row { display: flex; gap: 10px; flex-wrap: wrap; margin-top: 12px; }

/* ===== SEARCH & BROWSE ===== */
.search-bar {
  display: flex; gap: 10px; margin-bottom: 16px; flex-wrap: wrap;
}
.search-input {
  flex: 1; min-width: 200px;
  background: var(--bg3); border: 1px solid var(--border);
  color: var(--text); border-radius: var(--radius-sm);
  padding: 10px 16px; font-size: 14px; font-family: inherit;
  outline: none;
}
.search-input:focus { border-color: var(--accent); }
.filter-group { display: flex; gap: 8px; flex-wrap: wrap; }
.filter-btn {
  padding: 6px 14px; font-size: 12px; font-weight: 600;
  border-radius: 20px; border: 1px solid var(--border);
  background: transparent; color: var(--text-muted);
  cursor: pointer; transition: all .18s;
}
.filter-btn.active { border-color: var(--accent); color: var(--accent); background: rgba(88,166,255,.1); }
.filter-btn:hover { border-color: var(--accent); color: var(--accent); }

.word-table { width: 100%; border-collapse: collapse; font-size: 14px; }
.word-table th {
  text-align: left; padding: 10px 14px;
  color: var(--text-muted); font-size: 12px; font-weight: 600;
  border-bottom: 1px solid var(--border);
  letter-spacing: .5px; text-transform: uppercase;
}
.word-table td { padding: 10px 14px; border-bottom: 1px solid rgba(48,54,61,.5); vertical-align: middle; }
.word-table tr:hover td { background: rgba(88,166,255,.03); }
.word-en { font-weight: 700; color: var(--text); }
.word-pos { color: var(--accent); font-size: 12px; }
.word-cn { color: var(--text-muted); }
.word-ex { font-size: 12px; color: var(--text-dim); font-style: italic; max-width: 280px; }
.search-count { font-size: 13px; color: var(--text-muted); margin-bottom: 12px; }
.search-count span { color: var(--accent); font-weight: 700; }

/* ===== SETTINGS ===== */
.settings-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(300px, 1fr)); gap: 20px; max-width: 800px; }
.settings-section-title { font-size: 11px; text-transform: uppercase; letter-spacing: 1px; color: var(--text-muted); margin-bottom: 16px; font-weight: 700; }
.setting-row { margin-bottom: 18px; }
.setting-row label { display: flex; justify-content: space-between; font-size: 14px; color: var(--text); margin-bottom: 8px; }
.setting-row label span { color: var(--accent); font-weight: 700; }
.setting-row input[type=range] { width: 100%; accent-color: var(--accent); }
.settings-actions { margin-top: 24px; display: flex; gap: 10px; flex-wrap: wrap; }

/* ===== PROGRESS RING ===== */
.progress-ring-wrap { display: flex; align-items: center; gap: 16px; }
.progress-ring { transform: rotate(-90deg); }
.ring-track { fill: none; stroke: var(--border); }
.ring-fill { fill: none; stroke: var(--accent3); stroke-linecap: round; transition: stroke-dashoffset .6s; }

/* ===== BADGE LEVEL ===== */
.lv-初級 { background: rgba(63,185,80,.15); color: var(--accent3); border: 1px solid rgba(63,185,80,.3); padding: 2px 8px; border-radius: 10px; font-size: 11px; }
.lv-中級 { background: rgba(88,166,255,.15); color: var(--accent); border: 1px solid rgba(88,166,255,.3); padding: 2px 8px; border-radius: 10px; font-size: 11px; }
.lv-高級 { background: rgba(188,140,255,.15); color: var(--accent2); border: 1px solid rgba(188,140,255,.3); padding: 2px 8px; border-radius: 10px; font-size: 11px; }

/* ===== TOAST ===== */
.toast {
  position: fixed; bottom: 24px; right: 24px;
  background: var(--bg3); border: 1px solid var(--border);
  color: var(--text); padding: 12px 20px;
  border-radius: var(--radius-sm); font-size: 14px;
  box-shadow: var(--shadow); z-index: 9999;
  transform: translateY(20px); opacity: 0;
  transition: all .3s; pointer-events: none;
}
.toast.show { transform: translateY(0); opacity: 1; }

/* ===== MOBILE ===== */
.menu-toggle {
  display: none; background: none; border: none;
  color: var(--text); font-size: 22px; cursor: pointer;
  padding: 4px;
}
@media (max-width: 768px) {
  .sidebar { transform: translateX(-100%); }
  .sidebar.open { transform: translateX(0); }
  .main { margin-left: 0; }
  .menu-toggle { display: block; }
  .fc-word { font-size: 28px; }
  .fc-scene { height: 260px; }
  .sleep-layout { grid-template-columns: 1fr; }
  .sleep-timer { font-size: 56px; }
  .match-grid { grid-template-columns: 1fr; }
  .content { padding: 20px; }
  .topbar { padding: 12px 20px; }
}
.overlay {
  display: none; position: fixed; inset: 0;
  background: rgba(0,0,0,.6); z-index: 99;
}
.overlay.show { display: block; }
</style>
</head>
<body>

<div class="overlay" id="overlay" onclick="closeSidebar()"></div>
<div class="toast" id="toast"></div>

<div class="app">
<!-- ===== SIDEBAR ===== -->
<nav class="sidebar" id="sidebar">
  <div class="sidebar-logo">
    <h1>114 台大英文 A</h1>
    <p>單字複習系統</p>
  </div>
  <ul class="nav-list">
    <li class="nav-item active" onclick="showPanel('flashcard')" data-panel="flashcard">
      <span class="nav-icon">🃏</span> 單字卡
    </li>
    <li class="nav-item" onclick="showPanel('quiz')" data-panel="quiz">
      <span class="nav-icon">✏️</span> 填空測驗
    </li>
    <li class="nav-item" onclick="showPanel('match')" data-panel="match">
      <span class="nav-icon">🔗</span> 配對測驗
    </li>
    <li class="nav-item" onclick="showPanel('sleep')" data-panel="sleep">
      <span class="nav-icon">🌙</span> 睡眠複習
    </li>
    <li class="nav-item" onclick="showPanel('browse')" data-panel="browse">
      <span class="nav-icon">🔍</span> 搜尋瀏覽
    </li>
    <li class="nav-item" onclick="showPanel('settings')" data-panel="settings">
      <span class="nav-icon">⚙️</span> 設定
    </li>
  </ul>
  <div class="sidebar-stats">
    <div class="stat-row"><span>總單字數</span><span class="stat-val" id="stat-total">145</span></div>
    <div class="stat-row"><span>已熟</span><span class="stat-val" id="stat-mastered">0</span></div>
    <div class="stat-row"><span>測驗正確率</span><span class="stat-val" id="stat-acc">—</span></div>
  </div>
</nav>

<!-- ===== MAIN ===== -->
<div class="main">
  <div class="topbar">
    <div style="display:flex;align-items:center;gap:12px">
      <button class="menu-toggle" onclick="toggleSidebar()">☰</button>
      <span class="topbar-title" id="topbar-title">單字卡</span>
    </div>
    <div class="topbar-badges">
      <span class="badge badge-green" id="badge-mastered">已熟 0</span>
      <span class="badge badge-blue" id="badge-total">共 145 字</span>
    </div>
  </div>

  <div class="content">

    <!-- ===== FLASHCARD PANEL ===== -->
    <div class="panel active" id="panel-flashcard">
      <div class="fc-controls-top">
        <button class="btn btn-outline btn-sm" onclick="toggleShowMastered()">
          <span id="show-mastered-txt">🙈 隱藏已熟</span>
        </button>
        <button class="btn btn-outline btn-sm" onclick="shuffleFlashcards()">🔀 隨機</button>
        <button class="btn btn-outline btn-sm" onclick="resetFlashcards()">↺ 重置順序</button>
        <span class="fc-progress">
          <span id="fc-cur">1</span> / <span id="fc-total">145</span>
        </span>
      </div>

      <div class="fc-scene" onclick="flipCard()">
        <div class="fc-card" id="fc-card">
          <div class="fc-face fc-front">
            <span class="fc-level" id="fc-level-badge"></span>
            <div class="fc-pos" id="fc-pos">v. 動詞</div>
            <div class="fc-word" id="fc-word">resign</div>
            <div class="fc-hint">點擊翻面查看中文</div>
          </div>
          <div class="fc-face fc-back">
            <div class="fc-meaning" id="fc-meaning">辭職；放棄職位</div>
            <div class="fc-audio-row">
              <button class="btn btn-outline btn-sm" onclick="event.stopPropagation();speakWord()">🔊 單字</button>
              <button class="btn btn-outline btn-sm" onclick="event.stopPropagation();speakExample()">🔊 例句</button>
            </div>
            <div class="fc-example" id="fc-example">She decided to resign from her job due to stress.</div>
            <div class="fc-translation" id="fc-translation">她因為壓力而決定辭職。</div>
          </div>
        </div>
      </div>

      <div class="fc-controls-bot">
        <button class="btn btn-outline" onclick="prevCard()">← 上一張</button>
        <button class="btn btn-primary" onclick="nextCard()">下一張 →</button>
        <button class="btn btn-green" onclick="markMastered()" id="btn-mastered">✓ 標記已熟</button>
        <button class="btn btn-ghost" onclick="speakWord()">🔊</button>
      </div>
    </div>

    <!-- ===== QUIZ PANEL ===== -->
    <div class="panel" id="panel-quiz">
      <div class="quiz-header">
        <div class="quiz-stat"><div class="quiz-stat-label">得分</div><div class="quiz-stat-val" id="q-score">0</div></div>
        <div class="quiz-stat"><div class="quiz-stat-label">答題數</div><div class="quiz-stat-val" id="q-total">0</div></div>
        <div class="quiz-stat"><div class="quiz-stat-label">正確率</div><div class="quiz-stat-val" id="q-acc">—</div></div>
        <button class="btn btn-outline btn-sm" style="margin-left:auto;align-self:center" onclick="resetQuiz()">↺ 重新開始</button>
      </div>

      <div class="card quiz-card">
        <div class="quiz-prompt" id="q-prompt">載入中…</div>
        <div class="quiz-translation" id="q-zh"></div>
        <div class="quiz-input-row">
          <input class="quiz-input" id="q-input" placeholder="輸入答案…" autocomplete="off"
            onkeydown="if(event.key==='Enter')submitQuiz()">
          <button class="btn btn-primary" onclick="submitQuiz()">送出</button>
        </div>
        <div class="quiz-feedback" id="q-feedback"></div>
        <div style="display:flex;gap:10px;flex-wrap:wrap">
          <button class="btn btn-outline btn-sm" id="q-next-btn" onclick="nextQuiz()" style="display:none">下一題 →</button>
          <button class="btn btn-ghost btn-sm" onclick="skipQuiz()">略過</button>
          <button class="btn btn-ghost btn-sm" onclick="speakQuizExample()">🔊 聽例句</button>
        </div>
      </div>
    </div>

    <!-- ===== MATCH PANEL ===== -->
    <div class="panel" id="panel-match">
      <div class="match-header">
        <div class="quiz-stat"><div class="quiz-stat-label">完成</div><div class="quiz-stat-val" id="m-done">0</div></div>
        <div class="quiz-stat"><div class="quiz-stat-label">錯誤</div><div class="quiz-stat-val" id="m-errors" style="color:var(--danger)">0</div></div>
        <button class="btn btn-outline btn-sm" onclick="loadMatchRound()">↺ 換一組</button>
        <span id="m-complete-msg" style="color:var(--accent3);font-weight:700;display:none">✓ 完成！</span>
      </div>
      <div class="match-grid" id="match-grid"></div>
    </div>

    <!-- ===== SLEEP PANEL ===== -->
    <div class="panel" id="panel-sleep">
      <div class="sleep-layout">
        <div class="sleep-display">
          <div class="sleep-timer" id="sleep-timer">00:00</div>
          <div class="sleep-now-word" id="sleep-word">—</div>
          <div class="sleep-now-meaning" id="sleep-meaning">設定後開始複習</div>
          <div class="sleep-progress-bar"><div class="sleep-progress-fill" id="sleep-pbar" style="width:100%"></div></div>
        </div>

        <div class="card sleep-config">
          <div class="settings-section-title">播放設定</div>
          <label>播放時間（分鐘）</label>
          <select id="sleep-duration">
            <option value="5">5 分鐘</option>
            <option value="10">10 分鐘</option>
            <option value="15" selected>15 分鐘</option>
            <option value="30">30 分鐘</option>
            <option value="60">60 分鐘</option>
            <option value="custom">自訂…</option>
          </select>
          <input type="number" id="sleep-custom" placeholder="自訂分鐘數" min="1" max="180" style="display:none">
          <label>每字重複次數</label>
          <select id="sleep-repeat">
            <option value="1">1 次</option>
            <option value="2" selected>2 次</option>
            <option value="3">3 次</option>
            <option value="5">5 次</option>
          </select>
          <label style="display:flex;align-items:center;gap:8px;cursor:pointer">
            <input type="checkbox" id="sleep-shuffle" checked> 隨機播放
          </label>
          <div class="sleep-btn-row">
            <button class="btn btn-primary" onclick="startSleep()">▶ 開始</button>
            <button class="btn btn-outline" onclick="pauseSleep()" id="sleep-pause-btn" disabled>⏸ 暫停</button>
            <button class="btn btn-red btn-sm" onclick="stopSleep()" id="sleep-stop-btn" disabled>■ 停止</button>
          </div>
        </div>

        <div class="card sleep-config">
          <div class="settings-section-title">播放選項</div>
          <label>語速 <span id="sleep-rate-val">0.85</span></label>
          <input type="range" id="sleep-rate" min="0.5" max="1.5" step="0.05" value="0.85"
            oninput="document.getElementById('sleep-rate-val').textContent=this.value">
          <label>間隔時間（秒）</label>
          <select id="sleep-gap">
            <option value="1000">1 秒</option>
            <option value="1500" selected>1.5 秒</option>
            <option value="2000">2 秒</option>
            <option value="3000">3 秒</option>
          </select>
          <label style="display:flex;align-items:center;gap:8px;cursor:pointer">
            <input type="checkbox" id="sleep-include-sentence" checked> 播放例句
          </label>
        </div>
      </div>
    </div>

    <!-- ===== BROWSE PANEL ===== -->
    <div class="panel" id="panel-browse">
      <div class="search-bar">
        <input class="search-input" id="search-input" placeholder="搜尋英文、中文、例句…"
          oninput="renderBrowse()">
      </div>
      <div class="filter-group" style="margin-bottom:10px">
        <span style="font-size:12px;color:var(--text-muted);align-self:center">難度：</span>
        <button class="filter-btn active" data-level="all" onclick="setFilter('level','all',this)">全部</button>
        <button class="filter-btn" data-level="初級" onclick="setFilter('level','初級',this)">初級</button>
        <button class="filter-btn" data-level="中級" onclick="setFilter('level','中級',this)">中級</button>
        <button class="filter-btn" data-level="高級" onclick="setFilter('level','高級',this)">高級</button>
      </div>
      <div class="filter-group" style="margin-bottom:16px">
        <span style="font-size:12px;color:var(--text-muted);align-self:center">詞性：</span>
        <button class="filter-btn active" data-pos="all" onclick="setFilter('pos','all',this)">全部</button>
        <button class="filter-btn" data-pos="動詞" onclick="setFilter('pos','動詞',this)">動詞</button>
        <button class="filter-btn" data-pos="名詞" onclick="setFilter('pos','名詞',this)">名詞</button>
        <button class="filter-btn" data-pos="形容詞" onclick="setFilter('pos','形容詞',this)">形容詞</button>
        <button class="filter-btn" data-pos="副詞" onclick="setFilter('pos','副詞',this)">副詞</button>
        <button class="filter-btn" data-pos="片語" onclick="setFilter('pos','片語',this)">片語</button>
      </div>
      <div class="search-count">找到 <span id="browse-count">145</span> 筆</div>
      <div style="overflow-x:auto">
        <table class="word-table">
          <thead><tr>
            <th>單字</th><th>詞性</th><th>中文</th><th>難度</th><th>例句</th><th>操作</th>
          </tr></thead>
          <tbody id="browse-tbody"></tbody>
        </table>
      </div>
    </div>

    <!-- ===== SETTINGS PANEL ===== -->
    <div class="panel" id="panel-settings">
      <div class="settings-grid">
        <div class="card">
          <div class="settings-section-title">發音設定</div>
          <div class="setting-row">
            <label>語速 <span id="s-rate-val">0.9</span></label>
            <input type="range" id="s-rate" min="0.5" max="2" step="0.05" value="0.9"
              oninput="updateSetting('rate',this.value,'s-rate-val')">
          </div>
          <div class="setting-row">
            <label>音量 <span id="s-vol-val">1.0</span></label>
            <input type="range" id="s-vol" min="0" max="1" step="0.1" value="1"
              oninput="updateSetting('volume',this.value,'s-vol-val')">
          </div>
          <div class="setting-row">
            <label>音高 <span id="s-pitch-val">1.0</span></label>
            <input type="range" id="s-pitch" min="0.5" max="2" step="0.1" value="1"
              oninput="updateSetting('pitch',this.value,'s-pitch-val')">
          </div>
          <button class="btn btn-outline btn-sm" onclick="testSpeech()">🔊 測試發音</button>
        </div>

        <div class="card">
          <div class="settings-section-title">學習偏好</div>
          <div class="setting-row" style="display:flex;align-items:center;gap:10px;margin-bottom:14px">
            <input type="checkbox" id="s-random" style="accent-color:var(--accent)">
            <label for="s-random" style="cursor:pointer;font-size:14px">單字卡隨機順序</label>
          </div>
          <div class="setting-row" style="display:flex;align-items:center;gap:10px;margin-bottom:14px">
            <input type="checkbox" id="s-hide-mastered" style="accent-color:var(--accent)">
            <label for="s-hide-mastered" style="cursor:pointer;font-size:14px">預設隱藏已熟單字</label>
          </div>
        </div>

        <div class="card">
          <div class="settings-section-title">學習統計</div>
          <div style="display:flex;flex-direction:column;gap:10px">
            <div class="stat-row" style="font-size:14px">
              <span>已熟單字數</span><span class="stat-val" id="settings-mastered-count">0</span>
            </div>
            <div class="stat-row" style="font-size:14px">
              <span>填空答題總數</span><span class="stat-val" id="settings-quiz-total">0</span>
            </div>
            <div class="stat-row" style="font-size:14px">
              <span>填空答對總數</span><span class="stat-val" id="settings-quiz-correct">0</span>
            </div>
            <div class="stat-row" style="font-size:14px">
              <span>配對總錯誤次數</span><span class="stat-val" id="settings-match-errors">0</span>
            </div>
          </div>
        </div>
      </div>
      <div class="settings-actions">
        <button class="btn btn-outline" onclick="saveSettings()">💾 儲存設定</button>
        <button class="btn btn-red btn-sm" onclick="clearMastered()">清除已熟記錄</button>
        <button class="btn btn-red btn-sm" onclick="clearStats()">清除測驗記錄</button>
      </div>
    </div>

  </div><!-- /content -->
</div><!-- /main -->
</div><!-- /app -->

<script>
/* ========================================================
   ▼ 單字資料庫 — 145 個單字
   ======================================================== */
const vocabularyData = [
  { word:"resign", partOfSpeech:"v. 動詞", meaning:"辭職；放棄職位", example:"She decided to resign from her job due to stress.", translation:"她因為壓力而決定辭職。", level:"中級" },
  { word:"persist", partOfSpeech:"v. 動詞", meaning:"持續存在；堅持", example:"He persisted in asking the same question.", translation:"他堅持問同樣的問題。", level:"中級" },
  { word:"acquire", partOfSpeech:"v. 動詞", meaning:"取得；學得", example:"She acquired fluency in French through years of study.", translation:"她經過多年學習習得了流利的法語。", level:"中級" },
  { word:"step down", partOfSpeech:"phr. 片語", meaning:"下台；辭職", example:"The manager will step down at the end of the year.", translation:"經理將於年底卸任。", level:"中級" },
  { word:"confidential", partOfSpeech:"adj. 形容詞", meaning:"機密的；保密的", example:"He shared some confidential documents with his lawyer.", translation:"他與律師分享了一些機密文件。", level:"中級" },
  { word:"fall into the wrong hands", partOfSpeech:"phr. 片語", meaning:"落入壞人手中", example:"The data must not fall into the wrong hands.", translation:"這些資料絕不能落入壞人手中。", level:"中級" },
  { word:"peer into", partOfSpeech:"phr. 片語", meaning:"仔細看進去／穿過", example:"She peered into the dark room, trying to see who was inside.", translation:"她往黑暗的房間裡窺視，試圖看清裡面是誰。", level:"中級" },
  { word:"stare", partOfSpeech:"v. 動詞", meaning:"盯著看；凝視", example:"Don't stare at people—it's rude.", translation:"不要盯著人看——這很沒禮貌。", level:"初級" },
  { word:"assume", partOfSpeech:"v. 動詞", meaning:"假設；承擔", example:"We shouldn't assume he's guilty without proof.", translation:"我們不應該在沒有證據的情況下假定他有罪。", level:"中級" },
  { word:"oversee", partOfSpeech:"v. 動詞", meaning:"監督；管理", example:"She was hired to oversee the construction project.", translation:"她被雇用來監督建築工程。", level:"中級" },
  { word:"delegate", partOfSpeech:"v. 動詞", meaning:"委派；授權", example:"The manager delegated tasks to her assistant.", translation:"經理把任務委派給了助理。", level:"中級" },
  { word:"neglect", partOfSpeech:"v. 動詞", meaning:"忽視；疏忽", example:"He neglected his health for years.", translation:"他多年來忽視自己的健康。", level:"中級" },
  { word:"refine", partOfSpeech:"v. 動詞", meaning:"改進；精煉", example:"The company is refining its hiring process.", translation:"公司正在改進其招聘流程。", level:"中級" },
  { word:"refine one's ideas", partOfSpeech:"phr. 片語", meaning:"修正想法；精煉概念", example:"After feedback, she refined her ideas for the project.", translation:"在收到回饋後，她精煉了自己的企劃想法。", level:"中級" },
  { word:"discard", partOfSpeech:"v. 動詞", meaning:"丟棄；拋棄", example:"Please discard any outdated materials.", translation:"請丟棄所有過時的資料。", level:"中級" },
  { word:"deduce", partOfSpeech:"v. 動詞", meaning:"推斷；演繹", example:"We can deduce from the evidence that he was present.", translation:"我們可以從證據推斷他當時在場。", level:"高級" },
  { word:"obliterate", partOfSpeech:"v. 動詞", meaning:"徹底摧毀；抹去", example:"The explosion obliterated the building completely.", translation:"爆炸完全摧毀了那棟建築。", level:"高級" },
  { word:"evoke", partOfSpeech:"v. 動詞", meaning:"喚起（情感或記憶）", example:"The music evoked memories of her childhood.", translation:"這音樂喚起了她童年的回憶。", level:"中級" },
  { word:"deter", partOfSpeech:"v. 動詞", meaning:"嚇阻；阻止", example:"High fines are meant to deter speeding.", translation:"高額罰款旨在嚇阻超速行為。", level:"中級" },
  { word:"trivial", partOfSpeech:"adj. 形容詞", meaning:"微不足道的；瑣碎的", example:"Let's not argue over trivial matters.", translation:"我們別為瑣事爭吵了。", level:"中級" },
  { word:"erudite", partOfSpeech:"adj. 形容詞", meaning:"博學的", example:"The professor was known for his erudite lectures.", translation:"這位教授以博學的演講著稱。", level:"高級" },
  { word:"superficial", partOfSpeech:"adj. 形容詞", meaning:"表面的；膚淺的", example:"She made a superficial analysis of the issue.", translation:"她對這個問題做了膚淺的分析。", level:"中級" },
  { word:"stance", partOfSpeech:"n. 名詞", meaning:"立場；態度", example:"His stance on climate change is very progressive.", translation:"他在氣候變遷上的立場非常進步。", level:"中級" },
  { word:"decisive", partOfSpeech:"adj. 形容詞", meaning:"果斷的；決定性的", example:"Her decisive response ended the debate.", translation:"她果斷的回應結束了辯論。", level:"中級" },
  { word:"ambiguous", partOfSpeech:"adj. 形容詞", meaning:"模稜兩可的；不明確的", example:"His answer was ambiguous and confusing.", translation:"他的回答模稜兩可且令人困惑。", level:"中級" },
  { word:"explicit", partOfSpeech:"adj. 形容詞", meaning:"明確的；直白的", example:"The instructions were explicit and easy to follow.", translation:"這些指示很明確，易於遵循。", level:"中級" },
  { word:"transparent", partOfSpeech:"adj. 形容詞", meaning:"透明的；公開的", example:"We value transparent communication at work.", translation:"我們重視職場上公開的溝通。", level:"中級" },
  { word:"precise", partOfSpeech:"adj. 形容詞", meaning:"精確的；準確的", example:"She gave a precise description of the suspect.", translation:"她提供了對嫌犯精確的描述。", level:"中級" },
  { word:"casual", partOfSpeech:"adj. 形容詞", meaning:"隨意的；輕鬆的", example:"He wore casual clothes to the meeting.", translation:"他穿著便服參加會議。", level:"初級" },
  { word:"archaic", partOfSpeech:"adj. 形容詞", meaning:"古老的；過時的", example:"Some laws still use archaic language.", translation:"有些法律仍使用過時的語言。", level:"高級" },
  { word:"contemporary", partOfSpeech:"adj. 形容詞", meaning:"當代的；現代的", example:"This exhibition showcases contemporary art.", translation:"這個展覽展示了當代藝術。", level:"中級" },
  { word:"demeanor", partOfSpeech:"n. 名詞", meaning:"舉止；態度", example:"His calm demeanor impressed the interviewers.", translation:"他冷靜的舉止給面試官留下深刻印象。", level:"高級" },
  { word:"intimidate", partOfSpeech:"v. 動詞", meaning:"恐嚇；威嚇", example:"The large dog intimidated the children.", translation:"那隻大狗嚇到了小孩們。", level:"中級" },
  { word:"austere", partOfSpeech:"adj. 形容詞", meaning:"嚴厲的；樸素的", example:"The monk lived an austere life in the mountains.", translation:"那位和尚在山中過著簡樸的生活。", level:"高級" },
  { word:"gregarious", partOfSpeech:"adj. 形容詞", meaning:"愛交際的；群居的", example:"She is gregarious and loves going to parties.", translation:"她很愛社交，也愛參加派對。", level:"高級" },
  { word:"indulgent", partOfSpeech:"adj. 形容詞", meaning:"縱容的；溺愛的", example:"His indulgent parents never said no to him.", translation:"他那溺愛的父母從不拒絕他。", level:"高級" },
  { word:"negligent", partOfSpeech:"adj. 形容詞", meaning:"疏忽的；粗心的", example:"The accident happened because the guard was negligent.", translation:"事故是因為警衛疏忽所致。", level:"中級" },
  { word:"lethargic", partOfSpeech:"adj. 形容詞", meaning:"無精打采的；昏昏欲睡的", example:"She felt lethargic after staying up all night.", translation:"她熬夜後感到昏昏沉沉。", level:"高級" },
  { word:"herculean", partOfSpeech:"adj. 形容詞", meaning:"艱鉅的；力大無比的", example:"Cleaning up after the flood was a herculean task.", translation:"洪水過後的清理工作是一項艱鉅任務。", level:"高級" },
  { word:"compatible", partOfSpeech:"adj. 形容詞", meaning:"相容的；合得來的", example:"This software is compatible with most systems.", translation:"這款軟體與大多數系統相容。", level:"中級" },
  { word:"harmonious", partOfSpeech:"adj. 形容詞", meaning:"和諧的；協調的", example:"They have a harmonious relationship.", translation:"他們關係和諧。", level:"中級" },
  { word:"complementary", partOfSpeech:"adj. 形容詞", meaning:"互補的", example:"Their skills are complementary in the team.", translation:"他們在團隊中的技能是互補的。", level:"高級" },
  { word:"precedent", partOfSpeech:"n. 名詞", meaning:"先例；前例", example:"This case could set a legal precedent.", translation:"這個案例可能會成為法律上的先例。", level:"中級" },
  { word:"conjecture", partOfSpeech:"n. 名詞", meaning:"推測；猜想", example:"His theory is based on pure conjecture.", translation:"他的理論完全是推測。", level:"高級" },
  { word:"speculation", partOfSpeech:"n. 名詞", meaning:"猜測；推測", example:"There is speculation about the company's future.", translation:"外界對這家公司的未來有很多猜測。", level:"中級" },
  { word:"anomaly", partOfSpeech:"n. 名詞", meaning:"異常；反常事物", example:"This result is an anomaly and needs further study.", translation:"這個結果很反常，需要進一步研究。", level:"高級" },
  { word:"tranquility", partOfSpeech:"n. 名詞", meaning:"寧靜；平靜", example:"She enjoyed the tranquility of the countryside.", translation:"她喜歡鄉村的寧靜。", level:"高級" },
  { word:"compliance", partOfSpeech:"n. 名詞", meaning:"遵守；服從", example:"The company was fined for lack of compliance.", translation:"公司因未遵守規定而被罰款。", level:"中級" },
  { word:"uproar", partOfSpeech:"n. 名詞", meaning:"喧囂；騷動", example:"The decision caused public uproar.", translation:"這項決定引起了民眾的騷動。", level:"中級" },
  { word:"concord", partOfSpeech:"n. 名詞", meaning:"一致；和睦", example:"The two nations lived in concord for decades.", translation:"兩國和平共處數十年。", level:"高級" },
  { word:"rebuttal", partOfSpeech:"n. 名詞", meaning:"反駁；辯駁", example:"She gave a strong rebuttal to the accusation.", translation:"她對指控提出了有力的反駁。", level:"高級" },
  { word:"endorsement", partOfSpeech:"n. 名詞", meaning:"背書；支持", example:"The product received celebrity endorsement.", translation:"這項產品獲得名人背書。", level:"中級" },
  { word:"consensus", partOfSpeech:"n. 名詞", meaning:"共識", example:"There was a general consensus on the plan.", translation:"大家對這項計劃大致達成共識。", level:"中級" },
  { word:"conformity", partOfSpeech:"n. 名詞", meaning:"一致；從眾", example:"The school encourages creativity over conformity.", translation:"這所學校鼓勵創造力而非盲從。", level:"高級" },
  { word:"unforeseen", partOfSpeech:"adj. 形容詞", meaning:"意料之外的", example:"They were unprepared for the unforeseen expenses.", translation:"他們對這些突如其來的費用毫無準備。", level:"中級" },
  { word:"make do with", partOfSpeech:"phr. 片語", meaning:"將就使用；湊合應付", example:"We'll have to make do with what we have.", translation:"我們只好將就現有的東西。", level:"中級" },
  { word:"turn down", partOfSpeech:"phr. 片語", meaning:"拒絕", example:"She turned down the job offer.", translation:"她拒絕了那份工作邀請。", level:"初級" },
  { word:"fall through", partOfSpeech:"phr. 片語", meaning:"落空；失敗", example:"Our vacation plans fell through last minute.", translation:"我們的假期計劃在最後一刻泡湯了。", level:"中級" },
  { word:"put up with", partOfSpeech:"phr. 片語", meaning:"忍受；容忍", example:"I can't put up with this noise anymore.", translation:"我再也無法忍受這種噪音了。", level:"中級" },
  { word:"put out", partOfSpeech:"phr. 片語", meaning:"熄滅；發行；使不方便", example:"They quickly put out the fire.", translation:"他們迅速撲滅了火勢。", level:"中級" },
  { word:"consequences", partOfSpeech:"n. 名詞", meaning:"後果；結果", example:"He didn't consider the consequences of his actions.", translation:"他沒有考慮自己行為的後果。", level:"初級" },
  { word:"impetuously", partOfSpeech:"adv. 副詞", meaning:"衝動地；魯莽地", example:"She impetuously quit her job without another offer.", translation:"她衝動地辭掉工作，卻沒有其他工作機會。", level:"高級" },
  { word:"cautiously", partOfSpeech:"adv. 副詞", meaning:"謹慎地；小心地", example:"He cautiously entered the dark room.", translation:"他小心翼翼地走進黑暗的房間。", level:"中級" },
  { word:"consciously", partOfSpeech:"adv. 副詞", meaning:"有意識地；故意地", example:"She consciously avoided discussing politics.", translation:"她有意避開政治話題。", level:"中級" },
  { word:"deliberately", partOfSpeech:"adv. 副詞", meaning:"故意地；慎重地", example:"He deliberately ignored the warning signs.", translation:"他故意忽略那些警告標誌。", level:"中級" },
  { word:"seamless", partOfSpeech:"adj. 形容詞", meaning:"無縫的；順暢的", example:"The transition was seamless and went unnoticed.", translation:"過渡非常順利，幾乎沒人察覺。", level:"中級" },
  { word:"flippantly", partOfSpeech:"adv. 副詞", meaning:"輕率地；無禮地", example:"He answered flippantly during the serious discussion.", translation:"他在嚴肅討論中輕率地作答。", level:"高級" },
  { word:"masterfully", partOfSpeech:"adv. 副詞", meaning:"巧妙地；技藝高超地", example:"The artist painted the scene masterfully.", translation:"這位藝術家巧妙地描繪了這個場景。", level:"高級" },
  { word:"oversight", partOfSpeech:"n. 名詞", meaning:"疏忽；監督", example:"Due to an oversight, the form wasn't submitted.", translation:"由於疏忽，表格沒有被提交。", level:"中級" },
  { word:"maliciously", partOfSpeech:"adv. 副詞", meaning:"惡意地", example:"The software was maliciously designed to steal data.", translation:"這個軟體是為了竊取資料而惡意設計的。", level:"高級" },
  { word:"antecedent", partOfSpeech:"n. 名詞", meaning:"前事；先例；先行詞", example:"Historical antecedents help us understand current events.", translation:"歷史的先例有助於我們理解當前事件。", level:"高級" },
  { word:"bias", partOfSpeech:"n. 名詞", meaning:"偏見；偏好", example:"She tried to write the article without bias.", translation:"她試著客觀地撰寫這篇文章。", level:"中級" },
  { word:"exacerbate", partOfSpeech:"v. 動詞", meaning:"惡化；加劇", example:"The drought exacerbated the food shortage.", translation:"乾旱加劇了糧食短缺的問題。", level:"高級" },
  { word:"eradication", partOfSpeech:"n. 名詞", meaning:"根除；消滅", example:"The eradication of smallpox was a medical breakthrough.", translation:"天花的根除是一項醫學突破。", level:"高級" },
  { word:"presence", partOfSpeech:"n. 名詞", meaning:"出現；存在", example:"The presence of police calmed the crowd.", translation:"警方的出現讓群眾冷靜下來。", level:"初級" },
  { word:"obscure", partOfSpeech:"v./adj. 動詞／形容詞", meaning:"使模糊／模糊的；鮮為人知的", example:"The meaning of the poem was obscure to many readers.", translation:"這首詩的意義對許多讀者來說很模糊。", level:"中級" },
  { word:"amplify", partOfSpeech:"v. 動詞", meaning:"擴大；增強", example:"The microphone amplified his voice.", translation:"麥克風放大了他的聲音。", level:"中級" },
  { word:"predominant", partOfSpeech:"adj. 形容詞", meaning:"主要的；佔優勢的", example:"English is the predominant language in business.", translation:"英文是商業上主要使用的語言。", level:"高級" },
  { word:"transparency", partOfSpeech:"n. 名詞", meaning:"透明；公開", example:"Transparency in government builds trust.", translation:"政府的透明度能建立信任。", level:"中級" },
  { word:"accessibility", partOfSpeech:"n. 名詞", meaning:"可達性；無障礙性", example:"The building was improved for wheelchair accessibility.", translation:"這棟建築已改善無障礙設施。", level:"中級" },
  { word:"undermine", partOfSpeech:"v. 動詞", meaning:"削弱；破壞", example:"Spreading rumors undermines morale.", translation:"散布謠言會削弱士氣。", level:"中級" },
  { word:"embellish", partOfSpeech:"v. 動詞", meaning:"修飾；美化", example:"She embellished her story to make it more interesting.", translation:"她為了讓故事更有趣而加油添醋。", level:"高級" },
  { word:"safeguard", partOfSpeech:"v./n. 動詞／名詞", meaning:"保護；保障措施", example:"Laws are in place to safeguard workers' rights.", translation:"已有法律保障勞工權益。", level:"中級" },
  { word:"tweak", partOfSpeech:"v. 動詞", meaning:"微調；稍作修改", example:"He tweaked the design to improve performance.", translation:"他微調設計以提升效能。", level:"中級" },
  { word:"erode", partOfSpeech:"v. 動詞", meaning:"侵蝕；削弱", example:"The coastline is slowly being eroded by the sea.", translation:"海岸線正逐漸被海水侵蝕。", level:"中級" },
  { word:"validate", partOfSpeech:"v. 動詞", meaning:"證實；驗證", example:"The data validated our assumptions.", translation:"數據證實了我們的假設。", level:"中級" },
  { word:"coerce", partOfSpeech:"v. 動詞", meaning:"強迫；脅迫", example:"He was coerced into signing the contract.", translation:"他被強迫簽下合約。", level:"高級" },
  { word:"transformative", partOfSpeech:"adj. 形容詞", meaning:"具變革性的；轉變的", example:"The course had a transformative impact on her career.", translation:"這門課對她的職涯有變革性的影響。", level:"高級" },
  { word:"obsolete", partOfSpeech:"adj. 形容詞", meaning:"過時的；淘汰的", example:"CDs have become largely obsolete in the digital age.", translation:"在數位時代，CD 已大多過時。", level:"中級" },
  { word:"implement", partOfSpeech:"v. 動詞", meaning:"實施；執行", example:"The school will implement a new dress code next year.", translation:"學校明年將實施新的服裝規定。", level:"中級" },
  { word:"scam", partOfSpeech:"n. 名詞", meaning:"詐騙；騙局", example:"He fell victim to an online scam.", translation:"他成了網路詐騙的受害者。", level:"初級" },
  { word:"suspect", partOfSpeech:"v./n. 動詞／名詞", meaning:"懷疑；嫌疑犯", example:"The police suspect him of theft.", translation:"警方懷疑他犯了竊盜罪。", level:"初級" },
  { word:"panic", partOfSpeech:"n./v. 名詞／動詞", meaning:"恐慌；驚慌", example:"There was panic when the fire alarm went off.", translation:"火警響起時人群一片恐慌。", level:"初級" },
  { word:"skeptical", partOfSpeech:"adj. 形容詞", meaning:"懷疑的", example:"He was skeptical of their promises.", translation:"他對他們的承諾抱持懷疑態度。", level:"中級" },
  { word:"deceive into", partOfSpeech:"phr. 片語", meaning:"欺騙某人去做…", example:"He deceived her into signing the document.", translation:"他騙她簽署了文件。", level:"中級" },
  { word:"reassure", partOfSpeech:"v. 動詞", meaning:"使安心；打消疑慮", example:"She reassured her friend that everything would be fine.", translation:"她安慰朋友一切都會好起來。", level:"初級" },
  { word:"trick someone", partOfSpeech:"phr. 片語", meaning:"用手法欺騙某人", example:"He tricked me by pretending to be a bank officer.", translation:"他假裝是銀行職員來騙我。", level:"中級" },
  { word:"suspicious", partOfSpeech:"adj. 形容詞", meaning:"可疑的；懷疑的", example:"The man looked suspicious near the crime scene.", translation:"那男子在案發現場附近行跡可疑。", level:"初級" },
  { word:"suspend", partOfSpeech:"v. 動詞", meaning:"暫停；吊銷", example:"The student was suspended for cheating.", translation:"該生因作弊被停學。", level:"中級" },
  { word:"susceptible", partOfSpeech:"adj. 形容詞", meaning:"易受影響的；易患病的", example:"Children are more susceptible to colds.", translation:"兒童較容易感冒。", level:"高級" },
  { word:"appeal to", partOfSpeech:"phr. 片語", meaning:"吸引；訴諸", example:"The commercial appeals to young adults.", translation:"這個廣告吸引年輕人。", level:"中級" },
  { word:"coast", partOfSpeech:"n. 名詞", meaning:"海岸", example:"They walked along the coast enjoying the sea breeze.", translation:"他們沿著海岸散步享受海風。", level:"初級" },
  { word:"reef", partOfSpeech:"n. 名詞", meaning:"礁石；暗礁", example:"Coral reefs are home to many marine species.", translation:"珊瑚礁是許多海洋生物的棲息地。", level:"中級" },
  { word:"habitat", partOfSpeech:"n. 名詞", meaning:"棲息地", example:"Deforestation destroys animal habitats.", translation:"砍伐森林破壞了動物棲息地。", level:"中級" },
  { word:"organism", partOfSpeech:"n. 名詞", meaning:"生物；有機體", example:"All living organisms need water to survive.", translation:"所有生物都需要水才能生存。", level:"中級" },
  { word:"mitigate", partOfSpeech:"v. 動詞", meaning:"減緩；緩解", example:"We must act to mitigate climate change.", translation:"我們必須採取行動減緩氣候變遷。", level:"高級" },
  { word:"encompassing", partOfSpeech:"adj. 形容詞", meaning:"包含的；包羅萬象的", example:"It's a broad and encompassing topic.", translation:"這是一個廣泛且包羅萬象的主題。", level:"中級" },
  { word:"vast", partOfSpeech:"adj. 形容詞", meaning:"廣大的；龐大的", example:"The desert is a vast area of sand and heat.", translation:"沙漠是一片廣大的沙地與高溫地區。", level:"初級" },
  { word:"linguist", partOfSpeech:"n. 名詞", meaning:"語言學家", example:"The linguist studied ancient languages.", translation:"這位語言學家研究古代語言。", level:"高級" },
  { word:"indigenous", partOfSpeech:"adj. 形容詞", meaning:"本土的；原住民的", example:"The plant is indigenous to Taiwan.", translation:"這種植物原產於台灣。", level:"高級" },
  { word:"hypothesis", partOfSpeech:"n. 名詞", meaning:"假設；前提", example:"We tested the hypothesis through several experiments.", translation:"我們透過幾次實驗驗證該假設。", level:"高級" },
  { word:"migrate", partOfSpeech:"v. 動詞", meaning:"遷徙", example:"Birds migrate south in the winter.", translation:"鳥類在冬季往南遷徙。", level:"中級" },
  { word:"scarcity", partOfSpeech:"n. 名詞", meaning:"稀缺；不足", example:"Water scarcity is a global issue.", translation:"水資源稀缺是一項全球性問題。", level:"中級" },
  { word:"seafaring", partOfSpeech:"adj. 形容詞", meaning:"航海的；海上的", example:"They come from a long line of seafaring people.", translation:"他們家族世代從事航海。", level:"高級" },
  { word:"phonology", partOfSpeech:"n. 名詞", meaning:"語音學", example:"Phonology deals with the sound systems of languages.", translation:"語音學研究語言的聲音系統。", level:"高級" },
  { word:"reconstruct", partOfSpeech:"v. 動詞", meaning:"重建；重構", example:"Archaeologists reconstructed the ancient temple.", translation:"考古學家重建了古代寺廟。", level:"中級" },
  { word:"ancestral", partOfSpeech:"adj. 形容詞", meaning:"祖先的；世襲的", example:"He visited his ancestral hometown.", translation:"他拜訪了祖先的故鄉。", level:"高級" },
  { word:"maritime", partOfSpeech:"adj. 形容詞", meaning:"海事的；海上的", example:"Maritime law regulates international shipping.", translation:"海事法規範國際航運。", level:"高級" },
  { word:"a window into", partOfSpeech:"phr. 片語", meaning:"了解…的管道", example:"The documentary offers a window into ancient culture.", translation:"這部紀錄片讓人了解古代文化。", level:"高級" },
  { word:"archaeological", partOfSpeech:"adj. 形容詞", meaning:"考古的", example:"They found archaeological evidence of early settlements.", translation:"他們發現早期聚落的考古證據。", level:"高級" },
  { word:"excavation", partOfSpeech:"n. 名詞", meaning:"挖掘；發掘", example:"Excavation at the site revealed ancient tools.", translation:"該地點的挖掘發現了古代工具。", level:"中級" },
  { word:"pottery", partOfSpeech:"n. 名詞", meaning:"陶器；陶藝", example:"The museum displayed ancient pottery.", translation:"博物館展出了古代陶器。", level:"初級" },
  { word:"distinctive", partOfSpeech:"adj. 形容詞", meaning:"獨特的；有特色的", example:"She has a distinctive voice.", translation:"她的聲音很有特色。", level:"中級" },
  { word:"sophisticated", partOfSpeech:"adj. 形容詞", meaning:"精密的；老練的", example:"The robot uses sophisticated technology.", translation:"這台機器人採用了高科技技術。", level:"中級" },
  { word:"exhibit", partOfSpeech:"v./n. 動詞／名詞", meaning:"展示；展覽品", example:"The artist exhibited her paintings in a gallery.", translation:"這位藝術家在畫廊展示了她的作品。", level:"初級" },
  { word:"revitalization", partOfSpeech:"n. 名詞", meaning:"復興；振興", example:"The government invested in urban revitalization.", translation:"政府投資於城市振興。", level:"高級" },
  { word:"carry out", partOfSpeech:"phr. 片語", meaning:"執行；進行", example:"The scientists carried out a new experiment.", translation:"科學家進行了一項新實驗。", level:"中級" },
  { word:"preserve", partOfSpeech:"v. 動詞", meaning:"保存；保護", example:"Efforts are being made to preserve endangered species.", translation:"正努力保護瀕危物種。", level:"初級" },
  { word:"embedded", partOfSpeech:"adj. 形容詞", meaning:"嵌入的；根深蒂固的", example:"Values are embedded in our culture.", translation:"這些價值觀根植於我們的文化中。", level:"高級" },
  { word:"commitment", partOfSpeech:"n. 名詞", meaning:"承諾；投入", example:"He showed great commitment to his job.", translation:"他對工作表現出極大的投入。", level:"中級" },
  { word:"inclusivity", partOfSpeech:"n. 名詞", meaning:"包容性", example:"The school promotes diversity and inclusivity.", translation:"學校提倡多元與包容。", level:"高級" },
  { word:"accommodate", partOfSpeech:"v. 動詞", meaning:"容納；適應", example:"The hotel can accommodate 200 guests.", translation:"這家飯店可容納 200 位客人。", level:"中級" },
  { word:"segregate", partOfSpeech:"v. 動詞", meaning:"分隔；隔離", example:"The policy segregated people by race.", translation:"這項政策依種族進行隔離。", level:"高級" },
  { word:"cater", partOfSpeech:"v. 動詞", meaning:"迎合；提供飲食", example:"This restaurant caters to vegetarians.", translation:"這家餐廳迎合素食者需求。", level:"中級" },
  { word:"adoption", partOfSpeech:"n. 名詞", meaning:"採納；收養", example:"The adoption of new policies improved efficiency.", translation:"新政策的採納提高了效率。", level:"中級" },
  { word:"advocate", partOfSpeech:"v./n. 動詞／名詞", meaning:"提倡；擁護者", example:"She advocates for mental health awareness.", translation:"她倡導心理健康意識。", level:"中級" },
  { word:"dignity", partOfSpeech:"n. 名詞", meaning:"尊嚴", example:"Everyone deserves to live with dignity.", translation:"每個人都應擁有有尊嚴的生活。", level:"中級" },
  { word:"anxiety", partOfSpeech:"n. 名詞", meaning:"焦慮；不安", example:"She suffers from social anxiety.", translation:"她患有社交焦慮症。", level:"初級" },
  { word:"discrimination", partOfSpeech:"n. 名詞", meaning:"歧視；辨別", example:"We must fight against racial discrimination.", translation:"我們必須對抗種族歧視。", level:"中級" },
  { word:"misuse", partOfSpeech:"v./n. 動詞／名詞", meaning:"誤用；濫用", example:"The misuse of power can lead to corruption.", translation:"濫權可能導致貪腐。", level:"中級" },
  { word:"range from A to B", partOfSpeech:"phr. 片語", meaning:"從 A 到 B 不等", example:"Participants ranged from teenagers to elderly adults.", translation:"參與者從青少年到年長者都有。", level:"中級" },
  { word:"aim to", partOfSpeech:"phr. 片語", meaning:"旨在；打算", example:"The campaign aims to raise awareness.", translation:"這場活動旨在提高認知。", level:"初級" },
  { word:"dispel", partOfSpeech:"v. 動詞", meaning:"驅散；消除", example:"The teacher dispelled students' fears about the exam.", translation:"老師消除了學生對考試的恐懼。", level:"高級" },
  { word:"momentum", partOfSpeech:"n. 名詞", meaning:"動力；勢頭", example:"The movement is gaining momentum worldwide.", translation:"這股運動正在全球獲得動能。", level:"中級" }
];
/* ========== END OF VOCABULARY DATA ========== */

/* ===== STATE ===== */
let settings = { rate:0.9, volume:1.0, pitch:1.0 };
let masteredSet = new Set();
let quizStats = { total:0, correct:0 };
let matchStats = { errors:0 };

// flashcard state
let fcOrder = [];
let fcIndex = 0;
let showMastered = true;

// quiz state
let quizQueue = [];
let quizCurrent = null;
let quizAnswered = false;

// match state
let matchSelected = { left:null, right:null };
let matchData = [];
let matchPairs = {};
let matchDone = 0;

// sleep state
let sleepInterval = null;
let sleepSpeakTimeout = null;
let sleepRemaining = 0;
let sleepTotal = 0;
let sleepPaused = false;
let sleepQueue = [];
let sleepQueueIdx = 0;

// browse state
let browseFilters = { level:'all', pos:'all' };

/* ===== INIT ===== */
function init() {
  loadStorage();
  buildFCOrder();
  renderFC();
  loadQuiz();
  loadMatchRound();
  renderBrowse();
  updateSidebar();
  loadSettingsUI();
}

/* ===== STORAGE ===== */
function loadStorage() {
  try {
    const s = JSON.parse(localStorage.getItem('vocab114_settings') || '{}');
    settings = { rate: s.rate??0.9, volume: s.volume??1.0, pitch: s.pitch??1.0 };
    const m = JSON.parse(localStorage.getItem('vocab114_mastered') || '[]');
    masteredSet = new Set(m);
    const q = JSON.parse(localStorage.getItem('vocab114_quizstats') || '{}');
    quizStats = { total: q.total??0, correct: q.correct??0 };
    const me = JSON.parse(localStorage.getItem('vocab114_matcherrors') || '0');
    matchStats.errors = me;
  } catch(e){}
}
function saveStorage() {
  localStorage.setItem('vocab114_settings', JSON.stringify(settings));
  localStorage.setItem('vocab114_mastered', JSON.stringify([...masteredSet]));
  localStorage.setItem('vocab114_quizstats', JSON.stringify(quizStats));
  localStorage.setItem('vocab114_matcherrors', JSON.stringify(matchStats.errors));
}
function updateSidebar() {
  const mc = masteredSet.size;
  document.getElementById('stat-mastered').textContent = mc;
  document.getElementById('stat-total').textContent = vocabularyData.length;
  const acc = quizStats.total > 0 ? Math.round(quizStats.correct/quizStats.total*100)+'%' : '—';
  document.getElementById('stat-acc').textContent = acc;
  document.getElementById('badge-mastered').textContent = '已熟 ' + mc;
  document.getElementById('badge-total').textContent = '共 ' + vocabularyData.length + ' 字';
  // settings page
  document.getElementById('settings-mastered-count').textContent = mc;
  document.getElementById('settings-quiz-total').textContent = quizStats.total;
  document.getElementById('settings-quiz-correct').textContent = quizStats.correct;
  document.getElementById('settings-match-errors').textContent = matchStats.errors;
}

/* ===== NAVIGATION ===== */
const panelTitles = { flashcard:'單字卡', quiz:'填空測驗', match:'配對測驗', sleep:'睡眠複習', browse:'搜尋瀏覽', settings:'設定' };
function showPanel(id) {
  document.querySelectorAll('.panel').forEach(p => p.classList.remove('active'));
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  document.getElementById('panel-'+id).classList.add('active');
  document.querySelector(`[data-panel="${id}"]`).classList.add('active');
  document.getElementById('topbar-title').textContent = panelTitles[id];
  closeSidebar();
  if(id==='browse') renderBrowse();
  if(id==='settings') { loadSettingsUI(); updateSidebar(); }
}
function toggleSidebar() {
  document.getElementById('sidebar').classList.toggle('open');
  document.getElementById('overlay').classList.toggle('show');
}
function closeSidebar() {
  document.getElementById('sidebar').classList.remove('open');
  document.getElementById('overlay').classList.remove('show');
}

/* ===== SPEECH ===== */
function getVoice() {
  const voices = speechSynthesis.getVoices();
  return voices.find(v => v.lang === 'en-US') ||
         voices.find(v => v.lang.startsWith('en')) ||
         null;
}
function speak(text) {
  if (!text) return;
  speechSynthesis.cancel();
  const u = new SpeechSynthesisUtterance(text);
  u.lang = 'en-US';
  u.rate = settings.rate;
  u.volume = settings.volume;
  u.pitch = settings.pitch;
  const voice = getVoice();
  if (voice) u.voice = voice;
  speechSynthesis.speak(u);
}
function speakWord() {
  const w = vocabularyData[fcOrder[fcIndex]];
  if(w) speak(w.word);
}
function speakExample() {
  const w = vocabularyData[fcOrder[fcIndex]];
  if(w) speak(w.example);
}
function speakQuizExample() {
  if(quizCurrent) speak(quizCurrent.example);
}
function testSpeech() {
  speak('Hello! This is a test of the American English pronunciation.');
}

/* ===== FLASHCARD ===== */
function buildFCOrder() {
  const arr = vocabularyData.map((_,i)=>i);
  if(!showMastered) {
    fcOrder = arr.filter(i => !masteredSet.has(i));
  } else {
    fcOrder = arr;
  }
  if(fcIndex >= fcOrder.length) fcIndex = 0;
}
function renderFC() {
  if(fcOrder.length === 0) {
    document.getElementById('fc-word').textContent = '全部已熟！';
    document.getElementById('fc-meaning').textContent = '太棒了 🎉';
    document.getElementById('fc-pos').textContent = '';
    document.getElementById('fc-example').textContent = '';
    document.getElementById('fc-translation').textContent = '';
    document.getElementById('fc-level-badge').innerHTML = '';
    document.getElementById('fc-cur').textContent = 0;
    document.getElementById('fc-total').textContent = 0;
    return;
  }
  const w = vocabularyData[fcOrder[fcIndex]];
  document.getElementById('fc-word').textContent = w.word;
  document.getElementById('fc-pos').textContent = w.partOfSpeech;
  document.getElementById('fc-meaning').textContent = w.meaning;
  document.getElementById('fc-example').textContent = w.example;
  document.getElementById('fc-translation').textContent = w.translation;
  document.getElementById('fc-level-badge').innerHTML = `<span class="lv-${w.level}">${w.level}</span>`;
  document.getElementById('fc-cur').textContent = fcIndex + 1;
  document.getElementById('fc-total').textContent = fcOrder.length;
  document.getElementById('fc-card').classList.remove('flipped');
  const btn = document.getElementById('btn-mastered');
  if(masteredSet.has(fcOrder[fcIndex])) {
    btn.textContent = '✓ 已熟 (取消)';
    btn.className = 'btn btn-outline';
  } else {
    btn.textContent = '✓ 標記已熟';
    btn.className = 'btn btn-green';
  }
}
function flipCard() { document.getElementById('fc-card').classList.toggle('flipped'); }
function nextCard() {
  fcIndex = (fcIndex + 1) % fcOrder.length;
  renderFC();
}
function prevCard() {
  fcIndex = (fcIndex - 1 + fcOrder.length) % fcOrder.length;
  renderFC();
}
function shuffleFlashcards() {
  for(let i=fcOrder.length-1;i>0;i--){
    const j=Math.floor(Math.random()*(i+1));
    [fcOrder[i],fcOrder[j]]=[fcOrder[j],fcOrder[i]];
  }
  fcIndex=0; renderFC(); showToast('已隨機排列單字卡');
}
function resetFlashcards() {
  buildFCOrder(); fcIndex=0; renderFC(); showToast('已重置順序');
}
function toggleShowMastered() {
  showMastered = !showMastered;
  document.getElementById('show-mastered-txt').textContent = showMastered ? '🙈 隱藏已熟' : '👁 顯示已熟';
  buildFCOrder(); fcIndex=0; renderFC();
}
function markMastered() {
  const idx = fcOrder[fcIndex];
  if(masteredSet.has(idx)) {
    masteredSet.delete(idx);
    showToast('已取消標記');
  } else {
    masteredSet.add(idx);
    showToast('✓ 已標記為已熟！');
  }
  saveStorage(); updateSidebar();
  if(!showMastered) { buildFCOrder(); renderFC(); } else renderFC();
}

/* ===== QUIZ ===== */
function buildQuizQueue() {
  quizQueue = [...vocabularyData].sort(()=>Math.random()-.5);
}
function loadQuiz() {
  buildQuizQueue();
  nextQuiz();
}
function nextQuiz() {
  if(quizQueue.length === 0) buildQuizQueue();
  quizCurrent = quizQueue.pop();
  quizAnswered = false;
  const blank = '_____';
  // try to replace the word in the example sentence
  const wordLower = quizCurrent.word.toLowerCase();
  let prompt = quizCurrent.example;
  // find the word (or a conjugated form) in the sentence
  const regex = new RegExp('\\b(' + escapeReg(wordLower) + '\\w*)\\b', 'i');
  if(regex.test(prompt)) {
    prompt = prompt.replace(regex, `<span class="blank">${blank}</span>`);
  } else {
    prompt = `${quizCurrent.meaning}：<span class="blank">${blank}</span>`;
  }
  document.getElementById('q-prompt').innerHTML = prompt;
  document.getElementById('q-zh').textContent = quizCurrent.translation;
  document.getElementById('q-input').value = '';
  document.getElementById('q-input').className = 'quiz-input';
  document.getElementById('q-input').disabled = false;
  document.getElementById('q-feedback').className = 'quiz-feedback';
  document.getElementById('q-next-btn').style.display = 'none';
  document.getElementById('q-score').textContent = quizStats.correct;
  document.getElementById('q-total').textContent = quizStats.total;
  document.getElementById('q-acc').textContent = quizStats.total>0 ? Math.round(quizStats.correct/quizStats.total*100)+'%' : '—';
  setTimeout(()=>document.getElementById('q-input').focus(), 50);
}
function escapeReg(s) { return s.replace(/[.*+?^${}()|[\]\\]/g,'\\$&'); }
function submitQuiz() {
  if(quizAnswered) return;
  const ans = document.getElementById('q-input').value.trim().toLowerCase();
  if(!ans) return;
  quizAnswered = true;
  quizStats.total++;
  const fb = document.getElementById('q-feedback');
  const inp = document.getElementById('q-input');
  inp.disabled = true;
  // check if answer matches word
  const correct = quizCurrent.word.toLowerCase();
  const isOk = ans === correct || correct.startsWith(ans) || ans.startsWith(correct.split(' ')[0]);
  if(isOk) {
    quizStats.correct++;
    inp.className = 'quiz-input correct';
    fb.className = 'quiz-feedback correct show';
    fb.innerHTML = `🎉 答對了！ <strong>${quizCurrent.word}</strong> — ${quizCurrent.meaning}`;
  } else {
    inp.className = 'quiz-input wrong';
    fb.className = 'quiz-feedback wrong show';
    fb.innerHTML = `❌ 答案是：<strong>${quizCurrent.word}</strong> — ${quizCurrent.meaning}`;
  }
  document.getElementById('q-next-btn').style.display = 'inline-flex';
  document.getElementById('q-score').textContent = quizStats.correct;
  document.getElementById('q-total').textContent = quizStats.total;
  document.getElementById('q-acc').textContent = Math.round(quizStats.correct/quizStats.total*100)+'%';
  saveStorage(); updateSidebar();
}
function skipQuiz() { nextQuiz(); }
function resetQuiz() {
  quizStats = { total:0, correct:0 };
  saveStorage(); buildQuizQueue(); nextQuiz(); updateSidebar();
  showToast('測驗已重置');
}

/* ===== MATCH ===== */
function loadMatchRound() {
  const pool = [...vocabularyData].sort(()=>Math.random()-.5).slice(0,6);
  matchData = pool;
  matchPairs = {};
  pool.forEach(w => matchPairs[w.word] = w.meaning);
  matchSelected = { left:null, right:null };
  matchDone = 0;
  document.getElementById('m-done').textContent = 0;
  document.getElementById('m-complete-msg').style.display = 'none';
  renderMatchGrid();
}
function renderMatchGrid() {
  const grid = document.getElementById('match-grid');
  const lefts = matchData.map(w=>w.word);
  const rights = matchData.map(w=>w.meaning).sort(()=>Math.random()-.5);
  let html = '<div class="match-col" id="mc-left">';
  lefts.forEach(w => {
    html += `<div class="match-item" data-side="left" data-val="${escHtml(w)}" onclick="matchClick(this)">${escHtml(w)}</div>`;
  });
  html += '</div><div class="match-col" id="mc-right">';
  rights.forEach(m => {
    html += `<div class="match-item" data-side="right" data-val="${escHtml(m)}" onclick="matchClick(this)">${escHtml(m)}</div>`;
  });
  html += '</div>';
  grid.innerHTML = html;
}
function escHtml(s) { return s.replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;'); }
function matchClick(el) {
  if(el.classList.contains('matched') || el.classList.contains('disabled')) return;
  const side = el.dataset.side;
  // deselect same side
  document.querySelectorAll(`.match-item[data-side="${side}"].selected`).forEach(e=>e.classList.remove('selected'));
  el.classList.add('selected');
  matchSelected[side] = el;
  if(matchSelected.left && matchSelected.right) {
    const lw = matchSelected.left.dataset.val;
    const rm = matchSelected.right.dataset.val;
    if(matchPairs[lw] === rm) {
      matchSelected.left.classList.remove('selected');
      matchSelected.right.classList.remove('selected');
      matchSelected.left.classList.add('matched');
      matchSelected.right.classList.add('matched');
      matchDone++;
      document.getElementById('m-done').textContent = matchDone;
      if(matchDone === matchData.length) {
        document.getElementById('m-complete-msg').style.display = 'inline';
        showToast('🎉 配對全部完成！');
      }
    } else {
      matchStats.errors++;
      document.getElementById('m-errors').textContent = matchStats.errors;
      matchSelected.left.classList.add('error');
      matchSelected.right.classList.add('error');
      const l = matchSelected.left, r = matchSelected.right;
      setTimeout(()=>{ l.classList.remove('error','selected'); r.classList.remove('error','selected'); },600);
      saveStorage(); updateSidebar();
    }
    matchSelected = { left:null, right:null };
  }
}

/* ===== SLEEP TIMER ===== */
document.getElementById('sleep-duration').addEventListener('change', function() {
  document.getElementById('sleep-custom').style.display = this.value==='custom' ? 'block' : 'none';
});

function getSleepDurationMs() {
  const sel = document.getElementById('sleep-duration').value;
  if(sel==='custom') {
    const v = parseInt(document.getElementById('sleep-custom').value) || 15;
    return v * 60 * 1000;
  }
  return parseInt(sel) * 60 * 1000;
}

function startSleep() {
  if(sleepPaused) { resumeSleep(); return; }
  sleepTotal = getSleepDurationMs();
  sleepRemaining = sleepTotal;
  sleepPaused = false;
  // build queue
  const shuffle = document.getElementById('sleep-shuffle').checked;
  const repeat = parseInt(document.getElementById('sleep-repeat').value);
  let arr = [...vocabularyData];
  if(shuffle) arr.sort(()=>Math.random()-.5);
  sleepQueue = [];
  arr.forEach(w => { for(let i=0;i<repeat;i++) sleepQueue.push(w); });
  sleepQueueIdx = 0;
  document.getElementById('sleep-pause-btn').disabled = false;
  document.getElementById('sleep-stop-btn').disabled = false;
  startSleepClock();
  sleepNext();
}
function startSleepClock() {
  clearInterval(sleepInterval);
  sleepInterval = setInterval(()=>{
    if(sleepPaused) return;
    sleepRemaining -= 1000;
    updateSleepDisplay();
    if(sleepRemaining <= 0) stopSleep(true);
  }, 1000);
}
function updateSleepDisplay() {
  const m = Math.floor(sleepRemaining/60000).toString().padStart(2,'0');
  const s = Math.floor((sleepRemaining%60000)/1000).toString().padStart(2,'0');
  document.getElementById('sleep-timer').textContent = m+':'+s;
  const pct = Math.max(0,sleepRemaining/sleepTotal)*100;
  document.getElementById('sleep-pbar').style.width = pct+'%';
}
function sleepNext() {
  if(sleepPaused || sleepRemaining<=0) return;
  if(sleepQueueIdx >= sleepQueue.length) sleepQueueIdx = 0;
  const w = sleepQueue[sleepQueueIdx++];
  document.getElementById('sleep-word').textContent = w.word + ' (' + w.partOfSpeech + ')';
  document.getElementById('sleep-meaning').textContent = w.meaning;
  const rate = parseFloat(document.getElementById('sleep-rate').value);
  const gap = parseInt(document.getElementById('sleep-gap').value);
  const includeSentence = document.getElementById('sleep-include-sentence').checked;
  speechSynthesis.cancel();
  const u1 = new SpeechSynthesisUtterance(w.word);
  u1.lang='en-US'; u1.rate=rate; u1.volume=settings.volume; u1.pitch=settings.pitch;
  const voice=getVoice(); if(voice){u1.voice=voice;}
  if(includeSentence) {
    u1.onend = () => {
      sleepSpeakTimeout = setTimeout(()=>{
        if(sleepPaused||sleepRemaining<=0) return;
        const u2=new SpeechSynthesisUtterance(w.example);
        u2.lang='en-US'; u2.rate=rate; u2.volume=settings.volume; u2.pitch=settings.pitch;
        if(voice) u2.voice=voice;
        u2.onend=()=>{ sleepSpeakTimeout=setTimeout(sleepNext, gap); };
        speechSynthesis.speak(u2);
      }, gap/2);
    };
  } else {
    u1.onend = () => { sleepSpeakTimeout = setTimeout(sleepNext, gap); };
  }
  speechSynthesis.speak(u1);
}
function pauseSleep() {
  if(!sleepPaused) {
    sleepPaused = true;
    speechSynthesis.pause();
    clearTimeout(sleepSpeakTimeout);
    document.getElementById('sleep-pause-btn').textContent = '▶ 繼續';
  } else {
    resumeSleep();
  }
}
function resumeSleep() {
  sleepPaused = false;
  document.getElementById('sleep-pause-btn').textContent = '⏸ 暫停';
  speechSynthesis.resume();
  sleepNext();
}
function stopSleep(auto) {
  clearInterval(sleepInterval);
  clearTimeout(sleepSpeakTimeout);
  speechSynthesis.cancel();
  sleepPaused = false;
  sleepRemaining = 0;
  document.getElementById('sleep-pause-btn').disabled = true;
  document.getElementById('sleep-stop-btn').disabled = true;
  document.getElementById('sleep-pause-btn').textContent = '⏸ 暫停';
  document.getElementById('sleep-timer').textContent = '00:00';
  document.getElementById('sleep-pbar').style.width = '0%';
  if(auto) {
    document.getElementById('sleep-word').textContent = '✅ 睡眠複習完成！';
    document.getElementById('sleep-meaning').textContent = '好眠🌙';
    showToast('✅ 睡眠複習時間結束！');
  } else {
    document.getElementById('sleep-word').textContent = '—';
    document.getElementById('sleep-meaning').textContent = '設定後開始複習';
  }
}

/* ===== BROWSE ===== */
function setFilter(type, val, btn) {
  browseFilters[type] = val;
  const group = btn.parentElement;
  group.querySelectorAll('.filter-btn').forEach(b=>b.classList.remove('active'));
  btn.classList.add('active');
  renderBrowse();
}
function renderBrowse() {
  const q = document.getElementById('search-input').value.toLowerCase();
  const lvl = browseFilters.level;
  const pos = browseFilters.pos;
  const filtered = vocabularyData.filter(w => {
    const matchQ = !q || w.word.toLowerCase().includes(q) || w.meaning.includes(q) || w.example.toLowerCase().includes(q);
    const matchLvl = lvl==='all' || w.level===lvl;
    const matchPos = pos==='all' || w.partOfSpeech.includes(pos);
    return matchQ && matchLvl && matchPos;
  });
  document.getElementById('browse-count').textContent = filtered.length;
  const tbody = document.getElementById('browse-tbody');
  tbody.innerHTML = filtered.map((w,i) => `
    <tr>
      <td><span class="word-en">${escHtml(w.word)}</span></td>
      <td><span class="word-pos">${escHtml(w.partOfSpeech)}</span></td>
      <td class="word-cn">${escHtml(w.meaning)}</td>
      <td><span class="lv-${w.level}">${w.level}</span></td>
      <td class="word-ex">${escHtml(w.example)}</td>
      <td>
        <button class="btn btn-ghost btn-sm" onclick="speak('${escHtml(w.word).replace(/'/g,"\\'")}')">🔊</button>
      </td>
    </tr>
  `).join('');
}

/* ===== SETTINGS ===== */
function loadSettingsUI() {
  document.getElementById('s-rate').value = settings.rate;
  document.getElementById('s-rate-val').textContent = settings.rate;
  document.getElementById('s-vol').value = settings.volume;
  document.getElementById('s-vol-val').textContent = settings.volume;
  document.getElementById('s-pitch').value = settings.pitch;
  document.getElementById('s-pitch-val').textContent = settings.pitch;
}
function updateSetting(key, val, spanId) {
  settings[key] = parseFloat(val);
  document.getElementById(spanId).textContent = parseFloat(val).toFixed(2);
}
function saveSettings() {
  saveStorage();
  showToast('💾 設定已儲存');
}
function clearMastered() {
  if(!confirm('確定要清除所有已熟記錄嗎？')) return;
  masteredSet.clear();
  saveStorage(); updateSidebar(); buildFCOrder(); renderFC();
  showToast('已清除已熟記錄');
}
function clearStats() {
  if(!confirm('確定要清除測驗記錄嗎？')) return;
  quizStats={total:0,correct:0}; matchStats.errors=0;
  saveStorage(); updateSidebar();
  showToast('已清除測驗記錄');
}

/* ===== TOAST ===== */
let toastTimer = null;
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(()=>t.classList.remove('show'), 2500);
}

/* ===== VOICE LOADING ===== */
speechSynthesis.onvoiceschanged = () => {};

/* ===== KEYBOARD ===== */
document.addEventListener('keydown', e => {
  const active = document.querySelector('.panel.active');
  if(!active) return;
  const id = active.id;
  if(id==='panel-flashcard') {
    if(e.key==='ArrowRight') nextCard();
    if(e.key==='ArrowLeft') prevCard();
    if(e.key===' ') { e.preventDefault(); flipCard(); }
  }
});

/* ===== START ===== */
init();
</script>
</body>
</html>
