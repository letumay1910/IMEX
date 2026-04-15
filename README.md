<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động. Mua sắm điện thoại, máy tính bảng, phụ kiện chính hãng với giá tốt nhất.">
    <title>IMEX - Thiết Bị Di Động Chuyên Nghiệp</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Roboto:wght@400;500;700&amp;display=swap');
        
        :root {
            --tw-color-primary: #dc2626;
        }
        
        * {
            transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
            transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
            transition-duration: 150ms;
        }
        
        .tailwind-ready {
            font-family: 'Inter', system_ui, sans-serif;
        }
        
        .logo-font {
            font-family: 'Roboto', sans-serif;
        }

        .hero-bg {
            background: linear-gradient(92deg, #dc2626 0%, #b91c1c 100%);
        }
        
        .product-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: 25px 25px 0 -10px #dc2626;
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
            background-color: #dc2626;
        }
        
        .nav-link:hover:after {
            width: 100%;
        }
        
        .cart-count {
            animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
        }
        
        .section-header {
            position: relative;
        }
        
        .section-header:after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background: #dc2626;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 9999px;
        }
    </style>
</head>
<body class="tailwind-ready">
    <!-- NAVBAR -->
    <nav class="bg-white border-b-2 border-red-600 sticky top-0 z-50 shadow-lg">
        <div class="max-w-7xl mx-auto">
            <div class="px-6 py-5 flex items-center justify-between">
                
                <!-- Logo -->
                <div class="flex items-center gap-x-3">
                    <div class="w-10 h-10 bg-red-600 rounded-2xl flex items-center justify-center shadow-inner text-white text-3xl">
                        📱
                    </div>
                    <h1 class="logo-font text-3xl font-bold tracking-tighter text-red-600">IMEX</h1>
                    <span class="text-sm font-medium text-gray-500 tracking-[2px] mt-1">MOBILE</span>
                </div>

                <!-- Desktop Menu -->
                <div class="hidden md:flex items-center gap-x-8 text-base font-medium">
                    <a href="#home" onclick="navigateToSection('home')" class="nav-link text-gray-800 hover:text-red-600">Trang chủ</a>
                    <a href="#shop" onclick="navigateToSection('shop')" class="nav-link text-gray-800 hover:text-red-600">Cửa hàng</a>
                    <a href="#categories" onclick="navigateToSection('categories')" class="nav-link text-gray-800 hover:text-red-600">Danh mục</a>
                    <a href="#deals" onclick="navigateToSection('deals')" class="nav-link text-gray-800 hover:text-red-600">Khuyến mãi</a>
                    <a href="#about" onclick="navigateToSection('about')" class="nav-link text-gray-800 hover:text-red-600">Về IMEX</a>
                </div>

                <div class="flex items-center gap-x-4">
                    <!-- Search -->
                    <div onclick="toggleSearch()" class="relative cursor-pointer">
                        <div class="flex items-center bg-gray-100 hover:bg-gray-200 rounded-3xl px-5 py-2.5 text-sm font-medium gap-x-3">
                            <i class="fa-solid fa-magnifying-glass text-red-600"></i>
                            <input id="search-input" 
                                   type="text" 
                                   placeholder="Tìm điện thoại, phụ kiện..." 
                                   class="bg-transparent outline-none w-52 hidden md:block text-sm placeholder-gray-400">
                        </div>
                    </div>

                    <!-- Cart -->
                    <div onclick="showCart()" class="relative cursor-pointer flex items-center justify-center w-11 h-11 hover:bg-red-50 rounded-2xl">
                        <i class="fa-solid fa-shopping-cart text-2xl text-gray-700"></i>
                        <span id="cart-count-badge" 
                              class="cart-count absolute -top-1 -right-1 bg-red-600 text-white text-[10px] font-bold w-5 h-5 flex items-center justify-center rounded-full shadow">
                            0
                        </span>
                    </div>

                    <!-- User -->
                    <div onclick="showLoginModal()" class="flex items-center justify-center w-11 h-11 hover:bg-red-50 rounded-2xl cursor-pointer">
                        <i class="fa-solid fa-user text-2xl text-gray-700"></i>
                    </div>

                    <!-- Mobile Hamburger -->
                    <button onclick="toggleMobileMenu()" class="md:hidden w-11 h-11 flex items-center justify-center text-3xl text-red-600">
                        <i id="hamburger-icon" class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t px-6 py-6 shadow-xl">
            <div class="flex flex-col gap-y-6 text-lg font-medium">
                <a href="#home" onclick="navigateToSection('home');toggleMobileMenu()" class="flex items-center gap-x-3"><i class="fa-solid fa-house w-6"></i> Trang chủ</a>
                <a href="#shop" onclick="navigateToSection('shop');toggleMobileMenu()" class="flex items-center gap-x-3"><i class="fa-solid fa-store w-6"></i> Cửa hàng</a>
                <a href="#categories" onclick="navigateToSection('categories');toggleMobileMenu()" class="flex items-center gap-x-3"><i class="fa-solid fa-layer-group w-6"></i> Danh mục</a>
                <a href="#deals" onclick="navigateToSection('deals');toggleMobileMenu()" class="flex items-center gap-x-3"><i class="fa-solid fa-fire w-6"></i> Khuyến mãi HOT</a>
                <a href="#about" onclick="navigateToSection('about');toggleMobileMenu()" class="flex items-center gap-x-3"><i class="fa-solid fa-info-circle w-6"></i> Về IMEX</a>
                <div class="pt-6 border-t text-red-600 flex items-center justify-between">
                    <span class="font-medium">Hotline: 1900 636 636</span>
                    <span class="text-sm text-gray-500">24/7 hỗ trợ</span>
                </div>
            </div>
        </div>
    </nav>

    <!-- HERO SECTION -->
    <section id="home" class="hero-bg text-white min-h-screen flex items-center relative overflow-hidden">
        <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
            <!-- Left content -->
            <div class="space-y-8 pt-12 md:pt-0">
                <div class="inline-flex items-center bg-white/20 backdrop-blur-md text-white text-sm font-medium px-5 py-2 rounded-3xl gap-x-2">
                    <i class="fa-solid fa-medal"></i>
                    CHUYÊN THIẾT BỊ DI ĐỘNG CHÍNH HÃNG
                </div>
                
                <h1 class="text-6xl md:text-7xl font-bold leading-none tracking-tighter">
                    IMEX<br>
                    <span class="text-white/90">Thế giới di động</span><br>
                    trong tầm tay bạn
                </h1>
                
                <p class="text-2xl text-white/90 max-w-md">
                    Điện thoại • Máy tính bảng • Phụ kiện<br>
                    Giao hàng siêu tốc • Bảo hành 24 tháng
                </p>

                <div class="flex items-center gap-4">
                    <button onclick="navigateToSection('shop')" 
                            class="bg-white text-red-600 hover:bg-amber-100 px-8 py-5 rounded-3xl font-semibold text-xl flex items-center gap-x-3 shadow-2xl">
                        <i class="fa-solid fa-cart-shopping"></i>
                        MUA NGAY
                    </button>
                    
                    <button onclick="watchVideo()" 
                            class="border-2 border-white/80 hover:border-white text-white px-8 py-5 rounded-3xl font-semibold text-xl flex items-center gap-x-3">
                        <i class="fa-solid fa-play-circle"></i>
                        XEM VIDEO
                    </button>
                </div>

                <div class="flex items-center gap-x-8 text-sm">
                    <div class="flex -space-x-4">
                        <div class="w-8 h-8 bg-white rounded-2xl flex items-center justify-center text-red-600 text-xs font-bold ring-2 ring-red-600">✓</div>
                        <div class="w-8 h-8 bg-white rounded-2xl flex items-center justify-center text-red-600 text-xs font-bold ring-2 ring-red-600">✓</div>
                        <div class="w-8 h-8 bg-white rounded-2xl flex items-center justify-center text-red-600 text-xs font-bold ring-2 ring-red-600">✓</div>
                    </div>
                    <div>
                        <p class="font-medium">Hơn 50.000 khách hàng đã tin tưởng</p>
                        <p class="text-white/70 text-xs">Đánh giá 4.98/5 trên Shopee &amp; Tiki</p>
                    </div>
                </div>
            </div>

            <!-- Right visual -->
            <div class="relative hidden md:flex justify-center items-center">
                <div class="absolute w-96 h-96 bg-white/10 backdrop-blur-3xl rounded-[4rem] rotate-12 shadow-2xl"></div>
                <div class="relative z-10 bg-white text-red-600 rounded-3xl shadow-2xl p-4 rotate-[-8deg] w-72">
                    <div class="bg-black rounded-3xl p-3">
                        <img src="https://picsum.photos/id/1015/600/800" 
                             alt="iPhone 16 Pro" 
                             class="rounded-3xl w-full shadow-inner">
                    </div>
                    <div class="text-center mt-4">
                        <p class="font-bold text-2xl">iPhone 16 Pro Max</p>
                        <p class="text-red-600 text-lg">Chỉ từ 29.990.000 ₫</p>
                    </div>
                </div>
                
                <!-- Floating badges -->
                <div class="absolute -top-8 -left-8 bg-white text-red-600 text-sm font-bold px-6 py-3 rounded-3xl shadow-xl flex items-center gap-2">
                    <i class="fa-solid fa-truck"></i>
                    Giao hàng trong 2h
                </div>
                <div class="absolute -bottom-8 right-12 bg-white text-red-600 text-sm font-bold px-6 py-3 rounded-3xl shadow-xl flex items-center gap-2">
                    <i class="fa-solid fa-shield-halved"></i>
                    Bảo hành 24 tháng
                </div>
            </div>
        </div>

        <!-- Scroll indicator -->
        <div class="absolute bottom-10 left-1/2 hidden md:flex flex-col items-center text-white/70 text-xs tracking-widest">
            <div class="mb-2">KÉO XUỐNG</div>
            <i class="fa-solid fa-chevron-down animate-bounce text-2xl"></i>
        </div>
    </section>

    <!-- CATEGORIES -->
    <section id="categories" class="max-w-7xl mx-auto px-6 py-16">
        <div class="flex justify-between items-end mb-10">
            <div>
                <span class="px-4 py-1 bg-red-100 text-red-600 text-sm font-semibold rounded-full">DANH MỤC</span>
                <h2 class="section-header text-4xl font-semibold text-gray-900 mt-3">Chọn thiết bị của bạn</h2>
            </div>
            <a href="#shop" onclick="navigateToSection('shop')" class="text-red-600 font-medium flex items-center gap-x-2 hover:gap-x-4">
                Xem tất cả <i class="fa-solid fa-arrow-right"></i>
            </a>
        </div>

        <div class="grid grid-cols-2 md:grid-cols-4 gap-6">
            <!-- Category 1 -->
            <div onclick="filterCategory('phone')" 
                 class="bg-white border border-gray-100 rounded-3xl p-8 hover:border-red-600 group cursor-pointer">
                <div class="w-16 h-16 bg-red-100 text-red-600 rounded-2xl flex items-center justify-center text-4xl mb-6 group-hover:scale-110">📱</div>
                <h3 class="text-2xl font-semibold">Điện thoại</h3>
                <p class="text-gray-500 mt-1">iPhone, Samsung, Xiaomi...</p>
                <div class="mt-8 text-red-600 text-sm font-medium flex items-center">152 sản phẩm <i class="fa-solid fa-arrow-right ml-auto"></i></div>
            </div>
            
            <!-- Category 2 -->
            <div onclick="filterCategory('tablet')" 
                 class="bg-white border border-gray-100 rounded-3xl p-8 hover:border-red-600 group cursor-pointer">
                <div class="w-16 h-16 bg-red-100 text-red-600 rounded-2xl flex items-center justify-center text-4xl mb-6 group-hover:scale-110">📟</div>
                <h3 class="text-2xl font-semibold">Máy tính bảng</h3>
                <p class="text-gray-500 mt-1">iPad, Galaxy Tab, Lenovo...</p>
                <div class="mt-8 text-red-600 text-sm font-medium flex items-center">89 sản phẩm <i class="fa-solid fa-arrow-right ml-auto"></i></div>
            </div>
            
            <!-- Category 3 -->
            <div onclick="filterCategory('accessory')" 
                 class="bg-white border border-gray-100 rounded-3xl p-8 hover:border-red-600 group cursor-pointer">
                <div class="w-16 h-16 bg-red-100 text-red-600 rounded-2xl flex items-center justify-center text-4xl mb-6 group-hover:scale-110">🔌</div>
                <h3 class="text-2xl font-semibold">Phụ kiện</h3>
                <p class="text-gray-500 mt-1">Ốp lưng, sạc, tai nghe...</p>
                <div class="mt-8 text-red-600 text-sm font-medium flex items-center">324 sản phẩm <i class="fa-solid fa-arrow-right ml-auto"></i></div>
            </div>
            
            <!-- Category 4 -->
            <div onclick="filterCategory('watch')" 
                 class="bg-white border border-gray-100 rounded-3xl p-8 hover:border-red-600 group cursor-pointer">
                <div class="w-16 h-16 bg-red-100 text-red-600 rounded-2xl flex items-center justify-center text-4xl mb-6 group-hover:scale-110">⌚</div>
                <h3 class="text-2xl font-semibold">Đồng hồ thông minh</h3>
                <p class="text-gray-500 mt-1">Apple Watch, Galaxy Watch...</p>
                <div class="mt-8 text-red-600 text-sm font-medium flex items-center">67 sản phẩm <i class="fa-solid fa-arrow-right ml-auto"></i></div>
            </div>
        </div>
    </section>

    <!-- SHOP - SẢN PHẨM NỔI BẬT -->
    <section id="shop" class="bg-gray-50 py-16">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex justify-between items-baseline mb-10">
                <h2 class="section-header text-4xl font-semibold text-gray-900">Sản phẩm nổi bật</h2>
                <div class="flex gap-x-2 text-sm">
                    <button onclick="filterAll()" 
                            class="active-filter px-6 py-2 rounded-3xl font-medium bg-red-600 text-white">Tất cả</button>
                    <button onclick="filterCategory('phone')" 
                            class="px-6 py-2 rounded-3xl font-medium hover:bg-white border">Điện thoại</button>
                    <button onclick="filterCategory('tablet')" 
                            class="px-6 py-2 rounded-3xl font-medium hover:bg-white border">Tablet</button>
                </div>
            </div>

            <!-- Products Grid -->
            <div id="products-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
                <!-- JS sẽ render sản phẩm vào đây -->
            </div>
        </div>
    </section>

    <!-- KHUYẾN MÃI HOT -->
    <section id="deals" class="max-w-7xl mx-auto px-6 py-16">
        <div class="flex items-center justify-between mb-10">
            <div class="flex items-center gap-x-3">
                <i class="fa-solid fa-fire text-red-600 text-4xl"></i>
                <h2 class="section-header text-4xl font-semibold">Khuyến mãi HOT hôm nay</h2>
            </div>
            <p class="text-red-600 text-sm font-medium">⏰ Còn 48 giờ</p>
        </div>

        <div class="grid grid-cols-2 md:grid-cols-4 gap-8" id="deals-grid">
            <!-- JS render deals -->
        </div>
    </section>

    <!-- ABOUT US -->
    <section id="about" class="bg-white py-20 border-t-4 border-red-600">
        <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-12 gap-16 items-center">
            <div class="md:col-span-5">
                <h2 class="text-5xl font-semibold leading-none">IMEX – Nền tảng<br>thương mại điện tử<br>chuyên biệt thiết bị di động</h2>
                <p class="mt-8 text-lg text-gray-600">
                    Thành lập năm 2024 tại Việt Nam, IMEX cam kết mang đến trải nghiệm mua sắm thiết bị di động tốt nhất: 
                    sản phẩm chính hãng 100%, giá cạnh tranh, hậu mãi vượt trội.
                </p>
                <div class="grid grid-cols-3 gap-8 mt-12">
                    <div>
                        <div class="text-5xl font-bold text-red-600">50k+</div>
                        <div class="text-sm text-gray-500">Khách hàng</div>
                    </div>
                    <div>
                        <div class="text-5xl font-bold text-red-600">1.200+</div>
                        <div class="text-sm text-gray-500">Sản phẩm</div>
                    </div>
                    <div>
                        <div class="text-5xl font-bold text-red-600">98%</div>
                        <div class="text-sm text-gray-500">Đánh giá 5 sao</div>
                    </div>
                </div>
            </div>
            
            <div class="md:col-span-7 bg-red-50 rounded-3xl p-8 text-center">
                <div class="max-w-md mx-auto">
                    <p class="italic text-2xl">"Tôi mua iPhone 16 tại IMEX và được hỗ trợ cực kỳ chuyên nghiệp. Giao hàng nhanh, bảo hành rõ ràng!"</p>
                    <div class="mt-8 flex items-center gap-x-4 justify-center">
                        <div class="w-12 h-12 bg-white rounded-2xl flex items-center justify-center text-4xl">👩‍💼</div>
                        <div>
                            <p class="font-semibold">Chị Lan – Hà Nội</p>
                            <p class="text-sm text-gray-500">Khách hàng VIP</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-gray-900 text-white">
        <div class="max-w-7xl mx-auto px-6 py-16 grid md:grid-cols-12 gap-y-10">
            <div class="md:col-span-4">
                <div class="flex items-center gap-x-3 mb-6">
                    <div class="w-10 h-10 bg-red-600 rounded-2xl flex items-center justify-center text-white text-3xl">📱</div>
                    <h1 class="logo-font text-4xl font-bold">IMEX</h1>
                </div>
                <p class="text-gray-400">Nền tảng thương mại điện tử chuyên biệt cho thiết bị di động.<br>Vinh, Nghệ An • Toàn quốc.</p>
                <div class="flex gap-x-4 mt-8">
                    <i class="fa-brands fa-facebook text-3xl cursor-pointer hover:text-red-500"></i>
                    <i class="fa-brands fa-tiktok text-3xl cursor-pointer hover:text-red-500"></i>
                    <i class="fa-brands fa-youtube text-3xl cursor-pointer hover:text-red-500"></i>
                </div>
            </div>

            <div class="md:col-span-2">
                <h5 class="font-semibold mb-4 text-red-400">CỬA HÀNG</h5>
                <ul class="space-y-2 text-gray-400 text-sm">
                    <li>Điện thoại</li>
                    <li>Máy tính bảng</li>
                    <li>Phụ kiện</li>
                    <li>Đồng hồ thông minh</li>
                </ul>
            </div>
            
            <div class="md:col-span-2">
                <h5 class="font-semibold mb-4 text-red-400">HỖ TRỢ</h5>
                <ul class="space-y-2 text-gray-400 text-sm">
                    <li>Chính sách bảo hành</li>
                    <li>Vận chuyển &amp; thanh toán</li>
                    <li>Đổi trả trong 30 ngày</li>
                    <li>Hotline: 1900 636 636</li>
                </ul>
            </div>

            <div class="md:col-span-4">
                <h5 class="font-semibold mb-4 text-red-400">ĐĂNG KÝ NHẬN ƯU ĐÃI</h5>
                <div class="flex">
                    <input type="email" id="email-subscribe" 
                           placeholder="Email của bạn" 
                           class="bg-white/10 border border-white/30 rounded-l-3xl px-6 py-5 flex-1 outline-none text-sm">
                    <button onclick="subscribe()" 
                            class="bg-red-600 hover:bg-red-700 px-10 rounded-r-3xl font-medium">ĐĂNG KÝ</button>
                </div>
                <p class="text-xs text-gray-400 mt-3">Nhận ngay mã giảm 200.000 ₫ cho đơn hàng đầu tiên</p>
            </div>
        </div>

        <div class="border-t border-white/10 py-6 text-center text-xs text-gray-500">
            © 2026 IMEX Mobile. All Rights Reserved. Made with ❤️ for Việt Nam.
        </div>
    </footer>

    <!-- CART MODAL -->
    <div onclick="if(event.target.id === 'cart-modal')hideCart()" 
         id="cart-modal"
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-end md:items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-lg rounded-t-3xl md:rounded-3xl shadow-2xl max-h-[90vh] overflow-hidden">
            <div class="px-6 py-5 border-b flex items-center justify-between">
                <h3 class="text-2xl font-semibold flex items-center"><i class="fa-solid fa-shopping-cart mr-3"></i>Giỏ hàng của bạn</h3>
                <i onclick="hideCart()" class="fa-solid fa-xmark text-3xl cursor-pointer"></i>
            </div>
            
            <div id="cart-items" class="px-6 py-4 max-h-[420px] overflow-auto space-y-6">
                <!-- JS render cart items -->
            </div>
            
            <div class="p-6 border-t">
                <div class="flex justify-between text-lg">
                    <span class="font-medium">Tổng cộng</span>
                    <span id="cart-total" class="font-bold text-2xl text-red-600">0 ₫</span>
                </div>
                <button onclick="checkout()" 
                        class="w-full mt-6 bg-red-600 hover:bg-red-700 text-white py-6 text-xl font-semibold rounded-3xl">
                    TIẾN HÀNH THANH TOÁN
                </button>
                <p class="text-center text-xs text-gray-400 mt-4">Hoặc thanh toán khi nhận hàng • Miễn phí vận chuyển từ 2 triệu</p>
            </div>
        </div>
    </div>

    <!-- LOGIN MODAL -->
    <div onclick="if(event.target.id === 'login-modal')hideLoginModal()" 
         id="login-modal"
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white rounded-3xl w-full max-w-md p-8">
            <h3 class="text-3xl font-semibold text-center mb-8">Đăng nhập IMEX</h3>
            <div class="space-y-4">
                <input type="text" placeholder="Số điện thoại hoặc email" 
                       class="w-full border border-gray-300 rounded-3xl px-6 py-5 outline-none">
                <input type="password" placeholder="Mật khẩu" 
                       class="w-full border border-gray-300 rounded-3xl px-6 py-5 outline-none">
                <button onclick="fakeLogin()" 
                        class="w-full bg-red-600 text-white rounded-3xl py-5 text-lg font-medium">ĐĂNG NHẬP</button>
            </div>
            <div class="text-center text-sm mt-6 text-gray-500">Chưa có tài khoản? <span onclick="hideLoginModal()" class="text-red-600 cursor-pointer">Đăng ký ngay</span></div>
        </div>
    </div>

    <script>
        // TailwindCSS initialization
        function initializeTailwind() {
            return {
                config(userConfig = {}) {
                    return {
                        configUser: userConfig,
                        theme: {
                            extend: {
                                colors: {
                                    primary: '#dc2626'
                                }
                            }
                        }
                    }
                },
                theme(userConfig = {}) {
                    return {
                        ...this.defaultTheme(),
                        ...this.config(userConfig).theme
                    }
                },
                defaultTheme() {
                    return {
                        extend: {}
                    }
                }
            }
        }
        
        // Sample products data (Vietnamese)
        const products = [
            {
                id: 1,
                name: "iPhone 16 Pro Max 256GB",
                category: "phone",
                price: 32990000,
                oldPrice: 35990000,
                discount: 8,
                image: "https://picsum.photos/id/1015/600/800",
                rating: 5
            },
            {
                id: 2,
                name: "Samsung Galaxy S25 Ultra",
                category: "phone",
                price: 28990000,
                oldPrice: 31990000,
                discount: 9,
                image: "https://picsum.photos/id/201/600/800",
                rating: 4
            },
            {
                id: 3,
                name: "iPad Air 6 128GB Wi-Fi",
                category: "tablet",
                price: 15990000,
                oldPrice: 17990000,
                discount: 11,
                image: "https://picsum.photos/id/301/600/800",
                rating: 5
            },
            {
                id: 4,
                name: "Xiaomi Redmi Note 14 Pro",
                category: "phone",
                price: 6990000,
                oldPrice: 7990000,
                discount: 13,
                image: "https://picsum.photos/id/401/600/800",
                rating: 4
            },
            {
                id: 5,
                name: "Apple Watch Ultra 2",
                category: "watch",
                price: 18990000,
                oldPrice: 21990000,
                discount: 14,
                image: "https://picsum.photos/id/501/600/800",
                rating: 5
            },
            {
                id: 6,
                name: "Galaxy Tab S10 Ultra",
                category: "tablet",
                price: 22990000,
                oldPrice: 25990000,
                discount: 12,
                image: "https://picsum.photos/id/601/600/800",
                rating: 5
            },
            {
                id: 7,
                name: "Tai nghe AirPods Pro 2",
                category: "accessory",
                price: 5990000,
                oldPrice: 6990000,
                discount: 14,
                image: "https://picsum.photos/id/701/600/800",
                rating: 5
            },
            {
                id: 8,
                name: "Sạc không dây MagSafe 3",
                category: "accessory",
                price: 1290000,
                oldPrice: 1590000,
                discount: 19,
                image: "https://picsum.photos/id/801/600/800",
                rating: 4
            }
        ]

        // Cart array
        let cart = []

        // Render products
        function renderProducts(filteredProducts) {
            const grid = document.getElementById('products-grid')
            grid.innerHTML = ''
            
            filteredProducts.forEach(product => {
                const cardHTML = `
                <div class="product-card bg-white rounded-3xl overflow-hidden border border-gray-100 shadow-sm">
                    <div class="relative">
                        <img src="${product.image}" alt="${product.name}" class="w-full h-64 object-cover">
                        ${product.discount ? 
                        `<div class="absolute top-4 left-4 bg-red-600 text-white text-xs font-bold px-3 py-1 rounded-3xl flex items-center">
                            -${product.discount}%
                        </div>` : ''}
                    </div>
                    <div class="p-6">
                        <div class="flex justify-between items-start">
                            <div>
                                <h4 class="font-semibold text-lg leading-tight">${product.name}</h4>
                                <div class="flex text-amber-400 mt-1">
                                    ${Array(5).fill().map((_, i) => `<i class="fa-solid fa-star ${i < product.rating ? 'text-amber-400' : 'text-gray-200'}"></i>`).join('')}
                                </div>
                            </div>
                            <div class="text-right">
                                <p class="text-red-600 text-2xl font-bold">${(product.price / 1000000).toFixed(1)}tr</p>
                                ${product.oldPrice ? `<p class="text-xs line-through text-gray-400">${(product.oldPrice / 1000000).toFixed(1)}tr</p>` : ''}
                            </div>
                        </div>
                        
                        <button onclick="addToCart(${product.id}); event.stopImmediatePropagation()" 
                                class="mt-6 w-full bg-red-600 hover:bg-red-700 text-white rounded-3xl py-4 font-semibold flex items-center justify-center gap-x-2">
                            <i class="fa-solid fa-cart-plus"></i>
                            THÊM VÀO GIỎ
                        </button>
                    </div>
                </div>`
                grid.innerHTML += cardHTML
            })
            
            if (filteredProducts.length === 0) {
                grid.innerHTML = `<p class="col-span-full text-center py-20 text-gray-400 text-xl">Không tìm thấy sản phẩm phù hợp.</p>`
            }
        }

        // Render deals (same products with bigger discount)
        function renderDeals() {
            const dealsGrid = document.getElementById('deals-grid')
            const dealProducts = products.filter(p => p.discount >= 10).slice(0, 4)
            
            dealsGrid.innerHTML = ''
            
            dealProducts.forEach(product => {
                const html = `
                <div class="bg-white rounded-3xl p-4 shadow-sm border border-red-100 hover:border-red-300">
                    <div class="relative">
                        <img src="${product.image}" alt="" class="w-full aspect-square object-cover rounded-3xl">
                        <div class="absolute top-4 right-4 bg-red-600 text-white text-xs font-bold px-4 h-8 flex items-center rounded-3xl">HOT</div>
                    </div>
                    <div class="mt-6 px-2">
                        <h4 class="font-semibold">${product.name}</h4>
                        <div class="flex justify-between mt-3">
                            <div>
                                <span class="text-red-600 text-3xl font-bold">${(product.price / 1000000).toFixed(1)}tr</span>
                                <span class="block text-xs text-gray-400 line-through">${(product.oldPrice / 1000000).toFixed(1)}tr</span>
                            </div>
                            <button onclick="addToCart(${product.id});" class="text-sm bg-red-600 text-white px-6 rounded-3xl font-medium">Mua ngay</button>
                        </div>
                    </div>
                </div>`
                dealsGrid.innerHTML += html
            })
        }

        // Add to cart
        function addToCart(id) {
            const product = products.find(p => p.id === id)
            if (!product) return
            
            // Check if already in cart
            const existing = cart.find(item => item.id === id)
            if (existing) {
                existing.quantity = (existing.quantity || 1) + 1
            } else {
                cart.push({...product, quantity: 1})
            }
            
            updateCartCount()
            
            // Toast
            showToast(`${product.name} đã được thêm vào giỏ hàng!`)
        }

        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + (item.quantity || 1), 0)
            document.getElementById('cart-count-badge').innerText = count
        }

        // Show cart
        function showCart() {
            const modal = document.getElementById('cart-modal')
            const container = document.getElementById('cart-items')
            
            container.innerHTML = ''
            
            if (cart.length === 0) {
                container.innerHTML = `
                <div class="text-center py-20">
                    <i class="fa-solid fa-shopping-cart text-7xl text-gray-200 mb-6"></i>
                    <p class="text-xl font-medium text-gray-400">Giỏ hàng trống</p>
                    <p class="text-sm mt-2">Hãy thêm một số thiết bị di động yêu thích!</p>
                </div>`
                document.getElementById('cart-total').innerText = '0 ₫'
                modal.classList.remove('hidden')
                modal.classList.add('flex')
                return
            }
            
            let total = 0
            
            cart.forEach((item, index) => {
                const qty = item.quantity || 1
                const itemTotal = item.price * qty
                total += itemTotal
                
                const row = `
                <div class="flex gap-4 border-b pb-6 last:border-none">
                    <img src="${item.image}" class="w-20 h-20 object-cover rounded-2xl">
                    <div class="flex-1">
                        <p class="font-medium">${item.name}</p>
                        <p class="text-red-600 text-sm">${(item.price / 1000000).toFixed(1)}tr × ${qty}</p>
                        
                        <div class="flex items-center gap-x-4 mt-4">
                            <button onclick="changeQuantity(${index}, -1)" class="w-8 h-8 border rounded-2xl flex items-center justify-center text-lg">-</button>
                            <span class="font-semibold">${qty}</span>
                            <button onclick="changeQuantity(${index}, 1)" class="w-8 h-8 border rounded-2xl flex items-center justify-center text-lg">+</button>
                            
                            <button onclick="removeFromCart(${index})" class="ml-auto text-red-500 text-xs flex items-center">
                                <i class="fa-solid fa-trash mr-1"></i> Xóa
                            </button>
                        </div>
                    </div>
                    <div class="text-right font-bold text-xl">${(itemTotal / 1000000).toFixed(1)}tr</div>
                </div>`
                container.innerHTML += row
            })
            
            document.getElementById('cart-total').innerText = `${(total / 1000000).toFixed(1)}tr ₫`
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }

        function hideCart() {
            const modal = document.getElementById('cart-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }

        function changeQuantity(index, change) {
            const item = cart[index]
            if (!item) return
            item.quantity = Math.max(1, (item.quantity || 1) + change)
            showCart()
            updateCartCount()
        }

        function removeFromCart(index) {
            cart.splice(index, 1)
            showCart()
            updateCartCount()
        }

        // Fake checkout
        function checkout() {
            hideCart()
            setTimeout(() => {
                alert('🎉 Cảm ơn bạn! Đơn hàng đã được xác nhận. Chúng tôi sẽ giao thiết bị di động đến tay bạn sớm nhất.')
                cart = []
                updateCartCount()
            }, 800)
        }

        // Simple toast
        function showToast(message) {
            const toast = document.createElement('div')
            toast.style.cssText = 'position:fixed; bottom:24px; right:24px; background:#dc2626; color:white; padding:18px 24px; border-radius:9999px; box-shadow:10px 10px 20px -5px rgb(220 38 38); display:flex; align-items:center; gap:12px; z-index:99999'
            toast.innerHTML = `<i class="fa-solid fa-check-circle"></i> ${message}`
            document.body.appendChild(toast)
            
            setTimeout(() => {
                toast.style.transform = 'translateY(100px)'
                toast.style.opacity = '0'
                setTimeout(() => toast.remove(), 600)
            }, 2800)
        }

        // Filter functions
        function filterAll() {
            renderProducts(products)
        }

        function filterCategory(cat) {
            const filtered = products.filter(p => p.category === cat)
            renderProducts(filtered)
        }

        // Mobile menu
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

        // Search toggle
        function toggleSearch() {
            const input = document.getElementById('search-input')
            input.classList.toggle('hidden')
            if (!input.classList.contains('hidden')) input.focus()
        }

        // Fake login
        function showLoginModal() {
            document.getElementById('login-modal').classList.remove('hidden')
            document.getElementById('login-modal').classList.add('flex')
        }
        
        function hideLoginModal() {
            const modal = document.getElementById('login-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        function fakeLogin() {
            hideLoginModal()
            showToast('Đăng nhập thành công! Chào mừng bạn đến với IMEX 🎟️')
        }

        function subscribe() {
            const email = document.getElementById('email-subscribe').value
            if (email) {
                showToast('Cảm ơn bạn! Mã giảm giá 200k đã được gửi vào email.')
                document.getElementById('email-subscribe').value = ''
            }
        }

        function watchVideo() {
            showToast('📹 Đang phát video giới thiệu IMEX... (trong phiên bản thật sẽ nhúng YouTube)')
        }

        function navigateToSection(section) {
            const el = document.getElementById(section)
            if (el) {
                el.scrollIntoView({ behavior: 'smooth' })
            }
        }

        // Main initialization
        window.onload = function() {
            initializeTailwind()
            renderProducts(products)
            renderDeals()
            updateCartCount()
            
            console.log('%c✅ Trang web IMEX đã sẵn sàng! Chuyên nghiệp, đẹp mắt, dễ sử dụng với màu đỏ - trắng chủ đạo.', 'color:#dc2626; font-size:13px; font-weight:bold')
        }
    </script>
</body>
</html>
