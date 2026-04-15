# IMEX
Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IMEX – Thiết Bị Di Động Chính Hãng</title>
<link href="https://fonts.googleapis.com/css2?family=Rajdhani:wght@400;500;600;700&family=Be+Vietnam+Pro:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  :root {
    --blue-deep: #0a1628;
    --blue-primary: #0057ff;
    --blue-bright: #2979ff;
    --blue-light: #5c9aff;
    --blue-pale: #c8dcff;
    --blue-ghost: #e8f1ff;
    --white: #ffffff;
    --gray-100: #f4f7ff;
    --gray-200: #dce6f7;
    --gray-400: #8fa6c8;
    --gray-600: #4a6080;
    --accent-cyan: #00c6ff;
    --accent-gold: #ffd700;
    --accent-red: #ff3b3b;
    --shadow-blue: 0 8px 40px rgba(0,87,255,0.18);
    --shadow-card: 0 2px 24px rgba(10,22,40,0.10);
    --radius: 18px;
    --radius-sm: 10px;
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Be Vietnam Pro', sans-serif;
    background: var(--white);
    color: var(--blue-deep);
    overflow-x: hidden;
  }

  /* ── SCROLLBAR ── */
  ::-webkit-scrollbar { width: 6px; }
  ::-webkit-scrollbar-track { background: var(--gray-100); }
  ::-webkit-scrollbar-thumb { background: var(--blue-primary); border-radius: 3px; }

  /* ══════════════════════════════════════
     TOP BAR
  ══════════════════════════════════════ */
  .topbar {
    background: var(--blue-deep);
    color: var(--blue-pale);
    font-size: 12px;
    padding: 6px 0;
    text-align: center;
    letter-spacing: 0.5px;
  }
  .topbar span { color: var(--accent-cyan); font-weight: 600; }

  /* ══════════════════════════════════════
     HEADER
  ══════════════════════════════════════ */
  header {
    position: sticky;
    top: 0;
    z-index: 100;
    background: rgba(255,255,255,0.95);
    backdrop-filter: blur(12px);
    border-bottom: 1.5px solid var(--blue-ghost);
    box-shadow: 0 2px 24px rgba(0,87,255,0.07);
  }
  .header-inner {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
    height: 72px;
    display: flex;
    align-items: center;
    gap: 28px;
  }

  /* Logo */
  .logo {
    display: flex;
    align-items: center;
    gap: 10px;
    text-decoration: none;
    flex-shrink: 0;
  }
  .logo-icon {
    width: 42px; height: 42px;
    background: var(--blue-primary);
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-family: 'Rajdhani', sans-serif;
    font-size: 18px; font-weight: 700;
    color: var(--white);
    letter-spacing: 1px;
    box-shadow: 0 4px 16px rgba(0,87,255,0.35);
  }
  .logo-text {
    font-family: 'Rajdhani', sans-serif;
    font-size: 24px;
    font-weight: 700;
    color: var(--blue-deep);
    letter-spacing: 2px;
    line-height: 1;
  }
  .logo-text span { color: var(--blue-primary); }

  /* Search */
  .search-wrap {
    flex: 1;
    position: relative;
    max-width: 560px;
  }
  .search-wrap input {
    width: 100%;
    padding: 11px 52px 11px 18px;
    border: 2px solid var(--blue-ghost);
    border-radius: 50px;
    font-family: inherit;
    font-size: 14px;
    color: var(--blue-deep);
    background: var(--gray-100);
    outline: none;
    transition: border-color 0.2s, box-shadow 0.2s;
  }
  .search-wrap input:focus {
    border-color: var(--blue-primary);
    box-shadow: 0 0 0 3px rgba(0,87,255,0.12);
    background: var(--white);
  }
  .search-wrap input::placeholder { color: var(--gray-400); }
  .search-btn {
    position: absolute; right: 6px; top: 50%; transform: translateY(-50%);
    width: 36px; height: 36px;
    background: var(--blue-primary);
    border: none; border-radius: 50%;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    transition: background 0.2s, transform 0.15s;
  }
  .search-btn:hover { background: var(--blue-bright); transform: translateY(-50%) scale(1.06); }
  .search-btn svg { width: 16px; height: 16px; fill: var(--white); }

  /* Nav Actions */
  .nav-actions {
    display: flex;
    align-items: center;
    gap: 8px;
    margin-left: auto;
  }
  .nav-btn {
    display: flex; flex-direction: column; align-items: center; gap: 2px;
    padding: 8px 14px;
    border: none; background: transparent;
    cursor: pointer;
    border-radius: var(--radius-sm);
    transition: background 0.15s;
    color: var(--blue-deep);
    font-family: inherit;
    font-size: 11px;
    font-weight: 500;
    position: relative;
  }
  .nav-btn:hover { background: var(--blue-ghost); color: var(--blue-primary); }
  .nav-btn svg { width: 22px; height: 22px; stroke: currentColor; fill: none; stroke-width: 1.8; }
  .badge {
    position: absolute; top: 4px; right: 8px;
    background: var(--accent-red);
    color: #fff;
    font-size: 10px; font-weight: 700;
    width: 18px; height: 18px;
    border-radius: 50%;
    display: flex; align-items: center; justify-content: center;
    border: 2px solid var(--white);
  }

  /* Nav Menu */
  nav.main-nav {
    background: var(--blue-deep);
  }
  .nav-inner {
    max-width: 1280px;
    margin: 0 auto;
    padding: 0 24px;
    display: flex;
    align-items: center;
    gap: 0;
  }
  .nav-item {
    padding: 12px 20px;
    color: rgba(255,255,255,0.82);
    font-size: 14px;
    font-weight: 500;
    cursor: pointer;
    transition: color 0.15s, background 0.15s;
    position: relative;
    white-space: nowrap;
  }
  .nav-item:hover, .nav-item.active {
    color: var(--white);
    background: rgba(255,255,255,0.08);
  }
  .nav-item.active::after {
    content: '';
    position: absolute;
    bottom: 0; left: 20px; right: 20px;
    height: 2px;
    background: var(--accent-cyan);
    border-radius: 2px 2px 0 0;
  }
  .nav-hot { color: var(--accent-gold) !important; font-weight: 600; }
  .nav-hot::before { content: '🔥 '; }

  /* ══════════════════════════════════════
     HERO BANNER
  ══════════════════════════════════════ */
  .hero {
    background: linear-gradient(135deg, var(--blue-deep) 0%, #0d2c72 55%, #0a1e5e 100%);
    position: relative;
    overflow: hidden;
    padding: 0;
  }
  .hero::before {
    content: '';
    position: absolute;
    top: -60px; right: -60px;
    width: 500px; height: 500px;
    background: radial-gradient(circle, rgba(0,198,255,0.18) 0%, transparent 70%);
    border-radius: 50%;
    pointer-events: none;
  }
  .hero::after {
    content: '';
    position: absolute;
    bottom: -80px; left: 10%;
    width: 400px; height: 400px;
    background: radial-gradient(circle, rgba(0,87,255,0.22) 0%, transparent 70%);
    border-radius: 50%;
    pointer-events: none;
  }

  /* Geometric deco */
  .hero-geo {
    position: absolute;
    top: 0; left: 0; right: 0; bottom: 0;
    overflow: hidden;
    pointer-events: none;
  }
  .hero-geo span {
    position: absolute;
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 50%;
    animation: pulse-ring 6s ease-in-out infinite;
  }
  .hero-geo span:nth-child(1) { width: 320px; height: 320px; top: -80px; right: 80px; animation-delay: 0s; }
  .hero-geo span:nth-child(2) { width: 200px; height: 200px; top: 20px; right: 160px; animation-delay: 1s; }
  .hero-geo span:nth-child(3) { width: 120px; height: 120px; top: 70px; right: 210px; animation-delay: 2s; }

  @keyframes pulse-ring {
    0%, 100% { opacity: 0.4; transform: scale(1); }
    50% { opacity: 0.12; transform: scale(1.05); }
  }

  .hero-inner {
    max-width: 1280px;
    margin: 0 auto;
    padding: 60px 24px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 40px;
    align-items: center;
    position: relative;
    z-index: 1;
  }
  .hero-content {}
  .hero-label {
    display: inline-flex;
    align-items: center;
    gap: 8px;
    background: rgba(0,198,255,0.15);
    border: 1px solid rgba(0,198,255,0.3);
    color: var(--accent-cyan);
    font-size: 12px;
    font-weight: 600;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    padding: 6px 14px;
    border-radius: 50px;
    margin-bottom: 20px;
    animation: fadeSlideUp 0.6s ease both;
  }
  .hero-label::before { content: '●'; font-size: 8px; animation: blink 1.5s ease infinite; }
  @keyframes blink { 0%,100%{opacity:1} 50%{opacity:0.3} }

  .hero-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 56px;
    font-weight: 700;
    color: var(--white);
    line-height: 1.05;
    margin-bottom: 16px;
    animation: fadeSlideUp 0.6s 0.1s ease both;
  }
  .hero-title em {
    font-style: normal;
    background: linear-gradient(90deg, var(--accent-cyan), var(--blue-light));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }
  .hero-desc {
    color: rgba(255,255,255,0.65);
    font-size: 16px;
    line-height: 1.7;
    max-width: 460px;
    margin-bottom: 32px;
    animation: fadeSlideUp 0.6s 0.2s ease both;
  }
  .hero-actions {
    display: flex;
    gap: 14px;
    animation: fadeSlideUp 0.6s 0.3s ease both;
  }
  .btn-primary {
    padding: 14px 32px;
    background: var(--blue-primary);
    color: var(--white);
    border: none;
    border-radius: 50px;
    font-family: inherit;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    transition: transform 0.15s, box-shadow 0.15s;
    box-shadow: 0 6px 24px rgba(0,87,255,0.45);
    text-decoration: none;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .btn-primary:hover { transform: translateY(-2px); box-shadow: 0 10px 32px rgba(0,87,255,0.55); }
  .btn-outline {
    padding: 14px 32px;
    background: transparent;
    color: var(--white);
    border: 2px solid rgba(255,255,255,0.3);
    border-radius: 50px;
    font-family: inherit;
    font-size: 15px;
    font-weight: 600;
    cursor: pointer;
    transition: border-color 0.15s, background 0.15s;
    text-decoration: none;
    display: inline-flex; align-items: center; gap: 8px;
  }
  .btn-outline:hover { border-color: var(--accent-cyan); background: rgba(0,198,255,0.08); }

  .hero-stats {
    display: flex;
    gap: 32px;
    margin-top: 40px;
    animation: fadeSlideUp 0.6s 0.4s ease both;
  }
  .stat { }
  .stat-num {
    font-family: 'Rajdhani', sans-serif;
    font-size: 28px;
    font-weight: 700;
    color: var(--white);
  }
  .stat-num span { color: var(--accent-cyan); }
  .stat-label { font-size: 12px; color: rgba(255,255,255,0.5); margin-top: 2px; }

  /* Hero phone showcase */
  .hero-visual {
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    animation: fadeSlideUp 0.6s 0.2s ease both;
  }
  .phone-mockup {
    width: 260px;
    height: 520px;
    background: linear-gradient(160deg, #1a1a2e, #16213e, #0f3460);
    border-radius: 40px;
    position: relative;
    box-shadow: 0 40px 100px rgba(0,0,0,0.5), 0 0 0 1px rgba(255,255,255,0.08), inset 0 1px 0 rgba(255,255,255,0.12);
    transform: perspective(800px) rotateY(-8deg) rotateX(3deg);
    animation: float 4s ease-in-out infinite;
  }
  @keyframes float {
    0%, 100% { transform: perspective(800px) rotateY(-8deg) rotateX(3deg) translateY(0); }
    50% { transform: perspective(800px) rotateY(-8deg) rotateX(3deg) translateY(-12px); }
  }
  .phone-screen {
    position: absolute;
    top: 16px; left: 10px; right: 10px; bottom: 16px;
    background: linear-gradient(160deg, #0057ff 0%, #00c6ff 50%, #0a1628 100%);
    border-radius: 32px;
    overflow: hidden;
    display: flex; flex-direction: column; align-items: center; justify-content: center;
  }
  .phone-notch {
    position: absolute; top: 10px; left: 50%; transform: translateX(-50%);
    width: 80px; height: 22px;
    background: #0a1628;
    border-radius: 0 0 14px 14px;
    z-index: 2;
  }
  .phone-ui {
    color: white;
    text-align: center;
    padding: 0 16px;
    position: relative;
    z-index: 1;
  }
  .phone-ui-logo {
    font-family: 'Rajdhani', sans-serif;
    font-size: 32px;
    font-weight: 700;
    letter-spacing: 3px;
    margin-bottom: 8px;
  }
  .phone-ui-sub { font-size: 11px; opacity: 0.7; letter-spacing: 1px; }
  .phone-glow {
    position: absolute;
    top: 50%; left: 50%;
    transform: translate(-50%, -50%);
    width: 180px; height: 180px;
    background: radial-gradient(circle, rgba(0,198,255,0.3) 0%, transparent 70%);
    border-radius: 50%;
    animation: glow 3s ease-in-out infinite;
  }
  @keyframes glow { 0%,100%{opacity:0.6;transform:translate(-50%,-50%) scale(1)} 50%{opacity:1;transform:translate(-50%,-50%) scale(1.2)} }

  .floating-badge {
    position: absolute;
    background: var(--white);
    border-radius: 14px;
    padding: 10px 14px;
    box-shadow: 0 8px 32px rgba(0,0,0,0.18);
    font-size: 12px;
    font-weight: 600;
    color: var(--blue-deep);
    display: flex; align-items: center; gap: 8px;
    animation: float-badge 3.5s ease-in-out infinite;
  }
  .floating-badge.left { left: -30px; top: 30%; animation-delay: 0.5s; }
  .floating-badge.right { right: -30px; bottom: 28%; }
  @keyframes float-badge {
    0%,100%{transform:translateY(0)} 50%{transform:translateY(-6px)}
  }
  .fb-icon { font-size: 20px; }
  .fb-val { font-size: 16px; font-weight: 700; color: var(--blue-primary); }

  @keyframes fadeSlideUp {
    from { opacity: 0; transform: translateY(20px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ══════════════════════════════════════
     SECTION COMMON
  ══════════════════════════════════════ */
  .section { padding: 60px 24px; max-width: 1280px; margin: 0 auto; }
  .section-header {
    display: flex;
    align-items: baseline;
    justify-content: space-between;
    margin-bottom: 32px;
  }
  .section-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 30px;
    font-weight: 700;
    color: var(--blue-deep);
  }
  .section-title span { color: var(--blue-primary); }
  .section-line {
    display: inline-block;
    width: 40px; height: 4px;
    background: var(--blue-primary);
    border-radius: 2px;
    margin-left: 10px;
    vertical-align: middle;
  }
  .see-all {
    font-size: 13px;
    font-weight: 600;
    color: var(--blue-primary);
    cursor: pointer;
    display: flex; align-items: center; gap: 4px;
    transition: gap 0.15s;
  }
  .see-all:hover { gap: 8px; }
  .see-all::after { content: '→'; }

  /* ══════════════════════════════════════
     BRAND CATEGORIES
  ══════════════════════════════════════ */
  .brands-strip {
    background: var(--gray-100);
    border-top: 1px solid var(--gray-200);
    border-bottom: 1px solid var(--gray-200);
  }
  .brands-inner {
    max-width: 1280px;
    margin: 0 auto;
    padding: 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 16px;
  }
  .brand-chip {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 8px;
    padding: 14px 20px;
    background: var(--white);
    border: 2px solid var(--gray-200);
    border-radius: var(--radius);
    cursor: pointer;
    transition: border-color 0.15s, box-shadow 0.15s, transform 0.15s;
    flex: 1;
    min-width: 80px;
  }
  .brand-chip:hover {
    border-color: var(--blue-primary);
    box-shadow: var(--shadow-blue);
    transform: translateY(-3px);
  }
  .brand-chip.active {
    border-color: var(--blue-primary);
    background: var(--blue-ghost);
  }
  .brand-logo {
    font-family: 'Rajdhani', sans-serif;
    font-size: 18px;
    font-weight: 700;
    color: var(--blue-deep);
    letter-spacing: 1px;
  }
  .brand-count { font-size: 11px; color: var(--gray-400); }

  /* ══════════════════════════════════════
     FLASH SALE BANNER
  ══════════════════════════════════════ */
  .flash-banner {
    background: linear-gradient(90deg, #ff3b3b 0%, #ff6b35 100%);
    border-radius: var(--radius);
    padding: 20px 32px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 24px;
    margin: 0 24px;
    max-width: calc(1280px - 48px);
    margin-left: auto;
    margin-right: auto;
    box-shadow: 0 8px 32px rgba(255,59,59,0.3);
  }
  .flash-left {
    display: flex;
    align-items: center;
    gap: 16px;
  }
  .flash-icon { font-size: 36px; animation: shake 0.8s ease infinite; }
  @keyframes shake {
    0%,100%{transform:rotate(0)} 25%{transform:rotate(-10deg)} 75%{transform:rotate(10deg)}
  }
  .flash-text h3 {
    font-family: 'Rajdhani', sans-serif;
    font-size: 24px;
    font-weight: 700;
    color: var(--white);
    letter-spacing: 1px;
  }
  .flash-text p { font-size: 13px; color: rgba(255,255,255,0.8); margin-top: 2px; }
  .countdown {
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .count-box {
    background: rgba(0,0,0,0.25);
    color: var(--white);
    border-radius: 8px;
    padding: 8px 12px;
    text-align: center;
    min-width: 52px;
  }
  .count-box .num {
    font-family: 'Rajdhani', sans-serif;
    font-size: 28px;
    font-weight: 700;
    line-height: 1;
  }
  .count-box .lbl { font-size: 9px; opacity: 0.7; letter-spacing: 1px; text-transform: uppercase; }
  .count-sep { color: rgba(255,255,255,0.6); font-size: 24px; font-weight: 700; }

  /* ══════════════════════════════════════
     PRODUCT GRID
  ══════════════════════════════════════ */
  .product-grid {
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    gap: 16px;
  }
  .product-card {
    background: var(--white);
    border: 1.5px solid var(--gray-200);
    border-radius: var(--radius);
    overflow: hidden;
    cursor: pointer;
    transition: transform 0.2s, box-shadow 0.2s, border-color 0.2s;
    position: relative;
  }
  .product-card:hover {
    transform: translateY(-5px);
    box-shadow: var(--shadow-blue);
    border-color: var(--blue-pale);
  }
  .product-img {
    aspect-ratio: 1;
    background: var(--gray-100);
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
    overflow: hidden;
  }
  .product-img-inner {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 72px;
    transition: transform 0.3s;
  }
  .product-card:hover .product-img-inner { transform: scale(1.08); }

  .product-tag {
    position: absolute;
    top: 10px; left: 10px;
    background: var(--accent-red);
    color: var(--white);
    font-size: 11px;
    font-weight: 700;
    padding: 3px 10px;
    border-radius: 20px;
    letter-spacing: 0.5px;
  }
  .product-tag.new { background: var(--blue-primary); }
  .product-tag.hot { background: #ff6b35; }

  .product-wish {
    position: absolute;
    top: 10px; right: 10px;
    width: 32px; height: 32px;
    background: rgba(255,255,255,0.92);
    border: none; border-radius: 50%;
    cursor: pointer;
    display: flex; align-items: center; justify-content: center;
    font-size: 16px;
    transition: transform 0.15s, background 0.15s;
    box-shadow: 0 2px 8px rgba(0,0,0,0.1);
  }
  .product-wish:hover { transform: scale(1.15); background: var(--white); }

  .product-info { padding: 14px; }
  .product-brand {
    font-size: 11px;
    font-weight: 600;
    color: var(--blue-primary);
    text-transform: uppercase;
    letter-spacing: 0.5px;
    margin-bottom: 4px;
  }
  .product-name {
    font-size: 13px;
    font-weight: 600;
    color: var(--blue-deep);
    margin-bottom: 8px;
    line-height: 1.4;
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
  .product-price-wrap {
    display: flex;
    align-items: baseline;
    gap: 8px;
    margin-bottom: 10px;
  }
  .price-now {
    font-family: 'Rajdhani', sans-serif;
    font-size: 20px;
    font-weight: 700;
    color: var(--blue-primary);
  }
  .price-old {
    font-size: 12px;
    color: var(--gray-400);
    text-decoration: line-through;
  }
  .price-save {
    font-size: 11px;
    font-weight: 600;
    color: var(--accent-red);
    background: rgba(255,59,59,0.08);
    padding: 2px 6px;
    border-radius: 4px;
  }
  .product-rating {
    display: flex;
    align-items: center;
    gap: 4px;
    font-size: 12px;
    color: var(--gray-400);
    margin-bottom: 12px;
  }
  .stars { color: var(--accent-gold); letter-spacing: 1px; }
  .product-btn {
    width: 100%;
    padding: 9px;
    background: var(--blue-primary);
    color: var(--white);
    border: none;
    border-radius: var(--radius-sm);
    font-family: inherit;
    font-size: 13px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s, transform 0.1s;
  }
  .product-btn:hover { background: var(--blue-bright); transform: scale(1.01); }
  .product-btn:active { transform: scale(0.98); }

  /* ══════════════════════════════════════
     PROMO BANNERS GRID
  ══════════════════════════════════════ */
  .promo-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr;
    gap: 16px;
  }
  .promo-card {
    border-radius: var(--radius);
    overflow: hidden;
    position: relative;
    cursor: pointer;
    min-height: 180px;
    display: flex;
    align-items: flex-end;
    padding: 24px;
    transition: transform 0.2s;
  }
  .promo-card:hover { transform: scale(1.02); }
  .promo-card.blue { background: linear-gradient(135deg, var(--blue-deep) 0%, #0d4bbd 100%); }
  .promo-card.cyan { background: linear-gradient(135deg, #0a3d62 0%, #006994 100%); }
  .promo-card.dark { background: linear-gradient(135deg, #1a1a2e 0%, #16213e 100%); }
  .promo-deco {
    position: absolute;
    top: 0; right: 0;
    width: 180px; height: 100%;
    pointer-events: none;
    display: flex; align-items: center; justify-content: center;
    font-size: 80px;
    opacity: 0.18;
  }
  .promo-content { position: relative; z-index: 1; }
  .promo-tag {
    font-size: 11px;
    font-weight: 600;
    color: var(--accent-cyan);
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 6px;
  }
  .promo-title {
    font-family: 'Rajdhani', sans-serif;
    font-size: 22px;
    font-weight: 700;
    color: var(--white);
    margin-bottom: 8px;
    line-height: 1.1;
  }
  .promo-btn {
    padding: 8px 18px;
    background: rgba(255,255,255,0.15);
    border: 1px solid rgba(255,255,255,0.3);
    border-radius: 20px;
    color: var(--white);
    font-family: inherit;
    font-size: 12px;
    font-weight: 600;
    cursor: pointer;
    transition: background 0.15s;
  }
  .promo-btn:hover { background: rgba(255,255,255,0.25); }

  /* ══════════════════════════════════════
     CATEGORY ICONS
  ══════════════════════════════════════ */
  .category-grid {
    display: grid;
    grid-template-columns: repeat(8, 1fr);
    gap: 12px;
  }
  .cat-item {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10px;
    padding: 18px 8px;
    background: var(--white);
    border: 1.5px solid var(--gray-200);
    border-radius: var(--radius);
    cursor: pointer;
    transition: all 0.2s;
    text-align: center;
  }
  .cat-item:hover {
    border-color: var(--blue-primary);
    background: var(--blue-ghost);
    transform: translateY(-3px);
    box-shadow: var(--shadow-blue);
  }
  .cat-icon { font-size: 28px; }
  .cat-name { font-size: 11px; font-weight: 600; color: var(--blue-deep); line-height: 1.3; }

  /* ══════════════════════════════════════
     FEATURES STRIP
  ══════════════════════════════════════ */
  .features-strip {
    background: var(--blue-deep);
    padding: 40px 24px;
  }
  .features-inner {
    max-width: 1280px;
    margin: 0 auto;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 0;
  }
  .feature-item {
    display: flex;
    align-items: center;
    gap: 16px;
    padding: 0 32px;
    border-right: 1px solid rgba(255,255,255,0.1);
  }
  .feature-item:first-child { padding-left: 0; }
  .feature-item:last-child { border-right: none; }
  .feature-ico {
    width: 48px; height: 48px;
    background: rgba(0,87,255,0.2);
    border: 1px solid rgba(0,87,255,0.3);
    border-radius: 12px;
    display: flex; align-items: center; justify-content: center;
    font-size: 22px;
    flex-shrink: 0;
  }
  .feature-text h4 {
    font-size: 15px;
    font-weight: 600;
    color: var(--white);
    margin-bottom: 3px;
  }
  .feature-text p { font-size: 12px; color: rgba(255,255,255,0.5); }

  /* ══════════════════════════════════════
     FOOTER
  ══════════════════════════════════════ */
  footer {
    background: var(--blue-deep);
    border-top: 1px solid rgba(255,255,255,0.06);
    padding: 48px 24px 24px;
  }
  .footer-inner {
    max-width: 1280px;
    margin: 0 auto;
  }
  .footer-grid {
    display: grid;
    grid-template-columns: 2fr 1fr 1fr 1fr;
    gap: 40px;
    margin-bottom: 40px;
  }
  .footer-brand .logo { margin-bottom: 16px; }
  .footer-brand p { font-size: 13px; color: rgba(255,255,255,0.5); line-height: 1.7; max-width: 280px; }
  .social-links { display: flex; gap: 10px; margin-top: 20px; }
  .social-btn {
    width: 36px; height: 36px;
    background: rgba(255,255,255,0.08);
    border: 1px solid rgba(255,255,255,0.12);
    border-radius: 8px;
    display: flex; align-items: center; justify-content: center;
    cursor: pointer;
    font-size: 16px;
    transition: background 0.15s;
  }
  .social-btn:hover { background: var(--blue-primary); }
  .footer-col h4 {
    font-size: 14px;
    font-weight: 600;
    color: var(--white);
    margin-bottom: 16px;
    letter-spacing: 0.5px;
  }
  .footer-col ul { list-style: none; }
  .footer-col ul li {
    font-size: 13px;
    color: rgba(255,255,255,0.5);
    padding: 5px 0;
    cursor: pointer;
    transition: color 0.15s;
  }
  .footer-col ul li:hover { color: var(--accent-cyan); }
  .footer-bottom {
    border-top: 1px solid rgba(255,255,255,0.08);
    padding-top: 24px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    font-size: 12px;
    color: rgba(255,255,255,0.35);
  }
  .payment-icons { display: flex; gap: 8px; }
  .pay-ico {
    background: rgba(255,255,255,0.08);
    border-radius: 6px;
    padding: 4px 10px;
    font-size: 11px;
    font-weight: 600;
    color: rgba(255,255,255,0.5);
    letter-spacing: 0.5px;
  }

  /* ══════════════════════════════════════
     RESPONSIVE
  ══════════════════════════════════════ */
  @media (max-width: 1024px) {
    .product-grid { grid-template-columns: repeat(4, 1fr); }
    .category-grid { grid-template-columns: repeat(4, 1fr); }
    .footer-grid { grid-template-columns: 1fr 1fr; }
  }
  @media (max-width: 768px) {
    .hero-inner { grid-template-columns: 1fr; }
    .hero-visual { display: none; }
    .hero-title { font-size: 36px; }
    .product-grid { grid-template-columns: repeat(2, 1fr); }
    .promo-grid { grid-template-columns: 1fr; }
    .brands-inner { flex-wrap: wrap; }
    .features-inner { grid-template-columns: 1fr 1fr; gap: 24px; }
    .feature-item { border-right: none; border-bottom: 1px solid rgba(255,255,255,0.1); padding: 0 0 24px 0; }
    .category-grid { grid-template-columns: repeat(4, 1fr); }
    .footer-grid { grid-template-columns: 1fr; }
    .nav-actions .nav-btn span { display: none; }
  }
</style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
  🚀 Miễn phí vận chuyển cho đơn hàng từ <span>2.000.000đ</span> &nbsp;|&nbsp; 
  Hotline: <span>1800-IMEX</span> &nbsp;|&nbsp; 
  Đổi trả <span>30 ngày</span> — bảo hành chính hãng
</div>

<!-- HEADER -->
<header>
  <div class="header-inner">
    <a href="#" class="logo">
      <div class="logo-icon">IM</div>
      <div class="logo-text">IMEX<span>.</span></div>
    </a>

    <div class="search-wrap">
      <input type="text" placeholder="Tìm kiếm iPhone, Samsung, OPPO, Xiaomi...">
      <button class="search-btn">
        <svg viewBox="0 0 24 24"><circle cx="11" cy="11" r="8"/><path d="m21 21-4.35-4.35" stroke-linecap="round"/></svg>
      </button>
    </div>

    <div class="nav-actions">
      <button class="nav-btn" onclick="alert('Đăng nhập tài khoản IMEX')">
        <svg viewBox="0 0 24 24"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"/><circle cx="12" cy="7" r="4"/></svg>
        <span>Tài khoản</span>
      </button>
      <button class="nav-btn" onclick="alert('So sánh sản phẩm')">
        <svg viewBox="0 0 24 24"><path d="M8 3H2v13h6M16 8h6v13h-6"/><path d="M12 3v18M2 16h6M16 8h6" stroke-linecap="round"/></svg>
        <span>So sánh</span>
      </button>
      <button class="nav-btn" onclick="alert('Danh sách yêu thích')">
        <svg viewBox="0 0 24 24"><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"/></svg>
        <span>Yêu thích</span>
        <div class="badge">3</div>
      </button>
      <button class="nav-btn" onclick="alert('Giỏ hàng của bạn')">
        <svg viewBox="0 0 24 24"><path d="M6 2 3 6v14a2 2 0 0 0 2 2h14a2 2 0 0 0 2-2V6l-3-4z"/><line x1="3" y1="6" x2="21" y2="6"/><path d="M16 10a4 4 0 0 1-8 0"/></svg>
        <span>Giỏ hàng</span>
        <div class="badge">2</div>
      </button>
    </div>
  </div>

  <!-- NAV MENU -->
  <nav class="main-nav">
    <div class="nav-inner">
      <div class="nav-item active">Trang chủ</div>
      <div class="nav-item">iPhone</div>
      <div class="nav-item">Samsung</div>
      <div class="nav-item">Xiaomi</div>
      <div class="nav-item">OPPO</div>
      <div class="nav-item">Realme</div>
      <div class="nav-item">Vivo</div>
      <div class="nav-item">Máy tính bảng</div>
      <div class="nav-item">Phụ kiện</div>
      <div class="nav-item">Laptop</div>
      <div class="nav-item nav-hot">Khuyến mãi</div>
      <div class="nav-item">Tin tức</div>
    </div>
  </nav>
</header>

<!-- HERO -->
<section class="hero">
  <div class="hero-geo">
    <span></span><span></span><span></span>
  </div>
  <div class="hero-inner">
    <div class="hero-content">
      <div class="hero-label">Nền tảng di động hàng đầu Việt Nam</div>
      <h1 class="hero-title">
        Khám phá thế giới<br>
        <em>Smartphone</em><br>
        chính hãng
      </h1>
      <p class="hero-desc">
        IMEX cung cấp hàng nghìn mẫu thiết bị di động chính hãng với giá tốt nhất, 
        bảo hành đầy đủ và giao hàng toàn quốc trong 24 giờ.
      </p>
      <div class="hero-actions">
        <a href="#products" class="btn-primary">🛒 Mua ngay</a>
        <a href="#categories" class="btn-outline">📱 Xem danh mục</a>
      </div>
      <div class="hero-stats">
        <div class="stat">
          <div class="stat-num">50<span>K+</span></div>
          <div class="stat-label">Sản phẩm</div>
        </div>
        <div class="stat">
          <div class="stat-num">200<span>K+</span></div>
          <div class="stat-label">Khách hàng</div>
        </div>
        <div class="stat">
          <div class="stat-num">99<span>%</span></div>
          <div class="stat-label">Hài lòng</div>
        </div>
      </div>
    </div>

    <div class="hero-visual">
      <div class="floating-badge left">
        <span class="fb-icon">🏆</span>
        <div>
          <div class="fb-val">#1</div>
          <div>Chính hãng</div>
        </div>
      </div>
      <div class="phone-mockup">
        <div class="phone-notch"></div>
        <div class="phone-screen">
          <div class="phone-glow"></div>
          <div class="phone-ui">
            <div class="phone-ui-logo">IMEX</div>
            <div class="phone-ui-sub">MOBILE STORE</div>
          </div>
        </div>
      </div>
      <div class="floating-badge right">
        <span class="fb-icon">🚀</span>
        <div>
          <div class="fb-val">24h</div>
          <div>Giao hàng</div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- BRANDS -->
<div class="brands-strip">
  <div class="brands-inner">
    <div class="brand-chip active">
      <div class="brand-logo">Apple</div>
      <div class="brand-count">128 sản phẩm</div>
    </div>
    <div class="brand-chip">
      <div class="brand-logo">Samsung</div>
      <div class="brand-count">215 sản phẩm</div>
    </div>
    <div class="brand-chip">
      <div class="brand-logo">Xiaomi</div>
      <div class="brand-count">183 sản phẩm</div>
    </div>
    <div class="brand-chip">
      <div class="brand-logo">OPPO</div>
      <div class="brand-count">142 sản phẩm</div>
    </div>
    <div class="brand-chip">
      <div class="brand-logo">Realme</div>
      <div class="brand-count">97 sản phẩm</div>
    </div>
    <div class="brand-chip">
      <div class="brand-logo">Vivo</div>
      <div class="brand-count">88 sản phẩm</div>
    </div>
    <div class="brand-chip">
      <div class="brand-logo">Nokia</div>
      <div class="brand-count">54 sản phẩm</div>
    </div>
    <div class="brand-chip">
      <div class="brand-logo">Tecno</div>
      <div class="brand-count">41 sản phẩm</div>
    </div>
  </div>
</div>

<!-- FLASH SALE -->
<div style="max-width:1280px;margin:0 auto;padding:32px 24px 0;">
  <div class="flash-banner">
    <div class="flash-left">
      <div class="flash-icon">⚡</div>
      <div class="flash-text">
        <h3>FLASH SALE IMEX</h3>
        <p>Giảm đến 40% — Số lượng có hạn, nhanh tay kẻo hết!</p>
      </div>
    </div>
    <div class="countdown" id="countdown">
      <div class="count-box"><div class="num" id="h">06</div><div class="lbl">GIỜ</div></div>
      <div class="count-sep">:</div>
      <div class="count-box"><div class="num" id="m">24</div><div class="lbl">PHÚT</div></div>
      <div class="count-sep">:</div>
      <div class="count-box"><div class="num" id="s">00</div><div class="lbl">GIÂY</div></div>
    </div>
    <button class="btn-primary" style="flex-shrink:0">Xem ngay →</button>
  </div>
</div>

<!-- CATEGORIES -->
<div class="section" id="categories">
  <div class="section-header">
    <h2 class="section-title">Danh mục <span>sản phẩm</span><span class="section-line"></span></h2>
    <div class="see-all">Tất cả danh mục</div>
  </div>
  <div class="category-grid">
    <div class="cat-item"><div class="cat-icon">📱</div><div class="cat-name">Điện thoại</div></div>
    <div class="cat-item"><div class="cat-icon">💻</div><div class="cat-name">Máy tính bảng</div></div>
    <div class="cat-item"><div class="cat-icon">⌚</div><div class="cat-name">Đồng hồ thông minh</div></div>
    <div class="cat-item"><div class="cat-icon">🎧</div><div class="cat-name">Tai nghe</div></div>
    <div class="cat-item"><div class="cat-icon">🔋</div><div class="cat-name">Pin sạc dự phòng</div></div>
    <div class="cat-item"><div class="cat-icon">📷</div><div class="cat-name">Camera hành trình</div></div>
    <div class="cat-item"><div class="cat-icon">🖥️</div><div class="cat-name">Laptop</div></div>
    <div class="cat-item"><div class="cat-icon">🛡️</div><div class="cat-name">Ốp lưng & Dán màn</div></div>
  </div>
</div>

<!-- PROMO BANNERS -->
<div class="section" style="padding-top:0">
  <div class="promo-grid">
    <div class="promo-card blue">
      <div class="promo-deco">📱</div>
      <div class="promo-content">
        <div class="promo-tag">New Arrival</div>
        <div class="promo-title">iPhone 16 Series<br>Vừa ra mắt 🔥</div>
        <button class="promo-btn">Khám phá ngay</button>
      </div>
    </div>
    <div class="promo-card cyan">
      <div class="promo-deco">⌚</div>
      <div class="promo-content">
        <div class="promo-tag">Sale 30%</div>
        <div class="promo-title">Galaxy Watch</div>
        <button class="promo-btn">Mua ngay</button>
      </div>
    </div>
    <div class="promo-card dark">
      <div class="promo-deco">🎧</div>
      <div class="promo-content">
        <div class="promo-tag">Bundle Deal</div>
        <div class="promo-title">Tai nghe + Ốp lưng</div>
        <button class="promo-btn">Xem combo</button>
      </div>
    </div>
  </div>
</div>

<!-- PRODUCTS - FEATURED -->
<div class="section" id="products">
  <div class="section-header">
    <h2 class="section-title">Sản phẩm <span>nổi bật</span><span class="section-line"></span></h2>
    <div class="see-all">Xem tất cả</div>
  </div>
  <div class="product-grid">

    <!-- Product 1 -->
    <div class="product-card">
      <div class="product-img" style="background:#f0f4ff">
        <div class="product-img-inner">📱</div>
        <div class="product-tag">-15%</div>
        <button class="product-wish">🤍</button>
      </div>
      <div class="product-info">
        <div class="product-brand">Apple</div>
        <div class="product-name">iPhone 16 Pro Max 256GB Titan Tự Nhiên</div>
        <div class="product-price-wrap">
          <div class="price-now">34.990.000₫</div>
        </div>
        <div class="product-price-wrap" style="margin-top:-6px">
          <div class="price-old">41.190.000₫</div>
          <div class="price-save">-15%</div>
        </div>
        <div class="product-rating"><span class="stars">★★★★★</span> 4.9 (2.1k)</div>
        <button class="product-btn" onclick="alert('Đã thêm vào giỏ hàng!')">Thêm vào giỏ</button>
      </div>
    </div>

    <!-- Product 2 -->
    <div class="product-card">
      <div class="product-img" style="background:#fff8f0">
        <div class="product-img-inner">📲</div>
        <div class="product-tag new">Mới</div>
        <button class="product-wish">🤍</button>
      </div>
      <div class="product-info">
        <div class="product-brand">Samsung</div>
        <div class="product-name">Samsung Galaxy S25 Ultra 512GB Xanh Navy</div>
        <div class="product-price-wrap">
          <div class="price-now">31.490.000₫</div>
        </div>
        <div class="product-price-wrap" style="margin-top:-6px">
          <div class="price-old">33.990.000₫</div>
          <div class="price-save">-7%</div>
        </div>
        <div class="product-rating"><span class="stars">★★★★★</span> 4.8 (1.7k)</div>
        <button class="product-btn" onclick="alert('Đã thêm vào giỏ hàng!')">Thêm vào giỏ</button>
      </div>
    </div>

    <!-- Product 3 -->
    <div class="product-card">
      <div class="product-img" style="background:#f0fff8">
        <div class="product-img-inner">🤖</div>
        <div class="product-tag hot">Hot</div>
        <button class="product-wish">❤️</button>
      </div>
      <div class="product-info">
        <div class="product-brand">Xiaomi</div>
        <div class="product-name">Xiaomi 15 Pro 256GB Đen Huyền Bí</div>
        <div class="product-price-wrap">
          <div class="price-now">22.990.000₫</div>
        </div>
        <div class="product-price-wrap" style="margin-top:-6px">
          <div class="price-old">27.490.000₫</div>
          <div class="price-save">-16%</div>
        </div>
        <div class="product-rating"><span class="stars">★★★★☆</span> 4.7 (983)</div>
        <button class="product-btn" onclick="alert('Đã thêm vào giỏ hàng!')">Thêm vào giỏ</button>
      </div>
    </div>

    <!-- Product 4 -->
    <div class="product-card">
      <div class="product-img" style="background:#fff0f8">
        <div class="product-img-inner">🌟</div>
        <div class="product-tag">-22%</div>
        <button class="product-wish">🤍</button>
      </div>
      <div class="product-info">
        <div class="product-brand">OPPO</div>
        <div class="product-name">OPPO Find X8 Pro 512GB Trắng Băng Giá</div>
        <div class="product-price-wrap">
          <div class="price-now">19.490.000₫</div>
        </div>
        <div class="product-price-wrap" style="margin-top:-6px">
          <div class="price-old">24.990.000₫</div>
          <div class="price-save">-22%</div>
        </div>
        <div class="product-rating"><span class="stars">★★★★☆</span> 4.6 (743)</div>
        <button class="product-btn" onclick="alert('Đã thêm vào giỏ hàng!')">Thêm vào giỏ</button>
      </div>
    </div>

    <!-- Product 5 -->
    <div class="product-card">
      <div class="product-img" style="background:#f5f0ff">
        <div class="product-img-inner">⚡</div>
        <div class="product-tag new">Mới</div>
        <button class="product-wish">🤍</button>
      </div>
      <div class="product-info">
        <div class="product-brand">Realme</div>
        <div class="product-name">Realme GT 7 Pro 256GB Vũ Trụ Đen</div>
        <div class="product-price-wrap">
          <div class="price-now">14.990.000₫</div>
        </div>
        <div class="product-price-wrap" style="margin-top:-6px">
          <div class="price-old">16.990.000₫</div>
          <div class="price-save">-12%</div>
        </div>
        <div class="product-rating"><span class="stars">★★★★☆</span> 4.5 (521)</div>
        <button class="product-btn" onclick="alert('Đã thêm vào giỏ hàng!')">Thêm vào giỏ</button>
      </div>
    </div>

  </div>
</div>

<!-- FEATURES -->
<div class="features-strip">
  <div class="features-inner">
    <div class="feature-item">
      <div class="feature-ico">🚀</div>
      <div class="feature-text">
        <h4>Giao hàng siêu tốc</h4>
        <p>Toàn quốc trong 24 giờ</p>
      </div>
    </div>
    <div class="feature-item">
      <div class="feature-ico">🛡️</div>
      <div class="feature-text">
        <h4>Bảo hành chính hãng</h4>
        <p>12–24 tháng tại hãng</p>
      </div>
    </div>
    <div class="feature-item">
      <div class="feature-ico">🔄</div>
      <div class="feature-text">
        <h4>Đổi trả dễ dàng</h4>
        <p>Miễn phí trong 30 ngày</p>
      </div>
    </div>
    <div class="feature-item">
      <div class="feature-ico">💳</div>
      <div class="feature-text">
        <h4>Thanh toán linh hoạt</h4>
        <p>Trả góp 0% lãi suất</p>
      </div>
    </div>
  </div>
</div>

<!-- FOOTER -->
<footer>
  <div class="footer-inner">
    <div class="footer-grid">
      <div class="footer-brand">
        <a href="#" class="logo">
          <div class="logo-icon">IM</div>
          <div class="logo-text" style="color:#fff">IMEX<span>.</span></div>
        </a>
        <p>Nền tảng thương mại điện tử chuyên biệt thiết bị di động hàng đầu Việt Nam. Chính hãng 100%, bảo hành đầy đủ.</p>
        <div class="social-links">
          <div class="social-btn">📘</div>
          <div class="social-btn">📸</div>
          <div class="social-btn">▶️</div>
          <div class="social-btn">💬</div>
        </div>
      </div>
      <div class="footer-col">
        <h4>Hỗ trợ khách hàng</h4>
        <ul>
          <li>Chính sách bảo hành</li>
          <li>Hướng dẫn mua hàng</li>
          <li>Tra cứu đơn hàng</li>
          <li>Đổi trả & hoàn tiền</li>
          <li>Câu hỏi thường gặp</li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Về IMEX</h4>
        <ul>
          <li>Giới thiệu</li>
          <li>Tuyển dụng</li>
          <li>Tin tức & Blog</li>
          <li>Đối tác</li>
          <li>Liên hệ</li>
        </ul>
      </div>
      <div class="footer-col">
        <h4>Liên hệ</h4>
        <ul>
          <li>📞 1800-IMEX (miễn phí)</li>
          <li>✉️ support@imex.vn</li>
          <li>🕐 8:00 – 22:00 mỗi ngày</li>
          <li>📍 Toàn quốc</li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <span>© 2025 IMEX Mobile. Bảo lưu mọi quyền.</span>
      <div class="payment-icons">
        <div class="pay-ico">VISA</div>
        <div class="pay-ico">MasterCard</div>
        <div class="pay-ico">MoMo</div>
        <div class="pay-ico">ZaloPay</div>
        <div class="pay-ico">VNPay</div>
      </div>
    </div>
  </div>
</footer>

<script>
  // Countdown timer
  let totalSeconds = 6 * 3600 + 24 * 60;
  function updateCountdown() {
    const h = Math.floor(totalSeconds / 3600);
    const m = Math.floor((totalSeconds % 3600) / 60);
    const s = totalSeconds % 60;
    document.getElementById('h').textContent = String(h).padStart(2, '0');
    document.getElementById('m').textContent = String(m).padStart(2, '0');
    document.getElementById('s').textContent = String(s).padStart(2, '0');
    if (totalSeconds > 0) totalSeconds--;
  }
  setInterval(updateCountdown, 1000);
  updateCountdown();

  // Brand chip active
  document.querySelectorAll('.brand-chip').forEach(chip => {
    chip.addEventListener('click', function() {
      document.querySelectorAll('.brand-chip').forEach(c => c.classList.remove('active'));
      this.classList.add('active');
    });
  });

  // Nav item active
  document.querySelectorAll('.nav-item').forEach(item => {
    item.addEventListener('click', function() {
      document.querySelectorAll('.nav-item').forEach(i => i.classList.remove('active'));
      this.classList.add('active');
    });
  });

  // Wishlist toggle
  document.querySelectorAll('.product-wish').forEach(btn => {
    btn.addEventListener('click', function(e) {
      e.stopPropagation();
      this.textContent = this.textContent === '🤍' ? '❤️' : '🤍';
    });
  });

  // Scroll reveal
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) {
        entry.target.style.animation = 'fadeSlideUp 0.5s ease both';
      }
    });
  }, { threshold: 0.1 });
  document.querySelectorAll('.product-card, .cat-item, .promo-card').forEach(el => observer.observe(el));
</script>
</body>
</html>
