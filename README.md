<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEX - Nền Tảng Thiết Bị Điện Tử Hàng Đầu</title>
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
            --radius: 12px;
            --shadow-sm: 0 1px 3px rgba(10,37,64,0.08);
            --shadow-md: 0 4px 16px rgba(10,37,64,0.12);
            --shadow-lg: 0 8px 32px rgba(10,37,64,0.16);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Nunito', sans-serif;
            background: var(--gray-50);
            color: var(--gray-800);
            line-height: 1.6;
        }

        /* ==================== SCROLLBAR ==================== */
        ::-webkit-scrollbar { width: 6px; height: 6px; }
        ::-webkit-scrollbar-track { background: var(--gray-100); }
        ::-webkit-scrollbar-thumb { background: var(--accent); border-radius: 3px; }

        /* ==================== HEADER & TOPBAR ==================== */
        .topbar {
            background: var(--primary-dark);
            color: rgba(255,255,255,0.8);
            font-size: 12.5px;
            padding: 7px 0;
        }
        .topbar-inner {
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        header {
            background: var(--primary);
            position: sticky;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 20px rgba(0,0,0,0.25);
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
            color: white;
        }
        .logo-icon {
            width: 42px;
            height: 42px;
            background: linear-gradient(135deg, var(--accent-bright), #00c6ff);
            border-radius: 10px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-family: 'Space Mono', monospace;
            font-weight: 700;
            font-size: 14px;
            color: white;
        }
        .logo-text {
            font-size: 24px;
            font-weight: 900;
            letter-spacing: -0.6px;
        }
        .logo-text span { color: #00c6ff; }

        .search-bar {
            flex: 1;
            max-width: 620px;
            display: flex;
            position: relative;
        }
        .search-bar input {
            flex: 1;
            padding: 12px 16px;
            border: none;
            border-radius: 8px 0 0 8px;
            font-size: 15px;
            outline: none;
        }
        .search-bar select {
            padding: 12px 14px;
            border: none;
            background: white;
            border-left: 1px solid var(--gray-200);
            font-size: 14px;
            color: var(--gray-600);
        }
        .search-btn {
            padding: 0 24px;
            background: var(--accent-bright);
            color: white;
            border: none;
            border-radius: 0 8px 8px 0;
            cursor: pointer;
            font-size: 18px;
        }

        .header-actions {
            display: flex;
            gap: 8px;
        }
        .header-btn {
            display: flex;
            flex-direction: column;
            align-items: center;
            padding: 8px 12px;
            color: white;
            background: transparent;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.2s;
            position: relative;
        }
        .header-btn:hover { background: rgba(255,255,255,0.1); }
        .header-btn .icon { font-size: 21px; }
        .header-btn .label { font-size: 11px; margin-top: 2px; }
        .badge {
            position: absolute;
            top: 3px;
            right: 6px;
            background: #ff4444;
            color: white;
            font-size: 10px;
            font-weight: 700;
            min-width: 17px;
            height: 17px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        /* ==================== NAV ==================== */
        nav {
            background: var(--primary-light);
            border-bottom: 1px solid rgba(255,255,255,0.08);
        }
        .nav-inner {
            max-width: 1280px;
            margin: 0 auto;
            padding: 0 20px;
            display: flex;
            overflow-x: auto;
            gap: 4px;
        }
        .nav-item {
            padding: 12px 16px;
            color: rgba(255,255,255,0.9);
            font-weight: 600;
            font-size: 13.5px;
            white-space: nowrap;
            cursor: pointer;
            border-bottom: 3px solid transparent;
            transition: all 0.2s;
        }
        .nav-item:hover, .nav-item.active {
            color: white;
            border-bottom-color: #00c6ff;
        }

        /* ==================== MAIN CONTENT ==================== */
        .main-layout {
            max-width: 1280px;
            margin: 0 auto;
            padding: 20px;
        }

        /* Hero */
        .hero {
            display: grid;
            grid-template-columns: 1fr 280px;
            gap: 16px;
            margin-bottom: 32px;
        }
        .hero-slider {
            background: linear-gradient(135deg, #0a2540, #1565c0, #0288d1);
            border-radius: 20px;
            padding: 48px 40px;
            position: relative;
            overflow: hidden;
            min-height: 360px;
            display: flex;
            align-items: center;
        }
        .hero-content { position: relative; z-index: 2; max-width: 460px; }
        .hero-badge {
            background: var(--gold);
            color: var(--primary-dark);
            font-size: 11px;
            font-weight: 800;
            padding: 5px 14px;
            border-radius: 30px;
            display: inline-block;
            margin-bottom: 12px;
        }
        .hero-title {
            font-size: 38px;
            font-weight: 900;
            line-height: 1.1;
            color: white;
            margin-bottom: 12px;
        }
        .hero-title span { color: #00c6ff; }
        .hero-price {
            font-size: 32px;
            font-weight: 900;
            color: var(--gold);
            margin: 16px 0 4px;
        }

        /* Product Card */
        .product-card {
            background: white;
            border-radius: 16px;
            overflow: hidden;
            box-shadow: var(--shadow-sm);
            transition: all 0.3s ease;
            cursor: pointer;
        }
        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: var(--shadow-lg);
        }
        .product-img {
            height: 180px;
            background: #f8fafc;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 90px;
            position: relative;
        }
        .product-info {
            padding: 14px;
        }
        .product-name {
            font-weight: 600;
            font-size: 13.8px;
            line-height: 1.4;
            display: -webkit-box;
            -webkit-line-clamp: 2;
            -webkit-box-orient: vertical;
            overflow: hidden;
            margin-bottom: 8px;
        }
        .price-new {
            font-size: 18px;
            font-weight: 800;
            color: #e53935;
        }
        .add-cart-btn {
            width: 100%;
            margin-top: 10px;
            padding: 10px;
            background: var(--accent-light);
            color: var(--accent);
            border: 1px solid var(--accent);
            border-radius: 8px;
            font-weight: 700;
            cursor: pointer;
        }

        /* Toast */
        .toast {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: var(--primary);
            color: white;
            padding: 14px 20px;
            border-radius: 12px;
            box-shadow: var(--shadow-lg);
            display: none;
            align-items: center;
            gap: 10px;
            z-index: 9999;
            font-weight: 600;
        }
        .toast.show { display: flex; animation: slideUp 0.3s ease; }

        @keyframes slideUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* Modal */
        .modal-overlay {
            position: fixed;
            inset: 0;
            background: rgba(0,0,0,0.6);
            display: none;
            align-items: center;
            justify-content: center;
            z-index: 2000;
        }
        .modal-overlay.open { display: flex; }
        .modal {
            background: white;
            border-radius: 20px;
            width: 90%;
            max-width: 820px;
            max-height: 92vh;
            overflow: hidden;
        }

        /* Mobile Bottom Nav */
        .mobile-nav {
            display: none;
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            border-top: 1px solid var(--gray-200);
            padding: 8px 0 4px;
            z-index: 1000;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
        }
        @media (max-width: 768px) {
            .hero { grid-template-columns: 1fr; }
            .mobile-nav { display: flex; }
        }
    </style>
</head>
<body>

<!-- TOP BAR -->
<div class="topbar">
    <div class="topbar-inner">
        <div>🇻🇳 Kênh người bán | Tải ứng dụng IMEX | Kết nối với IMEX</div>
        <div>
            <a href="#" style="color:inherit;margin-left:20px;">Thông báo</a>
            <a href="#" style="color:inherit;margin-left:20px;">Hỗ trợ</a>
            <a href="#" style="color:inherit;margin-left:20px;">Tiếng Việt</a>
        </div>
    </div>
</div>

<!-- HEADER -->
<header>
    <div class="header-inner">
        <a href="#" class="logo" onclick="showPage('home')">
            <div class="logo-icon">iMX</div>
            <div class="logo-text">IM<span>EX</span></div>
        </a>

        <div class="search-bar">
            <select id="searchCat">
                <option value="">Tất cả</option>
                <option value="phone">Điện thoại</option>
                <option value="laptop">Laptop</option>
                <option value="tablet">Máy tính bảng</option>
            </select>
            <input type="text" id="searchInput" placeholder="Tìm kiếm sản phẩm..." onkeyup="handleSearch(event)">
            <button class="search-btn" onclick="doSearch()">🔍</button>
        </div>

        <div class="header-actions">
            <button class="header-btn" onclick="toggleCart()">
                <span class="icon">🛒</span>
                <span class="label">Giỏ hàng</span>
                <span class="badge" id="cartBadge">0</span>
            </button>
            <button class="header-btn" onclick="showToast('❤️ Danh sách yêu thích')">
                <span class="icon">❤️</span>
                <span class="label">Yêu thích</span>
            </button>
            <button class="header-btn" onclick="showToast('👤 Tài khoản')">
                <span class="icon">👤</span>
                <span class="label">Tài khoản</span>
            </button>
        </div>
    </div>
</header>

<!-- NAV -->
<nav>
    <div class="nav-inner">
        <div class="nav-item active" onclick="setNav(this)">🏠 Trang chủ</div>
        <div class="nav-item" onclick="setNav(this)">📱 Điện thoại</div>
        <div class="nav-item" onclick="setNav(this)">💻 Laptop</div>
        <div class="nav-item" onclick="setNav(this)">📟 Tablet</div>
        <div class="nav-item" onclick="setNav(this)">⌚ Đồng hồ</div>
        <div class="nav-item" onclick="setNav(this)">📷 Camera</div>
        <div class="nav-item" onclick="setNav(this)">🎮 Gaming</div>
        <div class="nav-item" onclick="setNav(this)">🔌 Phụ kiện</div>
    </div>
</nav>

<div class="main-layout" id="mainContent">
    <!-- Nội dung trang sẽ được render động ở đây nếu cần -->
    <h2 style="margin: 20px 0 10px; font-size: 24px;">Chào mừng bạn đến với IMEX!</h2>
    <p style="color: var(--gray-600);">Nền tảng mua sắm thiết bị điện tử uy tín nhất Việt Nam</p>
</div>

<!-- TOAST -->
<div class="toast" id="toast">
    <span id="toastMessage"></span>
</div>

<!-- CART SIDEBAR (có thể mở rộng sau) -->
<div id="cartOverlay" style="display:none; position:fixed; inset:0; background:rgba(0,0,0,0.5); z-index:3000; justify-content:flex-end;">
    <div style="width:420px; background:white; height:100%; padding:20px;">
        <h3>Giỏ hàng của bạn</h3>
        <div id="cartContent">Giỏ hàng trống</div>
    </div>
</div>

<!-- MOBILE BOTTOM NAV -->
<div class="mobile-nav">
    <div style="display:flex; justify-content:space-around; font-size:11px; color:#475569;">
        <div onclick="showToast('🏠 Trang chủ')" style="text-align:center;">🏠<br>Trang chủ</div>
        <div onclick="showToast('📱 Danh mục')" style="text-align:center;">📱<br>Danh mục</div>
        <div onclick="toggleCart()" style="text-align:center;">🛒<br>Giỏ hàng</div>
        <div onclick="showToast('❤️ Yêu thích')" style="text-align:center;">❤️<br>Yêu thích</div>
        <div onclick="showToast('👤 Tài khoản')" style="text-align:center;">👤<br>Tôi</div>
    </div>
</div>

<script>
// ==================== DATA ====================
let cart = [];

// ==================== UTILITIES ====================
function formatPrice(price) {
    return price.toLocaleString('vi-VN') + ' ₫';
}

function showToast(message) {
    const toast = document.getElementById('toast');
    const toastMsg = document.getElementById('toastMessage');
    toastMsg.textContent = message;
    toast.classList.add('show');
    
    setTimeout(() => {
        toast.classList.remove('show');
    }, 3000);
}

// ==================== CART FUNCTIONS ====================
function addToCart(product) {
    const existing = cart.find(item => item.id === product.id);
    if (existing) {
        existing.qty = (existing.qty || 1) + 1;
    } else {
        cart.push({...product, qty: 1});
    }
    updateCartBadge();
    showToast(`✅ Đã thêm ${product.name} vào giỏ hàng!`);
}

function updateCartBadge() {
    const totalItems = cart.reduce((sum, item) => sum + (item.qty || 1), 0);
    document.getElementById('cartBadge').textContent = totalItems;
}

function toggleCart() {
    const overlay = document.getElementById('cartOverlay');
    overlay.style.display = overlay.style.display === 'flex' ? 'none' : 'flex';
    
    // Có thể render chi tiết giỏ hàng sau
    document.getElementById('cartContent').innerHTML = cart.length === 0 
        ? '<p>Giỏ hàng của bạn đang trống</p>' 
        : cart.map(item => `
            <div style="display:flex; gap:12px; margin-bottom:16px;">
                <div style="font-size:40px;">${item.emoji || '📦'}</div>
                <div style="flex:1;">
                    <div style="font-weight:600;">${item.name}</div>
                    <div style="color:#e53935; font-weight:700;">${formatPrice(item.price)}</div>
                </div>
                <div>x${item.qty || 1}</div>
            </div>
        `).join('');
}

// ==================== SEARCH ====================
function handleSearch(e) {
    if (e.key === 'Enter') {
        doSearch();
    }
}

function doSearch() {
    const keyword = document.getElementById('searchInput').value.trim();
    if (keyword === '') {
        showToast('Vui lòng nhập từ khóa tìm kiếm');
        return;
    }
    showToast(`🔍 Đang tìm kiếm: "${keyword}"`);
    // Ở đây bạn có thể thêm logic filter sản phẩm
}

// ==================== NAV & PAGE ====================
function setNav(el) {
    document.querySelectorAll('.nav-item').forEach(item => item.classList.remove('active'));
    if (el) el.classList.add('active');
    showToast('📂 Đang tải danh mục...');
}

function showPage(page) {
    showToast(`📄 Chuyển đến trang: ${page}`);
}

// ==================== INIT ====================
window.onload = function() {
    updateCartBadge();
    showToast('🎉 Chào mừng bạn đến với IMEX Electronics!');
    
    // Ví dụ thêm sản phẩm test vào giỏ
    // cart.push({id:1, name:'iPhone 16 Pro Max', price:29990000, emoji:'📱'});
    // updateCartBadge();
};
</script>
</body>
</html>
