# my-project
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>WorkLink — Find Skilled Workers</title>
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet"/>
<style>
  :root {
    --bg: #0d0f0e;
    --surface: #161918;
    --card: #1c1f1e;
    --border: #2a2e2c;
    --accent: #b8f55a;
    --accent2: #5affd4;
    --text: #e8ede9;
    --muted: #7a8a7d;
    --danger: #ff5a5a;
    --warn: #ffcc5a;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    background: var(--bg);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* NAV */
  nav {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 18px 40px;
    border-bottom: 1px solid var(--border);
    position: sticky;
    top: 0;
    background: rgba(13,15,14,0.92);
    backdrop-filter: blur(12px);
    z-index: 100;
  }
  .logo {
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    font-size: 22px;
    letter-spacing: -0.5px;
    color: var(--text);
  }
  .logo span { color: var(--accent); }
  .nav-links { display: flex; gap: 8px; align-items: center; }
  .nav-pill {
    padding: 8px 18px;
    border-radius: 100px;
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    border: none;
    transition: all 0.2s;
    text-decoration: none;
  }
  .nav-ghost { background: transparent; color: var(--muted); }
  .nav-ghost:hover { color: var(--text); }
  .nav-cta { background: var(--accent); color: #0d0f0e; font-weight: 600; }
  .nav-cta:hover { background: #caff70; }
  .nav-outline { background: transparent; color: var(--text); border: 1px solid var(--border); }
  .nav-outline:hover { border-color: var(--accent); color: var(--accent); }
  .badge-role {
    background: #1c2f1c;
    color: var(--accent);
    border: 1px solid #2e4a2e;
    padding: 5px 12px;
    border-radius: 100px;
    font-size: 12px;
    font-weight: 500;
  }

  /* HERO SECTION */
  .hero {
    padding: 64px 40px 48px;
    max-width: 1200px;
    margin: 0 auto;
  }
  .hero-eyebrow {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: #1a2a1a;
    border: 1px solid #2e4a2e;
    border-radius: 100px;
    padding: 6px 14px;
    font-size: 12px;
    color: var(--accent);
    margin-bottom: 24px;
  }
  .dot { width: 6px; height: 6px; border-radius: 50%; background: var(--accent); animation: pulse 2s infinite; }
  @keyframes pulse { 0%,100%{opacity:1} 50%{opacity:0.3} }
  .hero h1 {
    font-family: 'Syne', sans-serif;
    font-size: clamp(36px, 5vw, 58px);
    font-weight: 800;
    line-height: 1.05;
    letter-spacing: -1.5px;
    margin-bottom: 16px;
  }
  .hero h1 em { color: var(--accent); font-style: normal; }
  .hero p { color: var(--muted); font-size: 16px; max-width: 520px; line-height: 1.7; }

  /* SEARCH BAR */
  .search-wrap {
    margin: 36px 0 0;
    display: flex;
    gap: 12px;
    flex-wrap: wrap;
    align-items: center;
  }
  .search-box {
    display: flex;
    align-items: center;
    gap: 10px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 12px 18px;
    flex: 1;
    min-width: 260px;
    transition: border-color 0.2s;
  }
  .search-box:focus-within { border-color: var(--accent); }
  .search-box svg { flex-shrink: 0; opacity: 0.5; }
  .search-box input {
    background: none;
    border: none;
    outline: none;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 15px;
    width: 100%;
  }
  .search-box input::placeholder { color: var(--muted); }
  .filter-row {
    margin: 20px 0;
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    align-items: center;
  }
  .filter-label { font-size: 12px; color: var(--muted); margin-right: 4px; }
  .chip {
    padding: 7px 16px;
    border-radius: 100px;
    font-size: 13px;
    font-weight: 500;
    cursor: pointer;
    border: 1px solid var(--border);
    background: transparent;
    color: var(--muted);
    transition: all 0.18s;
  }
  .chip:hover { border-color: var(--accent); color: var(--accent); }
  .chip.active { background: var(--accent); border-color: var(--accent); color: #0d0f0e; }

  /* LAYOUT */
  .main-layout {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 40px 60px;
    display: grid;
    grid-template-columns: 260px 1fr;
    gap: 32px;
  }

  /* SIDEBAR FILTERS */
  .sidebar {
    position: sticky;
    top: 90px;
    align-self: start;
  }
  .sidebar-section {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 16px;
    padding: 22px;
    margin-bottom: 16px;
  }
  .sidebar-title {
    font-family: 'Syne', sans-serif;
    font-size: 13px;
    font-weight: 700;
    color: var(--muted);
    text-transform: uppercase;
    letter-spacing: 1px;
    margin-bottom: 16px;
  }
  .filter-option {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 9px 0;
    border-bottom: 1px solid var(--border);
    cursor: pointer;
    transition: all 0.15s;
  }
  .filter-option:last-child { border-bottom: none; }
  .filter-option:hover .fopt-label { color: var(--accent); }
  .fcheck {
    width: 18px; height: 18px;
    border-radius: 5px;
    border: 1.5px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
    transition: all 0.15s;
  }
  .fcheck.on { background: var(--accent); border-color: var(--accent); }
  .fcheck.on::after { content: '✓'; font-size: 11px; color: #0d0f0e; font-weight: 700; }
  .fopt-label { font-size: 14px; color: var(--text); flex: 1; }
  .fopt-count { font-size: 12px; color: var(--muted); background: var(--card); padding: 2px 8px; border-radius: 100px; }
  .skill-icon { font-size: 16px; }

  /* RATING STARS */
  .stars-filter { display: flex; gap: 6px; flex-direction: column; }
  .star-row { display: flex; align-items: center; gap: 8px; padding: 7px 0; cursor: pointer; border-bottom: 1px solid var(--border); }
  .star-row:last-child { border-bottom: none; }
  .star-row:hover .fopt-label { color: var(--accent); }
  .stars { color: #f5c842; font-size: 13px; }

  /* GRID */
  .cards-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  .result-count { font-size: 14px; color: var(--muted); }
  .result-count strong { color: var(--text); }
  .sort-select {
    background: var(--surface);
    border: 1px solid var(--border);
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 13px;
    padding: 8px 14px;
    border-radius: 8px;
    outline: none;
    cursor: pointer;
  }
  .cards-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 18px;
  }

  /* TALENT CARD */
  .talent-card {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 18px;
    overflow: hidden;
    cursor: pointer;
    transition: all 0.22s cubic-bezier(0.34,1.56,0.64,1);
    position: relative;
  }
  .talent-card:hover {
    border-color: var(--accent);
    transform: translateY(-4px);
    box-shadow: 0 12px 40px rgba(184,245,90,0.1);
  }
  .card-top {
    padding: 22px 22px 16px;
    display: flex;
    align-items: flex-start;
    gap: 14px;
  }
  .avatar {
    width: 52px; height: 52px;
    border-radius: 14px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    flex-shrink: 0;
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    position: relative;
  }
  .avatar-verified::after {
    content: '✓';
    position: absolute;
    bottom: -4px; right: -4px;
    width: 18px; height: 18px;
    background: var(--accent);
    border-radius: 50%;
    font-size: 10px;
    color: #0d0f0e;
    display: flex; align-items: center; justify-content: center;
    font-weight: 800;
    border: 2px solid var(--card);
  }
  .card-meta { flex: 1; min-width: 0; }
  .card-name {
    font-family: 'Syne', sans-serif;
    font-size: 16px;
    font-weight: 700;
    margin-bottom: 3px;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
  }
  .card-role { font-size: 13px; color: var(--muted); margin-bottom: 8px; }
  .card-rating { display: flex; align-items: center; gap: 5px; font-size: 13px; }
  .card-rating .stars { color: #f5c842; }
  .rating-num { font-weight: 600; color: var(--text); }
  .rating-count { color: var(--muted); }
  .otw-badge {
    position: absolute;
    top: 14px; right: 14px;
    background: #0d2010;
    border: 1px solid #2e5a20;
    color: var(--accent);
    font-size: 10px;
    font-weight: 700;
    padding: 4px 10px;
    border-radius: 100px;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .card-divider { height: 1px; background: var(--border); margin: 0 22px; }
  .card-body { padding: 16px 22px; }
  .card-skills { display: flex; gap: 6px; flex-wrap: wrap; margin-bottom: 14px; }
  .skill-tag {
    background: var(--surface);
    border: 1px solid var(--border);
    padding: 4px 10px;
    border-radius: 6px;
    font-size: 12px;
    color: var(--muted);
  }
  .card-footer {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 14px 22px;
    border-top: 1px solid var(--border);
    background: rgba(255,255,255,0.01);
  }
  .rate {
    font-family: 'Syne', sans-serif;
    font-size: 16px;
    font-weight: 700;
  }
  .rate span { font-size: 12px; color: var(--muted); font-weight: 400; font-family: 'DM Sans', sans-serif; }
  .hire-btn {
    background: var(--accent);
    color: #0d0f0e;
    border: none;
    padding: 9px 18px;
    border-radius: 100px;
    font-size: 13px;
    font-weight: 700;
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    transition: all 0.15s;
  }
  .hire-btn:hover { background: #caff70; transform: scale(1.03); }
  .location-row { display: flex; align-items: center; gap: 5px; font-size: 12px; color: var(--muted); margin-bottom: 10px; }

  /* DETAIL MODAL */
  .modal-overlay {
    position: fixed; inset: 0;
    background: rgba(0,0,0,0.75);
    backdrop-filter: blur(6px);
    z-index: 200;
    display: none;
    align-items: center;
    justify-content: center;
    padding: 20px;
  }
  .modal-overlay.open { display: flex; }
  .modal {
    background: var(--card);
    border: 1px solid var(--border);
    border-radius: 24px;
    width: 100%;
    max-width: 680px;
    max-height: 90vh;
    overflow-y: auto;
    animation: slideUp 0.28s cubic-bezier(0.34,1.56,0.64,1);
  }
  @keyframes slideUp { from { transform: translateY(30px); opacity: 0; } to { transform: none; opacity: 1; } }
  .modal-header {
    padding: 28px 28px 0;
    display: flex;
    align-items: flex-start;
    gap: 18px;
  }
  .modal-avatar {
    width: 72px; height: 72px;
    border-radius: 18px;
    display: flex; align-items: center; justify-content: center;
    font-size: 30px;
    font-family: 'Syne', sans-serif;
    font-weight: 800;
    flex-shrink: 0;
    position: relative;
  }
  .modal-avatar::after {
    content: '✓';
    position: absolute;
    bottom: -5px; right: -5px;
    width: 22px; height: 22px;
    background: var(--accent);
    border-radius: 50%;
    font-size: 11px;
    color: #0d0f0e;
    display: flex; align-items: center; justify-content: center;
    font-weight: 800;
    border: 2px solid var(--card);
  }
  .modal-meta { flex: 1; }
  .modal-name {
    font-family: 'Syne', sans-serif;
    font-size: 24px;
    font-weight: 800;
    letter-spacing: -0.5px;
    margin-bottom: 4px;
  }
  .modal-role { font-size: 14px; color: var(--muted); margin-bottom: 10px; }
  .modal-stats { display: flex; gap: 20px; flex-wrap: wrap; }
  .modal-stat { text-align: center; }
  .modal-stat strong { font-family: 'Syne', sans-serif; font-size: 20px; font-weight: 700; display: block; }
  .modal-stat span { font-size: 12px; color: var(--muted); }
  .modal-close {
    background: var(--surface);
    border: 1px solid var(--border);
    color: var(--text);
    width: 36px; height: 36px;
    border-radius: 50%;
    font-size: 18px;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    flex-shrink: 0;
    transition: all 0.15s;
    margin-left: auto;
  }
  .modal-close:hover { background: var(--border); }
  .modal-body { padding: 24px 28px; }
  .modal-section { margin-bottom: 24px; }
  .modal-section-title {
    font-family: 'Syne', sans-serif;
    font-size: 11px;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1.2px;
    color: var(--muted);
    margin-bottom: 12px;
  }
  .verify-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; }
  .verify-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 12px 14px;
    display: flex;
    align-items: center;
    gap: 10px;
  }
  .verify-icon { font-size: 18px; }
  .verify-label { font-size: 13px; color: var(--muted); }
  .verify-val { font-size: 13px; font-weight: 500; }
  .verified-badge {
    margin-left: auto;
    background: #0d2010;
    border: 1px solid #2e5a20;
    color: var(--accent);
    font-size: 11px;
    padding: 2px 8px;
    border-radius: 100px;
  }
  .pending-badge {
    margin-left: auto;
    background: #2a1a00;
    border: 1px solid #5a3a00;
    color: var(--warn);
    font-size: 11px;
    padding: 2px 8px;
    border-radius: 100px;
  }
  .reviews-list { display: flex; flex-direction: column; gap: 12px; }
  .review-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 14px 16px;
  }
  .review-top { display: flex; align-items: center; gap: 10px; margin-bottom: 8px; }
  .reviewer-avatar {
    width: 32px; height: 32px;
    border-radius: 8px;
    background: #2a2a3a;
    display: flex; align-items: center; justify-content: center;
    font-size: 13px;
    font-weight: 700;
    color: #a0a0d0;
  }
  .reviewer-name { font-size: 14px; font-weight: 500; }
  .review-date { font-size: 12px; color: var(--muted); margin-left: auto; }
  .review-text { font-size: 14px; color: var(--muted); line-height: 1.6; }
  .modal-actions {
    padding: 0 28px 28px;
    display: flex;
    gap: 10px;
  }
  .btn-hire {
    flex: 1;
    background: var(--accent);
    color: #0d0f0e;
    border: none;
    padding: 14px;
    border-radius: 12px;
    font-size: 15px;
    font-weight: 700;
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    transition: all 0.15s;
  }
  .btn-hire:hover { background: #caff70; }
  .btn-msg {
    background: var(--surface);
    border: 1px solid var(--border);
    color: var(--text);
    padding: 14px 24px;
    border-radius: 12px;
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    font-family: 'DM Sans', sans-serif;
    transition: all 0.15s;
  }
  .btn-msg:hover { border-color: var(--accent2); color: var(--accent2); }
  .skill-id-chip {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 100px;
    padding: 5px 12px 5px 8px;
    font-size: 12px;
    color: var(--muted);
  }
  .skill-id-chip code {
    font-family: 'DM Mono', monospace;
    color: var(--accent2);
    font-size: 12px;
  }

  /* EMPTY STATE */
  .stats-bar {
    max-width: 1200px;
    margin: 0 auto 0;
    padding: 24px 40px;
    display: flex;
    gap: 32px;
    border-bottom: 1px solid var(--border);
  }
  .stat-item { display: flex; align-items: center; gap: 10px; }
  .stat-num {
    font-family: 'Syne', sans-serif;
    font-size: 22px;
    font-weight: 800;
    color: var(--accent);
  }
  .stat-desc { font-size: 13px; color: var(--muted); line-height: 1.4; }

  /* SCROLLBAR */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: transparent; }
  ::-webkit-scrollbar-thumb { background: var(--border); border-radius: 10px; }

  @media (max-width: 900px) {
    .main-layout { grid-template-columns: 1fr; }
    .sidebar { position: static; }
    nav, .hero, .stats-bar, .main-layout { padding-left: 20px; padding-right: 20px; }
    .verify-grid { grid-template-columns: 1fr; }
  }
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="logo">Work<span>Link</span></div>
  <div class="nav-links">
    <span class="badge-role">Client View</span>
    <button class="nav-pill nav-ghost">How it works</button>
    <button class="nav-pill nav-outline">Post a Job</button>
    <button class="nav-pill nav-cta">Sign In</button>
  </div>
</nav>

<!-- STATS BAR -->
<div class="stats-bar">
  <div class="stat-item">
    <div class="stat-num">2,841</div>
    <div class="stat-desc">Verified<br>Workers</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">14</div>
    <div class="stat-desc">Skill<br>Categories</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">98%</div>
    <div class="stat-desc">ID<br>Verified</div>
  </div>
  <div class="stat-item">
    <div class="stat-num">4.8★</div>
    <div class="stat-desc">Avg<br>Rating</div>
  </div>
</div>

<!-- HERO -->
<div class="hero">
  <div class="hero-eyebrow"><div class="dot"></div> Open to Work — Available Now</div>
  <h1>Find verified,<br><em>skilled workers</em><br>near you.</h1>
  <p>Browse electricians, plumbers, mechanics, drivers and more — every worker is ID-verified with Aadhaar and carries their skill certificate.</p>
  <div class="search-wrap">
    <div class="search-box">
      <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="M21 21l-4.35-4.35"/></svg>
      <input type="text" placeholder="Search by skill, name or ID…"/>
    </div>
    <div class="search-box" style="flex:0 0 auto; min-width:180px;">
      <svg width="16" height="16" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24"><path d="M12 2C8.13 2 5 5.13 5 9c0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><circle cx="12" cy="9" r="2.5"/></svg>
      <input type="text" placeholder="Kochi, Kerala"/>
    </div>
    <button class="hire-btn" style="padding:13px 24px; border-radius:10px;">Search</button>
  </div>
  <div class="filter-row" style="margin-top:16px;">
    <span class="filter-label">Category:</span>
    <button class="chip active" onclick="filterChip(this)">All</button>
    <button class="chip" onclick="filterChip(this)">⚡ Electrician</button>
    <button class="chip" onclick="filterChip(this)">❄️ AC Mechanic</button>
    <button class="chip" onclick="filterChip(this)">🚿 Plumber</button>
    <button class="chip" onclick="filterChip(this)">🚗 Driver</button>
    <button class="chip" onclick="filterChip(this)">🌿 Gardener</button>
    <button class="chip" onclick="filterChip(this)">🧹 Car Wash</button>
  </div>
</div>

<!-- MAIN LAYOUT -->
<div class="main-layout">

  <!-- SIDEBAR -->
  <aside class="sidebar">
    <div class="sidebar-section">
      <div class="sidebar-title">Availability</div>
      <div class="filter-option" onclick="toggleCheck(this)">
        <div class="fcheck on"></div>
        <span class="fopt-label">Open to Work</span>
        <span class="fopt-count">142</span>
      </div>
      <div class="filter-option" onclick="toggleCheck(this)">
        <div class="fcheck"></div>
        <span class="fopt-label">Available Today</span>
        <span class="fopt-count">68</span>
      </div>
      <div class="filter-option" onclick="toggleCheck(this)">
        <div class="fcheck"></div>
        <span class="fopt-label">Weekend Available</span>
        <span class="fopt-count">94</span>
      </div>
    </div>

    <div class="sidebar-section">
      <div class="sidebar-title">Verification</div>
      <div class="filter-option" onclick="toggleCheck(this)">
        <div class="fcheck on"></div>
        <span class="fopt-label">Aadhaar Verified</span>
        <span class="fopt-count">201</span>
      </div>
      <div class="filter-option" onclick="toggleCheck(this)">
        <div class="fcheck on"></div>
        <span class="fopt-label">License Uploaded</span>
        <span class="fopt-count">158</span>
      </div>
      <div class="filter-option" onclick="toggleCheck(this)">
        <div class="fcheck"></div>
        <span class="fopt-label">Background Checked</span>
        <span class="fopt-count">89</span>
      </div>
    </div>

    <div class="sidebar-section">
      <div class="sidebar-title">Min. Rating</div>
      <div class="stars-filter">
        <div class="star-row" onclick="toggleStar(this)">
          <div class="fcheck"></div>
          <span class="stars">★★★★★</span>
          <span class="fopt-label" style="font-size:12px;">5 only</span>
          <span class="fopt-count">34</span>
        </div>
        <div class="star-row" onclick="toggleStar(this)">
          <div class="fcheck on"></div>
          <span class="stars">★★★★☆</span>
          <span class="fopt-label" style="font-size:12px;">4 & up</span>
          <span class="fopt-count">112</span>
        </div>
        <div class="star-row" onclick="toggleStar(this)">
          <div class="fcheck"></div>
          <span class="stars">★★★☆☆</span>
          <span class="fopt-label" style="font-size:12px;">3 & up</span>
          <span class="fopt-count">189</span>
        </div>
      </div>
    </div>

    <div class="sidebar-section">
      <div class="sidebar-title">Day Rate (₹)</div>
      <div style="padding:4px 0 10px;">
        <input type="range" min="200" max="2000" value="1200" id="rate-slider" style="width:100%; accent-color: var(--accent);" oninput="document.getElementById('rate-val').textContent='₹'+this.value"/>
        <div style="display:flex;justify-content:space-between;font-size:12px;color:var(--muted);margin-top:6px;">
          <span>₹200</span>
          <span id="rate-val" style="color:var(--accent);font-weight:600;">₹1200</span>
          <span>₹2000+</span>
        </div>
      </div>
    </div>
  </aside>

  <!-- CARDS -->
  <div>
    <div class="cards-header">
      <div class="result-count"><strong>48 workers</strong> found near Kochi</div>
      <select class="sort-select">
        <option>Sort: Top Rated</option>
        <option>Sort: Nearest</option>
        <option>Sort: Lowest Rate</option>
        <option>Sort: Most Reviews</option>
      </select>
    </div>
    <div class="cards-grid" id="cards-grid">

      <!-- Card 1 -->
      <div class="talent-card" onclick="openModal('ravi')">
        <div class="otw-badge">● Open to Work</div>
        <div class="card-top">
          <div class="avatar avatar-verified" style="background:#1a2e1a; color:#b8f55a;">RK</div>
          <div class="card-meta">
            <div class="card-name">Ravi Kumar</div>
            <div class="card-role">⚡ Senior Electrician</div>
            <div class="card-rating"><span class="stars">★★★★★</span><span class="rating-num">4.9</span><span class="rating-count">(84 jobs)</span></div>
          </div>
        </div>
        <div class="card-divider"></div>
        <div class="card-body">
          <div class="location-row">📍 Ernakulam · 2.3 km away</div>
          <div class="card-skills">
            <span class="skill-tag">Wiring</span>
            <span class="skill-tag">Panel work</span>
            <span class="skill-tag">Solar</span>
          </div>
        </div>
        <div class="card-footer">
          <div class="rate">₹850 <span>/ day</span></div>
          <button class="hire-btn">View Profile</button>
        </div>
      </div>

      <!-- Card 2 -->
      <div class="talent-card" onclick="openModal('arjun')">
        <div class="otw-badge">● Open to Work</div>
        <div class="card-top">
          <div class="avatar avatar-verified" style="background:#1a1a2e; color:#7ab4ff;">AM</div>
          <div class="card-meta">
            <div class="card-name">Arjun Menon</div>
            <div class="card-role">❄️ AC Mechanic</div>
            <div class="card-rating"><span class="stars">★★★★★</span><span class="rating-num">4.8</span><span class="rating-count">(61 jobs)</span></div>
          </div>
        </div>
        <div class="card-divider"></div>
        <div class="card-body">
          <div class="location-row">📍 Kakkanad · 5.1 km away</div>
          <div class="card-skills">
            <span class="skill-tag">AC Service</span>
            <span class="skill-tag">Installation</span>
            <span class="skill-tag">Gas Refill</span>
          </div>
        </div>
        <div class="card-footer">
          <div class="rate">₹700 <span>/ day</span></div>
          <button class="hire-btn">View Profile</button>
        </div>
      </div>

      <!-- Card 3 -->
      <div class="talent-card" onclick="openModal('suresh')">
        <div class="card-top">
          <div class="avatar avatar-verified" style="background:#2e1a1a; color:#ff9a7a;">SP</div>
          <div class="card-meta">
            <div class="card-name">Suresh Pillai</div>
            <div class="card-role">🚿 Plumber</div>
            <div class="card-rating"><span class="stars">★★★★☆</span><span class="rating-num">4.5</span><span class="rating-count">(39 jobs)</span></div>
          </div>
        </div>
        <div class="card-divider"></div>
        <div class="card-body">
          <div class="location-row">📍 Aluva · 8.7 km away</div>
          <div class="card-skills">
            <span class="skill-tag">Pipe Fitting</span>
            <span class="skill-tag">Bathroom</span>
            <span class="skill-tag">Leaks</span>
          </div>
        </div>
        <div class="card-footer">
          <div class="rate">₹600 <span>/ day</span></div>
          <button class="hire-btn">View Profile</button>
        </div>
      </div>

      <!-- Card 4 -->
      <div class="talent-card" onclick="openModal('biju')">
        <div class="otw-badge">● Open to Work</div>
        <div class="card-top">
          <div class="avatar avatar-verified" style="background:#1c2a1a; color:#80e87a;">BT</div>
          <div class="card-meta">
            <div class="card-name">Biju Thomas</div>
            <div class="card-role">🚗 Driver + Own Car</div>
            <div class="card-rating"><span class="stars">★★★★★</span><span class="rating-num">5.0</span><span class="rating-count">(120 jobs)</span></div>
          </div>
        </div>
        <div class="card-divider"></div>
        <div class="card-body">
          <div class="location-row">📍 Thrippunithura · 3.9 km away</div>
          <div class="card-skills">
            <span class="skill-tag">Own Car (Swift)</span>
            <span class="skill-tag">Outstation</span>
            <span class="skill-tag">Night OK</span>
          </div>
        </div>
        <div class="card-footer">
          <div class="rate">₹1,100 <span>/ day</span></div>
          <button class="hire-btn">View Profile</button>
        </div>
      </div>

      <!-- Card 5 -->
      <div class="talent-card" onclick="openModal('priya')">
        <div class="card-top">
          <div class="avatar avatar-verified" style="background:#2a1a2a; color:#e07aff;">PN</div>
          <div class="card-meta">
            <div class="card-name">Priya Nair</div>
            <div class="card-role">🌿 Gardener</div>
            <div class="card-rating"><span class="stars">★★★★☆</span><span class="rating-num">4.7</span><span class="rating-count">(28 jobs)</span></div>
          </div>
        </div>
        <div class="card-divider"></div>
        <div class="card-body">
          <div class="location-row">📍 Edappally · 1.8 km away</div>
          <div class="card-skills">
            <span class="skill-tag">Landscaping</span>
            <span class="skill-tag">Pruning</span>
            <span class="skill-tag">Organic</span>
          </div>
        </div>
        <div class="card-footer">
          <div class="rate">₹450 <span>/ day</span></div>
          <button class="hire-btn">View Profile</button>
        </div>
      </div>

      <!-- Card 6 -->
      <div class="talent-card" onclick="openModal('anoop')">
        <div class="otw-badge">● Open to Work</div>
        <div class="card-top">
          <div class="avatar avatar-verified" style="background:#1a2020; color:#5affd4;">AV</div>
          <div class="card-meta">
            <div class="card-name">Anoop Varghese</div>
            <div class="card-role">🧹 Car Wash Specialist</div>
            <div class="card-rating"><span class="stars">★★★★☆</span><span class="rating-num">4.6</span><span class="rating-count">(54 jobs)</span></div>
          </div>
        </div>
        <div class="card-divider"></div>
        <div class="card-body">
          <div class="location-row">📍 Vyttila · 4.2 km away</div>
          <div class="card-skills">
            <span class="skill-tag">Detailing</span>
            <span class="skill-tag">Interior</span>
            <span class="skill-tag">Doorstep</span>
          </div>
        </div>
        <div class="card-footer">
          <div class="rate">₹400 <span>/ day</span></div>
          <button class="hire-btn">View Profile</button>
        </div>
      </div>

    </div>
  </div>
</div>

<!-- MODAL -->
<div class="modal-overlay" id="modal-overlay" onclick="closeModalBg(event)">
  <div class="modal" id="modal">
    <div class="modal-header">
      <div class="modal-avatar" id="m-avatar" style="background:#1a2e1a;color:#b8f55a;">RK</div>
      <div class="modal-meta">
        <div style="display:flex;align-items:center;gap:10px;flex-wrap:wrap;">
          <div class="modal-name" id="m-name">Ravi Kumar</div>
          <span class="otw-badge" id="m-otw" style="position:static;">● Open to Work</span>
        </div>
        <div class="modal-role" id="m-role">⚡ Senior Electrician</div>
        <div style="display:flex;align-items:center;gap:8px;flex-wrap:wrap;">
          <div class="card-rating"><span class="stars" id="m-stars">★★★★★</span><span class="rating-num" id="m-rating">4.9</span><span class="rating-count" id="m-rcount">(84 jobs)</span></div>
          <div class="skill-id-chip">Skill ID: <code id="m-skillid">WL-EL-00142</code></div>
        </div>
      </div>
      <button class="modal-close" onclick="closeModal()">✕</button>
    </div>

    <div class="modal-body">

      <!-- Stats -->
      <div class="modal-stats" style="margin-bottom:20px; background:var(--surface); border:1px solid var(--border); border-radius:12px; padding:16px; display:flex; gap:0; justify-content:space-around;">
        <div class="modal-stat"><strong id="m-jobs">84</strong><span>Jobs Done</span></div>
        <div style="width:1px;background:var(--border);"></div>
        <div class="modal-stat"><strong id="m-exp">6 yrs</strong><span>Experience</span></div>
        <div style="width:1px;background:var(--border);"></div>
        <div class="modal-stat"><strong id="m-rate">₹850</strong><span>Day Rate</span></div>
        <div style="width:1px;background:var(--border);"></div>
        <div class="modal-stat"><strong id="m-loc">2.3 km</strong><span>Away</span></div>
      </div>

      <!-- About -->
      <div class="modal-section">
        <div class="modal-section-title">About</div>
        <p id="m-about" style="font-size:14px;color:var(--muted);line-height:1.7;">Experienced electrician with 6 years in residential and commercial wiring, solar installations, and panel work. Available for both short and long-term projects. Fully licensed and Aadhaar verified.</p>
      </div>

      <!-- Verification -->
      <div class="modal-section">
        <div class="modal-section-title">Verification & Documents</div>
        <div class="verify-grid">
          <div class="verify-item">
            <span class="verify-icon">🪪</span>
            <div>
              <div class="verify-label">Aadhaar UID</div>
              <div class="verify-val">XXXX-XXXX-8421</div>
            </div>
            <span class="verified-badge">✓ Verified</span>
          </div>
          <div class="verify-item">
            <span class="verify-icon">📋</span>
            <div>
              <div class="verify-label">Skill Certificate</div>
              <div class="verify-val">ITI Electrician</div>
            </div>
            <span class="verified-badge">✓ Uploaded</span>
          </div>
          <div class="verify-item">
            <span class="verify-icon">🪪</span>
            <div>
              <div class="verify-label">Contractor License</div>
              <div class="verify-val">KL-ELEC-2019</div>
            </div>
            <span class="verified-badge">✓ Valid</span>
          </div>
          <div class="verify-item">
            <span class="verify-icon">📸</span>
            <div>
              <div class="verify-label">Background Check</div>
              <div class="verify-val">Police Clearance</div>
            </div>
            <span class="pending-badge">⏳ Pending</span>
          </div>
        </div>
      </div>

      <!-- Reviews -->
      <div class="modal-section">
        <div class="modal-section-title">Client Reviews</div>
        <div class="reviews-list">
          <div class="review-item">
            <div class="review-top">
              <div class="reviewer-avatar">SR</div>
              <div>
                <div class="reviewer-name">Sreelekha R.</div>
                <div class="stars" style="font-size:12px;">★★★★★</div>
              </div>
              <div class="review-date">Apr 2025</div>
            </div>
            <div class="review-text">Ravi did a fantastic job rewiring our kitchen. On time, clean work, explained everything clearly. Will definitely hire again.</div>
          </div>
          <div class="review-item">
            <div class="review-top">
              <div class="reviewer-avatar">MJ</div>
              <div>
                <div class="reviewer-name">Mohammed J.</div>
                <div class="stars" style="font-size:12px;">★★★★★</div>
              </div>
              <div class="review-date">Mar 2025</div>
            </div>
            <div class="review-text">Fixed our solar inverter issue in under 2 hours. Very professional and reasonably priced. Highly recommend.</div>
          </div>
          <div class="review-item">
            <div class="review-top">
              <div class="reviewer-avatar">AP</div>
              <div>
                <div class="reviewer-name">Asha P.</div>
                <div class="stars" style="font-size:12px;">★★★★☆</div>
              </div>
              <div class="review-date">Feb 2025</div>
            </div>
            <div class="review-text">Good work overall, arrived slightly late but communicated ahead. Work quality was excellent.</div>
          </div>
        </div>
      </div>
    </div>

    <div class="modal-actions">
      <button class="btn-hire">Hire Ravi — ₹850/day</button>
      <button class="btn-msg">💬 Message</button>
    </div>
  </div>
</div>

<script>
function filterChip(el) {
  document.querySelectorAll('.chip').forEach(c => c.classList.remove('active'));
  el.classList.add('active');
}
function toggleCheck(el) {
  const chk = el.querySelector('.fcheck');
  chk.classList.toggle('on');
}
function toggleStar(el) {
  document.querySelectorAll('.star-row .fcheck').forEach(c => c.classList.remove('on'));
  el.querySelector('.fcheck').classList.add('on');
}

const profiles = {
  ravi: { avatar:'RK', bg:'#1a2e1a', color:'#b8f55a', name:'Ravi Kumar', role:'⚡ Senior Electrician', stars:'★★★★★', rating:'4.9', rcount:'(84 jobs)', skillid:'WL-EL-00142', jobs:'84', exp:'6 yrs', rate:'₹850', loc:'2.3 km', about:'Experienced electrician with 6 years in residential and commercial wiring, solar installations, and panel work. Available for both short and long-term projects. Fully licensed and Aadhaar verified.', otw:true },
  arjun: { avatar:'AM', bg:'#1a1a2e', color:'#7ab4ff', name:'Arjun Menon', role:'❄️ AC Mechanic', stars:'★★★★★', rating:'4.8', rcount:'(61 jobs)', skillid:'WL-AC-00089', jobs:'61', exp:'4 yrs', rate:'₹700', loc:'5.1 km', about:'Certified AC technician specialising in split and window unit servicing, gas refilling, and fresh installations. Works with all major brands. Quick, clean, and reliable.', otw:true },
  suresh: { avatar:'SP', bg:'#2e1a1a', color:'#ff9a7a', name:'Suresh Pillai', role:'🚿 Plumber', stars:'★★★★☆', rating:'4.5', rcount:'(39 jobs)', skillid:'WL-PL-00214', jobs:'39', exp:'8 yrs', rate:'₹600', loc:'8.7 km', about:'Skilled plumber with 8 years experience in pipe fitting, bathroom renovation, and leak repairs. Takes on emergency and scheduled jobs. Uses quality materials and guarantees work for 30 days.', otw:false },
  biju: { avatar:'BT', bg:'#1c2a1a', color:'#80e87a', name:'Biju Thomas', role:'🚗 Driver + Own Car', stars:'★★★★★', rating:'5.0', rcount:'(120 jobs)', skillid:'WL-DR-00031', jobs:'120', exp:'10 yrs', rate:'₹1,100', loc:'3.9 km', about:'Professional driver with 10 years experience, own Maruti Swift Dzire. Available for outstation trips, airport transfers, and daily commutes. Night trips are fine. All documents current.', otw:true },
  priya: { avatar:'PN', bg:'#2a1a2a', color:'#e07aff', name:'Priya Nair', role:'🌿 Gardener', stars:'★★★★☆', rating:'4.7', rcount:'(28 jobs)', skillid:'WL-GD-00178', jobs:'28', exp:'3 yrs', rate:'₹450', loc:'1.8 km', about:'Passionate gardener with experience in residential and commercial landscaping. Specialises in organic methods, terrace gardens, and regular garden maintenance. Brings own tools.', otw:false },
  anoop: { avatar:'AV', bg:'#1a2020', color:'#5affd4', name:'Anoop Varghese', role:'🧹 Car Wash Specialist', stars:'★★★★☆', rating:'4.6', rcount:'(54 jobs)', skillid:'WL-CW-00099', jobs:'54', exp:'2 yrs', rate:'₹400', loc:'4.2 km', about:'Doorstep car washing and detailing service. Offers exterior wash, interior vacuum, and full detailing packages. Brings equipment and water. Eco-friendly products used.', otw:true }
};

function openModal(id) {
  const p = profiles[id];
  document.getElementById('m-avatar').textContent = p.avatar;
  document.getElementById('m-avatar').style.background = p.bg;
  document.getElementById('m-avatar').style.color = p.color;
  document.getElementById('m-name').textContent = p.name;
  document.getElementById('m-role').textContent = p.role;
  document.getElementById('m-stars').textContent = p.stars;
  document.getElementById('m-rating').textContent = p.rating;
  document.getElementById('m-rcount').textContent = p.rcount;
  document.getElementById('m-skillid').textContent = p.skillid;
  document.getElementById('m-jobs').textContent = p.jobs;
  document.getElementById('m-exp').textContent = p.exp;
  document.getElementById('m-rate').textContent = p.rate;
  document.getElementById('m-loc').textContent = p.loc;
  document.getElementById('m-about').textContent = p.about;
  const otw = document.getElementById('m-otw');
  otw.style.display = p.otw ? 'inline-flex' : 'none';
  document.querySelector('.btn-hire').textContent = 'Hire ' + p.name.split(' ')[0] + ' — ' + p.rate + '/day';
  document.getElementById('modal-overlay').classList.add('open');
  document.body.style.overflow = 'hidden';
}
function closeModal() {
  document.getElementById('modal-overlay').classList.remove('open');
  document.body.style.overflow = '';
}
function closeModalBg(e) {
  if (e.target === document.getElementById('modal-overlay')) closeModal();
}
document.addEventListener('keydown', e => { if (e.key === 'Escape') closeModal(); });
</script>
</body>
</html>
