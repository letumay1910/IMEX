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

/* ===== TOP BAR, HEADER, NAV, ... (giữ nguyên toàn bộ CSS cũ của bạn) ===== */
.topbar { background: var(--primary-dark); color: rgba(255,255,255,0.8); font-size: 12px; padding: 6px 0; }
.topbar-inner { max-width: 1280px; margin: 0 auto; padding: 0 20px; display: flex; justify-content: space-between; align-items: center; }
.topbar a { color: rgba(255,255,255,0.8); text-decoration: none; margin-left: 16px; }
.topbar a:hover { color: var(--white); }

header { background: var(--primary); position: sticky; top: 0; z-index: 1000; box-shadow: 0 2px 20px rgba(0,0,0,0.3); }
.header-inner { max-width: 1280px; margin: 0 auto; padding: 14px 20px; display: flex; align-items: center; gap: 20px; }
.logo { display: flex; align-items: center; gap: 10px; text-decoration: none; flex-shrink: 0; }
.logo-icon { width: 40px; height: 40px; background: linear-gradient(135deg, var(--accent-bright), #00c6ff); border-radius: 10px; display: flex; align-items: center; justify-content: center; font-family: 'Space Mono', monospace; font-weight: 700; font-size: 13px; color: white; }
.logo-text { color: white; font-size: 22px; font-weight: 900; letter-spacing: -0.5px; }
.logo-text span { color: #00c6ff; }

.search-bar { flex: 1; display: flex; max-width: 600px; }
.search-bar input { flex: 1; padding: 10px 16px; border: none; border-radius: var(--radius-sm) 0 0 var(--radius-sm); font-family: 'Nunito', sans-serif; font-size: 14px; outline: none; background: white; }
.search-bar select { padding: 10px 12px; border: none; border-left: 1px solid var(--gray-200); background: white; font-family: 'Nunito', sans-serif; font-size: 13px; cursor: pointer; outline: none; color: var(--gray-600); }
.search-btn { padding: 10px 20px; background: var(--accent-bright); color: white; border: none; border-radius: 0 var(--radius-sm) var(--radius-sm) 0; cursor: pointer; font-size: 16px; font-weight: 700; transition: background 0.2s; }
.search-btn:hover { background: #0077ee; }

.header-actions { display: flex; align-items: center; gap: 6px; flex-shrink: 0; }
.header-btn { display: flex; flex-direction: column; align-items: center; gap: 2px; padding: 8px 12px; color: white; cursor: pointer; border-radius: var(--radius-sm); border: none; background: transparent; font-family: 'Nunito', sans-serif; text-decoration: none; transition: background 0.2s; position: relative; }
.header-btn:hover { background: rgba(255,255,255,0.1); }
.header-btn .icon { font-size: 20px; }
.header-btn .label { font-size: 11px; color: rgba(255,255,255,0.8); }
.badge { position: absolute; top: 4px; right: 4px; background: #ff4444; color: white; font-size: 10px; font-weight: 700; min-width: 16px; height: 16px; border-radius: 8px; display: flex; align-items: center; justify-content: center; padding: 0 4px; }

/* Giữ nguyên phần CSS còn lại của bạn (nav, hero, product-card, modal, cart... ) */
 /* ... (tôi rút gọn để dễ nhìn, bạn copy toàn bộ CSS cũ từ file cũ vào đây) ... */

.modal-overlay {
  position: fixed; inset: 0; background: rgba(0,0,0,0.5); z-index: 2000;
  display: flex; align-items: center; justify-content: center; padding: 20px;
  opacity: 0; pointer-events: none; transition: opacity 0.3s;
}
.modal-overlay.open { opacity: 1; pointer-events: all; }
.modal {
  background: white; border-radius: var(--radius-xl); width: 100%; max-width: 760px;
  max-height: 85vh; overflow-y: auto; transform: scale(0.95); transition: transform 0.3s;
}
.modal-overlay.open .modal { transform: scale(1); }
.modal-header {
  padding: 20px 24px; border-bottom: 1px solid var(--gray-100);
  display: flex; align-items: center; justify-content: space-between;
  position: sticky; top: 0; background: white; z-index: 1;
}
.modal-title { font-size: 18px; font-weight: 900; color: var(--primary); }
.modal-close {
  width: 32px; height: 32px; border-radius: 50%; border: none;
  background: var(--gray-100); cursor: pointer; font-size: 16px;
  display: flex; align-items: center; justify-content: center;
}
.modal-close:hover { background: var(--gray-200); }
.modal-body { padding: 24px; }
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
      </div>
      <button class="search-btn" onclick="doSearch()">🔍</button>
    </div>

    <div class="header-actions">
      <!-- Nút Đăng nhập mới thêm -->
      <button class="header-btn" onclick="showLoginModal()">
        <span class="icon">🔑</span>
        <span class="label">Đăng nhập</span>
      </button>

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
    </div>
  </div>
</header>

<!-- NAV (giữ nguyên) -->
<nav>
  <div class="nav-inner">
    <div class="nav-item active" onclick="setNav(this,'home')">🏠 Trang chủ</div>
    <!-- các nav-item khác giữ nguyên -->
    <div class="nav-item" onclick="setNav(this,'phone')">📱 Điện thoại</div>
    <div class="nav-item" onclick="setNav(this,'laptop')">💻 Laptop</div>
    <!-- ... (copy đầy đủ nav-item từ file cũ) ... -->
  </div>
</nav>

<!-- MAIN CONTENT (giữ nguyên toàn bộ phần từ hero đến footer) -->
<div class="main-layout" id="mainContent">
  <!-- Hero, Features, Categories, Flash Sale, Brands, Promo, Vouchers, Products, Shops, Reviews... -->
  <!-- Bạn copy nguyên phần này từ file cũ vào đây -->
</div>

<!-- FOOTER (giữ nguyên) -->
<footer>
  <!-- copy nguyên footer cũ -->
</footer>

<!-- PRODUCT MODAL (giữ nguyên) -->
<div class="modal-overlay" id="productModal" onclick="closeModalOutside(event)">
  <!-- nội dung cũ -->
</div>

<!-- CART SIDEBAR (giữ nguyên) -->
<div class="cart-overlay" id="cartOverlay">
  <!-- nội dung cũ -->
</div>

<!-- ==================== LOGIN MODAL ==================== -->
<div class="modal-overlay" id="loginModal" onclick="closeModalOutsideLogin(event)">
  <div class="modal" style="max-width: 420px;">
    <div class="modal-header">
      <span class="modal-title">Đăng nhập vào IMEX</span>
      <button class="modal-close" onclick="closeLoginModal()">✕</button>
    </div>
    <div class="modal-body" style="padding: 32px 28px;">
      <div style="text-align:center; margin-bottom:24px;">
        <div class="logo" style="display:inline-flex; justify-content:center;">
          <div class="logo-icon" style="width:48px;height:48px;font-size:16px;">iMX</div>
        </div>
        <div class="logo-text" style="font-size:26px; margin-top:8px;">IM<span style="color:#00c6ff">EX</span></div>
      </div>

      <form id="loginForm" onsubmit="handleLogin(event)">
        <div style="margin-bottom:20px;">
          <label style="font-size:13px; font-weight:700; color:var(--gray-600); display:block; margin-bottom:6px;">Số điện thoại hoặc Email</label>
          <input type="text" id="loginUsername" placeholder="Nhập số điện thoại hoặc email" 
                 style="width:100%; padding:14px 16px; border:1px solid var(--gray-300); border-radius:var(--radius-sm); font-size:15px; outline:none;">
        </div>

        <div style="margin-bottom:20px;">
          <label style="font-size:13px; font-weight:700; color:var(--gray-600); display:block; margin-bottom:6px;">Mật khẩu</label>
          <input type="password" id="loginPassword" placeholder="Nhập mật khẩu" 
                 style="width:100%; padding:14px 16px; border:1px solid var(--gray-300); border-radius:var(--radius-sm); font-size:15px; outline:none;">
        </div>

        <div style="display:flex; justify-content:space-between; align-items:center; margin-bottom:24px; font-size:13px;">
          <label style="display:flex; align-items:center; gap:6px; cursor:pointer;">
            <input type="checkbox" checked> Ghi nhớ đăng nhập
          </label>
          <a href="#" onclick="forgotPassword(); return false;" style="color:var(--accent);">Quên mật khẩu?</a>
        </div>

        <button type="submit" 
                style="width:100%; padding:14px; background:var(--accent-bright); color:white; border:none; border-radius:var(--radius); font-size:16px; font-weight:800; cursor:pointer;">
          Đăng nhập
        </button>
      </form>

      <div style="text-align:center; margin:24px 0; color:var(--gray-400); font-size:13px;">hoặc</div>

      <div style="display:grid; grid-template-columns:1fr 1fr; gap:12px; margin-bottom:28px;">
        <button onclick="quickLogin('google')" 
                style="padding:12px; border:1px solid var(--gray-300); background:white; border-radius:var(--radius-sm); font-weight:700; cursor:pointer; display:flex; align-items:center; justify-content:center; gap:8px;">
          <span style="font-size:20px;">G</span> Google
        </button>
        <button onclick="quickLogin('facebook')" 
                style="padding:12px; border:1px solid var(--gray-300); background:white; border-radius:var(--radius-sm); font-weight:700; cursor:pointer; display:flex; align-items:center; justify-content:center; gap:8px;">
          <span style="font-size:20px; color:#1877f2;">f</span> Facebook
        </button>
      </div>

      <div style="text-align:center; font-size:14px;">
        Chưa có tài khoản? 
        <a href="#" onclick="switchToRegister(); return false;" style="color:var(--accent); font-weight:700;">Đăng ký ngay</a>
      </div>
    </div>
  </div>
</div>

<!-- TOAST -->
<div class="toast" id="toast"></div>

<!-- BACK TO TOP -->
<button class="back-to-top" id="backTop" onclick="scrollToTop()">↑</button>

<script>
// ====== DATA & RENDER FUNCTIONS (giữ nguyên toàn bộ code JS cũ của bạn) ======
// ... Copy toàn bộ phần script cũ từ <script> đến trước phần login mới ...

// ====== LOGIN FUNCTIONS ======
function showLoginModal() {
  document.getElementById('loginModal').classList.add('open');
  setTimeout(() => document.getElementById('loginUsername').focus(), 300);
}

function closeLoginModal() {
  document.getElementById('loginModal').classList.remove('open');
}

function closeModalOutsideLogin(e) {
  if (e.target.classList.contains('modal-overlay')) closeLoginModal();
}

function handleLogin(e) {
  e.preventDefault();
  const username = document.getElementById('loginUsername').value.trim();
  const password = document.getElementById('loginPassword').value.trim();

  if (!username || !password) {
    showToast('⚠️ Vui lòng nhập đầy đủ thông tin!');
    return;
  }

  showToast('✅ Đang đăng nhập...');

  setTimeout(() => {
    closeLoginModal();
    showToast('🎉 Đăng nhập thành công! Chào mừng bạn đến với IMEX');
  }, 1500);
}

function quickLogin(provider) {
  showToast(`🔄 Đang chuyển hướng đến ${provider === 'google' ? 'Google' : 'Facebook'}...`);
  setTimeout(() => {
    closeLoginModal();
    showToast(`✅ Đăng nhập thành công qua ${provider === 'google' ? 'Google' : 'Facebook'}`);
  }, 1200);
}

function forgotPassword() {
  showToast('📧 Chức năng khôi phục mật khẩu đang được phát triển...');
}

function switchToRegister() {
  closeLoginModal();
  showToast('📝 Chức năng đăng ký đang được phát triển...');
}

// ====== Các hàm cũ giữ nguyên (showToast, renderFlash, renderAll, openProduct, toggleCart...) ======
function showToast(msg) {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.classList.add('show');
  clearTimeout(window.toastTimer);
  window.toastTimer = setTimeout(() => t.classList.remove('show'), 3000);
}

// Các hàm render, countdown, init... giữ nguyên như file cũ

// INIT
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
