<!DOCTYPE html>
<html lang="ka">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Valuta.ge — საფინანსო პლატფორმა</title>
<link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700;900&family=DM+Sans:wght@300;400;500&display=swap" rel="stylesheet">
<style>
  :root {
    --ink: #0a0a0f;
    --surface: #111118;
    --panel: #18181f;
    --border: rgba(255,255,255,0.07);
    --gold: #c9a96e;
    --gold-light: #e8c98a;
    --text: #e8e6e0;
    --muted: #7a7a8a;
    --accent: #4f8ef7;
    --success: #3ecf8e;
    --radius: 16px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'DM Sans', sans-serif;
    background: var(--ink);
    color: var(--text);
    min-height: 100vh;
    overflow-x: hidden;
  }

  /* ─── NOISE OVERLAY ─── */
  body::before {
    content: '';
    position: fixed; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)' opacity='1'/%3E%3C/svg%3E");
    opacity: 0.025;
    pointer-events: none;
    z-index: 9999;
  }

  /* ─── HEADER ─── */
  header {
    position: sticky; top: 0; z-index: 100;
    background: rgba(10,10,15,0.85);
    backdrop-filter: blur(20px);
    border-bottom: 1px solid var(--border);
    padding: 0 40px;
  }

  .header-inner {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 72px;
  }

  .logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.6rem;
    font-weight: 900;
    letter-spacing: -0.02em;
    color: var(--gold);
    text-decoration: none;
  }

  .logo span { color: var(--text); }

  nav.main-nav { display: flex; gap: 8px; }

  nav.main-nav a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.85rem;
    font-weight: 500;
    padding: 8px 14px;
    border-radius: 8px;
    transition: all 0.2s;
    letter-spacing: 0.02em;
  }

  nav.main-nav a:hover, nav.main-nav a.active {
    color: var(--text);
    background: var(--panel);
  }

  .header-socials { display: flex; gap: 12px; align-items: center; }

  .header-socials a {
    width: 32px; height: 32px;
    border-radius: 8px;
    border: 1px solid var(--border);
    display: flex; align-items: center; justify-content: center;
    color: var(--muted);
    text-decoration: none;
    font-size: 0.7rem;
    font-weight: 700;
    transition: all 0.2s;
    letter-spacing: 0.05em;
  }

  .header-socials a:hover { color: var(--gold); border-color: var(--gold); }

  /* ─── HERO BAND ─── */
  .hero-band {
    background: linear-gradient(135deg, #0d0d14 0%, #1a1428 50%, #0d1420 100%);
    padding: 80px 40px 60px;
    position: relative;
    overflow: hidden;
  }

  .hero-band::before {
    content: '';
    position: absolute;
    top: -200px; right: -100px;
    width: 600px; height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(201,169,110,0.08) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-band::after {
    content: '';
    position: absolute;
    bottom: -150px; left: -50px;
    width: 400px; height: 400px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(79,142,247,0.06) 0%, transparent 70%);
    pointer-events: none;
  }

  .hero-inner {
    max-width: 1280px;
    margin: 0 auto;
    position: relative; z-index: 1;
  }

  .hero-eyebrow {
    font-size: 0.72rem;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    color: var(--gold);
    margin-bottom: 16px;
    font-weight: 500;
  }

  .hero-title {
    font-family: 'Playfair Display', serif;
    font-size: clamp(2.4rem, 5vw, 4rem);
    font-weight: 900;
    line-height: 1.1;
    letter-spacing: -0.03em;
    margin-bottom: 24px;
  }

  .hero-title em {
    font-style: normal;
    color: var(--gold);
  }

  .hero-sub {
    color: var(--muted);
    font-size: 1rem;
    max-width: 500px;
    line-height: 1.7;
  }

  /* ─── MAIN LAYOUT ─── */
  .main-wrapper {
    max-width: 1280px;
    margin: 0 auto;
    padding: 48px 40px;
    display: grid;
    grid-template-columns: 1fr 320px;
    gap: 32px;
  }

  .content-col { min-width: 0; }
  .sidebar-col { min-width: 0; }

  /* ─── SECTION LABEL ─── */
  .section-label {
    display: flex;
    align-items: center;
    gap: 12px;
    margin-bottom: 20px;
  }

  .section-label h2 {
    font-family: 'Playfair Display', serif;
    font-size: 1.1rem;
    font-weight: 700;
    letter-spacing: -0.01em;
  }

  .section-label::after {
    content: '';
    flex: 1;
    height: 1px;
    background: var(--border);
  }

  /* ─── PRODUCT CARDS GRID ─── */
  .cards-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 16px;
    margin-bottom: 40px;
  }

  .product-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    overflow: hidden;
    cursor: pointer;
    transition: transform 0.25s, border-color 0.25s, box-shadow 0.25s;
    position: relative;
  }

  .product-card:hover {
    transform: translateY(-4px);
    border-color: rgba(201,169,110,0.3);
    box-shadow: 0 20px 60px rgba(0,0,0,0.5);
  }

  .card-img {
    width: 100%; height: 160px;
    object-fit: cover;
    display: block;
    filter: grayscale(30%) brightness(0.6);
    transition: filter 0.3s;
  }

  .product-card:hover .card-img { filter: grayscale(10%) brightness(0.75); }

  .card-body {
    padding: 20px;
  }

  .card-tag {
    font-size: 0.65rem;
    letter-spacing: 0.15em;
    text-transform: uppercase;
    color: var(--gold);
    font-weight: 600;
    margin-bottom: 6px;
  }

  .card-title {
    font-family: 'Playfair Display', serif;
    font-size: 1.15rem;
    font-weight: 700;
    margin-bottom: 14px;
  }

  .card-links { display: flex; flex-direction: column; gap: 6px; }

  .card-links a {
    color: var(--muted);
    text-decoration: none;
    font-size: 0.82rem;
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 6px 0;
    border-bottom: 1px solid var(--border);
    transition: color 0.2s;
  }

  .card-links a:last-child { border-bottom: none; }

  .card-links a::before {
    content: '→';
    font-size: 0.7rem;
    color: var(--gold);
    transition: transform 0.2s;
  }

  .card-links a:hover { color: var(--text); }
  .card-links a:hover::before { transform: translateX(3px); }

  .card-arrow {
    position: absolute;
    top: 16px; right: 16px;
    width: 36px; height: 36px;
    border-radius: 50%;
    background: rgba(201,169,110,0.15);
    display: flex; align-items: center; justify-content: center;
    color: var(--gold);
    font-size: 1rem;
    transition: background 0.2s;
  }

  .product-card:hover .card-arrow { background: var(--gold); color: var(--ink); }

  /* Online card (full-width link card) */
  .card-online {
    grid-column: span 2;
    background: linear-gradient(135deg, #1a1428, #14203a);
    border: 1px solid rgba(79,142,247,0.2);
  }

  .card-online:hover { border-color: rgba(79,142,247,0.5); }

  .card-online .card-body {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 28px;
  }

  .card-online .card-tag { color: var(--accent); }

  .online-badge {
    background: rgba(79,142,247,0.15);
    border: 1px solid rgba(79,142,247,0.3);
    border-radius: 24px;
    padding: 10px 20px;
    font-size: 0.82rem;
    color: var(--accent);
    font-weight: 500;
    white-space: nowrap;
  }

  /* ─── CALCULATORS ─── */
  .calcs-section { margin-bottom: 40px; }

  .calc-tabs {
    display: flex;
    gap: 4px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 12px;
    padding: 4px;
    margin-bottom: 24px;
    width: fit-content;
  }

  .calc-tab-btn {
    background: none;
    border: none;
    color: var(--muted);
    padding: 8px 18px;
    border-radius: 8px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.82rem;
    font-weight: 500;
    cursor: pointer;
    transition: all 0.2s;
  }

  .calc-tab-btn.active {
    background: var(--panel);
    color: var(--text);
    box-shadow: 0 2px 8px rgba(0,0,0,0.3);
  }

  .calc-panel { display: none; }
  .calc-panel.active { display: block; }

  .calc-card {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 28px;
  }

  .calc-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 16px;
    margin-bottom: 16px;
  }

  .calc-row-2 { grid-template-columns: 1fr 1fr; }
  .calc-row-full { grid-template-columns: 1fr; }

  .field-group { display: flex; flex-direction: column; gap: 8px; }

  .field-label {
    font-size: 0.72rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    color: var(--muted);
    font-weight: 500;
  }

  .field-input {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.92rem;
    padding: 12px 14px;
    outline: none;
    transition: border-color 0.2s;
    width: 100%;
  }

  .field-input:focus { border-color: var(--gold); }
  .field-input:disabled { opacity: 0.5; cursor: not-allowed; background: rgba(255,255,255,0.02); }

  .field-input[type="range"] {
    padding: 6px 0;
    background: none;
    border: none;
    cursor: pointer;
    accent-color: var(--gold);
  }

  .input-with-unit {
    position: relative;
    display: flex;
    align-items: center;
  }

  .input-with-unit .field-input { padding-right: 40px; }

  .input-unit {
    position: absolute;
    right: 12px;
    color: var(--muted);
    font-size: 0.8rem;
    pointer-events: none;
  }

  .calc-btn {
    width: 100%;
    background: linear-gradient(135deg, var(--gold), var(--gold-light));
    color: var(--ink);
    border: none;
    border-radius: 10px;
    padding: 13px 20px;
    font-family: 'DM Sans', sans-serif;
    font-size: 0.88rem;
    font-weight: 700;
    cursor: pointer;
    letter-spacing: 0.04em;
    text-transform: uppercase;
    transition: opacity 0.2s, transform 0.1s;
  }

  .calc-btn:hover { opacity: 0.9; }
  .calc-btn:active { transform: scale(0.98); }

  .calc-results {
    margin-top: 20px;
    padding-top: 20px;
    border-top: 1px solid var(--border);
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 12px;
  }

  .result-item {
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    padding: 14px;
  }

  .result-label {
    font-size: 0.68rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--muted);
    margin-bottom: 6px;
  }

  .result-value {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    font-weight: 700;
    color: var(--gold);
  }

  /* Loan table */
  .loan-table-wrap {
    margin-top: 20px;
    overflow: auto;
    max-height: 320px;
    border-radius: 10px;
    border: 1px solid var(--border);
  }

  .loan-table {
    width: 100%;
    border-collapse: collapse;
    font-size: 0.82rem;
  }

  .loan-table thead {
    position: sticky; top: 0;
    background: var(--panel);
  }

  .loan-table th {
    padding: 12px 14px;
    text-align: left;
    color: var(--muted);
    font-weight: 500;
    font-size: 0.7rem;
    letter-spacing: 0.08em;
    text-transform: uppercase;
    border-bottom: 1px solid var(--border);
  }

  .loan-table td {
    padding: 10px 14px;
    border-bottom: 1px solid rgba(255,255,255,0.03);
    color: var(--text);
  }

  .loan-table tbody tr:hover td { background: rgba(255,255,255,0.02); }

  .loan-table td:first-child { color: var(--muted); }

  .empty-state {
    text-align: center;
    padding: 40px;
    color: var(--muted);
  }

  .empty-state .big-icon { font-size: 2.5rem; margin-bottom: 12px; opacity: 0.5; }
  .empty-state p { font-size: 0.85rem; line-height: 1.6; max-width: 280px; margin: 0 auto; }

  /* ─── SIDEBAR ─── */
  .sidebar-col { display: flex; flex-direction: column; gap: 20px; }

  /* Currency Widget */
  .currency-widget {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 24px;
  }

  .widget-header {
    display: flex; align-items: center; justify-content: space-between;
    margin-bottom: 20px;
  }

  .widget-title {
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    font-weight: 700;
  }

  .widget-badge {
    font-size: 0.62rem;
    letter-spacing: 0.1em;
    text-transform: uppercase;
    color: var(--success);
    background: rgba(62,207,142,0.1);
    border: 1px solid rgba(62,207,142,0.2);
    padding: 3px 8px;
    border-radius: 20px;
  }

  .currency-tabs {
    display: flex;
    gap: 4px;
    background: var(--surface);
    border-radius: 8px;
    padding: 3px;
    margin-bottom: 16px;
  }

  .currency-tab {
    flex: 1;
    background: none;
    border: none;
    color: var(--muted);
    padding: 7px;
    border-radius: 6px;
    font-size: 0.78rem;
    font-family: 'DM Sans', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
    font-weight: 500;
  }

  .currency-tab.active { background: var(--panel); color: var(--text); }

  .currency-tab-panel { display: none; }
  .currency-tab-panel.active { display: block; }

  .currency-input-row {
    display: flex;
    align-items: center;
    gap: 10px;
    margin-bottom: 16px;
  }

  .flag-input-wrap {
    flex: 1;
    position: relative;
  }

  .flag-label {
    position: absolute;
    left: 10px; top: 50%;
    transform: translateY(-50%);
    font-size: 0.7rem;
    font-weight: 700;
    color: var(--gold);
    letter-spacing: 0.05em;
    pointer-events: none;
  }

  .flag-input-wrap .field-input { padding-left: 42px; }

  .eq-sign { color: var(--muted); font-size: 1.1rem; flex-shrink: 0; }

  .currency-list { display: flex; flex-direction: column; gap: 8px; }

  .currency-row {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px 12px;
    background: var(--surface);
    border-radius: 8px;
    border: 1px solid var(--border);
    transition: border-color 0.2s;
  }

  .currency-row:hover { border-color: rgba(201,169,110,0.2); }

  .currency-info { display: flex; align-items: center; gap: 10px; }

  .currency-flag {
    width: 28px; height: 20px;
    border-radius: 4px;
    object-fit: cover;
    background: var(--border);
    display: flex; align-items: center; justify-content: center;
    font-size: 0.65rem;
    color: var(--muted);
  }

  .currency-name { font-size: 0.82rem; font-weight: 500; }
  .currency-code { font-size: 0.68rem; color: var(--muted); letter-spacing: 0.08em; }

  .currency-amount {
    font-family: 'Playfair Display', serif;
    font-size: 1rem;
    font-weight: 700;
    color: var(--text);
  }

  .currency-best { font-size: 0.62rem; color: var(--success); letter-spacing: 0.05em; text-transform: uppercase; }

  .select-org {
    width: 100%;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 8px;
    color: var(--text);
    font-family: 'DM Sans', sans-serif;
    font-size: 0.78rem;
    padding: 9px 12px;
    outline: none;
    cursor: pointer;
    margin-bottom: 14px;
    transition: border-color 0.2s;
  }

  .select-org:focus { border-color: var(--gold); }

  /* Savings mini-calc in sidebar */
  .savings-widget {
    background: var(--panel);
    border: 1px solid var(--border);
    border-radius: var(--radius);
    padding: 24px;
  }

  .savings-sub-tabs {
    display: flex; gap: 4px;
    background: var(--surface);
    border-radius: 8px;
    padding: 3px;
    margin-bottom: 16px;
  }

  .savings-sub-tab {
    flex: 1;
    background: none; border: none;
    color: var(--muted);
    padding: 6px;
    border-radius: 5px;
    font-size: 0.7rem;
    font-family: 'DM Sans', sans-serif;
    cursor: pointer;
    transition: all 0.2s;
    font-weight: 500;
  }

  .savings-sub-tab.active { background: var(--panel); color: var(--text); }

  .savings-tab-panel { display: none; }
  .savings-tab-panel.active { display: block; }

  .savings-field { margin-bottom: 12px; }

  .range-display {
    display: flex; justify-content: space-between;
    font-size: 0.72rem; color: var(--muted); margin-top: 4px;
  }

  .savings-result {
    background: linear-gradient(135deg, rgba(201,169,110,0.08), rgba(201,169,110,0.04));
    border: 1px solid rgba(201,169,110,0.15);
    border-radius: 10px;
    padding: 14px;
    margin-top: 14px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .s-result-label { font-size: 0.65rem; text-transform: uppercase; letter-spacing: 0.08em; color: var(--muted); margin-bottom: 4px; }
  .s-result-val { font-family: 'Playfair Display', serif; font-size: 1.05rem; font-weight: 700; color: var(--gold); }

  /* ─── FOOTER ─── */
  footer {
    background: var(--surface);
    border-top: 1px solid var(--border);
    padding: 40px;
    margin-top: 40px;
  }

  .footer-inner {
    max-width: 1280px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 24px;
    flex-wrap: wrap;
  }

  .footer-logo {
    font-family: 'Playfair Display', serif;
    font-size: 1.2rem;
    font-weight: 900;
    color: var(--gold);
  }

  .footer-copy { font-size: 0.78rem; color: var(--muted); }

  .footer-disclaimer {
    max-width: 1280px;
    margin: 20px auto 0;
    padding-top: 20px;
    border-top: 1px solid var(--border);
    font-size: 0.72rem;
    color: var(--muted);
    line-height: 1.7;
    letter-spacing: 0.01em;
  }

  /* ─── ANIMATIONS ─── */
  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(20px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .product-card, .calc-card, .currency-widget, .savings-widget {
    animation: fadeUp 0.5s ease both;
  }

  .product-card:nth-child(1) { animation-delay: 0.05s; }
  .product-card:nth-child(2) { animation-delay: 0.1s; }
  .product-card:nth-child(3) { animation-delay: 0.15s; }
  .product-card:nth-child(4) { animation-delay: 0.2s; }

  @media (max-width: 900px) {
    .main-wrapper { grid-template-columns: 1fr; padding: 24px 20px; }
    .cards-grid { grid-template-columns: 1fr; }
    .card-online { grid-column: span 1; }
    .hero-band { padding: 48px 20px; }
    header { padding: 0 20px; }
    .calc-row { grid-template-columns: 1fr 1fr; }
    .calc-results { grid-template-columns: 1fr 1fr; }
  }
</style>
</head>
<body>

<!-- HEADER -->
<header>
  <div class="header-inner">
    <a href="#" class="logo">Valuta<span>.ge</span></a>
    <nav class="main-nav">
      <a href="#" class="active">მთავარი</a>
      <a href="#">სესხები</a>
      <a href="#">ანაბრები</a>
      <a href="#">ვალუტა</a>
      <a href="#">შედარება</a>
      <a href="#">კითხვა / პასუხი</a>
    </nav>
    <div class="header-socials">
      <a href="https://www.facebook.com/SocietyAndBanks" target="_blank">FB</a>
      <a href="https://twitter.com/SocietyAndBanks" target="_blank">TW</a>
      <a href="https://www.linkedin.com/company/societyandbanks" target="_blank">IN</a>
      <a href="https://www.youtube.com/channel/UC70ia86ztBJLIlMVaL1IQww" target="_blank">YT</a>
    </div>
  </div>
</header>

<!-- HERO -->
<div class="hero-band">
  <div class="hero-inner">
    <div class="hero-eyebrow">საფინანსო პლატფორმა — Georgia</div>
    <h1 class="hero-title">შეადარე.<br>გამოთვალე. <em>გადაწყვიტე.</em></h1>
    <p class="hero-sub">ყველა ბანკისა და მიკროსაფინანსო ორგანიზაციის სესხები, ანაბრები და ვალუტის კურსი ერთ ადგილას.</p>
  </div>
</div>

<!-- MAIN CONTENT -->
<div class="main-wrapper">

  <!-- LEFT COLUMN -->
  <div class="content-col">

    <!-- PRODUCT CARDS -->
    <div class="section-label"><h2>პროდუქტები</h2></div>

    <div class="cards-grid">

      <!-- Bank loans -->
      <div class="product-card">
        <img class="card-img" src="https://images.unsplash.com/photo-1486325212027-8081e485255e?w=600&q=60" alt="">
        <div class="card-body">
          <div class="card-tag">საბანკო</div>
          <div class="card-title">სესხები</div>
          <div class="card-links">
            <a href="ge/loans?type=mortgage&organisation=bank">იპოთეკური სესხი</a>
            <a href="ge/loans?type=consumer_load&organisation=bank">სამომხმარებლო სესხი</a>
            <a href="ge/loans?type=auto_loan&organisation=bank">ავტო სესხი</a>
            <a href="ge/loans?type=installment&organisation=bank">განვადება</a>
            <a href="ge/loans?type=credit_card&organisation=bank">საკრედიტო ბარათი</a>
            <a href="ge/loans?type=business_loan&organisation=bank">ბიზნეს სესხი</a>
            <a href="ge/loans?type=gold_lombard&organisation=bank">ოქროს ლომბარდი</a>
          </div>
        </div>
        <div class="card-arrow">→</div>
      </div>

      <!-- Microfinance loans -->
      <div class="product-card">
        <img class="card-img" src="https://images.unsplash.com/photo-1579621970563-ebec7560ff3e?w=600&q=60" alt="">
        <div class="card-body">
          <div class="card-tag">მიკროსაფინანსო</div>
          <div class="card-title">სესხები</div>
          <div class="card-links">
            <a href="ge/loans?type=mortgage&organisation=micro">იპოთეკური სესხი</a>
            <a href="ge/loans?type=consumer_load&organisation=micro">სამომხმარებლო სესხი</a>
            <a href="ge/loans?type=auto_loan&organisation=micro">ავტო სესხი</a>
            <a href="ge/loans?type=business_loan&organisation=micro">ბიზნეს სესხი</a>
            <a href="ge/loans?type=gold_lombard&organisation=micro">ოქროს ლომბარდი</a>
          </div>
        </div>
        <div class="card-arrow">→</div>
      </div>

      <!-- Online loans (full-width) -->
      <div class="product-card card-online">
        <div class="card-body">
          <div>
            <div class="card-tag">სწრაფი და მარტივი</div>
            <div class="card-title" style="font-size:1.3rem; margin-bottom:0">ონლაინ სესხები</div>
          </div>
          <a href="ge/loans?type=all&organisation=online" class="online-badge">ყველა ნახვა →</a>
        </div>
      </div>

      <!-- Deposits -->
      <div class="product-card" style="grid-column: span 2;">
        <div class="card-body" style="display:flex; align-items:flex-start; justify-content:space-between; gap:24px;">
          <div>
            <div class="card-tag">შემნახველი</div>
            <div class="card-title">ანაბრები</div>
          </div>
          <div class="card-links" style="flex:1; display:grid; grid-template-columns:1fr 1fr; gap:0 24px;">
            <a href="ge/deposit?type=term&organisation=all">ვადიანი ანაბრები</a>
            <a href="ge/deposit?type=comulative&organisation=all">ზრდადი ანაბრები</a>
            <a href="ge/deposit?type=call&organisation=all">მოთხოვნამდე ანაბრები</a>
            <a href="ge/deposit?type=child&organisation=all">საბავშვო ანაბარი</a>
          </div>
        </div>
      </div>

    </div><!-- end cards-grid -->

    <!-- LOAN CALCULATOR -->
    <div class="calcs-section">
      <div class="section-label"><h2>სესხის კალკულატორი</h2></div>

      <div class="calc-card">
        <div class="calc-row">
          <div class="field-group">
            <label class="field-label">კრედიტის თანხა</label>
            <input id="loan-amount" type="number" class="field-input" placeholder="10 000">
          </div>
          <div class="field-group">
            <label class="field-label">წლიური პროცენტი</label>
            <div class="input-with-unit">
              <input id="loan-pct" type="number" class="field-input" placeholder="12" min="0" max="100" step="0.1">
              <span class="input-unit">%</span>
            </div>
          </div>
          <div class="field-group">
            <label class="field-label">ვადა (თვეები)</label>
            <div class="input-with-unit">
              <input id="loan-months" type="number" class="field-input" placeholder="24" min="1" max="360">
              <span class="input-unit">თვე</span>
            </div>
          </div>
        </div>

        <button class="calc-btn" onclick="calcLoan()">გამოთვლა ▼</button>

        <div class="calc-results" id="loan-results" style="display:none">
          <div class="result-item">
            <div class="result-label">ყოველთვიური</div>
            <div class="result-value" id="r-monthly">—</div>
          </div>
          <div class="result-item">
            <div class="result-label">ჯამი</div>
            <div class="result-value" id="r-total">—</div>
          </div>
          <div class="result-item">
            <div class="result-label">ზედმეტი</div>
            <div class="result-value" id="r-extra">—</div>
          </div>
        </div>

        <div class="loan-table-wrap" id="loan-table-wrap" style="display:none">
          <table class="loan-table">
            <thead>
              <tr>
                <th>თვე</th>
                <th>გადასახადი</th>
                <th>ძირი</th>
                <th>პროცენტი</th>
                <th>ნაშთი</th>
              </tr>
            </thead>
            <tbody id="loan-tbody"></tbody>
          </table>
        </div>

        <div class="empty-state" id="loan-empty">
          <div class="big-icon">📅</div>
          <p>გადახდის გრაფიკის შესადგენად შეავსეთ ველები და დააჭირეთ გამოთვლა</p>
        </div>
      </div>
    </div>

  </div><!-- end content-col -->

  <!-- RIGHT SIDEBAR -->
  <div class="sidebar-col">

    <!-- CURRENCY WIDGET -->
    <div class="currency-widget">
      <div class="widget-header">
        <div class="widget-title">ვალუტის კურსი</div>
        <div class="widget-badge">Live</div>
      </div>

      <select class="select-org" id="org-select">
        <option value="national-bank">ეროვნული ბანკი</option>
        <option value="12">საქართველოს ბანკი</option>
        <option value="17">თიბისი ბანკი</option>
        <option value="16">ლიბერთი ბანკი</option>
        <option value="14">ჰალიკ ბანკი</option>
        <option value="84">კრედო</option>
      </select>

      <div class="currency-tabs">
        <button class="currency-tab active" onclick="switchCurrTab('from',this)">ლარიდან</button>
        <button class="currency-tab" onclick="switchCurrTab('to',this)">ლარში</button>
      </div>

      <!-- From GEL -->
      <div class="currency-tab-panel active" id="curr-from">
        <div class="currency-input-row">
          <div class="flag-input-wrap" style="flex:1">
            <span class="flag-label">GEL</span>
            <input id="gel-amount" type="number" class="field-input" placeholder="100" oninput="convertFrom()">
          </div>
        </div>
        <div class="currency-list" id="curr-from-list">
          <!-- populated by JS -->
        </div>
      </div>

      <!-- To GEL -->
      <div class="currency-tab-panel" id="curr-to">
        <div class="currency-input-row">
          <div class="flag-input-wrap" style="flex:1">
            <span class="flag-label" id="to-flag-lbl">USD</span>
            <input id="fcy-amount" type="number" class="field-input" placeholder="100" oninput="convertTo()">
          </div>
          <span class="eq-sign">=</span>
          <div class="flag-input-wrap" style="flex:1">
            <span class="flag-label">GEL</span>
            <input id="gel-result" type="text" class="field-input" disabled>
          </div>
        </div>
        <div class="field-group" style="margin-bottom:12px">
          <label class="field-label">ვალუტა</label>
          <select class="select-org" id="to-currency" onchange="convertTo(); document.getElementById('to-flag-lbl').textContent=this.value.toUpperCase()">
            <option value="usd">USD</option>
            <option value="eur">EUR</option>
            <option value="gbp">GBP</option>
            <option value="rub">RUB</option>
            <option value="trl">TRL</option>
          </select>
        </div>
        <a href="/ge/currencies" style="display:block; text-align:center; margin-top:8px;">
          <button class="calc-btn" style="font-size:0.78rem; padding:10px">საუკეთესო კურსი ▶</button>
        </a>
      </div>
    </div>

    <!-- SAVINGS CALCULATOR -->
    <div class="savings-widget">
      <div class="widget-header">
        <div class="widget-title">ანაბრის კალკულატორი</div>
      </div>

      <div class="savings-sub-tabs">
        <button class="savings-sub-tab active" onclick="switchSavTab('term',this)">ვადიანი</button>
        <button class="savings-sub-tab" onclick="switchSavTab('cumulative',this)">ზრდადი</button>
        <button class="savings-sub-tab" onclick="switchSavTab('kids',this)">საბავშვო</button>
      </div>

      <!-- Term savings -->
      <div class="savings-tab-panel active" id="sav-term">
        <div class="savings-field field-group">
          <label class="field-label">საწყისი თანხა</label>
          <input id="t-amount" type="number" class="field-input" placeholder="5 000">
        </div>
        <div class="savings-field field-group">
          <label class="field-label">ვადა (თვეები): <span id="t-period-val">6</span></label>
          <input id="t-period" type="range" min="3" max="24" value="6" class="field-input" oninput="document.getElementById('t-period-val').textContent=this.value">
          <div class="range-display"><span>3</span><span>24</span></div>
        </div>
        <div class="savings-field field-group">
          <label class="field-label">წლიური პროცენტი</label>
          <div class="input-with-unit">
            <input id="t-pct" type="number" class="field-input" placeholder="8" min="0" step="0.1">
            <span class="input-unit">%</span>
          </div>
        </div>
        <div class="savings-field field-group">
          <label class="field-label">გატანის პერიოდი</label>
          <select id="t-freq" class="select-org" style="margin-bottom:0">
            <option value="end">ვადის ბოლოს</option>
            <option value="start">გახსნისას</option>
            <option value="monthly">ყოველთვიურად</option>
          </select>
        </div>
        <button class="calc-btn" onclick="calcTermSavings()">გამოთვლა ▼</button>
        <div class="savings-result" id="t-result" style="display:none">
          <div>
            <div class="s-result-label">ჯამური დანაზოგი</div>
            <div class="s-result-val" id="t-r-total">—</div>
          </div>
          <div>
            <div class="s-result-label">სარგებელი</div>
            <div class="s-result-val" id="t-r-interest">—</div>
          </div>
          <div id="t-monthly-wrap" style="display:none">
            <div class="s-result-label">თვიური სარგებელი</div>
            <div class="s-result-val" id="t-r-monthly">—</div>
          </div>
        </div>
      </div>

      <!-- Cumulative savings -->
      <div class="savings-tab-panel" id="sav-cumulative">
        <div class="savings-field field-group">
          <label class="field-label">საწყისი თანხა</label>
          <input id="c-amount" type="number" class="field-input" placeholder="1 000">
        </div>
        <div class="savings-field field-group">
          <label class="field-label">ვადა (თვეები): <span id="c-period-val">12</span></label>
          <input id="c-period" type="range" min="3" max="24" value="12" class="field-input" oninput="document.getElementById('c-period-val').textContent=this.value">
          <div class="range-display"><span>3</span><span>24</span></div>
        </div>
        <div class="savings-field field-group">
          <label class="field-label">წლიური პროცენტი</label>
          <div class="input-with-unit">
            <input id="c-pct" type="number" class="field-input" placeholder="9" min="0" step="0.1">
            <span class="input-unit">%</span>
          </div>
        </div>
        <div class="savings-field field-group">
          <label class="field-label">ყოველთვიური გადასახადი</label>
          <input id="c-monthly" type="number" class="field-input" placeholder="200">
        </div>
        <button class="calc-btn" onclick="calcCumulativeSavings()">გამოთვლა ▼</button>
        <div class="savings-result" id="c-result" style="display:none">
          <div>
            <div class="s-result-label">ჯამური</div>
            <div class="s-result-val" id="c-r-total">—</div>
          </div>
          <div>
            <div class="s-result-label">სარგებელი</div>
            <div class="s-result-val" id="c-r-interest">—</div>
          </div>
        </div>
      </div>

      <!-- Kids savings -->
      <div class="savings-tab-panel" id="sav-kids">
        <div class="savings-field field-group">
          <label class="field-label">საწყისი თანხა</label>
          <input id="k-amount" type="number" class="field-input" placeholder="500">
        </div>
        <div class="savings-field field-group">
          <label class="field-label">ვადა (წლები): <span id="k-period-val">8</span></label>
          <input id="k-period" type="range" min="2" max="18" value="8" class="field-input" oninput="document.getElementById('k-period-val').textContent=this.value">
          <div class="range-display"><span>2</span><span>18</span></div>
        </div>
        <div class="savings-field field-group">
          <label class="field-label">პროცენტი</label>
          <div class="input-with-unit">
            <input id="k-pct" type="number" class="field-input" placeholder="7" min="0" step="0.1">
            <span class="input-unit">%</span>
          </div>
        </div>
        <div class="savings-field field-group">
          <label class="field-label">თვიური გადასახადი</label>
          <input id="k-monthly" type="number" class="field-input" placeholder="50">
        </div>
        <button class="calc-btn" onclick="calcKidsSavings()">გამოთვლა ▼</button>
        <div class="savings-result" id="k-result" style="display:none">
          <div>
            <div class="s-result-label">ჯამური</div>
            <div class="s-result-val" id="k-r-total">—</div>
          </div>
          <div>
            <div class="s-result-label">სარგებელი</div>
            <div class="s-result-val" id="k-r-interest">—</div>
          </div>
        </div>
      </div>
    </div>

  </div><!-- end sidebar-col -->

</div><!-- end main-wrapper -->

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div class="footer-logo">Valuta.ge</div>
    <div class="footer-copy">© 2014 საზოგადოება და ბანკები</div>
    <a href="http://omedia.ge" target="_blank" style="color:var(--muted); font-size:0.78rem; text-decoration:none;">ვებსაიტი: ომედია</a>
  </div>
  <div class="footer-disclaimer">
    ვებგვერდზე განთავსებული ინფორმაცია წარმოადგენს საილუსტრაციო მასალას და მის სისწორეზე VALUTA.GE არ არის პასუხისმგებელი. ვებგვერდს აქვს მხოლოდ ზოგად-საორიენტაციო დანიშნულება და კონკრეტული პროდუქტის შესახებ ამომწურავი ინფორმაციისთვის, გთხოვთ, იხილოთ შესაბამისი საფინანსო ორგანიზაციის ოფიციალური ვებგვერდი.
  </div>
</footer>

<script>
  // ─── MOCK RATES (approximate GEL buy rates) ───
  const RATES = { usd: 2.72, eur: 2.95, gbp: 3.45, rub: 0.030, trl: 0.082 };
  const CURRENCIES = [
    { code: 'USD', key: 'usd', label: 'აშშ დოლარი', flag: '🇺🇸' },
    { code: 'EUR', key: 'eur', label: 'ევრო', flag: '🇪🇺' },
    { code: 'GBP', key: 'gbp', label: 'ბრიტ. ფუნტი', flag: '🇬🇧' },
    { code: 'RUB', key: 'rub', label: 'რუსული რუბლი', flag: '🇷🇺' },
    { code: 'TRL', key: 'trl', label: 'თურქული ლირა', flag: '🇹🇷' },
  ];

  function fmt(n) {
    if (isNaN(n) || n === undefined) return '—';
    return n.toLocaleString('ka-GE', { minimumFractionDigits: 2, maximumFractionDigits: 2 });
  }

  // ─── BUILD CURRENCY LIST ───
  function buildCurrList() {
    const wrap = document.getElementById('curr-from-list');
    wrap.innerHTML = CURRENCIES.map(c => `
      <div class="currency-row">
        <div class="currency-info">
          <div class="currency-flag">${c.flag}</div>
          <div>
            <div class="currency-name">${c.label}</div>
            <div class="currency-code">${c.code}</div>
          </div>
        </div>
        <div style="text-align:right">
          <div class="currency-amount" id="conv-${c.key}">—</div>
          <div class="currency-best">საუკეთ. კურსი</div>
        </div>
      </div>
    `).join('');
  }

  buildCurrList();

  function convertFrom() {
    const gel = parseFloat(document.getElementById('gel-amount').value) || 0;
    CURRENCIES.forEach(c => {
      const el = document.getElementById('conv-' + c.key);
      if (el) el.textContent = gel > 0 ? fmt(gel / RATES[c.key]) + ' ' + c.code : '—';
    });
  }

  function convertTo() {
    const fcy = parseFloat(document.getElementById('fcy-amount').value) || 0;
    const cur = document.getElementById('to-currency').value;
    const gel = fcy * RATES[cur];
    document.getElementById('gel-result').value = fcy > 0 ? fmt(gel) : '';
  }

  function switchCurrTab(tab, btn) {
    document.querySelectorAll('.currency-tab').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.currency-tab-panel').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('curr-' + tab).classList.add('active');
  }

  // ─── SAVINGS TAB SWITCH ───
  function switchSavTab(tab, btn) {
    document.querySelectorAll('.savings-sub-tab').forEach(b => b.classList.remove('active'));
    document.querySelectorAll('.savings-tab-panel').forEach(p => p.classList.remove('active'));
    btn.classList.add('active');
    document.getElementById('sav-' + tab).classList.add('active');
  }

  // ─── TERM SAVINGS CALC ───
  function calcTermSavings() {
    const P = parseFloat(document.getElementById('t-amount').value) || 0;
    const n = parseInt(document.getElementById('t-period').value) || 0;
    const r = parseFloat(document.getElementById('t-pct').value) / 100 || 0;
    const freq = document.getElementById('t-freq').value;

    const interest = P * r * (n / 12);
    const total = P + interest;
    const monthly = interest / n;

    document.getElementById('t-r-total').textContent = fmt(total) + ' ₾';
    document.getElementById('t-r-interest').textContent = fmt(interest) + ' ₾';
    document.getElementById('t-r-monthly').textContent = fmt(monthly) + ' ₾';

    const mWrap = document.getElementById('t-monthly-wrap');
    mWrap.style.display = freq === 'monthly' ? 'block' : 'none';

    document.getElementById('t-result').style.display = 'grid';
  }

  // ─── CUMULATIVE SAVINGS CALC ───
  function calcCumulativeSavings() {
    const P = parseFloat(document.getElementById('c-amount').value) || 0;
    const n = parseInt(document.getElementById('c-period').value) || 0;
    const r = parseFloat(document.getElementById('c-pct').value) / 100 / 12 || 0;
    const M = parseFloat(document.getElementById('c-monthly').value) || 0;

    let balance = P;
    for (let i = 0; i < n; i++) {
      balance = balance * (1 + r) + M;
    }
    const totalDeposited = P + M * n;
    const interest = balance - totalDeposited;

    document.getElementById('c-r-total').textContent = fmt(balance) + ' ₾';
    document.getElementById('c-r-interest').textContent = fmt(interest) + ' ₾';
    document.getElementById('c-result').style.display = 'grid';
  }

  // ─── KIDS SAVINGS CALC ───
  function calcKidsSavings() {
    const P = parseFloat(document.getElementById('k-amount').value) || 0;
    const years = parseInt(document.getElementById('k-period').value) || 0;
    const r = parseFloat(document.getElementById('k-pct').value) / 100 / 12 || 0;
    const M = parseFloat(document.getElementById('k-monthly').value) || 0;
    const n = years * 12;

    let balance = P;
    for (let i = 0; i < n; i++) {
      balance = balance * (1 + r) + M;
    }
    const totalDeposited = P + M * n;
    const interest = balance - totalDeposited;

    document.getElementById('k-r-total').textContent = fmt(balance) + ' ₾';
    document.getElementById('k-r-interest').textContent = fmt(interest) + ' ₾';
    document.getElementById('k-result').style.display = 'grid';
  }

  // ─── LOAN CALC ───
  function calcLoan() {
    const P = parseFloat(document.getElementById('loan-amount').value) || 0;
    const annualRate = parseFloat(document.getElementById('loan-pct').value) || 0;
    const n = parseInt(document.getElementById('loan-months').value) || 0;

    if (!P || !n) return;

    const r = annualRate / 100 / 12;
    let monthly;

    if (r === 0) {
      monthly = P / n;
    } else {
      monthly = P * r * Math.pow(1 + r, n) / (Math.pow(1 + r, n) - 1);
    }

    const total = monthly * n;
    const extra = total - P;

    document.getElementById('r-monthly').textContent = fmt(monthly) + ' ₾';
    document.getElementById('r-total').textContent = fmt(total) + ' ₾';
    document.getElementById('r-extra').textContent = fmt(extra) + ' ₾';

    document.getElementById('loan-results').style.display = 'grid';
    document.getElementById('loan-empty').style.display = 'none';

    // Build amortization table
    const tbody = document.getElementById('loan-tbody');
    tbody.innerHTML = '';
    let balance = P;

    for (let i = 1; i <= n; i++) {
      const interestPart = balance * r;
      const principalPart = r === 0 ? P / n : monthly - interestPart;
      balance -= principalPart;

      const tr = document.createElement('tr');
      tr.innerHTML = `
        <td>${i}</td>
        <td>${fmt(monthly)}</td>
        <td>${fmt(principalPart)}</td>
        <td>${fmt(interestPart)}</td>
        <td>${fmt(Math.max(0, balance))}</td>
      `;
      tbody.appendChild(tr);
    }

    document.getElementById('loan-table-wrap').style.display = 'block';
  }
</script>
</body>
</html>
