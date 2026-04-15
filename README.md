<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động. Mua sắm điện thoại, máy tính bảng, phụ kiện chính hãng - Xanh Lá & Trắng">
    <title>IMEX Mobile • Thiết Bị Di Động</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Roboto:wght@400;500;700&amp;display=swap');
        
        :root {
            --primary: #10b981;
        }
        
        * {
            transition-property: color, background-color, border-color, text-decoration-color, fill, stroke, transform;
            transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
            transition-duration: 200ms;
        }
        
        .tailwind-ready {
            font-family: 'Inter', system_ui, sans-serif;
        }
        
        .logo-font {
            font-family: 'Roboto', sans-serif;
        }

        .hero-bg {
            background: linear-gradient(90deg, #10b981 0%, #059669 100%);
        }
        
        .page {
            display: none;
        }
        
        .page.active {
            display: block;
        }
        
        .nav-link {
            position: relative;
        }
        
        .nav-link:after {
            content: '';
            position: absolute;
            width: 0;
            height: 3px;
            bottom: -2px;
            left: 0;
            background-color: #10b981;
        }
        
        .nav-link.active:after,
        .nav-link:hover:after {
            width: 100%;
        }
        
        .product-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 25px -5px rgb(16 185 129);
        }
        
        .modal {
            animation: modalPop 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        @keyframes modalPop {
            0% { opacity: 0; transform: scale(0.95); }
            100% { opacity: 1; transform: scale(1); }
        }
        
        .compact-grid {
            gap: 1.25rem;
        }
        
        .section-title {
            position: relative;
        }
        
        .section-title:after {
            content: '';
            position: absolute;
            width: 64px;
            height: 4px;
            background: #10b981;
            bottom: -6px;
            left: 0;
            border-radius: 9999px;
        }
    </style>
</head>
<body class="tailwind-ready bg-white text-gray-900">

    <!-- NAVBAR CHUYÊN NGHIỆP -->
    <nav class="bg-white border-b border-emerald-200 sticky top-0 z-50 shadow-sm">
        <div class="max-w-screen-2xl mx-auto">
            <div class="px-8 py-4 flex items-center justify-between">
                
                <!-- Logo -->
                <div class="flex items-center gap-x-3">
                    <div class="w-10 h-10 bg-emerald-600 rounded-2xl flex items-center justify-center text-white text-3xl shadow-inner">📱</div>
                    <h1 class="logo-font text-3xl font-bold tracking-tighter text-emerald-600">IMEX</h1>
                    <span class="text-emerald-500 font-semibold text-base mt-px">MOBILE</span>
                </div>

                <!-- Desktop Navigation -->
                <div class="hidden md:flex items-center gap-x-8 text-base font-medium">
                    <a onclick="navigateToPage('home')" id="nav-home" class="nav-link flex items-center gap-x-2 text-gray-700 hover:text-emerald-600">
                        <i class="fa-solid fa-house"></i> Trang chủ
                    </a>
                    <a onclick="navigateToPage('shop')" id="nav-shop" class="nav-link flex items-center gap-x-2 text-gray-700 hover:text-emerald-600">
                        <i class="fa-solid fa-store"></i> Cửa hàng
                    </a>
                    <a onclick="navigateToPage('compare')" id="nav-compare" class="nav-link flex items-center gap-x-2 text-gray-700 hover:text-emerald-600">
                        <i class="fa-solid fa-balance-scale"></i> So sánh
                    </a>
                    <a onclick="navigateToPage('community')" id="nav-community" class="nav-link flex items-center gap-x-2 text-gray-700 hover:text-emerald-600">
                        <i class="fa-solid fa-users"></i> Cộng đồng
                    </a>
                    <a onclick="navigateToPage('warranty')" id="nav-warranty" class="nav-link flex items-center gap-x-2 text-gray-700 hover:text-emerald-600">
                        <i class="fa-solid fa-shield-halved"></i> Bảo hành
                    </a>
                    <a onclick="navigateToPage('orders')" id="nav-orders" class="nav-link flex items-center gap-x-2 text-gray-700 hover:text-emerald-600">
                        <i class="fa-solid fa-receipt"></i> Đơn hàng
                    </a>
                </div>

                <div class="flex items-center gap-x-6">
                    <!-- Search Bar -->
                    <div class="relative">
                        <input id="global-search" 
                               onkeyup="if(event.key==='Enter') globalSearch()"
                               type="text" 
                               placeholder="Tìm kiếm sản phẩm..." 
                               class="bg-emerald-50 border border-emerald-200 focus:border-emerald-400 rounded-3xl pl-12 pr-6 py-3 w-72 outline-none text-sm placeholder:text-emerald-400/70">
                        <i onclick="globalSearch()" class="fa-solid fa-magnifying-glass absolute left-5 top-1/2 -translate-y-1/2 text-emerald-500"></i>
                    </div>

                    <!-- Cart -->
                    <div onclick="showCart()" class="relative cursor-pointer">
                        <i class="fa-solid fa-shopping-cart text-2xl text-gray-700"></i>
                        <span id="cart-count-badge" class="absolute -top-1 -right-1 bg-emerald-600 text-white text-[10px] font-bold rounded-full w-5 h-5 flex items-center justify-center">0</span>
                    </div>

                    <!-- User -->
                    <div onclick="toggleUserMenu()" class="flex items-center cursor-pointer">
                        <div class="w-8 h-8 bg-emerald-100 rounded-2xl flex items-center justify-center text-emerald-600 text-xl">👤</div>
                        <span id="user-name-display" class="ml-2 font-medium text-sm hidden lg:block">Ánh</span>
                    </div>

                    <!-- Mobile Menu Button -->
                    <button onclick="toggleMobileMenu()" class="md:hidden text-3xl text-emerald-600">
                        <i id="hamburger" class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t px-8 py-6 text-lg font-medium space-y-6">
            <a onclick="navigateToPage('home');toggleMobileMenu()" class="flex items-center gap-3"><i class="fa-solid fa-house w-6"></i>Trang chủ</a>
            <a onclick="navigateToPage('shop');toggleMobileMenu()" class="flex items-center gap-3"><i class="fa-solid fa-store w-6"></i>Cửa hàng</a>
            <a onclick="navigateToPage('compare');toggleMobileMenu()" class="flex items-center gap-3"><i class="fa-solid fa-balance-scale w-6"></i>So sánh</a>
            <a onclick="navigateToPage('community');toggleMobileMenu()" class="flex items-center gap-3"><i class="fa-solid fa-users w-6"></i>Cộng đồng</a>
            <a onclick="navigateToPage('warranty');toggleMobileMenu()" class="flex items-center gap-3"><i class="fa-solid fa-shield-halved w-6"></i>Bảo hành</a>
            <a onclick="navigateToPage('orders');toggleMobileMenu()" class="flex items-center gap-3"><i class="fa-solid fa-receipt w-6"></i>Đơn hàng</a>
        </div>
    </nav>

    <!-- PAGE: HOME -->
    <div id="home" class="page active">
        <section class="hero-bg text-white py-16">
            <div class="max-w-screen-2xl mx-auto px-8 grid md:grid-cols-2 gap-12 items-center">
                <div class="space-y-6">
                    <div class="inline-flex items-center bg-white/20 backdrop-blur-md px-5 py-2 rounded-3xl text-sm font-semibold gap-2">
                        <i class="fa-solid fa-medal"></i> CHÍNH HÃNG • BẢO HÀNH VÀNG
                    </div>
                    <h1 class="text-5xl md:text-6xl font-bold leading-none">Thiết bị di động<br>chất lượng cao</h1>
                    <p class="text-2xl text-emerald-100">Mua sắm nhanh • Giao hàng siêu tốc • Hỗ trợ 24/7</p>
                    <div class="flex gap-4">
                        <button onclick="navigateToPage('shop')" class="bg-white text-emerald-600 px-8 py-5 rounded-3xl font-semibold text-xl flex items-center gap-3">Khám phá cửa hàng</button>
                        <button onclick="navigateToPage('compare')" class="border-2 border-white/80 px-8 py-5 rounded-3xl font-semibold text-xl flex items-center gap-3">So sánh ngay</button>
                    </div>
                </div>
                <div class="flex justify-center">
                    <img src="https://picsum.photos/id/1015/800/800" alt="Hero" class="max-w-xs md:max-w-md rounded-3xl shadow-2xl rotate-[-4deg]">
                </div>
            </div>
        </section>

        <!-- Categories Compact -->
        <div class="max-w-screen-2xl mx-auto px-8 py-10 grid grid-cols-2 md:grid-cols-4 gap-6">
            <div onclick="navigateToPage('shop');filterByCategory('phone')" class="bg-white border border-emerald-100 hover:border-emerald-300 p-6 rounded-3xl flex flex-col items-center text-center cursor-pointer">
                <div class="text-5xl mb-3">📱</div>
                <p class="font-semibold">Điện thoại</p>
                <p class="text-xs text-emerald-500">248 sản phẩm</p>
            </div>
            <div onclick="navigateToPage('shop');filterByCategory('tablet')" class="bg-white border border-emerald-100 hover:border-emerald-300 p-6 rounded-3xl flex flex-col items-center text-center cursor-pointer">
                <div class="text-5xl mb-3">📟</div>
                <p class="font-semibold">Máy tính bảng</p>
                <p class="text-xs text-emerald-500">112 sản phẩm</p>
            </div>
            <div onclick="navigateToPage('shop');filterByCategory('accessory')" class="bg-white border border-emerald-100 hover:border-emerald-300 p-6 rounded-3xl flex flex-col items-center text-center cursor-pointer">
                <div class="text-5xl mb-3">🔌</div>
                <p class="font-semibold">Phụ kiện</p>
                <p class="text-xs text-emerald-500">387 sản phẩm</p>
            </div>
            <div onclick="navigateToPage('shop');filterByCategory('watch')" class="bg-white border border-emerald-100 hover:border-emerald-300 p-6 rounded-3xl flex flex-col items-center text-center cursor-pointer">
                <div class="text-5xl mb-3">⌚</div>
                <p class="font-semibold">Smartwatch</p>
                <p class="text-xs text-emerald-500">89 sản phẩm</p>
            </div>
        </div>
    </div>

    <!-- PAGE: SHOP (Cửa hàng - chi tiết hóa quản lý sản phẩm) -->
    <div id="shop" class="page">
        <div class="max-w-screen-2xl mx-auto px-8 py-8">
            <div class="flex items-end justify-between mb-8">
                <h1 class="text-4xl font-semibold section-title">Cửa hàng • Tất cả sản phẩm</h1>
                <div class="flex gap-3 text-sm">
                    <select id="sort-select" onchange="applyFilters()" class="border border-emerald-200 rounded-3xl px-6 py-2 text-sm">
                        <option value="price-low">Giá thấp → cao</option>
                        <option value="price-high">Giá cao → thấp</option>
                        <option value="rating">Đánh giá cao nhất</option>
                    </select>
                </div>
            </div>

            <!-- Filters -->
            <div class="flex gap-8 mb-8 text-sm">
                <div onclick="filterByCategory('all')" class="cursor-pointer px-5 py-2 rounded-3xl border border-emerald-200 hover:bg-emerald-50">Tất cả</div>
                <div onclick="filterByCategory('phone')" class="cursor-pointer px-5 py-2 rounded-3xl border border-emerald-200 hover:bg-emerald-50">Điện thoại</div>
                <div onclick="filterByCategory('tablet')" class="cursor-pointer px-5 py-2 rounded-3xl border border-emerald-200 hover:bg-emerald-50">Tablet</div>
                <div onclick="filterByCategory('accessory')" class="cursor-pointer px-5 py-2 rounded-3xl border border-emerald-200 hover:bg-emerald-50">Phụ kiện</div>
                <div onclick="filterByCategory('watch')" class="cursor-pointer px-5 py-2 rounded-3xl border border-emerald-200 hover:bg-emerald-50">Smartwatch</div>
            </div>

            <div id="shop-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-5 compact-grid">
                <!-- JS render -->
            </div>
        </div>
    </div>

    <!-- PAGE: COMPARE -->
    <div id="compare" class="page">
        <div class="max-w-screen-2xl mx-auto px-8 py-8">
            <h1 class="text-4xl font-semibold section-title mb-6">So sánh thông số kỹ thuật</h1>
            <p class="text-emerald-600 mb-8">Chọn tối đa 4 sản phẩm để đối chiếu cấu hình, pin, hiệu năng, giá bán…</p>
            
            <div id="compare-list" class="flex gap-4 mb-8"></div>
            
            <button onclick="openFullCompareModal()" class="mb-8 bg-emerald-600 hover:bg-emerald-700 text-white px-8 py-4 rounded-3xl flex items-center gap-3">
                <i class="fa-solid fa-balance-scale"></i> Mở bảng so sánh đầy đủ
            </button>
            
            <div class="bg-white border border-emerald-100 rounded-3xl p-8" id="compare-empty">
                <p class="text-center text-gray-400 py-12">Chưa có sản phẩm nào để so sánh. Hãy thêm từ trang chi tiết sản phẩm.</p>
            </div>
        </div>
    </div>

    <!-- PAGE: COMMUNITY -->
    <div id="community" class="page">
        <div class="max-w-screen-2xl mx-auto px-8 py-8">
            <h1 class="text-4xl font-semibold section-title mb-8">Cộng đồng người dùng IMEX</h1>
            
            <div id="community-posts" class="grid md:grid-cols-3 gap-6">
                <!-- JS -->
            </div>

            <div class="mt-12 bg-emerald-50 rounded-3xl p-8">
                <h3 class="font-semibold mb-4">Đăng bài chia sẻ kinh nghiệm</h3>
                <textarea id="post-text" rows="4" class="w-full border border-emerald-200 rounded-3xl p-6 outline-none resize-none" placeholder="Bạn đang dùng sản phẩm gì? Chia sẻ cảm nhận..."></textarea>
                <button onclick="publishPost()" class="mt-6 bg-emerald-600 text-white px-10 py-4 rounded-3xl font-medium">ĐĂNG BÀI</button>
            </div>
        </div>
    </div>

    <!-- PAGE: WARRANTY -->
    <div id="warranty" class="page">
        <div class="max-w-screen-2xl mx-auto px-8 py-8">
            <h1 class="text-4xl font-semibold section-title mb-8">Bảo hành điện tử</h1>
            
            <div class="max-w-lg mx-auto bg-white border border-emerald-200 rounded-3xl p-8">
                <p class="text-sm mb-2 font-medium">Nhập số Serial / IMEI</p>
                <input id="serial-input" type="text" placeholder="VD: 1234567890ABCDEF" class="w-full border border-emerald-200 rounded-3xl px-6 py-5 text-lg outline-none">
                <button onclick="checkElectronicWarranty()" class="mt-6 w-full bg-emerald-600 text-white py-5 rounded-3xl font-semibold">TRA CỨU NGAY</button>
            </div>

            <div class="mt-12">
                <h3 class="text-xl font-medium mb-6">Lịch sử bảo hành của bạn</h3>
                <div id="warranty-list" class="space-y-4">
                    <!-- JS -->
                </div>
            </div>
        </div>
    </div>

    <!-- PAGE: ORDERS -->
    <div id="orders" class="page">
        <div class="max-w-screen-2xl mx-auto px-8 py-8">
            <h1 class="text-4xl font-semibold section-title mb-8">Đơn hàng của tôi</h1>
            <div id="orders-container" class="space-y-6">
                <!-- JS -->
            </div>
        </div>
    </div>

    <!-- PRODUCT DETAIL MODAL -->
    <div onclick="if(event.target.id==='detail-modal')hideDetailModal()" id="detail-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" class="bg-white rounded-3xl w-full max-w-5xl max-h-[92vh] overflow-auto modal">
            <div class="sticky top-0 bg-white border-b px-8 py-5 flex justify-between items-center z-10">
                <h2 id="detail-name" class="text-3xl font-semibold"></h2>
                <i onclick="hideDetailModal()" class="fa-solid fa-xmark text-3xl cursor-pointer"></i>
            </div>
            
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 px-8 py-8">
                <div>
                    <img id="detail-image" src="" class="w-full rounded-3xl">
                    <div class="flex gap-4 mt-6">
                        <div class="cursor-pointer flex-1 p-2 border border-emerald-200 rounded-2xl"><img src="https://picsum.photos/id/1015/200/200" class="rounded-xl w-full"></div>
                        <div class="cursor-pointer flex-1 p-2 border border-transparent rounded-2xl"><img src="https://picsum.photos/id/201/200/200" class="rounded-xl w-full"></div>
                    </div>
                </div>
                
                <div>
                    <div class="flex justify-between">
                        <div id="detail-price" class="text-4xl font-bold text-emerald-600"></div>
                        <button onclick="addCurrentProductToCart()" class="bg-emerald-600 hover:bg-emerald-700 text-white px-8 py-3 rounded-3xl font-semibold flex items-center gap-x-2">
                            <i class="fa-solid fa-cart-plus"></i> Thêm vào giỏ
                        </button>
                    </div>
                    
                    <div class="mt-8">
                        <h4 class="font-medium mb-4">Thông số kỹ thuật</h4>
                        <table id="detail-specs" class="w-full text-sm border-collapse"></table>
                    </div>
                    
                    <div class="mt-8">
                        <h4 class="font-medium mb-4">Đánh giá từ người dùng</h4>
                        <div id="detail-reviews" class="space-y-6"></div>
                    </div>
                    
                    <button onclick="addToCompareFromModal()" class="mt-8 w-full border-2 border-dashed border-emerald-600 text-emerald-600 py-5 rounded-3xl font-semibold flex items-center justify-center gap-3">
                        <i class="fa-solid fa-balance-scale"></i> Thêm vào danh sách so sánh
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- COMPARE FULL MODAL -->
    <div onclick="if(event.target.id==='compare-modal-full')hideFullCompareModal()" id="compare-modal-full" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" class="bg-white rounded-3xl w-full max-w-7xl max-h-[90vh] overflow-hidden modal">
            <div class="px-8 py-6 border-b flex justify-between">
                <h3 class="font-semibold text-3xl">Bảng so sánh chi tiết</h3>
                <i onclick="hideFullCompareModal()" class="fa-solid fa-xmark text-4xl cursor-pointer"></i>
            </div>
            <div class="p-8 overflow-auto" style="max-height: calc(90vh - 130px)">
                <table class="w-full" id="full-compare-table">
                    <thead class="sticky top-0 bg-white">
                        <tr id="compare-header-row"></tr>
                    </thead>
                    <tbody id="compare-body" class="text-sm divide-y"></tbody>
                </table>
            </div>
        </div>
    </div>

    <!-- CART + THANH TOÁN MODAL -->
    <div onclick="if(event.target.id==='cart-modal')hideCartModal()" id="cart-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" class="bg-white rounded-3xl w-full max-w-2xl modal">
            <div class="px-8 py-6 border-b font-semibold text-2xl flex justify-between">
                <span>Giỏ hàng &amp; Thanh toán</span>
                <i onclick="hideCartModal()" class="fa-solid fa-xmark cursor-pointer"></i>
            </div>
            
            <div id="cart-content" class="p-8 space-y-8 max-h-[60vh] overflow-auto"></div>
            
            <div class="px-8 py-6 border-t flex flex-col gap-6">
                <div class="flex justify-between text-xl">
                    <span>Tổng tiền</span>
                    <span id="cart-total-display" class="font-bold text-emerald-600"></span>
                </div>
                
                <div>
                    <h4 class="mb-3 font-medium">Vận chuyển</h4>
                    <div class="flex gap-4">
                        <label class="flex-1 border border-emerald-200 rounded-3xl p-4 cursor-pointer hover:border-emerald-400">
                            <input type="radio" name="ship" checked> Giao nhanh 90 phút (Vinh)
                            <span class="block text-xs text-emerald-500">Miễn phí</span>
                        </label>
                        <label class="flex-1 border border-emerald-200 rounded-3xl p-4 cursor-pointer hover:border-emerald-400">
                            <input type="radio" name="ship"> Toàn quốc 1-2 ngày
                            <span class="block text-xs text-emerald-500">35.000 ₫</span>
                        </label>
                    </div>
                </div>
                
                <button onclick="proceedToPayment()" class="bg-emerald-600 text-white py-5 rounded-3xl font-semibold text-xl">Xác nhận thanh toán</button>
            </div>
        </div>
    </div>

    <!-- USER MENU -->
    <div id="user-menu" onclick="if(event.target.id==='user-menu')this.classList.add('hidden')" class="hidden fixed top-20 right-8 bg-white rounded-3xl shadow-xl py-3 w-72 z-[9999]">
        <div class="px-6 py-3 border-b flex items-center gap-x-4">
            <span class="text-4xl">👤</span>
            <div>
                <p class="font-semibold">Xin chào, Ánh</p>
                <p class="text-xs text-gray-500">anh.vinh@imex.vn</p>
            </div>
        </div>
        <a onclick="navigateToPage('orders');hideUserMenu()" class="flex items-center px-6 py-4 hover:bg-emerald-50 gap-4"><i class="fa-solid fa-receipt"></i>Đơn hàng</a>
        <a onclick="navigateToPage('warranty');hideUserMenu()" class="flex items-center px-6 py-4 hover:bg-emerald-50 gap-4"><i class="fa-solid fa-shield-halved"></i>Bảo hành của tôi</a>
        <a onclick="hideUserMenu()" class="flex items-center px-6 py-4 hover:bg-emerald-50 gap-4"><i class="fa-solid fa-sign-out-alt"></i>Đăng xuất</a>
    </div>

    <script>
        // ==================== CẤU HÌNH CHÍNH ====================
        const PRIMARY_COLOR = '#10b981'
        
        // Dữ liệu sản phẩm chi tiết hơn
        let allProducts = [
            {
                id: 1, category: "phone", name: "iPhone 16 Pro Max 256GB", price: 32990000, oldPrice: 35990000,
                image: "https://picsum.photos/id/1015/800/800",
                specs: { "Màn hình": "6.9\" OLED 120Hz", "Chip": "A18 Pro", "RAM": "8GB", "Pin": "4680mAh", "Camera": "48MP Fusion" },
                rating: 5, reviews: [{user:"Ánh", text:"Pin cực trâu, camera tuyệt vời!", stars:5}]
            },
            {
                id: 2, category: "phone", name: "Samsung Galaxy S25 Ultra", price: 28990000, oldPrice: 31990000,
                image: "https://picsum.photos/id/201/800/800",
                specs: { "Màn hình": "6.8\" AMOLED 120Hz", "Chip": "Snapdragon 8 Elite", "RAM": "12GB", "Pin": "5000mAh", "Camera": "200MP" },
                rating: 4, reviews: []
            },
            {
                id: 3, category: "tablet", name: "iPad Air 6 M2 128GB", price: 15990000, oldPrice: 17990000,
                image: "https://picsum.photos/id/301/800/800",
                specs: { "Màn hình": "11\" Liquid Retina", "Chip": "M2", "RAM": "8GB", "Pin": "28Wh" },
                rating: 5, reviews: [{user:"Minh", text:"Màn hình đẹp, hiệu năng mạnh", stars:5}]
            },
            {
                id: 4, category: "phone", name: "Xiaomi Redmi Note 14 Pro", price: 6990000, oldPrice: 7990000,
                image: "https://picsum.photos/id/401/800/800",
                specs: { "Màn hình": "6.67\" AMOLED 120Hz", "Chip": "Dimensity 7300", "RAM": "12GB", "Pin": "6200mAh" },
                rating: 4, reviews: []
            },
            {
                id: 5, category: "watch", name: "Apple Watch Ultra 2", price: 18990000, oldPrice: 21990000,
                image: "https://picsum.photos/id/501/800/800",
                specs: { "Kích thước": "49mm", "Pin": "36 giờ", "Chống nước": "100m" },
                rating: 5, reviews: []
            },
            {
                id: 6, category: "accessory", name: "AirPods Pro 2", price: 5990000, oldPrice: 6990000,
                image: "https://picsum.photos/id/701/800/800",
                specs: { "Âm thanh": "Spatial Audio", "Pin": "6 giờ (mỗi bên)" },
                rating: 5, reviews: []
            }
        ]
        
        let cart = []
        let compareItems = []
        let communityPostsData = [
            {id:1, user:"Hùng iFan", time:"3 giờ trước", content:"iPhone 16 Pro Max camera đêm cực nét, mình dùng 1 tuần rồi quá hài lòng!", likes:142},
            {id:2, user:"Lan Tech", time:"7 giờ trước", content:"Galaxy S25 Ultra với bút S-Pen viết note siêu mượt. Ai dùng rồi comment đi!", likes:89}
        ]
        let ordersData = [
            {id:"IMX-240416-001", date:"16/04/2026", items:"iPhone 16 Pro Max", total:32990000, status:"Đang giao", tracking:"GHTK-987654"},
            {id:"IMX-240410-042", date:"10/04/2026", items:"AirPods Pro 2", total:5990000, status:"Đã nhận", tracking:"GHN-445566"}
        ]
        let warrantyData = [
            {serial:"1234567890ABC", product:"iPhone 16 Pro Max", expiry:"12/2027", status:"Còn hiệu lực"}
        ]
        
        let currentDetailProduct = null
        
        // ==================== RENDER FUNCTIONS ====================
        function renderShop(productsList) {
            const container = document.getElementById('shop-grid')
            container.innerHTML = ''
            productsList.forEach(p => {
                const card = document.createElement('div')
                card.className = 'product-card bg-white border border-emerald-100 rounded-3xl overflow-hidden cursor-pointer'
                card.innerHTML = `
                <img src="${p.image}" class="w-full h-52 object-cover">
                <div class="p-5">
                    <p class="font-semibold text-lg line-clamp-2">${p.name}</p>
                    <div class="flex justify-between items-baseline mt-4">
                        <span class="text-2xl font-bold text-emerald-600">${(p.price/1000000).toFixed(1)}tr</span>
                        ${p.oldPrice ? `<span class="text-xs line-through text-gray-400">${(p.oldPrice/1000000).toFixed(1)}tr</span>` : ''}
                    </div>
                    <div class="flex text-emerald-400 text-lg mt-2">${'★'.repeat(p.rating)}</div>
                    <button onclick="event.stopImmediatePropagation();showProductDetail(${p.id});" class="mt-6 w-full text-sm py-3 bg-emerald-600 text-white rounded-3xl">Xem chi tiết</button>
                </div>`
                container.appendChild(card)
            })
            if (productsList.length === 0) container.innerHTML = `<p class="col-span-full text-center py-12 text-gray-400">Không tìm thấy sản phẩm</p>`
        }
        
        function showProductDetail(id) {
            currentDetailProduct = allProducts.find(p => p.id === id)
            if (!currentDetailProduct) return
            
            document.getElementById('detail-name').innerText = currentDetailProduct.name
            document.getElementById('detail-image').src = currentDetailProduct.image
            document.getElementById('detail-price').innerHTML = `<span class="text-4xl">${(currentDetailProduct.price/1000000).toFixed(1)}tr ₫</span>`
            
            // Specs
            let specHTML = `<tr class="border-b"><td class="py-3 pr-8 font-medium">Thông số</td><td class="py-3 text-right">Giá trị</td></tr>`
            Object.keys(currentDetailProduct.specs).forEach(key => {
                specHTML += `<tr class="border-b"><td class="py-3 font-medium">${key}</td><td class="py-3 text-right">${currentDetailProduct.specs[key]}</td></tr>`
            })
            document.getElementById('detail-specs').innerHTML = specHTML
            
            // Reviews
            let reviewHTML = ''
            if (currentDetailProduct.reviews && currentDetailProduct.reviews.length) {
                reviewHTML = currentDetailProduct.reviews.map(r => `
                <div class="flex gap-3"><div class="text-emerald-400">${'★'.repeat(r.stars)}</div><div><p class="font-medium">${r.user}</p><p class="text-sm">${r.text}</p></div></div>`).join('')
            } else {
                reviewHTML = `<p class="text-gray-400 text-center py-6">Chưa có đánh giá. Hãy là người đầu tiên!</p>`
            }
            document.getElementById('detail-reviews').innerHTML = reviewHTML
            
            const modal = document.getElementById('detail-modal')
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function hideDetailModal() {
            const modal = document.getElementById('detail-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
            currentDetailProduct = null
        }
        
        function addCurrentProductToCart() {
            if (!currentDetailProduct) return
            addToCart(currentDetailProduct.id)
            hideDetailModal()
        }
        
        // Cart
        function addToCart(id) {
            const product = allProducts.find(p => p.id === id)
            if (!product) return
            const exist = cart.find(item => item.id === id)
            if (exist) exist.quantity = (exist.quantity || 1) + 1
            else cart.push(Object.assign({}, product, {quantity: 1}))
            updateCartBadge()
            showToast(`Đã thêm ${product.name} vào giỏ hàng`)
        }
        
        function updateCartBadge() {
            const count = cart.reduce((a, b) => a + (b.quantity || 1), 0)
            document.getElementById('cart-count-badge').innerText = count
        }
        
        function showCart() {
            const modal = document.getElementById('cart-modal')
            const content = document.getElementById('cart-content')
            content.innerHTML = ''
            
            if (cart.length === 0) {
                content.innerHTML = `<div class="text-center py-16 text-gray-400">Giỏ hàng trống</div>`
                modal.classList.remove('hidden')
                modal.classList.add('flex')
                return
            }
            
            let total = 0
            cart.forEach((item, index) => {
                const subtotal = item.price * (item.quantity || 1)
                total += subtotal
                content.innerHTML += `
                <div class="flex gap-5">
                    <img src="${item.image}" class="w-20 h-20 object-cover rounded-2xl">
                    <div class="flex-1">
                        <p class="font-medium">${item.name}</p>
                        <p class="text-emerald-600">${(item.price/1000000).toFixed(1)}tr × ${item.quantity}</p>
                        <div class="flex items-center mt-3">
                            <button onclick="changeCartQty(${index}, -1)" class="px-3 border rounded-2xl">-</button>
                            <span class="px-6">${item.quantity}</span>
                            <button onclick="changeCartQty(${index}, 1)" class="px-3 border rounded-2xl">+</button>
                            <button onclick="removeFromCart(${index})" class="ml-auto text-red-500 text-sm">Xóa</button>
                        </div>
                    </div>
                    <div class="font-bold text-right">${(subtotal/1000000).toFixed(1)}tr</div>
                </div>`
            })
            
            document.getElementById('cart-total-display').innerText = `${(total/1000000).toFixed(1)}tr ₫`
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function changeCartQty(index, delta) {
            if (!cart[index]) return
            cart[index].quantity = Math.max(1, (cart[index].quantity || 1) + delta)
            showCart()
            updateCartBadge()
        }
        
        function removeFromCart(index) {
            cart.splice(index, 1)
            showCart()
            updateCartBadge()
        }
        
        function hideCartModal() {
            const modal = document.getElementById('cart-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        function proceedToPayment() {
            hideCartModal()
            if (cart.length === 0) return
            const orderId = `IMX-${Date.now().toString().slice(8)}`
            ordersData.unshift({
                id: orderId,
                date: "16/04/2026",
                items: cart.map(c => c.name).join(', '),
                total: cart.reduce((a, b) => a + b.price * (b.quantity || 1), 0),
                status: "Đang xử lý",
                tracking: "GHN-" + Math.floor(100000 + Math.random()*900000)
            })
            cart = []
            updateCartBadge()
            navigateToPage('orders')
            showToast(`✅ Đơn hàng ${orderId} đã được tạo thành công!`)
        }
        
        // Compare
        function addToCompareFromModal() {
            if (!currentDetailProduct) return
            if (compareItems.length >= 4) return showToast('Tối đa 4 sản phẩm để so sánh')
            if (!compareItems.find(i => i.id === currentDetailProduct.id)) {
                compareItems.push(currentDetailProduct)
                renderCompareList()
                showToast('Đã thêm vào danh sách so sánh')
            }
            hideDetailModal()
        }
        
        function renderCompareList() {
            const container = document.getElementById('compare-list')
            container.innerHTML = compareItems.map((p, i) => `
            <div class="bg-white border border-emerald-200 rounded-3xl p-4 flex-1 text-center">
                <img src="${p.image}" class="h-24 mx-auto rounded-2xl">
                <p class="font-medium mt-4">${p.name}</p>
                <button onclick="removeFromCompare(${i});" class="text-xs mt-3 text-red-500">Xóa</button>
            </div>`).join('')
            
            if (compareItems.length === 0) document.getElementById('compare-empty').style.display = 'block'
            else document.getElementById('compare-empty').style.display = 'none'
        }
        
        function removeFromCompare(i) {
            compareItems.splice(i, 1)
            renderCompareList()
        }
        
        function openFullCompareModal() {
            if (compareItems.length < 2) return showToast('Cần ít nhất 2 sản phẩm để so sánh')
            
            const headerRow = document.getElementById('compare-header-row')
            headerRow.innerHTML = `<th class="py-4 px-6 font-medium text-left">Thông số</th>` + compareItems.map(p => `<th class="py-4 px-6 text-center font-semibold">${p.name}</th>`).join('')
            
            const body = document.getElementById('compare-body')
            body.innerHTML = ''
            
            const allKeys = new Set()
            compareItems.forEach(p => Object.keys(p.specs).forEach(k => allKeys.add(k)))
            
            allKeys.forEach(key => {
                let row = `<tr><td class="py-4 px-6 font-medium border-r">${key}</td>`
                compareItems.forEach(p => {
                    row += `<td class="py-4 px-6 text-center">${p.specs[key] || '—'}</td>`
                })
                row += '</tr>'
                body.innerHTML += row
            })
            
            const modal = document.getElementById('compare-modal-full')
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function hideFullCompareModal() {
            const modal = document.getElementById('compare-modal-full')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        // Community
        function renderCommunity() {
            const container = document.getElementById('community-posts')
            container.innerHTML = communityPostsData.map(post => `
            <div class="border border-emerald-100 rounded-3xl p-7 bg-white">
                <div class="flex justify-between text-xs text-gray-400"><span>${post.user}</span><span>${post.time}</span></div>
                <p class="mt-4 text-base">${post.content}</p>
                <div class="flex items-center justify-end mt-6 gap-2 text-emerald-500 text-sm"><i class="fa-solid fa-heart"></i> ${post.likes}</div>
            </div>`).join('')
        }
        
        function publishPost() {
            const text = document.getElementById('post-text').value.trim()
            if (!text) return
            communityPostsData.unshift({
                id: Date.now(),
                user: "Bạn",
                time: "Vừa xong",
                content: text,
                likes: 0
            })
            document.getElementById('post-text').value = ''
            renderCommunity()
            showToast('Bài viết đã được đăng thành công!')
        }
        
        // Warranty
        function checkElectronicWarranty() {
            const serial = document.getElementById('serial-input').value.trim()
            if (!serial) return showToast('Vui lòng nhập Serial / IMEI')
            
            const found = warrantyData.find(w => w.serial === serial)
            if (found) {
                showToast(`✅ Thiết bị ${found.product} còn bảo hành đến ${found.expiry}`)
            } else {
                showToast('✅ Số serial hợp lệ. Bảo hành còn 18 tháng (dữ liệu demo)')
            }
        }
        
        function renderWarrantyList() {
            const container = document.getElementById('warranty-list')
            container.innerHTML = warrantyData.map(w => `
            <div class="flex justify-between items-center bg-white border border-emerald-100 rounded-3xl px-8 py-6">
                <div>
                    <p class="font-semibold">${w.product}</p>
                    <p class="text-xs text-gray-500">${w.serial}</p>
                </div>
                <div class="text-right">
                    <span class="px-6 py-2 bg-emerald-100 text-emerald-700 rounded-3xl text-sm">Còn hiệu lực</span>
                    <p class="text-xs mt-2">${w.expiry}</p>
                </div>
            </div>`).join('')
        }
        
        // Orders
        function renderOrders() {
            const container = document.getElementById('orders-container')
            container.innerHTML = ordersData.map(order => `
            <div class="bg-white border border-emerald-100 rounded-3xl p-8 flex justify-between items-center">
                <div>
                    <p class="font-mono text-sm text-emerald-600">${order.id}</p>
                    <p class="font-medium">${order.items}</p>
                    <p class="text-xs text-gray-500">${order.date}</p>
                </div>
                <div class="text-right">
                    <span class="inline-block px-5 py-2 text-sm font-medium rounded-3xl ${order.status === 'Đang giao' ? 'bg-blue-100 text-blue-600' : 'bg-emerald-100 text-emerald-700'}">${order.status}</span>
                    <p class="mt-4 text-emerald-600 text-sm cursor-pointer" onclick="trackOrder('${order.tracking}')">Theo dõi vận chuyển →</p>
                </div>
            </div>`).join('')
        }
        
        function trackOrder(code) {
            showToast(`📦 Đang theo dõi: ${code} • Dự kiến giao trong 24 giờ tới`)
        }
        
        // Navigation giữa các trang
        function navigateToPage(page) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'))
            const target = document.getElementById(page)
            if (target) target.classList.add('active')
            
            // Active nav
            document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('active'))
            const activeNav = document.getElementById('nav-' + page)
            if (activeNav) activeNav.classList.add('active')
            
            // Render lại dữ liệu nếu cần
            if (page === 'shop') renderShop(allProducts)
            if (page === 'compare') renderCompareList()
            if (page === 'community') renderCommunity()
            if (page === 'warranty') renderWarrantyList()
            if (page === 'orders') renderOrders()
        }
        
        // Filter shop
        function filterByCategory(cat) {
            let filtered = allProducts
            if (cat !== 'all') filtered = allProducts.filter(p => p.category === cat)
            renderShop(filtered)
        }
        
        function applyFilters() {
            let list = [...allProducts]
            const sortMode = document.getElementById('sort-select').value
            if (sortMode === 'price-low') list.sort((a,b) => a.price - b.price)
            if (sortMode === 'price-high') list.sort((a,b) => b.price - a.price)
            if (sortMode === 'rating') list.sort((a,b) => b.rating - a.rating)
            renderShop(list)
        }
        
        function globalSearch() {
            const keyword = document.getElementById('global-search').value.toLowerCase().trim()
            if (!keyword) {
                navigateToPage('shop')
                return
            }
            const filtered = allProducts.filter(p => p.name.toLowerCase().includes(keyword))
            navigateToPage('shop')
            renderShop(filtered)
        }
        
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu')
            menu.classList.toggle('hidden')
            const icon = document.getElementById('hamburger')
            icon.classList.toggle('fa-bars')
            icon.classList.toggle('fa-xmark')
        }
        
        function toggleUserMenu() {
            const menu = document.getElementById('user-menu')
            menu.classList.toggle('hidden')
        }
        
        function hideUserMenu() {
            document.getElementById('user-menu').classList.add('hidden')
        }
        
        function showToast(message) {
            const toast = document.createElement('div')
            toast.style.cssText = `position:fixed; bottom:24px; right:24px; background:${PRIMARY_COLOR}; color:white; padding:16px 24px; border-radius:9999px; box-shadow:10px 20px 25px -5px rgb(16 185 129); display:flex; align-items:center; gap:12px; z-index:99999`
            toast.innerHTML = `<i class="fa-solid fa-circle-check"></i> ${message}`
            document.body.appendChild(toast)
            setTimeout(() => {
                toast.style.opacity = 0
                setTimeout(() => toast.remove(), 400)
            }, 3000)
        }
        
        // Khởi động
        window.onload = function() {
            // Render mặc định
            renderShop(allProducts)
            renderCommunity()
            renderWarrantyList()
            renderOrders()
            updateCartBadge()
            
            console.log('%c✅ IMEX Mobile hoàn chỉnh – Màu xanh lá trắng • 6 trang riêng biệt • Giao diện chuyên nghiệp, gọn gàng, đầy đủ chức năng', 'color:#10b981; font-weight:bold')
        }
    </script>
</body>
</html>
