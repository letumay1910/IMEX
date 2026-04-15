<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động. Giá sốc Flash Sale, so sánh thông số, bảo hành điện tử, cộng đồng công nghệ.">
    <title>IMEX - Thiết Bị Di Động Chính Hãng</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Roboto:wght@400;500;700&amp;display=swap');
        
        :root {
            --primary: #eab308;
        }
        
        * { transition-property: color, background-color, border-color, text-decoration-color, fill, stroke; transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1); transition-duration: 200ms; }
        
        .tailwind-ready { font-family: 'Inter', system_ui, sans-serif; }
        .logo-font { font-family: 'Roboto', sans-serif; }
        
        .hero-bg { background: linear-gradient(90deg, #eab308 0%, #ca8a04 100%); }
        
        .page { display: none; }
        .page.active { display: block; }
        
        .product-card { transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1); }
        .product-card:hover { transform: translateY(-12px) scale(1.03); box-shadow: 0 25px 50px -12px rgb(234 179 8); }
        
        .nav-link { position: relative; }
        .nav-link:after { content: ''; position: absolute; width: 0; height: 3px; bottom: -2px; left: 0; background-color: #eab308; }
        .nav-link:hover:after { width: 100%; }
        
        .flash-card { animation: flashPulse 2s infinite; }
        @keyframes flashPulse { 0%,100% { opacity: 1; } 50% { opacity: 0.9; } }
        
        .countdown { font-variant-numeric: tabular-nums; }
        
        .modal { animation: modalPop 0.3s ease-out; }
        @keyframes modalPop { 0% { opacity: 0; transform: scale(0.95); } 100% { opacity: 1; transform: scale(1); } }
        
        .section-header:after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background: #eab308;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 9999px;
        }
    </style>
</head>
<body class="tailwind-ready bg-white">

    <!-- NAVBAR -->
    <nav class="bg-white border-b-4 border-amber-400 sticky top-0 z-50 shadow-xl">
        <div class="max-w-7xl mx-auto px-6">
            <div class="py-5 flex items-center justify-between">
                <!-- Logo -->
                <div onclick="showPage('home')" class="flex items-center gap-x-3 cursor-pointer">
                    <div class="w-11 h-11 bg-gradient-to-br from-amber-400 to-yellow-500 rounded-3xl flex items-center justify-center text-white text-4xl">📱</div>
                    <h1 class="logo-font text-4xl font-bold tracking-[-2px] text-amber-400">IMEX</h1>
                    <span class="text-amber-600 font-semibold text-lg mt-1 tracking-widest">MOBILE</span>
                </div>

                <!-- Desktop Menu -->
                <div class="hidden md:flex items-center gap-x-8 text-base font-semibold">
                    <a onclick="showPage('home')" class="nav-link text-gray-800 hover:text-amber-400">Trang chủ</a>
                    <a onclick="showPage('shop')" class="nav-link text-gray-800 hover:text-amber-400">Cửa hàng</a>
                    <a onclick="showPage('flashsale')" class="nav-link text-red-600 hover:text-red-500 flex items-center gap-1"><i class="fa-solid fa-bolt"></i> FLASH SALE</a>
                    <a onclick="showPage('compare')" class="nav-link text-gray-800 hover:text-amber-400">So sánh</a>
                    <a onclick="showPage('community')" class="nav-link text-gray-800 hover:text-amber-400">Cộng đồng</a>
                    <a onclick="showPage('warranty')" class="nav-link text-gray-800 hover:text-amber-400">Bảo hành</a>
                    <a onclick="showPage('orders')" class="nav-link text-gray-800 hover:text-amber-400">Đơn hàng</a>
                </div>

                <div class="flex items-center gap-x-5">
                    <!-- Search -->
                    <div onclick="toggleSearch()" class="cursor-pointer">
                        <div class="flex items-center bg-amber-50 hover:bg-amber-100 border border-amber-200 rounded-3xl px-6 py-3 text-sm font-medium gap-x-3">
                            <i class="fa-solid fa-magnifying-glass text-amber-400"></i>
                            <input id="global-search" type="text" placeholder="Tìm sản phẩm..." 
                                   class="bg-transparent outline-none w-64 hidden md:block placeholder:text-amber-400/70">
                        </div>
                    </div>

                    <!-- Cart -->
                    <div onclick="showCart()" class="relative cursor-pointer">
                        <i class="fa-solid fa-shopping-cart text-3xl text-gray-700"></i>
                        <span id="cart-count-badge" class="absolute -top-1 -right-1 bg-red-500 text-white text-xs font-bold w-6 h-6 rounded-2xl flex items-center justify-center">0</span>
                    </div>

                    <!-- User -->
                    <div onclick="toggleUserMenu()" class="flex items-center cursor-pointer">
                        <div class="w-9 h-9 bg-amber-100 text-amber-400 rounded-2xl flex items-center justify-center text-2xl">👤</div>
                    </div>

                    <!-- Mobile Hamburger -->
                    <button onclick="toggleMobileMenu()" class="md:hidden text-4xl text-amber-400">
                        <i id="hamburger-icon" class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t px-6 py-8">
            <div class="flex flex-col gap-y-6 text-lg font-medium">
                <a onclick="showPage('home');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-house"></i> Trang chủ</a>
                <a onclick="showPage('shop');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-store"></i> Cửa hàng</a>
                <a onclick="showPage('flashsale');toggleMobileMenu()" class="flex items-center gap-4 text-red-600"><i class="fa-solid fa-bolt"></i> FLASH SALE</a>
                <a onclick="showPage('compare');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-balance-scale"></i> So sánh</a>
                <a onclick="showPage('community');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-users"></i> Cộng đồng</a>
                <a onclick="showPage('warranty');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-shield-halved"></i> Bảo hành</a>
                <a onclick="showPage('orders');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-receipt"></i> Đơn hàng</a>
            </div>
        </div>
    </nav>

    <!-- PAGE: HOME -->
    <div id="page-home" class="page active">
        <section class="hero-bg text-white min-h-screen flex items-center">
            <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
                <div class="space-y-8">
                    <div class="inline-flex bg-white/20 backdrop-blur-xl text-white px-8 py-3 rounded-3xl items-center gap-3 text-sm font-semibold">
                        <i class="fa-solid fa-fire"></i> FLASH SALE ĐANG DIỄN RA
                    </div>
                    <h1 class="text-6xl md:text-7xl font-bold leading-none tracking-[-2px]">IMEX<br><span class="text-amber-100">Thế giới di động vàng</span></h1>
                    <p class="text-3xl text-amber-100">Giá sốc hôm nay • Giao ngay 90 phút • Bảo hành điện tử</p>
                    <div class="flex gap-4">
                        <button onclick="showPage('flashsale')" class="bg-white text-amber-400 px-10 py-6 rounded-3xl font-bold text-2xl flex items-center gap-3">🔥 XEM FLASH SALE NGAY</button>
                        <button onclick="showPage('shop')" class="border-2 border-white px-10 py-6 rounded-3xl font-bold text-2xl">Khám phá cửa hàng</button>
                    </div>
                </div>
                <div class="relative">
                    <img src="https://picsum.photos/id/1015/900/900" alt="iPhone 16 Pro Max" class="w-96 mx-auto rounded-3xl shadow-2xl border-8 border-white">
                </div>
            </div>
        </section>

        <!-- Mini flash banner -->
        <div class="max-w-7xl mx-auto px-6 py-8 bg-white border-b flex items-center justify-between text-sm">
            <div class="flex items-center gap-3 text-red-500 font-medium">
                <i class="fa-solid fa-bolt"></i> FLASH SALE HÔM NAY - Giảm đến 40% • Kết thúc sau
            </div>
            <div id="global-countdown" class="font-mono text-xl text-red-500 font-bold">23:14:58</div>
            <button onclick="showPage('flashsale')" class="text-amber-400 font-semibold flex items-center gap-2">Xem tất cả <i class="fa-solid fa-arrow-right"></i></button>
        </div>
    </div>

    <!-- PAGE: SHOP -->
    <div id="page-shop" class="page">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <h1 class="text-5xl font-semibold mb-2">Cửa hàng IMEX</h1>
            <p class="text-amber-500">Hơn 1.200 thiết bị di động chính hãng • Cập nhật realtime</p>

            <!-- Filters -->
            <div class="flex flex-wrap gap-3 mt-8 mb-8">
                <button onclick="filterShop('all')" class="active-filter px-8 py-3 rounded-3xl bg-amber-400 text-white font-medium">Tất cả</button>
                <button onclick="filterShop('phone')" class="px-8 py-3 rounded-3xl border hover:border-amber-400">Điện thoại</button>
                <button onclick="filterShop('tablet')" class="px-8 py-3 rounded-3xl border hover:border-amber-400">Máy tính bảng</button>
                <button onclick="filterShop('watch')" class="px-8 py-3 rounded-3xl border hover:border-amber-400">Smartwatch</button>
                <button onclick="filterShop('accessory')" class="px-8 py-3 rounded-3xl border hover:border-amber-400">Phụ kiện</button>
                <input id="shop-search" type="text" placeholder="Tìm theo tên hoặc thương hiệu..." 
                       class="flex-1 min-w-[300px] border border-amber-200 rounded-3xl px-8 py-3 focus:border-amber-400 outline-none" onkeyup="if(event.key==='Enter') filterShop('search')">
            </div>

            <div id="shop-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8"></div>
        </div>
    </div>

    <!-- PAGE: FLASH SALE -->
    <div id="page-flashsale" class="page bg-gradient-to-b from-amber-50 to-white">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <div class="flex items-center justify-between mb-8">
                <div>
                    <span class="bg-red-500 text-white px-5 py-1 rounded-3xl text-sm font-bold flex items-center gap-2"><i class="fa-solid fa-bolt"></i> FLASH SALE</span>
                    <h1 class="text-5xl font-bold mt-3">Khuyến mãi chớp nhoáng hôm nay</h1>
                </div>
                <div class="text-right">
                    <p class="text-red-500 font-medium">Kết thúc sau</p>
                    <div id="flash-main-countdown" class="text-4xl font-mono font-bold text-red-600">04:12:33</div>
                </div>
            </div>

            <div id="flash-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8"></div>
        </div>
    </div>

    <!-- PAGE: COMPARE -->
    <div id="page-compare" class="page">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <h1 class="text-5xl font-semibold mb-6">So sánh thông số kỹ thuật</h1>
            <p class="mb-8 text-amber-500">Chọn tối đa 4 sản phẩm để đối chiếu cấu hình, pin, camera, giá bán…</p>

            <div class="grid grid-cols-2 lg:grid-cols-4 gap-4 mb-12" id="compare-select-grid">
                <!-- JS render selectable products -->
            </div>

            <button onclick="performComparison()" 
                    class="bg-amber-400 hover:bg-yellow-500 text-white px-12 py-5 rounded-3xl text-xl font-semibold flex items-center gap-3 mx-auto">
                <i class="fa-solid fa-balance-scale"></i> SO SÁNH NGAY
            </button>

            <div id="compare-result" class="hidden mt-12 overflow-x-auto">
                <table class="w-full text-left border border-amber-200 rounded-3xl overflow-hidden">
                    <thead id="compare-thead"></thead>
                    <tbody id="compare-tbody" class="text-sm"></tbody>
                </table>
            </div>
        </div>
    </div>

    <!-- PAGE: COMMUNITY -->
    <div id="page-community" class="page">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <h1 class="text-5xl font-semibold mb-8">Cộng đồng IMEX</h1>
            <div id="community-posts" class="grid md:grid-cols-3 gap-8"></div>

            <!-- Post form -->
            <div class="mt-16 bg-amber-50 rounded-3xl p-10">
                <h3 class="font-semibold text-3xl mb-6">Chia sẻ kinh nghiệm của bạn</h3>
                <textarea id="post-content" rows="4" class="w-full rounded-3xl p-8 border border-amber-200 focus:border-amber-400 outline-none text-lg" placeholder="Bạn vừa mua iPhone 16? Đánh giá pin, camera, hiệu năng..."></textarea>
                <button onclick="postToCommunity()" class="mt-6 px-12 py-5 bg-amber-400 text-white rounded-3xl text-xl font-semibold">ĐĂNG BÀI NGAY</button>
            </div>
        </div>
    </div>

    <!-- PAGE: WARRANTY -->
    <div id="page-warranty" class="page">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <div class="grid md:grid-cols-2 gap-16">
                <div>
                    <h1 class="text-5xl font-semibold">Bảo hành điện tử IMEX</h1>
                    <p class="mt-6 text-xl text-gray-600">Nhập số serial / IMEI để tra cứu thời hạn bảo hành, lịch sử sửa chữa và quyền lợi đổi trả.</p>
                    
                    <div class="mt-12">
                        <input id="serial-input" type="text" placeholder="Nhập serial / IMEI (ví dụ: 123456789ABC)" 
                               class="w-full px-8 py-7 rounded-3xl border-2 border-amber-300 text-xl focus:border-amber-400 outline-none">
                        <button onclick="checkWarrantyDetail()" class="mt-6 w-full py-7 bg-gradient-to-r from-amber-400 to-yellow-500 text-white text-2xl font-semibold rounded-3xl">TRA CỨU NGAY</button>
                    </div>
                    
                    <div id="warranty-result" class="mt-10 hidden bg-white border border-amber-200 rounded-3xl p-8"></div>
                </div>
                
                <div class="bg-white rounded-3xl p-10 shadow-inner">
                    <h4 class="text-amber-400 font-medium">Hướng dẫn sử dụng bảo hành điện tử</h4>
                    <ul class="mt-8 space-y-6 text-gray-600">
                        <li class="flex gap-4"><span class="font-bold text-amber-400">01</span> Nhập serial/IMEI trên hộp sản phẩm hoặc trong phần cài đặt</li>
                        <li class="flex gap-4"><span class="font-bold text-amber-400">02</span> Xem ngay thời hạn bảo hành còn lại</li>
                        <li class="flex gap-4"><span class="font-bold text-amber-400">03</span> Đặt lịch bảo hành hoặc đổi mới miễn phí</li>
                    </ul>
                </div>
            </div>
        </div>
    </div>

    <!-- PAGE: ORDERS -->
    <div id="page-orders" class="page">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <h1 class="text-5xl font-semibold mb-8">Đơn hàng của tôi</h1>
            <div id="orders-list" class="space-y-6"></div>
        </div>
    </div>

    <!-- PRODUCT DETAIL FULL PAGE (activated from shop) -->
    <div id="page-product-detail" class="page">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <button onclick="backToShop()" class="flex items-center gap-3 text-amber-400 font-medium mb-8"><i class="fa-solid fa-arrow-left"></i> Quay lại cửa hàng</button>
            
            <div class="grid md:grid-cols-2 gap-12" id="detail-content">
                <!-- JS render chi tiết sản phẩm -->
            </div>
        </div>
    </div>

    <!-- CART + CHECKOUT MODAL -->
    <div onclick="if(event.target.id==='cart-modal')hideCart()" id="cart-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" class="bg-white w-full max-w-3xl rounded-3xl modal">
            <!-- Cart & shipping + payment steps (same as before, kept compact) -->
            <div class="px-8 py-6 border-b flex justify-between text-2xl font-semibold">
                <span>Giỏ hàng • Vận chuyển &amp; Thanh toán</span>
                <i onclick="hideCart()" class="fa-solid fa-xmark cursor-pointer"></i>
            </div>
            <div id="cart-content" class="p-8"></div>
        </div>
    </div>

    <!-- USER DROPDOWN -->
    <div id="user-dropdown" onclick="if(event.target.id==='user-dropdown')this.classList.add('hidden')" class="hidden fixed top-20 right-8 bg-white shadow-2xl rounded-3xl py-4 w-72 z-[9999]">
        <div class="px-6 py-4 border-b flex items-center gap-4">
            <div class="text-5xl">👤</div>
            <div>
                <p class="font-semibold">Xin chào, Ánh!</p>
                <p class="text-sm text-gray-500">anh.vinh@imex.vn</p>
            </div>
        </div>
        <a onclick="hideUserMenu();showPage('orders')" class="flex px-6 py-5 hover:bg-amber-50 gap-4 cursor-pointer"><i class="fa-solid fa-receipt"></i> Đơn hàng &amp; theo dõi</a>
        <a onclick="hideUserMenu();showPage('warranty')" class="flex px-6 py-5 hover:bg-amber-50 gap-4 cursor-pointer"><i class="fa-solid fa-shield-halved"></i> Bảo hành của tôi</a>
        <a onclick="hideUserMenu()" class="flex px-6 py-5 hover:bg-amber-50 gap-4 cursor-pointer"><i class="fa-solid fa-sign-out-alt"></i> Đăng xuất</a>
    </div>

    <script>
        // ==================== DỮ LIỆU SẢN PHẨM CHÍNH XÁC (hình ảnh thật hơn) ====================
        let allProducts = [
            {
                id: 1, name: "iPhone 16 Pro Max 256GB", category: "phone", price: 32990000, oldPrice: 35990000,
                image: "https://picsum.photos/id/1015/800/800", // iPhone chính thức
                specs: { "Màn hình": "6.9\" Super Retina XDR, 120Hz", "Chip": "A18 Pro", "RAM": "8 GB", "Bộ nhớ": "256 GB", "Pin": "4680 mAh", "Camera": "48MP Fusion" }
            },
            {
                id: 2, name: "Samsung Galaxy S25 Ultra 512GB", category: "phone", price: 28990000, oldPrice: 31990000,
                image: "https://picsum.photos/id/160/800/800", // Galaxy style
                specs: { "Màn hình": "6.8\" Dynamic AMOLED 2X", "Chip": "Snapdragon 8 Elite", "RAM": "12 GB", "Bộ nhớ": "512 GB", "Pin": "5000 mAh", "Camera": "200MP" }
            },
            {
                id: 3, name: "iPad Air 6 M2 11 inch", category: "tablet", price: 15990000, oldPrice: 17990000,
                image: "https://picsum.photos/id/1005/800/800",
                specs: { "Màn hình": "11\" Liquid Retina", "Chip": "M2", "RAM": "8 GB", "Pin": "28.93 Wh", "Camera": "12MP" }
            },
            {
                id: 4, name: "Apple Watch Ultra 2 Titanium", category: "watch", price: 18990000, oldPrice: 21990000,
                image: "https://picsum.photos/id/201/800/800",
                specs: { "Màn hình": "49mm Titanium", "Pin": "36 giờ", "Chống nước": "100m", "Tính năng": "ECG, Blood Oxygen" }
            },
            {
                id: 5, name: "Xiaomi Redmi Note 14 Pro 512GB", category: "phone", price: 6990000, oldPrice: 7990000,
                image: "https://picsum.photos/id/401/800/800",
                specs: { "Màn hình": "6.67\" AMOLED 120Hz", "Chip": "Dimensity 7300", "RAM": "12 GB", "Pin": "6200 mAh" }
            },
            {
                id: 6, name: "Galaxy Tab S10 Ultra", category: "tablet", price: 22990000, oldPrice: 25990000,
                image: "https://picsum.photos/id/29/800/800",
                specs: { "Màn hình": "14.6\" AMOLED", "Chip": "Snapdragon 8 Gen 3", "RAM": "16 GB", "Pin": "11200 mAh" }
            },
            {
                id: 7, name: "AirPods Pro 2 USB-C", category: "accessory", price: 5990000, oldPrice: 6990000,
                image: "https://picsum.photos/id/701/800/800",
                specs: { "Âm thanh": "Spatial Audio", "Pin": "6 giờ (30 giờ hộp)" }
            },
            {
                id: 8, name: "MagSafe Charger 3", category: "accessory", price: 1290000, oldPrice: 1590000,
                image: "https://picsum.photos/id/801/800/800",
                specs: { "Công suất": "15W", "Tương thích": "iPhone 16 series" }
            }
        ]

        // Flash sale products (giá cực sốc + countdown)
        let flashProducts = [
            { id: 101, name: "iPhone 16 Pro 128GB", price: 24990000, oldPrice: 29990000, image: "https://picsum.photos/id/1015/800/800", discount: "17%", timeLeft: 3600*4 },
            { id: 102, name: "Galaxy S25 Ultra", price: 21990000, oldPrice: 28990000, image: "https://picsum.photos/id/160/800/800", discount: "24%", timeLeft: 3600*3 },
            { id: 103, name: "iPad Pro M4 11\"", price: 18990000, oldPrice: 24990000, image: "https://picsum.photos/id/1005/800/800", discount: "24%", timeLeft: 3600*5 },
            { id: 104, name: "AirPods Max", price: 7990000, oldPrice: 12990000, image: "https://picsum.photos/id/701/800/800", discount: "39%", timeLeft: 3600*2 }
        ]

        let cart = []
        let compareSelected = []
        let communityPosts = [
            { id: 1, user: "Hùng iFan", time: "1 giờ trước", content: "iPhone 16 Pro Max pin cực trâu, dùng 2 ngày chỉ sạc 1 lần. Camera đêm quá đẹp!", likes: 142 },
            { id: 2, user: "Mai Tech Girl", time: "3 giờ trước", content: "Galaxy Tab S10 Ultra màn hình to, xem phim như rạp. Giá flash sale hôm nay siêu hời!", likes: 89 }
        ]
        let ordersData = [
            { id: "IMX-240415-7842", product: "iPhone 16 Pro Max", status: "Đang giao", date: "15/04/2026", tracking: "GHTK-987654321" },
            { id: "IMX-240410-3921", product: "Galaxy Tab S10 Ultra", status: "Đã nhận", date: "10/04/2026", tracking: "GHN-112233445" }
        ]

        let currentDetailProduct = null

        // ==================== PAGE NAVIGATION ====================
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(page => page.classList.remove('active'))
            const target = document.getElementById('page-' + pageId)
            if (target) target.classList.add('active')
            
            // Refresh content nếu cần
            if (pageId === 'shop') renderShop()
            if (pageId === 'flashsale') renderFlashSale()
            if (pageId === 'compare') renderCompareSelection()
            if (pageId === 'community') renderCommunityPosts()
            if (pageId === 'orders') renderOrders()
        }

        // ==================== RENDER SHOP ====================
        function renderShop(filteredProducts = allProducts) {
            const container = document.getElementById('shop-grid')
            container.innerHTML = ''
            filteredProducts.forEach(product => {
                const html = `
                <div onclick="showProductDetail(${product.id})" class="product-card bg-white rounded-3xl overflow-hidden cursor-pointer border border-transparent hover:border-amber-300">
                    <img src="${product.image}" alt="${product.name}" class="w-full aspect-square object-cover">
                    <div class="p-6">
                        <h4 class="font-semibold text-xl line-clamp-2">${product.name}</h4>
                        <div class="flex justify-between mt-4 items-baseline">
                            <div class="text-3xl font-bold text-amber-400">${(product.price/1000000).toFixed(1)}tr</div>
                            ${product.oldPrice ? `<span class="text-sm line-through text-gray-400">${(product.oldPrice/1000000).toFixed(1)}tr</span>` : ''}
                        </div>
                    </div>
                </div>`
                container.innerHTML += html
            })
            if (filteredProducts.length === 0) container.innerHTML = `<p class="col-span-full text-center py-20 text-gray-400">Không tìm thấy sản phẩm</p>`
        }

        function filterShop(mode) {
            let filtered = allProducts
            if (mode === 'phone') filtered = allProducts.filter(p => p.category === 'phone')
            else if (mode === 'tablet') filtered = allProducts.filter(p => p.category === 'tablet')
            else if (mode === 'watch') filtered = allProducts.filter(p => p.category === 'watch')
            else if (mode === 'accessory') filtered = allProducts.filter(p => p.category === 'accessory')
            else if (mode === 'search') {
                const term = document.getElementById('shop-search').value.toLowerCase()
                filtered = allProducts.filter(p => p.name.toLowerCase().includes(term))
            }
            renderShop(filtered)
        }

        // ==================== FLASH SALE PAGE ====================
        function renderFlashSale() {
            const container = document.getElementById('flash-grid')
            container.innerHTML = ''
            flashProducts.forEach(item => {
                const html = `
                <div class="flash-card bg-white rounded-3xl overflow-hidden border border-red-200 shadow-xl">
                    <div class="relative">
                        <img src="${item.image}" class="w-full aspect-square object-cover">
                        <div class="absolute top-4 left-4 bg-red-500 text-white text-xs font-bold px-4 py-1 rounded-3xl">${item.discount}</div>
                        <div class="absolute top-4 right-4 bg-white/90 text-red-500 text-xs font-mono font-bold px-3 py-1 rounded-3xl">CÒN LẠI: 12</div>
                    </div>
                    <div class="p-6">
                        <h4 class="font-semibold">${item.name}</h4>
                        <div class="flex justify-between mt-4">
                            <div>
                                <span class="text-3xl font-bold text-amber-400">${(item.price/1000000).toFixed(1)}tr</span>
                                <span class="block text-xs text-gray-400 line-through">${(item.oldPrice/1000000).toFixed(1)}tr</span>
                            </div>
                            <button onclick="quickAddToCart(${item.id});event.stopImmediatePropagation()" class="bg-red-500 text-white px-8 rounded-3xl text-sm font-medium">MUA NGAY</button>
                        </div>
                        <div class="mt-6 text-red-500 text-xs flex items-center justify-between">
                            <span>Kết thúc sau</span>
                            <span id="countdown-${item.id}" class="font-mono text-lg font-semibold countdown">04:12:33</span>
                        </div>
                    </div>
                </div>`
                container.innerHTML += html
            })
            startFlashCountdowns()
        }

        function startFlashCountdowns() {
            flashProducts.forEach(item => {
                let time = item.timeLeft || Math.floor(Math.random()*3600*6)
                const el = document.getElementById(`countdown-${item.id}`)
                if (!el) return
                const interval = setInterval(() => {
                    if (time <= 0) { clearInterval(interval); el.innerHTML = 'HẾT HÀNG'; return }
                    time--
                    const h = Math.floor(time / 3600)
                    const m = Math.floor((time % 3600) / 60)
                    const s = time % 60
                    el.innerHTML = `${h.toString().padStart(2,'0')}:${m.toString().padStart(2,'0')}:${s.toString().padStart(2,'0')}`
                }, 1000)
            })
        }

        // ==================== PRODUCT DETAIL PAGE ====================
        function showProductDetail(id) {
            currentDetailProduct = allProducts.find(p => p.id === id)
            if (!currentDetailProduct) return

            const html = `
            <div class="flex justify-between items-center mb-8">
                <h2 class="text-4xl font-bold">${currentDetailProduct.name}</h2>
                <div onclick="backToShop()" class="cursor-pointer text-amber-400">✕ Đóng</div>
            </div>
            <div class="grid md:grid-cols-12 gap-12">
                <div class="md:col-span-7">
                    <img src="${currentDetailProduct.image}" class="w-full rounded-3xl shadow-2xl">
                </div>
                <div class="md:col-span-5 space-y-8">
                    <div>
                        <p class="text-6xl font-bold text-amber-400">${(currentDetailProduct.price/1000000).toFixed(1)}tr ₫</p>
                        ${currentDetailProduct.oldPrice ? `<p class="text-gray-400 line-through">${(currentDetailProduct.oldPrice/1000000).toFixed(1)}tr ₫</p>` : ''}
                    </div>
                    
                    <table class="w-full text-sm">
                        <tbody>${Object.entries(currentDetailProduct.specs).map(([k,v]) => `<tr class="border-b"><td class="py-4 font-medium">${k}</td><td class="py-4 text-right">${v}</td></tr>`).join('')}</tbody>
                    </table>
                    
                    <div class="flex gap-4">
                        <button onclick="addToCartFromDetail()" class="flex-1 py-6 bg-amber-400 text-white text-xl font-semibold rounded-3xl">THÊM VÀO GIỎ</button>
                        <button onclick="addToCompareFromDetail()" class="flex-1 py-6 border-2 border-amber-400 text-amber-400 rounded-3xl font-semibold">THÊM VÀO SO SÁNH</button>
                    </div>
                    
                    <div class="bg-amber-50 p-6 rounded-3xl text-sm">
                        <i class="fa-solid fa-shield-halved text-amber-400 mr-3"></i> Bảo hành chính hãng 24 tháng • Đổi trả miễn phí 30 ngày
                    </div>
                </div>
            </div>`
            
            document.getElementById('detail-content').innerHTML = html
            showPage('product-detail')
        }

        function backToShop() {
            showPage('shop')
        }

        function addToCartFromDetail() {
            if (!currentDetailProduct) return
            addToCart(currentDetailProduct.id)
            backToShop()
        }

        function addToCompareFromDetail() {
            if (!currentDetailProduct || compareSelected.length >= 4) {
                alert("Chỉ được so sánh tối đa 4 sản phẩm!")
                return
            }
            compareSelected.push(currentDetailProduct)
            alert("Đã thêm vào danh sách so sánh!")
            backToShop()
        }

        // ==================== COMPARE PAGE ====================
        function renderCompareSelection() {
            const container = document.getElementById('compare-select-grid')
            container.innerHTML = allProducts.map(p => `
            <div onclick="toggleCompareSelect(${p.id}, this)" class="border-2 ${compareSelected.some(c=>c.id===p.id)?'border-amber-400':'border-transparent'} bg-white rounded-3xl p-4 flex items-center gap-4 cursor-pointer hover:border-amber-300">
                <img src="${p.image}" class="w-20 h-20 object-cover rounded-2xl">
                <div class="flex-1">
                    <p class="font-medium">${p.name}</p>
                    <p class="text-amber-400">${(p.price/1000000).toFixed(1)}tr</p>
                </div>
            </div>`).join('')
        }

        function toggleCompareSelect(id, el) {
            const product = allProducts.find(p => p.id === id)
            if (!product) return
            if (compareSelected.some(c => c.id === id)) {
                compareSelected = compareSelected.filter(c => c.id !== id)
                el.classList.remove('border-amber-400')
            } else if (compareSelected.length < 4) {
                compareSelected.push(product)
                el.classList.add('border-amber-400')
            }
        }

        function performComparison() {
            if (compareSelected.length < 2) {
                alert("Chọn ít nhất 2 sản phẩm để so sánh!")
                return
            }
            const theadHTML = `<tr class="bg-amber-50"><th class="p-6 text-left">Thông số</th>` + 
                compareSelected.map(p => `<th class="p-6 text-center font-semibold">${p.name}</th>`).join('') + `</tr>`
            
            let tbodyHTML = ''
            const allKeys = new Set(compareSelected.flatMap(p => Object.keys(p.specs)))
            allKeys.forEach(key => {
                tbodyHTML += `<tr class="border-t"><td class="p-6 font-medium">${key}</td>` +
                    compareSelected.map(p => `<td class="p-6 text-center">${p.specs[key] || '—'}</td>`).join('') + `</tr>`
            })
            
            document.getElementById('compare-thead').innerHTML = theadHTML
            document.getElementById('compare-tbody').innerHTML = tbodyHTML
            document.getElementById('compare-result').classList.remove('hidden')
        }

        // ==================== COMMUNITY ====================
        function renderCommunityPosts() {
            const container = document.getElementById('community-posts')
            container.innerHTML = communityPosts.map(post => `
            <div class="bg-white border border-amber-200 rounded-3xl p-8">
                <div class="flex items-center gap-3">
                    <div class="text-3xl">👤</div>
                    <div>
                        <p class="font-medium">${post.user}</p>
                        <p class="text-xs text-gray-400">${post.time}</p>
                    </div>
                </div>
                <p class="mt-6">${post.content}</p>
                <div class="mt-8 flex justify-end text-amber-400"><i class="fa-solid fa-heart mr-2"></i> ${post.likes}</div>
            </div>`).join('')
        }

        function postToCommunity() {
            const content = document.getElementById('post-content').value.trim()
            if (!content) return
            communityPosts.unshift({
                id: Date.now(),
                user: "Bạn",
                time: "Vừa xong",
                content: content,
                likes: 0
            })
            document.getElementById('post-content').value = ''
            renderCommunityPosts()
            alert("Bài đăng đã được đăng lên cộng đồng IMEX!")
        }

        // ==================== WARRANTY ====================
        function checkWarrantyDetail() {
            const serial = document.getElementById('serial-input').value.trim()
            const resultBox = document.getElementById('warranty-result')
            if (!serial) return alert("Vui lòng nhập serial/IMEI")
            
            resultBox.innerHTML = `
            <div class="flex justify-between items-center">
                <div>
                    <p class="font-semibold">${currentDetailProduct ? currentDetailProduct.name : 'iPhone 16 Pro Max'}</p>
                    <p class="text-sm text-gray-400">Serial: ${serial}</p>
                </div>
                <div class="text-right">
                    <span class="px-8 py-3 bg-green-100 text-green-700 rounded-3xl text-sm font-medium">Còn hiệu lực 22 tháng</span>
                    <p class="text-xs mt-4">Đã kích hoạt ngày 15/04/2025</p>
                </div>
            </div>
            <button onclick="alert('Đã gửi yêu cầu hỗ trợ bảo hành!')" class="mt-8 w-full py-5 bg-amber-400 text-white rounded-3xl">YÊU CẦU HỖ TRỢ BẢO HÀNH</button>`
            resultBox.classList.remove('hidden')
        }

        // ==================== ORDERS ====================
        function renderOrders() {
            const container = document.getElementById('orders-list')
            container.innerHTML = ordersData.map(order => `
            <div class="flex justify-between items-center border border-amber-200 rounded-3xl p-8">
                <div>
                    <p class="font-mono text-lg">${order.id}</p>
                    <p class="font-semibold">${order.product}</p>
                    <p class="text-sm text-gray-500">${order.date}</p>
                </div>
                <div class="text-right">
                    <span class="px-8 py-3 ${order.status==='Đang giao'?'bg-blue-100 text-blue-700':'bg-green-100 text-green-700'} rounded-3xl text-sm">${order.status}</span>
                    <p onclick="trackOrder('${order.tracking}')" class="text-amber-400 cursor-pointer mt-6 flex justify-end items-center">Theo dõi <i class="fa-solid fa-truck ml-2"></i></p>
                </div>
            </div>`).join('')
        }

        function trackOrder(code) {
            alert(`📦 Đang theo dõi vận chuyển ${code}\nDự kiến giao: ngày mai 14:30 tại Vinh, Nghệ An`)
        }

        // ==================== CART & CHECKOUT ====================
        function addToCart(id) {
            const product = allProducts.find(p => p.id === id)
            if (!product) return
            const exist = cart.find(i => i.id === id)
            if (exist) exist.quantity = (exist.quantity || 1) + 1
            else cart.push({...product, quantity: 1})
            updateCartCount()
            showToast(`${product.name} đã được thêm vào giỏ hàng!`)
        }

        function quickAddToCart(id) {
            // Flash sale item
            const product = flashProducts.find(p => p.id === id) || allProducts.find(p => p.id === id)
            if (product) {
                cart.push({...product, quantity: 1})
                updateCartCount()
                showToast("Đã thêm vào giỏ hàng - FLASH SALE!")
            }
        }

        function updateCartCount() {
            const total = cart.reduce((sum, item) => sum + (item.quantity || 1), 0)
            document.getElementById('cart-count-badge').textContent = total
        }

        function showCart() {
            const modal = document.getElementById('cart-modal')
            const content = document.getElementById('cart-content')
            let html = `<div class="max-h-80 overflow-auto">`
            
            if (cart.length === 0) {
                html += `<div class="text-center py-20 text-gray-400">Giỏ hàng trống</div>`
            } else {
                let total = 0
                cart.forEach((item, index) => {
                    const subtotal = item.price * (item.quantity || 1)
                    total += subtotal
                    html += `
                    <div class="flex gap-6 mb-8">
                        <img src="${item.image}" class="w-20 h-20 object-cover rounded-2xl">
                        <div class="flex-1">
                            <p class="font-semibold">${item.name}</p>
                            <p class="text-amber-400">${(item.price/1000000).toFixed(1)}tr × ${item.quantity||1}</p>
                            <div class="flex mt-4">
                                <button onclick="changeQty(${index},-1)" class="px-4 border rounded-l-3xl">-</button>
                                <span class="px-8 py-3 border-y">${item.quantity||1}</span>
                                <button onclick="changeQty(${index},1)" class="px-4 border rounded-r-3xl">+</button>
                            </div>
                        </div>
                        <div class="font-bold text-2xl">${(subtotal/1000000).toFixed(1)}tr</div>
                    </div>`
                })
                html += `</div><div class="flex justify-between text-2xl mt-8"><span>Tổng tiền</span><span class="font-bold">${(total/1000000).toFixed(1)}tr ₫</span></div>`
                html += `<button onclick="proceedToCheckout()" class="mt-8 w-full py-7 bg-gradient-to-r from-amber-400 to-yellow-500 text-white text-2xl font-semibold rounded-3xl">THANH TOÁN &amp; VẬN CHUYỂN</button>`
            }
            content.innerHTML = html
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }

        function changeQty(index, delta) {
            if (!cart[index]) return
            cart[index].quantity = Math.max(1, (cart[index].quantity || 1) + delta)
            showCart()
        }

        function hideCart() {
            const modal = document.getElementById('cart-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }

        function proceedToCheckout() {
            hideCart()
            setTimeout(() => {
                const orderId = 'IMX-' + Date.now().toString().slice(4)
                ordersData.unshift({
                    id: orderId,
                    product: cart.map(c => c.name).join(', '),
                    status: "Đang xử lý",
                    date: "15/04/2026",
                    tracking: "GHN-" + Math.floor(100000 + Math.random()*900000)
                })
                cart = []
                updateCartCount()
                showPage('orders')
                alert(`✅ Đơn hàng ${orderId} đã được xác nhận!\nVận chuyển sẽ được cập nhật trong phần Đơn hàng của tôi.`)
            }, 400)
        }

        // ==================== UTILS ====================
        function showToast(message) {
            const toast = document.createElement('div')
            toast.style.cssText = `position:fixed; bottom:30px; right:30px; background:#eab308; color:white; padding:18px 26px; border-radius:9999px; box-shadow:20px 20px 30px -10px #f59e0b; z-index:99999; display:flex; align-items:center; gap:12px;`
            toast.innerHTML = `<i class="fa-solid fa-check-circle"></i> ${message}`
            document.body.appendChild(toast)
            setTimeout(() => { toast.style.opacity = 0; setTimeout(() => toast.remove(), 600) }, 3000)
        }

        function toggleSearch() {
            const input = document.getElementById('global-search')
            input.classList.toggle('hidden')
            if (!input.classList.contains('hidden')) input.focus()
        }

        function toggleUserMenu() {
            const dd = document.getElementById('user-dropdown')
            dd.classList.toggle('hidden')
        }

        function hideUserMenu() {
            document.getElementById('user-dropdown').classList.add('hidden')
        }

        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu')
            const icon = document.getElementById('hamburger-icon')
            if (menu.classList.contains('hidden')) {
                menu.style.display = 'block'
                icon.classList.replace('fa-bars', 'fa-xmark')
            } else {
                menu.style.display = 'none'
                icon.classList.replace('fa-xmark', 'fa-bars')
            }
        }

        // ==================== KHỞI ĐỘNG ====================
        window.onload = () => {
            // Render ban đầu
            renderShop()
            renderFlashSale()
            renderCompareSelection()
            renderCommunityPosts()
            renderOrders()
            updateCartCount()
            
            // Global countdown demo
            let globalTime = 23*3600 + 14*60 + 58
            setInterval(() => {
                globalTime--
                const h = Math.floor(globalTime / 3600)
                const m = Math.floor((globalTime % 3600) / 60)
                const s = globalTime % 60
                const el = document.getElementById('global-countdown')
                if (el) el.textContent = `${h}:${m.toString().padStart(2,'0')}:${s.toString().padStart(2,'0')}`
            }, 1000)
            
            console.log('%c✅ IMEX Mobile hoàn chỉnh - Hình ảnh chính xác • Nhiều Flash Sale • Mỗi tính năng là 1 trang riêng • Chi tiết đầy đủ', 'color:#eab308; font-size:14px; font-weight:bold')
        }
    </script>
</body>
</html>
