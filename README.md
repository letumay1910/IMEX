<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>IMEX - Nền Tảng Thiết Bị Điện Tử Hàng Đầu</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;500;600;700;800;900&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
:root {
  --primary: #0a2540;
  --primary-light: #1a3a5c;
  --primary-dark: #061828;
  --accent: #0066cc;
  --accent-bright: #0088ff;
  --accent-light: #e8f4ff;
  --white: #ffffff;
  --gray-50: #f8fafc;
  --gray-100: #f1f5f9;
  --gray-200: #e2e8f0;
  --gray-300: #cbd5e1;
  --gray-400: #94a3b8;
  --gray-600: #475569;
  --gray-800: #1e293b;
  --success: #10b981;
  --warning: #f59e0b;
  --danger: #ef4444;
  --gold: #f5a623;
  --shadow-sm: 0 1px 3px rgba(10,37,64,0.08);
  --shadow-md: 0 4px 16px rgba(10,37,64,0.12);
  --shadow-lg: 0 8px 32px rgba(10,37,64,0.16);
  --radius: 12px;
  --radius-sm: 8px;
  --radius-lg: 16px;
  --radius-xl: 24px;
}

* { margin: 0; padding: 0; box-sizing: border-box; }

body {
  font-family: 'Nunito', sans-serif;
  background: var(--gray-50);
  color: var(--gray-800);
  min-height: 100vh;
  overflow-x: hidden;
}

/* ===== SCROLLBAR ===== */
::-webkit-scrollbar { width: 6px; height: 6px; }
::-webkit-scrollbar-track { background: var(--gray-100); }
::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 3px; }

/* ===== TOP BAR ===== */
.topbar {
  background: var(--primary-dark);
  color: rgba(255,255,255,0.8);
  font-size: 12px;
  padding: 6px 0;
}
.topbar-inner {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.topbar a { color: rgba(255,255,255,0.8); text-decoration: none; margin-left: 16px; }
.topbar a:hover { color: var(--white); }

/* ===== HEADER ===== */
header {
  background: var(--primary);
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 2px 20px rgba(0,0,0,0.3);
}
.header-inner {
  max-width: 1280px;
  margin: 0 auto;
  padding: 14px 20px;
  display: flex;
  align-items: center;
  gap: 20px;
}
.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  text-decoration: none;
  flex-shrink: 0;
}
.logo-icon {
  width: 40px;
  height: 40px;
  background: linear-gradient(135deg, var(--accent-bright), #00c6ff);
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Space Mono', monospace;
  font-weight: 700;
  font-size: 13px;
  color: white;
}
.logo-text { color: white; font-size: 22px; font-weight: 900; letter-spacing: -0.5px; }
.logo-text span { color: #00c6ff; }

.search-bar {
  flex: 1;
  display: flex;
  max-width: 600px;
}
.search-bar input {
  flex: 1;
  padding: 10px 16px;
  border: none;
  border-radius: var(--radius-sm) 0 0 var(--radius-sm);
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  outline: none;
  background: white;
}
.search-bar select {
  padding: 10px 12px;
  border: none;
  border-left: 1px solid var(--gray-200);
  background: white;
  font-family: 'Nunito', sans-serif;
  font-size: 13px;
  cursor: pointer;
  outline: none;
  color: var(--gray-600);
}
.search-btn {
  padding: 10px 20px;
  background: var(--accent-bright);
  color: white;
  border: none;
  border-radius: 0 var(--radius-sm) var(--radius-sm) 0;
  cursor: pointer;
  font-size: 16px;
  font-weight: 700;
  transition: background 0.2s;
}
.search-btn:hover { background: #0077ee; }

.header-actions {
  display: flex;
  align-items: center;
  gap: 6px;
  flex-shrink: 0;
}
.header-btn {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 2px;
  padding: 8px 12px;
  color: white;
  cursor: pointer;
  border-radius: var(--radius-sm);
  border: none;
  background: transparent;
  font-family: 'Nunito', sans-serif;
  text-decoration: none;
  transition: background 0.2s;
  position: relative;
}
.header-btn:hover { background: rgba(255,255,255,0.1); }
.header-btn .icon { font-size: 20px; }
.header-btn .label { font-size: 11px; color: rgba(255,255,255,0.8); }
.badge {
  position: absolute;
  top: 4px;
  right: 4px;
  background: #ff4444;
  color: white;
  font-size: 10px;
  font-weight: 700;
  min-width: 16px;
  height: 16px;
  border-radius: 8px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0 4px;
}

/* ===== NAV ===== */
nav {
  background: var(--primary-light);
  border-bottom: 1px solid rgba(255,255,255,0.05);
}
.nav-inner {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 20px;
  display: flex;
  align-items: center;
  gap: 2px;
  overflow-x: auto;
}
.nav-inner::-webkit-scrollbar { height: 0; }
.nav-item {
  padding: 10px 14px;
  color: rgba(255,255,255,0.85);
  font-size: 13px;
  font-weight: 600;
  cursor: pointer;
  white-space: nowrap;
  border-radius: 0;
  border-bottom: 2px solid transparent;
  transition: all 0.2s;
  position: relative;
}
.nav-item:hover, .nav-item.active {
  color: white;
  border-bottom-color: #00c6ff;
  background: rgba(255,255,255,0.05);
}

/* ===== MAIN LAYOUT ===== */
.main-layout {
  max-width: 1280px;
  margin: 0 auto;
  padding: 0 20px;
}

/* ===== HERO SECTION ===== */
.hero {
  margin: 20px 0;
  display: grid;
  grid-template-columns: 1fr 280px;
  gap: 16px;
}
.hero-slider {
  background: linear-gradient(135deg, var(--primary) 0%, #1565c0 50%, #0288d1 100%);
  border-radius: var(--radius-lg);
  padding: 40px;
  position: relative;
  overflow: hidden;
  min-height: 340px;
  display: flex;
  align-items: center;
  cursor: pointer;
}
.hero-slider::before {
  content: '';
  position: absolute;
  right: -40px;
  top: -40px;
  width: 350px;
  height: 350px;
  background: rgba(255,255,255,0.05);
  border-radius: 50%;
}
.hero-slider::after {
  content: '';
  position: absolute;
  right: 40px;
  bottom: -60px;
  width: 200px;
  height: 200px;
  background: rgba(0,198,255,0.15);
  border-radius: 50%;
}
.hero-content { position: relative; z-index: 1; }
.hero-badge {
  display: inline-block;
  background: var(--gold);
  color: var(--primary-dark);
  font-size: 11px;
  font-weight: 800;
  padding: 4px 12px;
  border-radius: 20px;
  margin-bottom: 12px;
  letter-spacing: 0.5px;
  text-transform: uppercase;
}
.hero-title {
  font-size: 36px;
  font-weight: 900;
  color: white;
  line-height: 1.15;
  margin-bottom: 12px;
  letter-spacing: -0.5px;
}
.hero-title span { color: #00c6ff; }
.hero-desc { color: rgba(255,255,255,0.8); font-size: 15px; margin-bottom: 24px; max-width: 420px; }
.hero-price { color: var(--gold); font-size: 28px; font-weight: 900; margin-bottom: 8px; }
.hero-old-price { color: rgba(255,255,255,0.5); font-size: 15px; text-decoration: line-through; margin-bottom: 20px; }
.btn-primary {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 12px 24px;
  background: white;
  color: var(--primary);
  border: none;
  border-radius: var(--radius);
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 800;
  cursor: pointer;
  transition: all 0.2s;
  text-decoration: none;
}
.btn-primary:hover { transform: translateY(-2px); box-shadow: 0 8px 20px rgba(0,0,0,0.2); }

.hero-device {
  position: absolute;
  right: 60px;
  top: 50%;
  transform: translateY(-50%);
  font-size: 160px;
  opacity: 0.15;
  pointer-events: none;
}

.hero-slider-dots {
  position: absolute;
  bottom: 16px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 6px;
}
.dot {
  width: 6px;
  height: 6px;
  border-radius: 3px;
  background: rgba(255,255,255,0.4);
  cursor: pointer;
  transition: all 0.3s;
}
.dot.active { width: 20px; background: white; }

.hero-sidebar {
  display: flex;
  flex-direction: column;
  gap: 12px;
}
.hero-banner {
  background: linear-gradient(135deg, #1a237e, #283593);
  border-radius: var(--radius);
  padding: 20px;
  color: white;
  cursor: pointer;
  transition: transform 0.2s;
  flex: 1;
  position: relative;
  overflow: hidden;
}
.hero-banner:hover { transform: translateY(-2px); }
.hero-banner .banner-icon { font-size: 32px; margin-bottom: 8px; }
.hero-banner .banner-title { font-size: 15px; font-weight: 800; margin-bottom: 4px; }
.hero-banner .banner-desc { font-size: 12px; color: rgba(255,255,255,0.7); }
.hero-banner .banner-tag {
  position: absolute;
  top: 12px;
  right: 12px;
  background: #ff4444;
  color: white;
  font-size: 10px;
  font-weight: 800;
  padding: 3px 8px;
  border-radius: 10px;
}
.hero-banner.green { background: linear-gradient(135deg, #1b5e20, #2e7d32); }
.hero-banner.orange { background: linear-gradient(135deg, #e65100, #bf360c); }

/* ===== FLASH SALE ===== */
.section { margin: 24px 0; }
.section-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}
.section-title {
  display: flex;
  align-items: center;
  gap: 10px;
}
.section-title h2 {
  font-size: 20px;
  font-weight: 900;
  color: var(--primary);
}
.title-accent {
  width: 4px;
  height: 24px;
  background: var(--accent-bright);
  border-radius: 2px;
}
.see-all {
  font-size: 13px;
  color: var(--accent);
  cursor: pointer;
  font-weight: 700;
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 4px;
}
.see-all:hover { color: var(--accent-bright); }

.flash-banner {
  background: linear-gradient(90deg, var(--primary) 0%, var(--accent) 100%);
  border-radius: var(--radius-lg) var(--radius-lg) 0 0;
  padding: 12px 20px;
  display: flex;
  align-items: center;
  gap: 16px;
}
.flash-title { color: white; font-size: 18px; font-weight: 900; }
.flash-icon { font-size: 22px; }
.countdown {
  display: flex;
  align-items: center;
  gap: 6px;
  margin-left: auto;
}
.countdown-label { color: rgba(255,255,255,0.8); font-size: 13px; }
.time-block {
  background: var(--primary-dark);
  color: white;
  font-family: 'Space Mono', monospace;
  font-size: 16px;
  font-weight: 700;
  padding: 4px 8px;
  border-radius: 6px;
  min-width: 36px;
  text-align: center;
}
.time-sep { color: white; font-weight: 900; }

/* ===== PRODUCT CARDS ===== */
.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 12px;
}
.products-scroll {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  padding-bottom: 8px;
  scroll-snap-type: x mandatory;
}
.products-scroll::-webkit-scrollbar { height: 4px; }
.products-scroll .product-card { flex: 0 0 200px; scroll-snap-align: start; }

.product-card {
  background: white;
  border-radius: var(--radius);
  overflow: hidden;
  box-shadow: var(--shadow-sm);
  transition: all 0.25s;
  cursor: pointer;
  position: relative;
  border: 1px solid var(--gray-100);
}
.product-card:hover {
  box-shadow: var(--shadow-md);
  transform: translateY(-4px);
  border-color: var(--accent-light);
}
.product-img {
  width: 100%;
  height: 170px;
  background: var(--gray-50);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 80px;
  position: relative;
  overflow: hidden;
}
.product-img-bg {
  position: absolute;
  inset: 0;
  background: linear-gradient(135deg, #f0f4ff 0%, #e8f4ff 100%);
}
.product-img .emoji { position: relative; z-index: 1; }
.product-tags {
  position: absolute;
  top: 8px;
  left: 8px;
  display: flex;
  flex-direction: column;
  gap: 4px;
}
.tag {
  font-size: 10px;
  font-weight: 800;
  padding: 2px 8px;
  border-radius: 10px;
  text-transform: uppercase;
  letter-spacing: 0.3px;
}
.tag-sale { background: #ff4444; color: white; }
.tag-new { background: var(--success); color: white; }
.tag-hot { background: var(--gold); color: var(--primary-dark); }
.tag-official { background: var(--accent); color: white; }
.tag-import { background: var(--primary); color: white; }

.product-wishlist {
  position: absolute;
  top: 8px;
  right: 8px;
  width: 30px;
  height: 30px;
  background: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 14px;
  cursor: pointer;
  box-shadow: var(--shadow-sm);
  border: none;
  transition: all 0.2s;
  z-index: 2;
}
.product-wishlist:hover { transform: scale(1.1); }

.product-info { padding: 12px; }
.product-shop {
  font-size: 10px;
  color: var(--accent);
  font-weight: 700;
  margin-bottom: 4px;
  display: flex;
  align-items: center;
  gap: 4px;
}
.shop-verified { color: var(--success); font-size: 10px; }
.product-name {
  font-size: 13px;
  font-weight: 600;
  color: var(--gray-800);
  line-height: 1.4;
  margin-bottom: 8px;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.product-price-row {
  display: flex;
  align-items: flex-end;
  gap: 6px;
  margin-bottom: 6px;
}
.price-new { font-size: 18px; font-weight: 900; color: #e53935; }
.price-old { font-size: 12px; color: var(--gray-400); text-decoration: line-through; }
.price-discount {
  font-size: 11px;
  background: #fff3e0;
  color: #e65100;
  padding: 1px 6px;
  border-radius: 4px;
  font-weight: 800;
  margin-left: auto;
}
.product-meta {
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 11px;
  color: var(--gray-400);
}
.rating { display: flex; align-items: center; gap: 3px; color: var(--gold); }
.rating span { color: var(--gray-400); }
.sold-count { font-size: 11px; }

.product-progress {
  margin-top: 8px;
  background: var(--gray-100);
  border-radius: 4px;
  height: 4px;
  overflow: hidden;
}
.product-progress-bar {
  height: 100%;
  background: linear-gradient(90deg, var(--accent-bright), #00c6ff);
  border-radius: 4px;
}
.progress-label {
  font-size: 10px;
  color: #e53935;
  font-weight: 700;
  margin-top: 4px;
  text-align: center;
}

.add-cart-btn {
  width: 100%;
  margin-top: 10px;
  padding: 8px;
  background: var(--accent-light);
  color: var(--accent);
  border: 1px solid var(--accent);
  border-radius: var(--radius-sm);
  font-family: 'Nunito', sans-serif;
  font-size: 12px;
  font-weight: 800;
  cursor: pointer;
  transition: all 0.2s;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
}
.add-cart-btn:hover { background: var(--accent); color: white; }

/* ===== CATEGORIES ===== */
.categories-grid {
  display: grid;
  grid-template-columns: repeat(6, 1fr);
  gap: 12px;
}
.cat-card {
  background: white;
  border-radius: var(--radius);
  padding: 16px 12px;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
  border: 1px solid var(--gray-100);
  box-shadow: var(--shadow-sm);
}
.cat-card:hover {
  border-color: var(--accent);
  box-shadow: var(--shadow-md);
  transform: translateY(-3px);
}
.cat-icon {
  font-size: 32px;
  margin-bottom: 8px;
  display: block;
}
.cat-name {
  font-size: 11px;
  font-weight: 700;
  color: var(--gray-800);
  line-height: 1.3;
}
.cat-count {
  font-size: 10px;
  color: var(--accent);
  font-weight: 600;
  margin-top: 2px;
}

/* ===== BRANDS ===== */
.brands-row {
  display: flex;
  gap: 12px;
  overflow-x: auto;
  padding-bottom: 8px;
}
.brand-card {
  flex: 0 0 auto;
  background: white;
  border-radius: var(--radius);
  padding: 12px 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  border: 1px solid var(--gray-200);
  font-size: 13px;
  font-weight: 800;
  color: var(--gray-600);
  transition: all 0.2s;
  min-width: 100px;
}
.brand-card:hover {
  border-color: var(--accent);
  color: var(--accent);
  box-shadow: var(--shadow-sm);
}

/* ===== FILTER BAR ===== */
.filter-bar {
  background: white;
  border-radius: var(--radius);
  padding: 16px;
  margin-bottom: 16px;
  display: flex;
  align-items: center;
  gap: 12px;
  flex-wrap: wrap;
  box-shadow: var(--shadow-sm);
  border: 1px solid var(--gray-100);
}
.filter-label { font-size: 13px; font-weight: 700; color: var(--gray-600); }
.filter-chip {
  padding: 6px 14px;
  border-radius: 20px;
  font-size: 12px;
  font-weight: 700;
  cursor: pointer;
  border: 1px solid var(--gray-200);
  background: white;
  color: var(--gray-600);
  transition: all 0.2s;
}
.filter-chip:hover, .filter-chip.active {
  background: var(--accent);
  color: white;
  border-color: var(--accent);
}
.filter-select {
  padding: 6px 12px;
  border-radius: var(--radius-sm);
  font-size: 12px;
  font-family: 'Nunito', sans-serif;
  font-weight: 600;
  border: 1px solid var(--gray-200);
  color: var(--gray-600);
  background: white;
  cursor: pointer;
  outline: none;
}
.filter-divider {
  width: 1px;
  height: 20px;
  background: var(--gray-200);
}

/* ===== SHOP SECTION ===== */
.shops-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.shop-card {
  background: white;
  border-radius: var(--radius-lg);
  padding: 20px;
  border: 1px solid var(--gray-100);
  box-shadow: var(--shadow-sm);
  cursor: pointer;
  transition: all 0.2s;
}
.shop-card:hover { box-shadow: var(--shadow-md); transform: translateY(-2px); }
.shop-header { display: flex; align-items: center; gap: 12px; margin-bottom: 12px; }
.shop-avatar {
  width: 50px;
  height: 50px;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--primary), var(--accent));
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
}
.shop-name { font-size: 15px; font-weight: 800; color: var(--primary); }
.shop-badge {
  font-size: 10px;
  background: var(--accent-light);
  color: var(--accent);
  padding: 2px 8px;
  border-radius: 10px;
  font-weight: 700;
  margin-top: 2px;
  display: inline-block;
}
.shop-stats { display: flex; gap: 16px; margin-bottom: 12px; }
.shop-stat { font-size: 12px; color: var(--gray-400); }
.shop-stat strong { color: var(--gray-800); display: block; font-size: 14px; }
.shop-products { display: flex; gap: 6px; }
.shop-product-thumb {
  width: 56px;
  height: 56px;
  border-radius: var(--radius-sm);
  background: var(--gray-50);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  border: 1px solid var(--gray-100);
}
.follow-btn {
  margin-top: 12px;
  width: 100%;
  padding: 8px;
  border: 1px solid var(--accent);
  border-radius: var(--radius-sm);
  background: white;
  color: var(--accent);
  font-family: 'Nunito', sans-serif;
  font-size: 12px;
  font-weight: 800;
  cursor: pointer;
  transition: all 0.2s;
}
.follow-btn:hover { background: var(--accent); color: white; }

/* ===== PROMO BANNERS ===== */
.promo-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 12px;
  margin: 24px 0;
}
.promo-card {
  border-radius: var(--radius-lg);
  padding: 20px 24px;
  position: relative;
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.2s;
  min-height: 120px;
  display: flex;
  align-items: center;
}
.promo-card:hover { transform: translateY(-2px); }
.promo-card.blue { background: linear-gradient(135deg, #1565c0, #0288d1); }
.promo-card.dark { background: linear-gradient(135deg, var(--primary), #283593); }
.promo-card.teal { background: linear-gradient(135deg, #00695c, #00897b); }
.promo-content { position: relative; z-index: 1; }
.promo-tag { font-size: 10px; color: rgba(255,255,255,0.8); text-transform: uppercase; font-weight: 700; margin-bottom: 6px; }
.promo-title { font-size: 18px; font-weight: 900; color: white; margin-bottom: 4px; }
.promo-desc { font-size: 12px; color: rgba(255,255,255,0.75); }
.promo-bg-icon {
  position: absolute;
  right: 16px;
  bottom: -10px;
  font-size: 72px;
  opacity: 0.15;
}

/* ===== REVIEW SECTION ===== */
.reviews-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 16px;
}
.review-card {
  background: white;
  border-radius: var(--radius);
  padding: 16px;
  border: 1px solid var(--gray-100);
  box-shadow: var(--shadow-sm);
}
.review-header { display: flex; align-items: center; gap: 10px; margin-bottom: 10px; }
.reviewer-avatar {
  width: 36px;
  height: 36px;
  border-radius: 50%;
  background: linear-gradient(135deg, var(--accent), #00c6ff);
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 14px;
  font-weight: 700;
  flex-shrink: 0;
}
.reviewer-name { font-size: 13px; font-weight: 700; }
.reviewer-date { font-size: 11px; color: var(--gray-400); }
.review-stars { color: var(--gold); font-size: 13px; margin-bottom: 6px; }
.review-text { font-size: 13px; color: var(--gray-600); line-height: 1.5; }
.review-product { font-size: 11px; color: var(--accent); margin-top: 8px; font-weight: 600; }
.review-images { display: flex; gap: 6px; margin-top: 8px; }
.review-img {
  width: 50px;
  height: 50px;
  border-radius: 6px;
  background: var(--gray-100);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 22px;
}

/* ===== FEATURES ===== */
.features-row {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 16px;
  margin: 24px 0;
}
.feature-card {
  background: white;
  border-radius: var(--radius);
  padding: 20px;
  text-align: center;
  border: 1px solid var(--gray-100);
  box-shadow: var(--shadow-sm);
}
.feature-icon { font-size: 32px; margin-bottom: 10px; }
.feature-title { font-size: 14px; font-weight: 800; color: var(--primary); margin-bottom: 4px; }
.feature-desc { font-size: 12px; color: var(--gray-400); line-height: 1.4; }

/* ===== NOTIFICATION TOAST ===== */
.toast {
  position: fixed;
  bottom: 24px;
  right: 24px;
  background: var(--primary);
  color: white;
  padding: 12px 20px;
  border-radius: var(--radius);
  font-size: 13px;
  font-weight: 600;
  z-index: 9999;
  display: flex;
  align-items: center;
  gap: 8px;
  box-shadow: var(--shadow-lg);
  transform: translateX(120%);
  transition: transform 0.3s ease;
}
.toast.show { transform: translateX(0); }

/* ===== MODAL ===== */
.modal-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0,0,0,0.5);
  z-index: 2000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s;
}
.modal-overlay.open { opacity: 1; pointer-events: all; }
.modal {
  background: white;
  border-radius: var(--radius-xl);
  width: 100%;
  max-width: 760px;
  max-height: 85vh;
  overflow-y: auto;
  transform: scale(0.95);
  transition: transform 0.3s;
}
.modal-overlay.open .modal { transform: scale(1); }
.modal-header {
  padding: 20px 24px;
  border-bottom: 1px solid var(--gray-100);
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: sticky;
  top: 0;
  background: white;
  z-index: 1;
}
.modal-title { font-size: 18px; font-weight: 900; color: var(--primary); }
.modal-close {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  border: none;
  background: var(--gray-100);
  cursor: pointer;
  font-size: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background 0.2s;
}
.modal-close:hover { background: var(--gray-200); }
.modal-body { padding: 24px; }

/* ===== PRODUCT DETAIL ===== */
.product-detail-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 24px;
}
.product-detail-images {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.product-main-img {
  background: var(--gray-50);
  border-radius: var(--radius);
  height: 220px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 100px;
  border: 1px solid var(--gray-100);
}
.product-thumb-row {
  display: flex;
  gap: 8px;
}
.product-thumb {
  width: 56px;
  height: 56px;
  background: var(--gray-50);
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 28px;
  border: 2px solid transparent;
  cursor: pointer;
  transition: border-color 0.2s;
}
.product-thumb.active { border-color: var(--accent); }
.detail-name { font-size: 18px; font-weight: 900; color: var(--primary); margin-bottom: 8px; line-height: 1.3; }
.detail-price { font-size: 28px; font-weight: 900; color: #e53935; margin-bottom: 4px; }
.detail-old-price { font-size: 14px; color: var(--gray-400); text-decoration: line-through; margin-bottom: 12px; }
.detail-rating { display: flex; align-items: center; gap: 8px; margin-bottom: 16px; font-size: 13px; }
.detail-rating .stars { color: var(--gold); }
.detail-specs {
  background: var(--gray-50);
  border-radius: var(--radius-sm);
  padding: 12px;
  margin-bottom: 16px;
  font-size: 12px;
}
.spec-row {
  display: flex;
  gap: 8px;
  margin-bottom: 4px;
}
.spec-row:last-child { margin-bottom: 0; }
.spec-key { color: var(--gray-400); width: 100px; flex-shrink: 0; }
.spec-val { color: var(--gray-800); font-weight: 600; }
.quantity-row {
  display: flex;
  align-items: center;
  gap: 12px;
  margin-bottom: 16px;
}
.qty-label { font-size: 13px; font-weight: 700; color: var(--gray-600); }
.qty-control {
  display: flex;
  align-items: center;
  border: 1px solid var(--gray-200);
  border-radius: var(--radius-sm);
  overflow: hidden;
}
.qty-btn {
  width: 32px;
  height: 32px;
  border: none;
  background: var(--gray-50);
  cursor: pointer;
  font-size: 16px;
  font-weight: 700;
  color: var(--gray-600);
  transition: background 0.2s;
}
.qty-btn:hover { background: var(--gray-200); }
.qty-input {
  width: 48px;
  height: 32px;
  border: none;
  text-align: center;
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 700;
  outline: none;
}
.btn-cart {
  flex: 1;
  padding: 12px;
  background: var(--accent-light);
  color: var(--accent);
  border: 2px solid var(--accent);
  border-radius: var(--radius);
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 800;
  cursor: pointer;
  transition: all 0.2s;
}
.btn-cart:hover { background: var(--accent); color: white; }
.btn-buy {
  flex: 1;
  padding: 12px;
  background: var(--accent);
  color: white;
  border: none;
  border-radius: var(--radius);
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  font-weight: 800;
  cursor: pointer;
  transition: background 0.2s;
}
.btn-buy:hover { background: var(--accent-bright); }
.btn-row { display: flex; gap: 10px; }

/* ===== CART SIDEBAR ===== */
.cart-overlay {
  position: fixed;
  inset: 0;
  z-index: 3000;
  display: flex;
  justify-content: flex-end;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s;
}
.cart-overlay.open { opacity: 1; pointer-events: all; }
.cart-bg {
  position: absolute;
  inset: 0;
  background: rgba(0,0,0,0.5);
}
.cart-panel {
  position: relative;
  width: 420px;
  background: white;
  height: 100%;
  display: flex;
  flex-direction: column;
  transform: translateX(100%);
  transition: transform 0.3s;
  box-shadow: -4px 0 24px rgba(0,0,0,0.15);
}
.cart-overlay.open .cart-panel { transform: translateX(0); }
.cart-header {
  padding: 20px;
  background: var(--primary);
  color: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.cart-header-title { font-size: 18px; font-weight: 900; }
.cart-close {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: none;
  background: rgba(255,255,255,0.2);
  color: white;
  cursor: pointer;
  font-size: 16px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.cart-items { flex: 1; overflow-y: auto; padding: 16px; }
.cart-item {
  display: flex;
  gap: 12px;
  padding: 12px 0;
  border-bottom: 1px solid var(--gray-100);
}
.cart-item-img {
  width: 60px;
  height: 60px;
  background: var(--gray-50);
  border-radius: var(--radius-sm);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 30px;
  flex-shrink: 0;
}
.cart-item-info { flex: 1; }
.cart-item-name { font-size: 13px; font-weight: 600; margin-bottom: 4px; }
.cart-item-price { font-size: 15px; font-weight: 900; color: #e53935; }
.cart-item-remove { color: var(--gray-400); cursor: pointer; font-size: 14px; padding: 4px; }
.cart-footer {
  padding: 16px 20px;
  border-top: 1px solid var(--gray-100);
}
.cart-total {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 12px;
}
.cart-total-label { font-size: 15px; font-weight: 700; }
.cart-total-amount { font-size: 22px; font-weight: 900; color: #e53935; }
.checkout-btn {
  width: 100%;
  padding: 14px;
  background: var(--accent);
  color: white;
  border: none;
  border-radius: var(--radius);
  font-family: 'Nunito', sans-serif;
  font-size: 15px;
  font-weight: 900;
  cursor: pointer;
  transition: background 0.2s;
}
.checkout-btn:hover { background: var(--accent-bright); }

/* ===== COMPARE BAR ===== */
.compare-bar {
  position: fixed;
  bottom: 0;
  left: 0;
  right: 0;
  background: var(--primary);
  padding: 12px 20px;
  display: flex;
  align-items: center;
  gap: 16px;
  z-index: 500;
  transform: translateY(100%);
  transition: transform 0.3s;
}
.compare-bar.show { transform: translateY(0); }
.compare-title { color: white; font-weight: 700; font-size: 14px; flex-shrink: 0; }
.compare-items { display: flex; gap: 12px; flex: 1; }
.compare-item {
  background: rgba(255,255,255,0.1);
  border-radius: var(--radius-sm);
  padding: 8px 12px;
  color: white;
  font-size: 12px;
  display: flex;
  align-items: center;
  gap: 8px;
}
.compare-item .remove { cursor: pointer; opacity: 0.7; }
.compare-btn {
  padding: 10px 20px;
  background: var(--accent-bright);
  color: white;
  border: none;
  border-radius: var(--radius);
  font-family: 'Nunito', sans-serif;
  font-weight: 800;
  font-size: 13px;
  cursor: pointer;
}

/* ===== FOOTER ===== */
footer {
  background: var(--primary-dark);
  color: rgba(255,255,255,0.8);
  margin-top: 48px;
}
.footer-top {
  max-width: 1280px;
  margin: 0 auto;
  padding: 40px 20px 32px;
  display: grid;
  grid-template-columns: 2fr 1fr 1fr 1fr 1fr;
  gap: 32px;
}
.footer-brand .logo-text { color: white; font-size: 24px; }
.footer-desc { font-size: 13px; margin-top: 12px; line-height: 1.6; max-width: 240px; }
.footer-socials { display: flex; gap: 10px; margin-top: 16px; }
.social-btn {
  width: 34px;
  height: 34px;
  border-radius: 50%;
  background: rgba(255,255,255,0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 16px;
  cursor: pointer;
  transition: background 0.2s;
  text-decoration: none;
}
.social-btn:hover { background: var(--accent); }
.footer-col h4 { font-size: 14px; font-weight: 800; color: white; margin-bottom: 12px; }
.footer-col a {
  display: block;
  font-size: 13px;
  color: rgba(255,255,255,0.65);
  text-decoration: none;
  margin-bottom: 8px;
  transition: color 0.2s;
}
.footer-col a:hover { color: #00c6ff; }
.footer-bottom {
  border-top: 1px solid rgba(255,255,255,0.08);
  padding: 16px 20px;
  max-width: 1280px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  justify-content: space-between;
  font-size: 12px;
}
.payment-icons { display: flex; gap: 8px; }
.payment-icon {
  background: white;
  border-radius: 4px;
  padding: 4px 8px;
  font-size: 11px;
  font-weight: 800;
  color: var(--primary);
}

/* ===== LOADING SKELETON ===== */
.skeleton {
  background: linear-gradient(90deg, var(--gray-100) 0%, var(--gray-50) 50%, var(--gray-100) 100%);
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
  border-radius: var(--radius-sm);
}
@keyframes shimmer {
  0% { background-position: -200% 0; }
  100% { background-position: 200% 0; }
}

/* ===== ANIMATIONS ===== */
@keyframes fadeInUp {
  from { opacity: 0; transform: translateY(20px); }
  to { opacity: 1; transform: translateY(0); }
}
.fade-in { animation: fadeInUp 0.4s ease both; }
.fade-in-1 { animation-delay: 0.1s; }
.fade-in-2 { animation-delay: 0.2s; }
.fade-in-3 { animation-delay: 0.3s; }

@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.6; }
}
.live-dot {
  display: inline-block;
  width: 8px;
  height: 8px;
  background: #ff4444;
  border-radius: 50%;
  animation: pulse 1s infinite;
}

/* ===== TABS ===== */
.tabs {
  display: flex;
  border-bottom: 2px solid var(--gray-100);
  margin-bottom: 20px;
  gap: 4px;
}
.tab {
  padding: 10px 20px;
  font-size: 14px;
  font-weight: 700;
  color: var(--gray-400);
  cursor: pointer;
  border-bottom: 2px solid transparent;
  margin-bottom: -2px;
  transition: all 0.2s;
}
.tab:hover { color: var(--accent); }
.tab.active { color: var(--accent); border-bottom-color: var(--accent); }

/* ===== SEARCH SUGGESTIONS ===== */
.search-suggestions {
  position: absolute;
  top: 100%;
  left: 0;
  right: 0;
  background: white;
  border-radius: 0 0 var(--radius) var(--radius);
  box-shadow: var(--shadow-md);
  z-index: 1000;
  display: none;
  border: 1px solid var(--gray-100);
  border-top: none;
}
.search-suggestions.show { display: block; }
.search-suggestion-item {
  padding: 10px 16px;
  font-size: 13px;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 10px;
  transition: background 0.15s;
}
.search-suggestion-item:hover { background: var(--gray-50); }
.search-suggestion-item .icon { color: var(--gray-400); font-size: 14px; }

/* ===== BACK TO TOP ===== */
.back-to-top {
  position: fixed;
  bottom: 24px;
  left: 24px;
  width: 44px;
  height: 44px;
  background: var(--accent);
  color: white;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 20px;
  cursor: pointer;
  box-shadow: var(--shadow-md);
  opacity: 0;
  transition: all 0.3s;
  border: none;
}
.back-to-top.show { opacity: 1; }
.back-to-top:hover { background: var(--accent-bright); transform: translateY(-2px); }

/* ===== VOUCHER ===== */
.voucher-row {
  display: flex;
  gap: 12px;
  flex-wrap: wrap;
}
.voucher-card {
  background: white;
  border: 1px dashed var(--accent);
  border-radius: var(--radius);
  padding: 12px 16px;
  display: flex;
  align-items: center;
  gap: 16px;
  cursor: pointer;
  transition: all 0.2s;
  position: relative;
  overflow: hidden;
}
.voucher-card::before {
  content: '';
  position: absolute;
  left: -6px;
  top: 50%;
  transform: translateY(-50%);
  width: 12px;
  height: 12px;
  background: var(--gray-50);
  border-radius: 50%;
  border: 1px dashed var(--accent);
}
.voucher-card::after {
  content: '';
  position: absolute;
  right: -6px;
  top: 50%;
  transform: translateY(-50%);
  width: 12px;
  height: 12px;
  background: var(--gray-50);
  border-radius: 50%;
  border: 1px dashed var(--accent);
}
.voucher-card:hover { background: var(--accent-light); }
.voucher-discount { font-size: 22px; font-weight: 900; color: #e53935; }
.voucher-label { font-size: 11px; color: var(--gray-400); }
.voucher-condition { font-size: 12px; color: var(--gray-600); font-weight: 600; }
.voucher-expiry { font-size: 10px; color: var(--gray-400); margin-top: 2px; }
.collect-btn {
  padding: 6px 14px;
  background: var(--accent);
  color: white;
  border: none;
  border-radius: var(--radius-sm);
  font-family: 'Nunito', sans-serif;
  font-size: 12px;
  font-weight: 800;
  cursor: pointer;
  white-space: nowrap;
}
.collect-btn.collected { background: var(--gray-200); color: var(--gray-400); cursor: default; }

/* ===== MOBILE BOTTOM NAV ===== */
.mobile-nav {
  display: none;
}

@media (max-width: 768px) {
  .categories-grid { grid-template-columns: repeat(4, 1fr); }
  .shops-grid { grid-template-columns: 1fr; }
  .footer-top { grid-template-columns: 1fr 1fr; }
  .hero { grid-template-columns: 1fr; }
  .hero-sidebar { display: none; }
  .features-row { grid-template-columns: repeat(2, 1fr); }
  .promo-grid { grid-template-columns: 1fr; }
  .reviews-grid { grid-template-columns: 1fr; }
  .product-detail-grid { grid-template-columns: 1fr; }
}
</style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
  <div class="topbar-inner">
    <div>🇻🇳 Kênh người bán &nbsp;|&nbsp; Tải ứng dụng &nbsp;|&nbsp; Kết nối</div>
    <div>
      <a href="#">Thông báo</a>
      <a href="#">Hỗ trợ</a>
      <a href="#">Tiếng Việt</a>
    </div>
  </div>
</div>

<!-- HEADER -->
<header>
  <div class="header-inner">
    <a class="logo" href="#" onclick="showPage('home')">
      <div class="logo-icon">iMX</div>
      <div class="logo-text">IM<span>EX</span></div>
    </a>

    <div class="search-bar" style="position:relative;">
      <select id="searchCat">
        <option>Tất cả</option>
        <option>Điện thoại</option>
        <option>Laptop</option>
        <option>Máy tính bảng</option>
        <option>Đồng hồ thông minh</option>
        <option>Camera</option>
        <option>Phụ kiện</option>
      </select>
      <input type="text" id="searchInput" placeholder="Tìm kiếm thiết bị điện tử..." 
        oninput="showSuggestions(this.value)" onblur="hideSuggestions()">
      <div class="search-suggestions" id="suggestions">
        <div class="search-suggestion-item"><span class="icon">🔍</span> iPhone 15 Pro Max</div>
        <div class="search-suggestion-item"><span class="icon">🔍</span> Samsung Galaxy S25 Ultra</div>
        <div class="search-suggestion-item"><span class="icon">🔍</span> MacBook Pro M4</div>
        <div class="search-suggestion-item"><span class="icon">🔍</span> iPad Pro 2025</div>
        <div class="search-suggestion-item"><span class="icon">🔍</span> Apple Watch Series 10</div>
        <div class="search-suggestion-item"><span class="icon">🔥</span> Laptop gaming RTX 4090</div>
      </div>
      <button class="search-btn" onclick="doSearch()">🔍</button>
    </div>

    <div class="header-actions">
      <button class="header-btn" onclick="toggleCart()">
        <span class="icon">🛒</span>
        <span class="label">Giỏ hàng</span>
        <span class="badge" id="cartBadge">3</span>
      </button>
      <button class="header-btn" onclick="showPage('wishlist')">
        <span class="icon">❤️</span>
        <span class="label">Yêu thích</span>
        <span class="badge">5</span>
      </button>
      <button class="header-btn" onclick="showPage('profile')">
        <span class="icon">👤</span>
        <span class="label">Tài khoản</span>
      </button>
      <button class="header-btn" onclick="showPage('orders')">
        <span class="icon">📦</span>
        <span class="label">Đơn hàng</span>
      </button>
    </div>
  </div>
</header>

<!-- NAV -->
<nav>
  <div class="nav-inner">
    <div class="nav-item active" onclick="setNav(this,'home')">🏠 Trang chủ</div>
    <div class="nav-item" onclick="setNav(this,'phone')">📱 Điện thoại</div>
    <div class="nav-item" onclick="setNav(this,'laptop')">💻 Laptop</div>
    <div class="nav-item" onclick="setNav(this,'tablet')">📟 Máy tính bảng</div>
    <div class="nav-item" onclick="setNav(this,'watch')">⌚ Đồng hồ TM</div>
    <div class="nav-item" onclick="setNav(this,'camera')">📷 Máy ảnh/Quay</div>
    <div class="nav-item" onclick="setNav(this,'portable')">🎮 Thiết bị di động</div>
    <div class="nav-item" onclick="setNav(this,'audio')">🎵 Nhạc số</div>
    <div class="nav-item" onclick="setNav(this,'wearable')">🥽 Wearable</div>
    <div class="nav-item" onclick="setNav(this,'accessory')">🔌 Phụ kiện</div>
    <div class="nav-item" onclick="setNav(this,'imex')">🌐 Hàng Nhập Khẩu</div>
    <div class="nav-item" onclick="setNav(this,'flash')">⚡ Flash Sale</div>
  </div>
</nav>

<!-- MAIN -->
<div class="main-layout" id="mainContent">

  <!-- HERO -->
  <div class="hero fade-in">
    <div class="hero-slider" onclick="openProduct(0)">
      <div class="hero-content">
        <div class="hero-badge">⚡ Flash Deal Hôm Nay</div>
        <div class="hero-title">iPhone 16 Pro Max<br><span>Titan Đen 256GB</span></div>
        <div class="hero-desc">Chip A18 Pro, Camera 48MP, Màn hình ProMotion 6.9"</div>
        <div class="hero-price">29.990.000 ₫</div>
        <div class="hero-old-price">34.990.000 ₫ &nbsp; -14%</div>
        <a class="btn-primary" href="#">🛒 Mua ngay</a>
      </div>
      <div class="hero-device">📱</div>
      <div class="hero-slider-dots">
        <div class="dot active"></div>
        <div class="dot"></div>
        <div class="dot"></div>
        <div class="dot"></div>
      </div>
    </div>
    <div class="hero-sidebar">
      <div class="hero-banner" onclick="setNav(document.querySelector('.nav-item:nth-child(3)'),'laptop')">
        <div class="banner-tag">HOT</div>
        <div class="banner-icon">💻</div>
        <div class="banner-title">MacBook Pro M4</div>
        <div class="banner-desc">Từ 32.990.000₫<br>Hàng chính hãng Apple</div>
      </div>
      <div class="hero-banner green" onclick="openProduct(4)">
        <div class="banner-tag">NEW</div>
        <div class="banner-icon">⌚</div>
        <div class="banner-title">Samsung Watch 7</div>
        <div class="banner-desc">Theo dõi sức khỏe 24/7</div>
      </div>
      <div class="hero-banner orange" onclick="openProduct(3)">
        <div class="banner-icon">🎮</div>
        <div class="banner-title">Gaming Handheld</div>
        <div class="banner-desc">PlayStation Portable 2025</div>
      </div>
    </div>
  </div>

  <!-- FEATURES -->
  <div class="features-row fade-in fade-in-1">
    <div class="feature-card">
      <div class="feature-icon">🚚</div>
      <div class="feature-title">Giao hàng nhanh</div>
      <div class="feature-desc">2h nội thành, miễn phí đơn từ 500k</div>
    </div>
    <div class="feature-card">
      <div class="feature-icon">🔒</div>
      <div class="feature-title">Bảo hành chính hãng</div>
      <div class="feature-desc">12-24 tháng, bảo hành tận nhà</div>
    </div>
    <div class="feature-card">
      <div class="feature-icon">↩️</div>
      <div class="feature-title">Đổi trả 15 ngày</div>
      <div class="feature-desc">Hoàn tiền 100% nếu lỗi sản phẩm</div>
    </div>
    <div class="feature-card">
      <div class="feature-icon">💳</div>
      <div class="feature-title">Trả góp 0%</div>
      <div class="feature-desc">12 tháng, duyệt trong 30 phút</div>
    </div>
  </div>

  <!-- CATEGORIES -->
  <div class="section fade-in fade-in-2">
    <div class="section-header">
      <div class="section-title">
        <div class="title-accent"></div>
        <h2>Danh mục thiết bị</h2>
      </div>
      <a href="#" class="see-all">Xem tất cả →</a>
    </div>
    <div class="categories-grid">
      <div class="cat-card" onclick="setNavByName('phone')">
        <span class="cat-icon">📱</span>
        <div class="cat-name">Điện thoại thông minh</div>
        <div class="cat-count">1.240 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('laptop')">
        <span class="cat-icon">💻</span>
        <div class="cat-name">Máy tính xách tay</div>
        <div class="cat-count">890 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('tablet')">
        <span class="cat-icon">📟</span>
        <div class="cat-name">Máy tính bảng</div>
        <div class="cat-count">456 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('watch')">
        <span class="cat-icon">⌚</span>
        <div class="cat-name">Đồng hồ thông minh</div>
        <div class="cat-count">320 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('camera')">
        <span class="cat-icon">📷</span>
        <div class="cat-name">Máy ảnh số (DSC)</div>
        <div class="cat-count">215 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('camera')">
        <span class="cat-icon">🎥</span>
        <div class="cat-name">Máy quay kỹ thuật số</div>
        <div class="cat-count">180 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('wearable')">
        <span class="cat-icon">🥽</span>
        <div class="cat-name">Màn hình gắn đầu (HMD)</div>
        <div class="cat-count">48 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('portable')">
        <span class="cat-icon">🎮</span>
        <div class="cat-name">Máy chơi game cầm tay</div>
        <div class="cat-count">156 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('audio')">
        <span class="cat-icon">🎵</span>
        <div class="cat-name">Máy nghe nhạc kỹ thuật số</div>
        <div class="cat-count">92 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('portable')">
        <span class="cat-icon">🧮</span>
        <div class="cat-name">Máy tính bỏ túi / đồ thị</div>
        <div class="cat-count">64 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('portable')">
        <span class="cat-icon">📡</span>
        <div class="cat-name">Thiết bị Internet di động</div>
        <div class="cat-count">230 sản phẩm</div>
      </div>
      <div class="cat-card" onclick="setNavByName('imex')">
        <span class="cat-icon">🌐</span>
        <div class="cat-name">Hàng nhập khẩu (IMEX)</div>
        <div class="cat-count">3.400+ sản phẩm</div>
      </div>
    </div>
  </div>

  <!-- FLASH SALE -->
  <div class="section fade-in fade-in-3">
    <div class="flash-banner">
      <span class="flash-icon">⚡</span>
      <span class="flash-title">FLASH SALE</span>
      <span class="live-dot"></span>
      <span style="color:rgba(255,255,255,0.8);font-size:12px;margin-left:6px;">ĐANG DIỄN RA</span>
      <div class="countdown">
        <span class="countdown-label">Kết thúc sau:</span>
        <span class="time-block" id="h">05</span>
        <span class="time-sep">:</span>
        <span class="time-block" id="m">42</span>
        <span class="time-sep">:</span>
        <span class="time-block" id="s">18</span>
      </div>
    </div>
    <div style="background:white;border-radius:0 0 var(--radius-lg) var(--radius-lg);padding:16px;border:1px solid var(--gray-100);border-top:none;">
      <div class="products-scroll" id="flashProducts"></div>
    </div>
  </div>

  <!-- BRANDS -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">
        <div class="title-accent"></div>
        <h2>Thương hiệu hàng đầu</h2>
      </div>
    </div>
    <div class="brands-row">
      <div class="brand-card">🍎 Apple</div>
      <div class="brand-card">📱 Samsung</div>
      <div class="brand-card">🤖 Google</div>
      <div class="brand-card">💻 Dell</div>
      <div class="brand-card">🖥️ HP</div>
      <div class="brand-card">⚡ Asus</div>
      <div class="brand-card">🎮 Sony</div>
      <div class="brand-card">📷 Canon</div>
      <div class="brand-card">🎵 Bose</div>
      <div class="brand-card">💡 Xiaomi</div>
      <div class="brand-card">📡 Huawei</div>
      <div class="brand-card">🎯 Lenovo</div>
    </div>
  </div>

  <!-- PROMO BANNERS -->
  <div class="promo-grid">
    <div class="promo-card blue" onclick="showToast('🌐 Đang chuyển đến trang hàng nhập khẩu...')">
      <div class="promo-content">
        <div class="promo-tag">IMEX EXCLUSIVE</div>
        <div class="promo-title">Hàng Nhập Khẩu<br>Chính Hãng</div>
        <div class="promo-desc">Nguồn gốc rõ ràng, bảo hành quốc tế</div>
      </div>
      <div class="promo-bg-icon">🌐</div>
    </div>
    <div class="promo-card dark" onclick="showToast('💳 Chương trình trả góp 0% lãi suất')">
      <div class="promo-content">
        <div class="promo-tag">TÀI CHÍNH</div>
        <div class="promo-title">Trả Góp 0%<br>12 Tháng</div>
        <div class="promo-desc">Duyệt nhanh, không cần thế chấp</div>
      </div>
      <div class="promo-bg-icon">💳</div>
    </div>
    <div class="promo-card teal" onclick="showToast('🛡️ Bảo hành chính hãng toàn quốc')">
      <div class="promo-content">
        <div class="promo-tag">BẢO HÀNH</div>
        <div class="promo-title">Bảo Hành<br>Chính Hãng 2 Năm</div>
        <div class="promo-desc">Sửa chữa tận nơi, đổi máy mới</div>
      </div>
      <div class="promo-bg-icon">🛡️</div>
    </div>
  </div>

  <!-- VOUCHERS -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">
        <div class="title-accent"></div>
        <h2>🎫 Mã giảm giá hôm nay</h2>
      </div>
    </div>
    <div class="voucher-row" id="voucherRow"></div>
  </div>

  <!-- FILTER + ALL PRODUCTS -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">
        <div class="title-accent"></div>
        <h2>Tất cả sản phẩm</h2>
      </div>
      <a href="#" class="see-all">Xem tất cả →</a>
    </div>
    <div class="filter-bar">
      <span class="filter-label">Sắp xếp:</span>
      <span class="filter-chip active" onclick="setFilter(this)">Phổ biến</span>
      <span class="filter-chip" onclick="setFilter(this)">Mới nhất</span>
      <span class="filter-chip" onclick="setFilter(this)">Bán chạy</span>
      <span class="filter-chip" onclick="setFilter(this)">Giá thấp</span>
      <span class="filter-chip" onclick="setFilter(this)">Đánh giá cao</span>
      <div class="filter-divider"></div>
      <span class="filter-label">Thương hiệu:</span>
      <select class="filter-select"><option>Tất cả</option><option>Apple</option><option>Samsung</option><option>Sony</option></select>
      <span class="filter-label">Giá:</span>
      <select class="filter-select"><option>Tất cả</option><option>Dưới 5 triệu</option><option>5-15 triệu</option><option>Trên 15 triệu</option></select>
      <span class="filter-label">Nguồn:</span>
      <span class="filter-chip" onclick="setFilter(this)">🌐 Hàng nhập</span>
      <span class="filter-chip" onclick="setFilter(this)">🏪 Nội địa</span>
    </div>
    <div class="products-grid" id="allProducts"></div>
  </div>

  <!-- SHOPS -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">
        <div class="title-accent"></div>
        <h2>🏪 Shop nổi bật</h2>
      </div>
      <a href="#" class="see-all">Xem tất cả shop →</a>
    </div>
    <div class="shops-grid" id="shopsGrid"></div>
  </div>

  <!-- REVIEWS -->
  <div class="section">
    <div class="section-header">
      <div class="section-title">
        <div class="title-accent"></div>
        <h2>⭐ Đánh giá từ khách hàng</h2>
      </div>
    </div>
    <div class="reviews-grid" id="reviewsGrid"></div>
  </div>

</div><!-- /main-layout -->

<!-- FOOTER -->
<footer>
  <div class="footer-top">
    <div class="footer-brand">
      <div class="logo-text">IM<span style="color:#00c6ff">EX</span></div>
      <p class="footer-desc">Nền tảng thương mại điện tử chuyên biệt cho thiết bị điện tử. Trung gian tin cậy giữa người tiêu dùng và các shop uy tín.</p>
      <div class="footer-socials">
        <a class="social-btn" href="#">f</a>
        <a class="social-btn" href="#">in</a>
        <a class="social-btn" href="#">yt</a>
        <a class="social-btn" href="#">tk</a>
        <a class="social-btn" href="#">ig</a>
      </div>
    </div>
    <div class="footer-col">
      <h4>Về IMEX</h4>
      <a href="#">Giới thiệu</a>
      <a href="#">Tuyển dụng</a>
      <a href="#">Chính sách bảo mật</a>
      <a href="#">Điều khoản dịch vụ</a>
      <a href="#">Quy chế hoạt động</a>
    </div>
    <div class="footer-col">
      <h4>Hỗ trợ</h4>
      <a href="#">Trung tâm hỗ trợ</a>
      <a href="#">Hướng dẫn mua hàng</a>
      <a href="#">Hướng dẫn thanh toán</a>
      <a href="#">Hướng dẫn hoàn trả</a>
      <a href="#">Liên hệ IMEX</a>
    </div>
    <div class="footer-col">
      <h4>Dành cho Shop</h4>
      <a href="#">Đăng ký bán hàng</a>
      <a href="#">Trung tâm shop</a>
      <a href="#">Chính sách shop</a>
      <a href="#">Quảng cáo IMEX</a>
      <a href="#">API tích hợp</a>
    </div>
    <div class="footer-col">
      <h4>Thanh toán</h4>
      <a href="#">IMEX Pay</a>
      <a href="#">Ví điện tử</a>
      <a href="#">Trả góp</a>
      <a href="#">COD</a>
      <a href="#">Banking</a>
    </div>
  </div>
  <div style="max-width:1280px;margin:0 auto;padding:0 20px;">
    <div style="border-top:1px solid rgba(255,255,255,0.08);padding:16px 0;display:flex;align-items:center;justify-content:space-between;">
      <span style="font-size:12px;">© 2025 IMEX Electronics. Bảo lưu mọi quyền.</span>
      <div class="payment-icons">
        <span class="payment-icon">VISA</span>
        <span class="payment-icon">MC</span>
        <span class="payment-icon">MOMO</span>
        <span class="payment-icon">VNPAY</span>
        <span class="payment-icon">ZP</span>
        <span class="payment-icon">COD</span>
      </div>
    </div>
  </div>
</footer>

<!-- PRODUCT MODAL -->
<div class="modal-overlay" id="productModal" onclick="closeModalOutside(event)">
  <div class="modal">
    <div class="modal-header">
      <span class="modal-title">Chi tiết sản phẩm</span>
      <button class="modal-close" onclick="closeModal('productModal')">✕</button>
    </div>
    <div class="modal-body">
      <div class="product-detail-grid" id="productDetailContent"></div>
      <div style="margin-top:20px;">
        <div class="tabs">
          <div class="tab active" onclick="setTab(this,'desc')">Mô tả</div>
          <div class="tab" onclick="setTab(this,'spec')">Thông số kỹ thuật</div>
          <div class="tab" onclick="setTab(this,'review')">Đánh giá (128)</div>
          <div class="tab" onclick="setTab(this,'policy')">Chính sách</div>
        </div>
        <div id="tabContent" style="font-size:13px;color:#475569;line-height:1.7;"></div>
      </div>
    </div>
  </div>
</div>

<!-- CART SIDEBAR -->
<div class="cart-overlay" id="cartOverlay">
  <div class="cart-bg" onclick="toggleCart()"></div>
  <div class="cart-panel">
    <div class="cart-header">
      <span class="cart-header-title">🛒 Giỏ hàng của bạn</span>
      <button class="cart-close" onclick="toggleCart()">✕</button>
    </div>
    <div class="cart-items" id="cartItems"></div>
    <div class="cart-footer">
      <div class="cart-total">
        <span class="cart-total-label">Tổng cộng</span>
        <span class="cart-total-amount" id="cartTotal">0 ₫</span>
      </div>
      <button class="checkout-btn" onclick="showToast('🚀 Đang chuyển đến trang thanh toán...')">Thanh toán ngay →</button>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<!-- BACK TO TOP -->
<button class="back-to-top" id="backTop" onclick="scrollToTop()">↑</button>

<script>
// ====== DATA ======
const products = [
  { id:0, name:'iPhone 16 Pro Max 256GB Titan Đen', price:29990000, oldPrice:34990000, rating:4.9, sold:2840, shop:'Apple Store VN', emoji:'📱', tags:['sale','hot'], progress:72, desc:'Chip A18 Pro, Camera 48MP Fusion, Màn hình Super Retina XDR 6.9", Titanium', brand:'Apple', cat:'phone', specs:{OS:'iOS 18',RAM:'8GB',Storage:'256GB',Display:'6.9" OLED',Battery:'4685mAh',Camera:'48+12+12MP'} },
  { id:1, name:'Samsung Galaxy S25 Ultra 512GB Shadow Blue', price:31990000, oldPrice:37990000, rating:4.8, sold:1920, shop:'Samsung Official', emoji:'📱', tags:['new','official'], progress:55, desc:'Snapdragon 8 Elite, S Pen tích hợp, Camera 200MP, AI Galaxy', brand:'Samsung', cat:'phone', specs:{OS:'Android 15',RAM:'12GB',Storage:'512GB',Display:'6.9" QHD+',Battery:'5000mAh',Camera:'200+50+10MP'} },
  { id:2, name:'MacBook Pro 16" M4 Pro 24GB 512GB', price:62990000, oldPrice:72990000, rating:4.9, sold:680, shop:'Apple Premium Reseller', emoji:'💻', tags:['hot','import'], progress:38, desc:'Chip M4 Pro 14-core CPU, 20-core GPU, màn hình Liquid Retina XDR', brand:'Apple', cat:'laptop', specs:{OS:'macOS 15',RAM:'24GB',Storage:'512GB SSD',Display:'16.2" Liquid Retina XDR',Battery:'22h',CPU:'Apple M4 Pro'} },
  { id:3, name:'PlayStation Portable 2 (PSP 2025)', price:8990000, oldPrice:10990000, rating:4.7, sold:450, shop:'Sony Gaming VN', emoji:'🎮', tags:['new','import'], progress:63, desc:'OLED 5.5", PS Store, Remote Play, DualSense Haptic', brand:'Sony', cat:'portable', specs:{OS:'Custom OS',RAM:'4GB',Storage:'1TB',Display:'5.5" OLED',Battery:'8h',CPU:'Custom ARM'} },
  { id:4, name:'Samsung Galaxy Watch 7 Pro 47mm', price:9490000, oldPrice:12490000, rating:4.8, sold:1230, shop:'Samsung Official', emoji:'⌚', tags:['sale'], progress:81, desc:'Titanium, theo dõi sức khỏe 24/7, GPS, ECG, pin 3 ngày', brand:'Samsung', cat:'watch', specs:{OS:'Wear OS 5',RAM:'2GB',Storage:'32GB',Display:'1.5" AMOLED',Battery:'60h',Sensor:'ECG,BPM,GPS'} },
  { id:5, name:'iPad Pro 13" M4 Wi-Fi 256GB Silver', price:32990000, oldPrice:38990000, rating:4.9, sold:890, shop:'Apple Store VN', emoji:'📟', tags:['new','hot'], progress:44, desc:'Chip M4, màn hình Ultra Retina XDR OLED, Apple Pencil Pro', brand:'Apple', cat:'tablet', specs:{OS:'iPadOS 18',RAM:'8GB',Storage:'256GB',Display:'13" OLED Ultra Retina',Battery:'10h',CPU:'Apple M4'} },
  { id:6, name:'Sony A7C II Full-Frame Mirrorless', price:52990000, oldPrice:58990000, rating:4.9, sold:320, shop:'Sony Pro VN', emoji:'📷', tags:['import','hot'], progress:29, desc:'61MP sensor, AI autofocus, 4K 120fps, thân gọn nhẹ', brand:'Sony', cat:'camera', specs:{Megapixel:'61MP',Sensor:'Full-Frame BSI CMOS',Video:'4K 120fps',AF:'AI Tracking',Battery:'530 shots',Mount:'Sony E-Mount'} },
  { id:7, name:'Apple Watch Ultra 2 Titanium 49mm', price:22990000, oldPrice:26990000, rating:4.9, sold:780, shop:'Apple Premium Reseller', emoji:'⌚', tags:['import'], progress:51, desc:'Titanium, GPS L5, Pin 36h, Action Button, MicroLED', brand:'Apple', cat:'watch', specs:{OS:'watchOS 11',RAM:'1GB',Storage:'64GB',Display:'2.1" MicroLED',Battery:'36h',GPS:'Dual L1/L5'} },
  { id:8, name:'Dell XPS 15 OLED Intel Core Ultra 9', price:48990000, oldPrice:55990000, rating:4.7, sold:290, shop:'Dell Official VN', emoji:'💻', tags:['sale','import'], progress:35, desc:'Core Ultra 9, RTX 4070, màn hình OLED 15.6" 3.5K 120Hz', brand:'Dell', cat:'laptop', specs:{OS:'Windows 11',RAM:'32GB',Storage:'1TB SSD',Display:'15.6" OLED 3.5K',Battery:'86Wh',GPU:'RTX 4070'} },
  { id:9, name:'Sony WH-1000XM6 Chống Ồn Cao Cấp', price:8490000, oldPrice:9990000, rating:4.8, sold:2100, shop:'Sony Audio VN', emoji:'🎧', tags:['sale','new'], progress:88, desc:'ANC 40dB, Hi-Res Audio, pin 30h, kết nối đa thiết bị', brand:'Sony', cat:'audio', specs:{Driver:'40mm',ANC:'Class Leading',Battery:'30h',Bluetooth:'5.3',Codec:'LDAC,aptX HD',Weight:'250g'} },
  { id:10, name:'Meta Quest 3 512GB Mixed Reality', price:15990000, oldPrice:18990000, rating:4.7, sold:560, shop:'Meta Store VN', emoji:'🥽', tags:['new','import'], progress:42, desc:'Mixed Reality, Snapdragon XR2 Gen 2, 40PPD display, Touch Plus', brand:'Meta', cat:'wearable', specs:{Display:'2.56K per eye',CPU:'Snapdragon XR2 Gen 2',RAM:'8GB',Storage:'512GB',Battery:'2h',Tracking:'Inside-out 6DOF'} },
  { id:11, name:'Xiaomi 14 Ultra Leica Camera Edition', price:24990000, oldPrice:28990000, rating:4.8, sold:1450, shop:'Xiaomi Official', emoji:'📱', tags:['sale','hot'], progress:67, desc:'Leica Summilux camera, Snapdragon 8 Gen 3, Ceramic Nano', brand:'Xiaomi', cat:'phone', specs:{OS:'HyperOS',RAM:'16GB',Storage:'512GB',Display:'6.73" AMOLED 120Hz',Battery:'5000mAh',Camera:'Leica 50MP x4'} },
];

const cartItems = [
  { ...products[0], qty: 1 },
  { ...products[4], qty: 2 },
  { ...products[9], qty: 1 },
];

const shops = [
  { name:'Apple Premium Store', emoji:'🍎', badge:'Apple Authorized Reseller', followers:'128K', rating:'4.9', products:[products[0],products[2],products[5]], chat:'98%' },
  { name:'Samsung Official VN', emoji:'📱', badge:'Official Brand Store', followers:'256K', rating:'4.9', products:[products[1],products[4],products[11]], chat:'99%' },
  { name:'Sony Electronics VN', emoji:'🎯', badge:'Official Brand Store', followers:'89K', rating:'4.8', products:[products[6],products[9],products[3]], chat:'97%' },
];

const vouchers = [
  { discount:'200K', condition:'Đơn tối thiểu 5 triệu', expiry:'Hết hạn: 30/04/2025', code:'IMEX200' },
  { discount:'15%', condition:'Đơn hàng laptop', expiry:'Hết hạn: 31/05/2025', code:'IMEX15' },
  { discount:'500K', condition:'Đơn tối thiểu 20 triệu', expiry:'Hết hạn: 15/05/2025', code:'IMEX500' },
  { discount:'Freeship', condition:'Miễn phí vận chuyển toàn quốc', expiry:'Hết hạn: 30/06/2025', code:'FREESHIP' },
];

const reviews = [
  { name:'Nguyễn Văn A', avatar:'NVA', stars:5, date:'12/04/2025', text:'Sản phẩm đúng như mô tả, đóng gói cẩn thận, ship nhanh. iPhone 16 Pro Max mình mua chính hãng, hoạt động tốt. Rất hài lòng!', product:'iPhone 16 Pro Max', emoji:'📱' },
  { name:'Trần Thị B', avatar:'TTB', stars:5, date:'10/04/2025', text:'MacBook M4 Pro siêu mượt, pin trâu không tưởng. Shop giao hàng đúng hẹn, có hóa đơn VAT đầy đủ. Sẽ ủng hộ tiếp.', product:'MacBook Pro M4', emoji:'💻' },
  { name:'Lê Minh C', avatar:'LMC', stars:4, date:'08/04/2025', text:'Galaxy Watch 7 Pro theo dõi sức khỏe chính xác. Thiết kế đẹp, tuy nhiên ứng dụng còn hơi lag. Nhìn chung rất đáng tiền.', product:'Samsung Galaxy Watch 7', emoji:'⌚' },
];

// ====== RENDER FUNCTIONS ======
function formatPrice(p) {
  return p.toLocaleString('vi-VN') + ' ₫';
}

function renderTagsHTML(tags) {
  return tags.map(t => {
    if(t==='sale') return '<span class="tag tag-sale">-SALE</span>';
    if(t==='new') return '<span class="tag tag-new">MỚI</span>';
    if(t==='hot') return '<span class="tag tag-hot">🔥 HOT</span>';
    if(t==='official') return '<span class="tag tag-official">CHÍNH HÃNG</span>';
    if(t==='import') return '<span class="tag tag-import">NHẬP KHẨU</span>';
    return '';
  }).join('');
}

function renderProductCard(p, showProgress=false) {
  const disc = Math.round((1 - p.price/p.oldPrice)*100);
  return `
    <div class="product-card" onclick="openProduct(${p.id})">
      <div class="product-img">
        <div class="product-img-bg"></div>
        <div class="emoji">${p.emoji}</div>
        <div class="product-tags">${renderTagsHTML(p.tags)}</div>
        <button class="product-wishlist" onclick="event.stopPropagation();toggleWish(this)">🤍</button>
      </div>
      <div class="product-info">
        <div class="product-shop">${p.shop} <span class="shop-verified">✓</span></div>
        <div class="product-name">${p.name}</div>
        <div class="product-price-row">
          <span class="price-new">${formatPrice(p.price)}</span>
          <span class="price-old">${formatPrice(p.oldPrice)}</span>
          <span class="price-discount">-${disc}%</span>
        </div>
        <div class="product-meta">
          <div class="rating">⭐ ${p.rating} <span>(${p.sold > 999 ? (p.sold/1000).toFixed(1)+'k' : p.sold})</span></div>
          <span class="sold-count">Đã bán ${p.sold > 999 ? (p.sold/1000).toFixed(1)+'k' : p.sold}</span>
        </div>
        ${showProgress ? `
          <div class="product-progress">
            <div class="product-progress-bar" style="width:${p.progress}%"></div>
          </div>
          <div class="progress-label">🔥 Còn ${100-p.progress}% sản phẩm</div>
        ` : ''}
        <button class="add-cart-btn" onclick="event.stopPropagation();addToCart(${p.id})">🛒 Thêm vào giỏ</button>
      </div>
    </div>
  `;
}

function renderFlash() {
  const container = document.getElementById('flashProducts');
  container.innerHTML = products.slice(0,8).map(p => {
    const disc = Math.round((1 - p.price/p.oldPrice)*100);
    return `
      <div class="product-card" onclick="openProduct(${p.id})">
        <div class="product-img">
          <div class="product-img-bg"></div>
          <div class="emoji">${p.emoji}</div>
          <div class="product-tags">${renderTagsHTML(p.tags)}</div>
          <button class="product-wishlist" onclick="event.stopPropagation();toggleWish(this)">🤍</button>
        </div>
        <div class="product-info">
          <div class="product-name">${p.name}</div>
          <div class="product-price-row">
            <span class="price-new">${formatPrice(p.price)}</span>
            <span class="price-discount">-${disc}%</span>
          </div>
          <div class="product-progress">
            <div class="product-progress-bar" style="width:${p.progress}%"></div>
          </div>
          <div class="progress-label">🔥 Còn ${100-p.progress}%</div>
        </div>
      </div>
    `;
  }).join('');
}

function renderAll() {
  document.getElementById('allProducts').innerHTML = products.map(p => renderProductCard(p, false)).join('');
}

function renderShops() {
  document.getElementById('shopsGrid').innerHTML = shops.map(s => `
    <div class="shop-card">
      <div class="shop-header">
        <div class="shop-avatar">${s.emoji}</div>
        <div>
          <div class="shop-name">${s.name}</div>
          <span class="shop-badge">✓ ${s.badge}</span>
        </div>
      </div>
      <div class="shop-stats">
        <div class="shop-stat"><strong>${s.followers}</strong> Followers</div>
        <div class="shop-stat"><strong>⭐ ${s.rating}</strong> Đánh giá</div>
        <div class="shop-stat"><strong>${s.chat}</strong> Chat</div>
      </div>
      <div class="shop-products">
        ${s.products.map(p => `<div class="shop-product-thumb">${p.emoji}</div>`).join('')}
        <div class="shop-product-thumb" style="font-size:12px;color:var(--gray-400);">+99</div>
      </div>
      <button class="follow-btn" onclick="showToast('✅ Đã theo dõi shop ${s.name}')">+ Theo dõi shop</button>
    </div>
  `).join('');
}

function renderReviews() {
  document.getElementById('reviewsGrid').innerHTML = reviews.map(r => `
    <div class="review-card">
      <div class="review-header">
        <div class="reviewer-avatar">${r.avatar}</div>
        <div>
          <div class="reviewer-name">${r.name}</div>
          <div class="reviewer-date">${r.date}</div>
        </div>
      </div>
      <div class="review-stars">${'⭐'.repeat(r.stars)}</div>
      <div class="review-text">${r.text}</div>
      <div class="review-product">📦 ${r.product}</div>
      <div class="review-images">
        <div class="review-img">${r.emoji}</div>
        <div class="review-img">📦</div>
      </div>
    </div>
  `).join('');
}

function renderVouchers() {
  const collected = new Set();
  document.getElementById('voucherRow').innerHTML = vouchers.map((v,i) => `
    <div class="voucher-card">
      <div>
        <div class="voucher-discount">${v.discount}</div>
        <div class="voucher-label">IMEX Voucher</div>
      </div>
      <div>
        <div class="voucher-condition">${v.condition}</div>
        <div class="voucher-expiry">${v.expiry}</div>
      </div>
      <button class="collect-btn" id="vbtn${i}" onclick="collectVoucher(${i},'${v.code}')">Lấy mã</button>
    </div>
  `).join('');
}

function collectVoucher(i, code) {
  const btn = document.getElementById('vbtn'+i);
  btn.textContent = '✓ Đã lưu';
  btn.classList.add('collected');
  btn.disabled = true;
  showToast(`🎫 Đã lưu mã ${code} vào tài khoản!`);
}

function renderCart() {
  document.getElementById('cartItems').innerHTML = cartItems.map((item,i) => `
    <div class="cart-item">
      <div class="cart-item-img">${item.emoji}</div>
      <div class="cart-item-info">
        <div class="cart-item-name">${item.name.length>40?item.name.substring(0,40)+'...':item.name}</div>
        <div style="display:flex;align-items:center;gap:10px;margin-top:6px;">
          <button onclick="changeQty(${i},-1)" style="width:22px;height:22px;border-radius:50%;border:1px solid var(--gray-200);background:white;cursor:pointer;font-size:14px;">-</button>
          <span style="font-size:13px;font-weight:700;">${item.qty}</span>
          <button onclick="changeQty(${i},1)" style="width:22px;height:22px;border-radius:50%;border:1px solid var(--gray-200);background:white;cursor:pointer;font-size:14px;">+</button>
        </div>
        <div class="cart-item-price">${formatPrice(item.price * item.qty)}</div>
      </div>
      <span class="cart-item-remove" onclick="removeFromCart(${i})">🗑</span>
    </div>
  `).join('') || '<div style="text-align:center;padding:40px;color:var(--gray-400);">🛒 Giỏ hàng trống</div>';
  const total = cartItems.reduce((s,i) => s + i.price*i.qty, 0);
  document.getElementById('cartTotal').textContent = formatPrice(total);
  document.getElementById('cartBadge').textContent = cartItems.reduce((s,i) => s + i.qty, 0);
}

// ====== ACTIONS ======
function addToCart(id) {
  const p = products[id];
  const existing = cartItems.find(i => i.id === id);
  if(existing) { existing.qty++; }
  else { cartItems.push({...p, qty:1}); }
  renderCart();
  showToast('🛒 Đã thêm vào giỏ hàng!');
}

function removeFromCart(i) {
  cartItems.splice(i,1);
  renderCart();
}

function changeQty(i, delta) {
  cartItems[i].qty = Math.max(1, cartItems[i].qty + delta);
  renderCart();
}

function toggleCart() {
  document.getElementById('cartOverlay').classList.toggle('open');
}

function toggleWish(btn) {
  btn.textContent = btn.textContent === '🤍' ? '❤️' : '🤍';
  if(btn.textContent === '❤️') showToast('❤️ Đã thêm vào danh sách yêu thích!');
}

function openProduct(id) {
  const p = products[id];
  const disc = Math.round((1-p.price/p.oldPrice)*100);
  document.getElementById('productDetailContent').innerHTML = `
    <div class="product-detail-images">
      <div class="product-main-img">${p.emoji}</div>
      <div class="product-thumb-row">
        <div class="product-thumb active">${p.emoji}</div>
        <div class="product-thumb">📦</div>
        <div class="product-thumb">🔌</div>
        <div class="product-thumb">📋</div>
      </div>
    </div>
    <div>
      <div style="margin-bottom:8px;">
        ${renderTagsHTML(p.tags)}
      </div>
      <div class="detail-name">${p.name}</div>
      <div class="detail-rating">
        <span class="stars">⭐⭐⭐⭐⭐</span>
        <span>${p.rating}/5</span>
        <span style="color:var(--gray-300);">|</span>
        <span>${p.sold.toLocaleString()} đã bán</span>
        <span style="color:var(--gray-300);">|</span>
        <span style="color:var(--accent);">128 đánh giá</span>
      </div>
      <div class="detail-price">${formatPrice(p.price)}</div>
      <div style="display:flex;align-items:center;gap:10px;margin-bottom:16px;">
        <div class="detail-old-price" style="margin:0;">${formatPrice(p.oldPrice)}</div>
        <span style="background:#ffebee;color:#e53935;font-size:12px;font-weight:800;padding:2px 8px;border-radius:4px;">-${disc}%</span>
      </div>
      <div class="detail-specs">
        ${Object.entries(p.specs).map(([k,v]) => `
          <div class="spec-row">
            <span class="spec-key">${k}</span>
            <span class="spec-val">${v}</span>
          </div>
        `).join('')}
      </div>
      <div class="quantity-row">
        <span class="qty-label">Số lượng:</span>
        <div class="qty-control">
          <button class="qty-btn" onclick="this.nextElementSibling.value=Math.max(1,+this.nextElementSibling.value-1)">-</button>
          <input class="qty-input" type="number" value="1" min="1" id="qtyInput">
          <button class="qty-btn" onclick="this.previousElementSibling.value=+this.previousElementSibling.value+1">+</button>
        </div>
        <span style="font-size:12px;color:var(--gray-400);">Kho: 999 sản phẩm</span>
      </div>
      <div class="btn-row">
        <button class="btn-cart" onclick="addToCart(${p.id});showToast('🛒 Đã thêm vào giỏ!')">🛒 Thêm vào giỏ</button>
        <button class="btn-buy" onclick="showToast('🚀 Đang chuyển đến thanh toán...')">Mua ngay</button>
      </div>
      <div style="margin-top:12px;font-size:12px;color:var(--gray-400);">
        🚚 Giao hàng nhanh 2h nội thành &nbsp; 🛡️ Bảo hành ${p.cat==='phone'||p.cat==='laptop'?'12 tháng':'6 tháng'} &nbsp; ↩️ Đổi trả 15 ngày
      </div>
    </div>
  `;
  setTab(document.querySelector('#productModal .tab'), 'desc', p);
  document.getElementById('productModal').classList.add('open');
}

function setTab(el, tab, p) {
  document.querySelectorAll('#productModal .tab').forEach(t => t.classList.remove('active'));
  if(el) el.classList.add('active');
  const content = {
    desc: `<p>${products.find(x=>x.id===0)?.desc || 'Sản phẩm chất lượng cao, được nhập khẩu chính hãng. Đầy đủ chứng từ, hóa đơn VAT.'}</p><br><p>✅ Hàng chính hãng, có tem IMEX<br>✅ Kèm đầy đủ phụ kiện trong hộp<br>✅ Bảo hành tại trung tâm ủy quyền<br>✅ Hỗ trợ trả góp 0%</p>`,
    spec: `<table style="width:100%;font-size:13px;"><tr><th style="text-align:left;padding:8px;background:var(--gray-50);">Thông số</th><th style="text-align:left;padding:8px;background:var(--gray-50);">Chi tiết</th></tr><tr><td style="padding:8px;">Xuất xứ</td><td style="padding:8px;">Nhập khẩu chính hãng</td></tr><tr><td style="padding:8px;">Bảo hành</td><td style="padding:8px;">12 tháng</td></tr><tr><td style="padding:8px;">Màu sắc</td><td style="padding:8px;">Nhiều màu</td></tr></table>`,
    review: `<div style="display:flex;gap:20px;"><div style="text-align:center;"><div style="font-size:48px;font-weight:900;color:var(--gold);">4.9</div><div>⭐⭐⭐⭐⭐</div><div style="font-size:12px;color:var(--gray-400);">128 đánh giá</div></div><div style="flex:1;"><div style="display:flex;gap:8px;align-items:center;margin-bottom:6px;"><span style="font-size:12px;width:40px;">5 ⭐</span><div style="flex:1;background:var(--gray-100);border-radius:4px;height:8px;"><div style="background:var(--gold);width:85%;height:100%;border-radius:4px;"></div></div><span style="font-size:12px;">85%</span></div><div style="display:flex;gap:8px;align-items:center;margin-bottom:6px;"><span style="font-size:12px;width:40px;">4 ⭐</span><div style="flex:1;background:var(--gray-100);border-radius:4px;height:8px;"><div style="background:var(--gold);width:10%;height:100%;border-radius:4px;"></div></div><span style="font-size:12px;">10%</span></div></div></div>`,
    policy: `<p>🛡️ <strong>Bảo hành:</strong> 12 tháng tại trung tâm bảo hành ủy quyền<br><br>↩️ <strong>Đổi trả:</strong> 15 ngày nếu lỗi từ nhà sản xuất, đổi máy mới trong 7 ngày<br><br>🚚 <strong>Vận chuyển:</strong> Giao nhanh 2h nội thành, 1-3 ngày toàn quốc<br><br>💳 <strong>Thanh toán:</strong> COD, chuyển khoản, MOMO, VNPAY, trả góp 0%</p>`,
  };
  document.getElementById('tabContent').innerHTML = content[tab] || content.desc;
}

function closeModal(id) { document.getElementById(id).classList.remove('open'); }
function closeModalOutside(e) { if(e.target.classList.contains('modal-overlay')) closeModal('productModal'); }

let toastTimer;
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(toastTimer);
  toastTimer = setTimeout(() => t.classList.remove('show'), 3000);
}

function setNav(el, page) {
  document.querySelectorAll('.nav-item').forEach(n => n.classList.remove('active'));
  if(el) el.classList.add('active');
  showToast('📂 Đang tải danh mục: ' + (el?.textContent.trim() || page));
}
function setNavByName(page) {
  const items = document.querySelectorAll('.nav-item');
  items.forEach(i => i.classList.remove('active'));
  showToast('📂 Đang tải danh mục...');
}

function setFilter(el) {
  document.querySelectorAll('.filter-chip').forEach(c => c.classList.remove('active'));
  el.classList.add('active');
}

function showSuggestions(v) {
  const s = document.getElementById('suggestions');
  s.classList.toggle('show', v.length > 0);
}
function hideSuggestions() {
  setTimeout(() => document.getElementById('suggestions').classList.remove('show'), 200);
}
function doSearch() {
  const v = document.getElementById('searchInput').value;
  if(v) showToast('🔍 Đang tìm kiếm: ' + v);
}

function showPage(page) { showToast('📄 Đang chuyển đến trang: ' + page); }

function scrollToTop() { window.scrollTo({top:0,behavior:'smooth'}); }
window.addEventListener('scroll', () => {
  document.getElementById('backTop').classList.toggle('show', window.scrollY > 400);
});

// ====== COUNTDOWN ======
function startCountdown() {
  let end = new Date().getTime() + 5*3600000 + 42*60000 + 18000;
  const tick = () => {
    const now = new Date().getTime();
    const diff = Math.max(0, end - now);
    const h = Math.floor(diff/3600000);
    const m = Math.floor((diff%3600000)/60000);
    const s = Math.floor((diff%60000)/1000);
    document.getElementById('h').textContent = String(h).padStart(2,'0');
    document.getElementById('m').textContent = String(m).padStart(2,'0');
    document.getElementById('s').textContent = String(s).padStart(2,'0');
    if(diff > 0) setTimeout(tick, 1000);
  };
  tick();
}

// ====== INIT ======
renderFlash();
renderAll();
renderShops();
renderReviews();
renderVouchers();
renderCart();
startCountdown();
</script>
</body>
</html>
