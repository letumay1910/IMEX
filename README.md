<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động. So sánh chi tiết thông số kỹ thuật.">
    <title>IMEX - Thiết Bị Di Động Chính Hãng</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Roboto:wght@400;500;700&amp;display=swap');
        
        :root { --primary: #eab308; }
        
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
        
        .compare-table td.best { background-color: #fefce8; font-weight: 600; position: relative; }
        .compare-table td.best::after { content: '★'; position: absolute; top: 8px; right: 8px; color: #eab308; font-size: 18px; }
        
        .modal { animation: modalPop 0.3s ease-out; }
        @keyframes modalPop { 0% { opacity: 0; transform: scale(0.95); } 100% { opacity: 1; transform: scale(1); } }
    </style>
</head>
<body class="tailwind-ready bg-white">

    <!-- NAVBAR -->
    <nav class="bg-white border-b-4 border-amber-400 sticky top-0 z-50 shadow-xl">
        <div class="max-w-7xl mx-auto px-6">
            <div class="py-5 flex items-center justify-between">
                <div onclick="showPage('home')" class="flex items-center gap-x-3 cursor-pointer">
                    <div class="w-11 h-11 bg-gradient-to-br from-amber-400 to-yellow-500 rounded-3xl flex items-center justify-center text-white text-4xl">📱</div>
                    <h1 class="logo-font text-4xl font-bold tracking-[-2px] text-amber-400">IMEX</h1>
                    <span class="text-amber-600 font-semibold text-lg mt-1 tracking-widest">MOBILE</span>
                </div>

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
                    <div onclick="toggleSearch()" class="cursor-pointer">
                        <div class="flex items-center bg-amber-50 hover:bg-amber-100 border border-amber-200 rounded-3xl px-6 py-3 text-sm font-medium gap-x-3">
                            <i class="fa-solid fa-magnifying-glass text-amber-400"></i>
                            <input id="global-search" type="text" placeholder="Tìm sản phẩm..." class="bg-transparent outline-none w-64 hidden md:block placeholder:text-amber-400/70">
                        </div>
                    </div>

                    <div onclick="showCart()" class="relative cursor-pointer">
                        <i class="fa-solid fa-shopping-cart text-3xl text-gray-700"></i>
                        <span id="cart-count-badge" class="absolute -top-1 -right-1 bg-red-500 text-white text-xs font-bold w-6 h-6 rounded-2xl flex items-center justify-center">0</span>
                    </div>

                    <div onclick="toggleUserMenu()" class="flex items-center cursor-pointer">
                        <div class="w-9 h-9 bg-amber-100 text-amber-400 rounded-2xl flex items-center justify-center text-2xl">👤</div>
                    </div>

                    <button onclick="toggleMobileMenu()" class="md:hidden text-4xl text-amber-400">
                        <i id="hamburger-icon" class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <div id="mobile-menu" class="hidden md:hidden bg-white border-t px-6 py-8">
            <div class="flex flex-col gap-y-6 text-lg font-medium">
                <a onclick="showPage('home');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-house"></i> Trang chủ</a>
                <a onclick="showPage('shop');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-store"></i> Cửa hàng</a>
                <a onclick="showPage('flashsale');toggleMobileMenu()" class="flex items-center gap-4 text-red-600"><i class="fa-solid fa-bolt"></i> FLASH SALE</a>
                <a onclick="showPage('compare');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-balance-scale"></i> So sánh chi tiết</a>
                <a onclick="showPage('community');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-users"></i> Cộng đồng</a>
                <a onclick="showPage('warranty');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-shield-halved"></i> Bảo hành</a>
                <a onclick="showPage('orders');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-receipt"></i> Đơn hàng</a>
            </div>
        </div>
    </nav>

    <!-- PAGE: COMPARE - ĐÃ CHI TIẾT HÓA -->
    <div id="page-compare" class="page">
        <div class="max-w-7xl mx-auto px-6 py-12">
            <div class="flex items-center justify-between mb-6">
                <div>
                    <h1 class="text-5xl font-semibold">So sánh thông số kỹ thuật</h1>
                    <p class="text-amber-500 text-xl mt-2">Chọn tối đa 4 thiết bị • So sánh chi tiết 30+ thông số • Tự động highlight giá trị tốt nhất</p>
                </div>
                <div class="text-sm bg-amber-100 text-amber-400 px-6 py-3 rounded-3xl flex items-center gap-3">
                    <i class="fa-solid fa-info-circle"></i>
                    <span>Bạn đã chọn <strong id="selected-count">0</strong>/4 sản phẩm</span>
                </div>
            </div>

            <!-- Danh sách chọn sản phẩm -->
            <div class="mb-12">
                <h3 class="font-medium text-lg mb-4 flex items-center gap-2">
                    <i class="fa-solid fa-list-check"></i> 
                    Chọn sản phẩm để so sánh
                </h3>
                <div id="compare-select-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-6"></div>
            </div>

            <!-- Nút so sánh -->
            <div class="flex justify-center mb-16">
                <button onclick="performDetailedComparison()" 
                        class="bg-amber-400 hover:bg-yellow-500 text-white px-14 py-6 rounded-3xl text-2xl font-semibold flex items-center gap-4 shadow-xl">
                    <i class="fa-solid fa-balance-scale"></i>
                    SO SÁNH CHI TIẾT NGAY
                </button>
            </div>

            <!-- K
