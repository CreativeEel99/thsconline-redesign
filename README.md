# thsconline-redesign
Redesign of THSC online prototype for a school project
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>thsconline — Practice papers for the NSW HSC</title>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Sora:wght@700;800&display=swap" rel="stylesheet" />
  <style>
    *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

    :root {
      --bg:        #f4f3ff;
      --surface:   #ffffff;
      --indigo:    #4338ca;
      --indigo-lt: #6366f1;
      --indigo-xl: #e0e7ff;
      --text:      #1e1b4b;
      --muted:     #6b7280;
      --border:    #e5e7eb;
      --radius:    16px;
    }

    body {
      font-family: 'Inter', sans-serif;
      background: var(--bg);
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
    }

    /* ── NAV ── */
    nav {
      display: flex;
      align-items: center;
      justify-content: space-between;
      padding: 20px 48px;
      background: transparent;
      position: relative;
      z-index: 10;
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 10px;
      text-decoration: none;
      color: var(--text);
    }

    .logo-icon {
      width: 36px; height: 36px;
      background: var(--indigo);
      border-radius: 10px;
      display: flex; align-items: center; justify-content: center;
    }

    .logo-icon svg { color: #fff; }

    .logo-text {
      font-family: 'Inter', sans-serif;
      font-weight: 600;
      font-size: 1.05rem;
      letter-spacing: -0.02em;
    }

    .nav-right { display: flex; align-items: center; gap: 24px; }

    .nav-link {
      text-decoration: none;
      color: var(--muted);
      font-size: 0.9rem;
      font-weight: 500;
      display: flex;
      align-items: center;
      gap: 6px;
      transition: color 0.2s;
    }
    .nav-link:hover { color: var(--indigo); }

    .nav-upload {
      background: var(--indigo);
      color: #fff;
      padding: 9px 18px;
      border-radius: 10px;
      font-size: 0.875rem;
      font-weight: 500;
      text-decoration: none;
      transition: background 0.2s, transform 0.15s;
    }
    .nav-upload:hover { background: #3730a3; transform: translateY(-1px); }

    /* ── HERO ── */
    .hero {
      display: grid;
      grid-template-columns: 1fr 1fr;
      align-items: center;
      gap: 48px;
      padding: 48px 48px 64px;
      max-width: 1200px;
      margin: 0 auto;
    }

    .hero-left { max-width: 520px; }

    .eyebrow {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      background: var(--indigo-xl);
      color: var(--indigo);
      font-size: 0.78rem;
      font-weight: 600;
      letter-spacing: 0.06em;
      text-transform: uppercase;
      padding: 5px 12px;
      border-radius: 99px;
      margin-bottom: 20px;
    }

    .eyebrow-dot {
      width: 6px; height: 6px;
      background: var(--indigo-lt);
      border-radius: 50%;
    }

    h1 {
      font-family: 'Sora', sans-serif;
      font-size: clamp(2.2rem, 4vw, 3.2rem);
      font-weight: 800;
      line-height: 1.1;
      letter-spacing: -0.03em;
      color: var(--text);
      margin-bottom: 16px;
    }

    h1 span {
      color: var(--indigo-lt);
    }

    .hero-sub {
      font-size: 1rem;
      color: var(--muted);
      line-height: 1.65;
      margin-bottom: 32px;
      max-width: 400px;
    }

    /* ── SEARCH ── */
    .search-wrap {
      position: relative;
      margin-bottom: 20px;
    }

    .search-icon {
      position: absolute;
      left: 16px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--muted);
      pointer-events: none;
    }

    .search-input {
      width: 100%;
      padding: 14px 16px 14px 46px;
      border: 1.5px solid var(--border);
      border-radius: var(--radius);
      font-family: 'Inter', sans-serif;
      font-size: 0.95rem;
      background: var(--surface);
      color: var(--text);
      outline: none;
      transition: border-color 0.2s, box-shadow 0.2s;
      box-shadow: 0 1px 3px rgba(0,0,0,0.04);
    }
    .search-input::placeholder { color: var(--muted); }
    .search-input:focus {
      border-color: var(--indigo-lt);
      box-shadow: 0 0 0 3px rgba(99,102,241,0.12);
    }

    .search-btn {
      position: absolute;
      right: 8px;
      top: 50%;
      transform: translateY(-50%);
      background: var(--indigo);
      color: #fff;
      border: none;
      padding: 8px 16px;
      border-radius: 10px;
      font-family: 'Inter', sans-serif;
      font-size: 0.85rem;
      font-weight: 500;
      cursor: pointer;
      transition: background 0.2s;
    }
    .search-btn:hover { background: #3730a3; }

    .search-hint {
      font-size: 0.8rem;
      color: var(--muted);
    }

    .search-hint strong {
      color: var(--text);
      font-weight: 500;
    }

    /* ── YEAR CARDS ── */
    .hero-right {}

    .cards-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 16px;
    }

    .year-card {
      background: var(--surface);
      border: 1.5px solid var(--border);
      border-radius: var(--radius);
      padding: 28px 24px;
      text-decoration: none;
      color: var(--text);
      display: flex;
      flex-direction: column;
      gap: 20px;
      transition: transform 0.2s, box-shadow 0.2s, border-color 0.2s;
      cursor: pointer;
    }

    .year-card:hover {
      transform: translateY(-3px);
      box-shadow: 0 8px 24px rgba(67,56,202,0.1);
      border-color: var(--indigo-lt);
    }

    .card-top {
      display: flex;
      align-items: flex-start;
      justify-content: space-between;
    }

    .card-icon {
      width: 44px; height: 44px;
      background: var(--indigo-xl);
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .card-icon svg { color: var(--indigo); }

    .card-arrow {
      color: var(--indigo-lt);
      opacity: 0;
      transform: translateX(-4px);
      transition: opacity 0.2s, transform 0.2s;
    }
    .year-card:hover .card-arrow {
      opacity: 1;
      transform: translateX(0);
    }

    .card-label {
      font-size: 0.72rem;
      font-weight: 600;
      letter-spacing: 0.07em;
      text-transform: uppercase;
      color: var(--muted);
    }

    .card-title {
      font-family: 'Sora', sans-serif;
      font-size: 1.2rem;
      font-weight: 700;
      letter-spacing: -0.02em;
      line-height: 1.25;
    }

    .card-count {
      font-size: 0.8rem;
      color: var(--muted);
    }

    /* card accent colors */
    .card-y9  .card-icon { background: #ede9fe; }
    .card-y9  .card-icon svg { color: #7c3aed; }
    .card-y10 .card-icon { background: #dbeafe; }
    .card-y10 .card-icon svg { color: #2563eb; }
    .card-y11 .card-icon { background: #dcfce7; }
    .card-y11 .card-icon svg { color: #16a34a; }
    .card-y12 .card-icon { background: #fef3c7; }
    .card-y12 .card-icon svg { color: #d97706; }

    /* ── STATS STRIP ── */
    .stats {
      background: var(--surface);
      border-top: 1px solid var(--border);
      border-bottom: 1px solid var(--border);
      padding: 24px 48px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 64px;
    }

    .stat { text-align: center; }

    .stat-num {
      font-family: 'Sora', sans-serif;
      font-size: 1.6rem;
      font-weight: 800;
      color: var(--indigo);
      letter-spacing: -0.03em;
    }

    .stat-label {
      font-size: 0.8rem;
      color: var(--muted);
      margin-top: 2px;
    }

    .stat-divider {
      width: 1px;
      height: 36px;
      background: var(--border);
    }

    /* ── BG BLOBS ── */
    .blob {
      position: fixed;
      border-radius: 50%;
      filter: blur(80px);
      opacity: 0.25;
      pointer-events: none;
      z-index: 0;
    }
    .blob-1 {
      width: 500px; height: 500px;
      background: #a5b4fc;
      bottom: -100px; left: -100px;
    }
    .blob-2 {
      width: 400px; height: 400px;
      background: #c7d2fe;
      top: -80px; right: -80px;
    }

    /* ── RESPONSIVE ── */
    @media (max-width: 768px) {
      nav { padding: 16px 20px; }
      .nav-upload { display: none; }
      .hero {
        grid-template-columns: 1fr;
        padding: 24px 20px 40px;
        gap: 32px;
      }
      .hero-left { max-width: 100%; }
      .stats { gap: 24px; padding: 20px; flex-wrap: wrap; }
      .stat-divider { display: none; }
    }

    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after { transition: none !important; }
    }
  </style>
</head>
<body>

  <!-- background blobs -->
  <div class="blob blob-1"></div>
  <div class="blob blob-2"></div>

  <!-- NAV -->
  <nav>
    <a href="#" class="logo">
      <div class="logo-icon">
        <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round">
          <path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/>
          <path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/>
        </svg>
      </div>
      <span class="logo-text">thsconline</span>
    </a>

    <div class="nav-right">
      <a href="#" class="nav-link">
        <svg width="15" height="15" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="12" cy="12" r="10"/><path d="M12 16v-4M12 8h.01"/></svg>
        About
      </a>
      <a href="#" class="nav-upload">↑ Upload papers</a>
    </div>
  </nav>

  <!-- HERO -->
  <main class="hero" style="position:relative;z-index:1;">

    <div class="hero-left">
      <div class="eyebrow">
        <span class="eyebrow-dot"></span>
        NSW curriculum
      </div>

      <h1>Practice papers<br>for the <span>NSW HSC</span></h1>

      <p class="hero-sub">
        Trial papers and past assessments from schools across New South Wales — free, forever.
      </p>

      <div class="search-wrap">
        <svg class="search-icon" width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35"/></svg>
        <input class="search-input" type="text" placeholder="Search subjects, e.g. "Physics", "English Adv"…" />
        <button class="search-btn">Search</button>
      </div>

      <p class="search-hint">Popular: <strong>Maths Ext 2</strong> · <strong>English Advanced</strong> · <strong>Chemistry</strong></p>
    </div>

    <div class="hero-right">
      <div class="cards-grid">

        <a href="#" class="year-card card-y9">
          <div class="card-top">
            <div class="card-icon">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>
            </div>
            <svg class="card-arrow" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
          <div>
            <div class="card-label">Stage 5</div>
            <div class="card-title">Year 9</div>
            <div class="card-count">12 subjects</div>
          </div>
        </a>

        <a href="#" class="year-card card-y10">
          <div class="card-top">
            <div class="card-icon">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M2 3h6a4 4 0 0 1 4 4v14a3 3 0 0 0-3-3H2z"/><path d="M22 3h-6a4 4 0 0 0-4 4v14a3 3 0 0 1 3-3h7z"/></svg>
            </div>
            <svg class="card-arrow" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
          <div>
            <div class="card-label">Stage 5</div>
            <div class="card-title">Year 10</div>
            <div class="card-count">14 subjects</div>
          </div>
        </a>

        <a href="#" class="year-card card-y11">
          <div class="card-top">
            <div class="card-icon">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M12 20h9"/><path d="M16.5 3.5a2.121 2.121 0 0 1 3 3L7 19l-4 1 1-4L16.5 3.5z"/></svg>
            </div>
            <svg class="card-arrow" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
          <div>
            <div class="card-label">Preliminary</div>
            <div class="card-title">Year 11</div>
            <div class="card-count">25 subjects</div>
          </div>
        </a>

        <a href="#" class="year-card card-y12">
          <div class="card-top">
            <div class="card-icon">
              <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 10v6M2 10l10-5 10 5-10 5z"/><path d="M6 12v5c3 3 9 3 12 0v-5"/></svg>
            </div>
            <svg class="card-arrow" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M5 12h14M12 5l7 7-7 7"/></svg>
          </div>
          <div>
            <div class="card-label">HSC</div>
            <div class="card-title">Year 12</div>
            <div class="card-count">28 subjects</div>
          </div>
        </a>

      </div>
    </div>

  </main>

  <!-- STATS -->
  <div class="stats">
    <div class="stat">
      <div class="stat-num">6,000+</div>
      <div class="stat-label">Papers available</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat">
      <div class="stat-num">28</div>
      <div class="stat-label">HSC subjects</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat">
      <div class="stat-num">100%</div>
      <div class="stat-label">Free, always</div>
    </div>
    <div class="stat-divider"></div>
    <div class="stat">
      <div class="stat-num">NSW</div>
      <div class="stat-label">Schools statewide</div>
    </div>
  </div>

</body>
</html>
