<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động">
    <title>IMEX - Thiết bị di động chính hãng</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Space+Grotesk:wght@500;600&display=swap');
        
        :root {
            --primary-blue: #0066FF;
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
            font-family: 'Space Grotesk', sans-serif;
        }

        .hero-bg {
            background: linear-gradient(92deg, #0066FF 0%, #00A3FF 100%);
        }
        
        .product-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: 25px 25px 50px -12px rgb(0 102 255 / 0.15);
        }
        
        .nav-link {
            position: relative;
        }
        
        .nav-link:after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: -2px;
            left: 0;
            background-color: #0066FF;
        }
        
        .nav-link:hover:after {
            width: 100%;
        }
        
        .cart-count {
            animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
        }
    </style>
</head>
<body class="tailwind-ready bg-white text-gray-900">
    <!-- NAVBAR -->
    <nav class="bg-white border-b sticky top-0 z-50 shadow-sm">
        <div class="max-w-screen-2xl mx-auto">
            <div class="px-8 py-5 flex items-center justify-between">
                
                <!-- Logo -->
                <div class="flex items-center gap-x-3">
                    <div class="w-10 h-10 bg-[#0066FF] rounded-2xl flex items-center justify-center text-white text-3xl shadow-inner">
                        📱
                    </div>
                    <h1 class="logo-font text-3xl font-semibold tracking-tighter text-[#0066FF]">IMEX</h1>
                    <span class="text-xs font-medium bg-[#0066FF] text-white px-2.5 py-0.5 rounded-3xl mt-1">MOBILE</span>
                </div>

                <!-- Menu -->
                <div class="hidden lg:flex items-center gap-x-8 text-base font-medium">
                    <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Trang chủ</a>
                    <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Điện thoại</a>
                    <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Máy tính bảng</a>
                    <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Phụ kiện</a>
                    <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Đồng hồ</a>
                    <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Tin tức</a>
                    <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Hỗ trợ</a>
                </div>

                <!-- Right side -->
                <div class="flex items-center gap-x-6">
                    
                    <!-- Search -->
                    <div onclick="toggleSearch()" class="flex items-center bg-gray-100 hover:bg-gray-200 rounded-3xl px-6 py-2.5 cursor-pointer w-80 max-w-xs">
                        <i class="fa-solid fa-magnifying-glass text-gray-400 mr-3"></i>
                        <input id="searchInput" 
                               type="text" 
                               placeholder="Tìm iPhone, Galaxy, Xiaomi..." 
                               class="bg-transparent outline-none flex-1 text-sm placeholder-gray-400">
                        <kbd class="hidden sm:inline-flex text-[10px] font-medium bg-white shadow border px-2 py-px rounded-lg text-gray-500">⌘K</kbd>
                    </div>

                    <!-- Account -->
                    <div class="flex items-center gap-x-2 cursor-pointer hover:text-[#0066FF]">
                        <i class="fa-solid fa-user text-xl"></i>
                        <div class="hidden md:block">
                            <p class="text-sm font-medium">Đăng nhập</p>
                            <p class="text-xs text-gray-500 -mt-0.5">Tài khoản</p>
                        </div>
                    </div>

                    <!-- Cart -->
                    <div onclick="toggleCart()" class="relative cursor-pointer flex items-center hover:text-[#0066FF]">
                        <i class="fa-solid fa-shopping-bag text-2xl"></i>
                        <span id="cart-count" 
                              class="cart-count absolute -top-1 -right-1 bg-red-500 text-white text-[10px] font-bold h-5 w-5 flex items-center justify-center rounded-full">3</span>
                    </div>

                    <!-- Mobile menu button -->
                    <button onclick="toggleMobileMenu()" class="lg:hidden text-2xl text-gray-700">
                        <i class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
            
            <!-- Mobile Menu -->
            <div id="mobileMenu" class="hidden lg:hidden bg-white border-t px-8 py-6">
                <div class="flex flex-col gap-y-5 text-lg font-medium">
                    <a href="#" class="py-2">Trang chủ</a>
                    <a href="#" class="py-2">Điện thoại</a>
                    <a href="#" class="py-2">Máy tính bảng</a>
                    <a href="#" class="py-2">Phụ kiện</a>
                    <a href="#" class="py-2">Đồng hồ thông minh</a>
                    <div class="pt-4 border-t flex items-center justify-between text-sm">
                        <button onclick="toggleCart()" class="flex items-center gap-x-3">
                            <i class="fa-solid fa-shopping-bag"></i>
                            <span>Giỏ hàng (<span id="mobile-cart-count">3</span>)</span>
                        </button>
                        <button class="flex-1 mx-4 bg-[#0066FF] text-white py-4 rounded-3xl font-semibold">Đăng nhập / Đăng ký</button>
                    </div>
                </div>
            </div>
        </div>
    </nav>

    <!-- HERO SECTION -->
    <header class="hero-bg text-white">
        <div class="max-w-screen-2xl mx-auto px-8 grid lg:grid-cols-2 gap-16 items-center py-16 lg:py-24">
            
            <div class="space-y-8">
                <div class="inline-flex items-center gap-x-2 bg-white/20 text-white text-sm font-medium px-6 py-3 rounded-3xl backdrop-blur-md">
                    <span class="relative flex h-3 w-3">
                        <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"></span>
                        <span class="relative inline-flex rounded-full h-3 w-3 bg-green-400"></span>
                    </span>
                    MỚI RA MẮT • iPhone 17 Pro Max
                </div>
                
                <h2 class="text-6xl lg:text-7xl font-semibold tracking-tighter leading-none">
                    IMEX<br>Thiết bị di động<br><span class="text-white/90">chính hãng • giá tốt nhất</span>
                </h2>
                
                <p class="text-xl text-white/80 max-w-md">
                    Nền tảng thương mại điện tử chuyên biệt cho điện thoại, máy tính bảng, phụ kiện. 
                    Giao hàng toàn quốc trong 2 giờ • Bảo hành 36 tháng
                </p>
                
                <div class="flex items-center gap-x-4">
                    <a onclick="fakeBuyNow()" 
                       class="flex-1 lg:flex-none bg-white text-[#0066FF] font-semibold text-lg px-10 py-6 rounded-3xl flex items-center justify-center gap-x-3 hover:shadow-2xl">
                        <i class="fa-solid fa-bolt"></i>
                        MUA NGAY
                    </a>
                    
                    <a onclick="watchVideo()" 
                       class="flex-1 lg:flex-none border-2 border-white/70 hover:border-white font-semibold text-lg px-8 py-6 rounded-3xl flex items-center justify-center gap-x-3">
                        <i class="fa-solid fa-play"></i>
                        XEM VIDEO
                    </a>
                </div>
                
                <div class="flex items-center gap-x-8 text-sm">
                    <div class="flex items-center">
                        <i class="fa-solid fa-shield-halved text-2xl mr-3"></i>
                        <div>
                            <p class="font-medium">Bảo hành 36 tháng</p>
                            <p class="text-white/70 text-xs">Toàn quốc</p>
                        </div>
                    </div>
                    <div class="flex items-center">
                        <i class="fa-solid fa-truck text-2xl mr-3"></i>
                        <div>
                            <p class="font-medium">Giao hàng 2 giờ</p>
                            <p class="text-white/70 text-xs">Hà Nội - TP.HCM</p>
                        </div>
                    </div>
                    <div class="flex items-center">
                        <i class="fa-solid fa-rotate-left text-2xl mr-3"></i>
                        <div>
                            <p class="font-medium">Đổi trả 30 ngày</p>
                            <p class="text-white/70 text-xs">Không lý do</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Hero visual -->
            <div class="relative flex justify-center">
                <div class="absolute -top-10 -left-10 w-80 h-80 bg-white/10 backdrop-blur-3xl rounded-[4rem] rotate-12 shadow-2xl"></div>
                <img src="https://picsum.photos/id/1015/800/800" 
                     alt="iPhone 17 Pro Max"
                     class="relative w-full max-w-md drop-shadow-2xl rounded-[3rem] border-8 border-white/20">
                <div class="absolute bottom-10 right-10 bg-white text-[#0066FF] rounded-3xl px-6 py-3 flex items-center shadow-xl">
                    <div class="text-4xl font-semibold">17</div>
                    <div class="ml-3">
                        <div class="text-sm font-medium">Pro Max</div>
                        <div class="text-xs text-gray-500">Từ 38.990.000đ</div>
                    </div>
                </div>
                <div class="absolute -bottom-4 -left-4 bg-white text-black text-sm font-medium px-4 h-10 rounded-3xl flex items-center shadow-lg">
                    <i class="fa-solid fa-fire text-red-500 mr-2"></i>
                    Chỉ còn 142 chiếc
                </div>
            </div>
        </div>
    </header>

    <!-- CATEGORIES -->
    <section class="max-w-screen-2xl mx-auto px-8 py-16">
        <div class="flex items-end justify-between mb-10">
            <h3 class="text-3xl font-semibold">Danh mục thiết bị</h3>
            <a href="#" class="text-[#0066FF] font-medium flex items-center gap-x-2 hover:gap-x-3">
                Xem tất cả <i class="fa-solid fa-arrow-right"></i>
            </a>
        </div>
        
        <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-6">
            <!-- Category 1 -->
            <div onclick="goToCategory(1)" class="group bg-white border border-gray-100 rounded-3xl p-6 hover:border-[#0066FF] cursor-pointer">
                <div class="h-40 flex items-center justify-center text-7xl mb-6 group-hover:scale-110">📱</div>
                <h4 class="text-center font-semibold text-xl">Điện thoại thông minh</h4>
                <p class="text-center text-sm text-gray-500 mt-1">120+ mẫu</p>
            </div>
            
            <!-- Category 2 -->
            <div onclick="goToCategory(2)" class="group bg-white border border-gray-100 rounded-3xl p-6 hover:border-[#0066FF] cursor-pointer">
                <div class="h-40 flex items-center justify-center text-7xl mb-6 group-hover:scale-110">💻</div>
                <h4 class="text-center font-semibold text-xl">Máy tính bảng</h4>
                <p class="text-center text-sm text-gray-500 mt-1">iPad • Galaxy Tab</p>
            </div>
            
            <!-- Category 3 -->
            <div onclick="goToCategory(3)" class="group bg-white border border-gray-100 rounded-3xl p-6 hover:border-[#0066FF] cursor-pointer">
                <div class="h-40 flex items-center justify-center text-7xl mb-6 group-hover:scale-110">🎧</div>
                <h4 class="text-center font-semibold text-xl">Tai nghe • Âm thanh</h4>
                <p class="text-center text-sm text-gray-500 mt-1">AirPods • Galaxy Buds</p>
            </div>
            
            <!-- Category 4 -->
            <div onclick="goToCategory(4)" class="group bg-white border border-gray-100 rounded-3xl p-6 hover:border-[#0066FF] cursor-pointer">
                <div class="h-40 flex items-center justify-center text-7xl mb-6 group-hover:scale-110">⌚</div>
                <h4 class="text-center font-semibold text-xl">Đồng hồ thông minh</h4>
                <p class="text-center text-sm text-gray-500 mt-1">Apple Watch • Galaxy Watch</p>
            </div>
            
            <!-- Category 5 -->
            <div onclick="goToCategory(5)" class="group bg-white border border-gray-100 rounded-3xl p-6 hover:border-[#0066FF] cursor-pointer">
                <div class="h-40 flex items-center justify-center text-7xl mb-6 group-hover:scale-110">🔌</div>
                <h4 class="text-center font-semibold text-xl">Phụ kiện sạc</h4>
                <p class="text-center text-sm text-gray-500 mt-1">Sạc nhanh • Pin dự phòng</p>
            </div>
            
            <!-- Category 6 -->
            <div onclick="goToCategory(6)" class="group bg-white border border-gray-100 rounded-3xl p-6 hover:border-[#0066FF] cursor-pointer">
                <div class="h-40 flex items-center justify-center text-7xl mb-6 group-hover:scale-110">🛡️</div>
                <h4 class="text-center font-semibold text-xl">Ốp lưng &amp; Bảo vệ</h4>
                <p class="text-center text-sm text-gray-500 mt-1">Chính hãng 100%</p>
            </div>
        </div>
    </section>

    <!-- FEATURED PRODUCTS -->
    <section class="bg-gray-50 py-16">
        <div class="max-w-screen-2xl mx-auto px-8">
            <div class="flex items-center justify-between mb-10">
                <div>
                    <span class="uppercase text-[#0066FF] text-sm font-bold tracking-widest">🔥 HOT</span>
                    <h3 class="text-3xl font-semibold">Sản phẩm nổi bật tuần này</h3>
                </div>
                <button onclick="viewAllProducts()" 
                        class="text-[#0066FF] font-medium flex items-center gap-x-2">
                    Xem toàn bộ <i class="fa-solid fa-arrow-right"></i>
                </button>
            </div>
            
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-8" id="product-grid">
                <!-- Products are generated by JavaScript -->
            </div>
        </div>
    </section>

    <!-- WHY IMEX -->
    <section class="max-w-screen-2xl mx-auto px-8 py-20 grid md:grid-cols-3 gap-12">
        <div class="text-center">
            <div class="mx-auto w-16 h-16 bg-[#0066FF] text-white rounded-3xl flex items-center justify-center text-4xl mb-6">🚀</div>
            <h4 class="font-semibold text-2xl mb-3">Giao nhanh 2 giờ</h4>
            <p class="text-gray-600">Hà Nội, TP.HCM, Đà Nẵng. Các tỉnh khác giao trong 24h.</p>
        </div>
        <div class="text-center">
            <div class="mx-auto w-16 h-16 bg-[#0066FF] text-white rounded-3xl flex items-center justify-center text-4xl mb-6">🔐</div>
            <h4 class="font-semibold text-2xl mb-3">Chính hãng 100%</h4>
            <p class="text-gray-600">Nhập khẩu trực tiếp từ Apple, Samsung, Xiaomi, OPPO…</p>
        </div>
        <div class="text-center">
            <div class="mx-auto w-16 h-16 bg-[#0066FF] text-white rounded-3xl flex items-center justify-center text-4xl mb-6">💰</div>
            <h4 class="font-semibold text-2xl mb-3">Giá luôn tốt nhất</h4>
            <p class="text-gray-600">Cam kết giá thấp hơn thị trường 5–15%. Trả góp 0% lãi suất.</p>
        </div>
    </section>

    <!-- TESTIMONIALS -->
    <section class="bg-white py-16 border-t">
        <div class="max-w-screen-2xl mx-auto px-8">
            <h3 class="text-center text-3xl font-semibold mb-12">Khách hàng nói gì về IMEX</h3>
            <div class="grid md:grid-cols-3 gap-8">
                <div class="border border-gray-100 rounded-3xl p-8">
                    <div class="flex gap-x-1 text-yellow-400 mb-6">
                        ★★★★☆
                    </div>
                    <p class="italic">"Mua iPhone 16 Pro Max chỉ sau 40 phút đã có hàng. Nhân viên hỗ trợ cực kỳ nhiệt tình, đóng gói rất đẹp!"</p>
                    <div class="flex items-center gap-x-3 mt-8">
                        <div class="w-10 h-10 bg-gray-200 rounded-2xl"></div>
                        <div>
                            <p class="font-medium">Nguyễn Thị Lan</p>
                            <p class="text-sm text-gray-500">Hà Nội • 2 ngày trước</p>
                        </div>
                    </div>
                </div>
                <div class="border border-gray-100 rounded-3xl p-8">
                    <div class="flex gap-x-1 text-yellow-400 mb-6">
                        ★★★★★
                    </div>
                    <p class="italic">"Galaxy S25 Ultra mua online mà còn được giảm thêm 2 triệu nhờ mã IMEXVIP. Giao hàng siêu nhanh!"</p>
                    <div class="flex items-center gap-x-3 mt-8">
                        <div class="w-10 h-10 bg-gray-200 rounded-2xl"></div>
                        <div>
                            <p class="font-medium">Trần Minh Quân</p>
                            <p class="text-sm text-gray-500">TP.HCM • 5 ngày trước</p>
                        </div>
                    </div>
                </div>
                <div class="border border-gray-100 rounded-3xl p-8">
                    <div class="flex gap-x-1 text-yellow-400 mb-6">
                        ★★★★☆
                    </div>
                    <p class="italic">"Đổi trả máy tính bảng iPad Air trong vòng 30 phút. Dịch vụ cực kỳ chuyên nghiệp!"</p>
                    <div class="flex items-center gap-x-3 mt-8">
                        <div class="w-10 h-10 bg-gray-200 rounded-2xl"></div>
                        <div>
                            <p class="font-medium">Lê Thị Hương</p>
                            <p class="text-sm text-gray-500">Đà Nẵng • 1 tuần trước</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-[#0A0A2C] text-white">
        <div class="max-w-screen-2xl mx-auto px-8 pt-16 pb-12 grid grid-cols-2 md:grid-cols-4 lg:grid-cols-5 gap-y-10">
            <div>
                <div class="flex items-center gap-x-3 mb-6">
                    <div class="w-10 h-10 bg-[#0066FF] rounded-2xl flex items-center justify-center text-3xl">📱</div>
                    <h1 class="logo-font text-3xl font-semibold tracking-tighter">IMEX</h1>
                </div>
                <p class="text-gray-400 text-sm">Nền tảng thương mại điện tử<br>chuyên biệt thiết bị di động</p>
                <div class="flex gap-x-4 mt-8">
                    <i class="fa-brands fa-facebook text-2xl"></i>
                    <i class="fa-brands fa-youtube text-2xl"></i>
                    <i class="fa-brands fa-tiktok text-2xl"></i>
                    <i class="fa-brands fa-instagram text-2xl"></i>
                </div>
            </div>
            
            <div>
                <h5 class="uppercase text-xs tracking-widest mb-4 text-gray-400">Sản phẩm</h5>
                <ul class="space-y-3 text-sm">
                    <li><a href="#" class="hover:text-[#0066FF]">Điện thoại Apple</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Điện thoại Samsung</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Xiaomi • OPPO • Realme</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Máy tính bảng</a></li>
                </ul>
            </div>
            
            <div>
                <h5 class="uppercase text-xs tracking-widest mb-4 text-gray-400">Dịch vụ</h5>
                <ul class="space-y-3 text-sm">
                    <li><a href="#" class="hover:text-[#0066FF]">Trả góp 0%</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Bảo hành chính hãng</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Đổi trả miễn phí</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Sửa chữa nhanh</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Thu cũ đổi mới</a></li>
                </ul>
            </div>
            
            <div>
                <h5 class="uppercase text-xs tracking-widest mb-4 text-gray-400">Hỗ trợ</h5>
                <ul class="space-y-3 text-sm">
                    <li><a href="#" class="hover:text-[#0066FF]">Hotline: 1900 6688</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Chat trực tiếp 24/7</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Câu hỏi thường gặp</a></li>
                    <li><a href="#" class="hover:text-[#0066FF]">Theo dõi đơn hàng</a></li>
                </ul>
            </div>
            
            <div class="col-span-2 md:col-span-1">
                <h5 class="uppercase text-xs tracking-widest mb-4 text-gray-400">Tải ứng dụng IMEX</h5>
                <div class="flex flex-col gap-y-4">
                    <button onclick="fakeDownloadApp()" class="flex items-center border border-white/30 hover:border-white rounded-2xl px-5 py-3">
                        <i class="fa-brands fa-app-store-ios text-4xl"></i>
                        <div class="ml-4 text-left">
                            <p class="text-xs">Tải trên</p>
                            <p class="font-semibold">App Store</p>
                        </div>
                    </button>
                    <button onclick="fakeDownloadApp()" class="flex items-center border border-white/30 hover:border-white rounded-2xl px-5 py-3">
                        <i class="fa-brands fa-google-play text-4xl"></i>
                        <div class="ml-4 text-left">
                            <p class="text-xs">Tải trên</p>
                            <p class="font-semibold">Google Play</p>
                        </div>
                    </button>
                </div>
            </div>
        </div>
        
        <div class="text-center py-8 border-t border-white/10 text-xs text-gray-400">
            © 2026 IMEX Vietnam. All rights reserved. | Nền tảng Thương mại điện tử chuyên Thiết bị di động
        </div>
    </footer>

    <!-- SIMPLE CART MODAL -->
    <div id="cartModal" onclick="if(event.target.id === 'cartModal') toggleCart()" 
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-end lg:items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-lg lg:rounded-3xl rounded-t-3xl h-[85vh] lg:h-auto overflow-hidden">
            <div class="px-8 py-6 border-b flex items-center justify-between">
                <h3 class="text-2xl font-semibold">Giỏ hàng</h3>
                <button onclick="toggleCart()" class="text-3xl">✕</button>
            </div>
            
            <div class="px-8 py-8 space-y-6 overflow-auto h-[calc(85vh-180px)]" id="cart-items">
                <!-- JS will fill -->
            </div>
            
            <div class="px-8 py-6 border-t">
                <div class="flex justify-between text-lg mb-6">
                    <p>Tổng tiền</p>
                    <p id="cart-total" class="font-semibold">0 ₫</p>
                </div>
                <button onclick="checkout()" 
                        class="w-full py-6 bg-[#0066FF] hover:bg-[#0055DD] text-white rounded-3xl text-xl font-semibold">
                    Thanh toán ngay
                </button>
                <p class="text-center text-xs text-gray-400 mt-6">Hoặc trả góp 0% trong 12 tháng</p>
            </div>
        </div>
    </div>

    <!-- SEARCH OVERLAY -->
    <div id="searchOverlay" onclick="if(event.target.id === 'searchOverlay') toggleSearch()" 
         class="hidden fixed inset-0 bg-black/70 z-[10000] flex items-start justify-center pt-24">
        <div class="w-full max-w-2xl bg-white rounded-3xl mx-4 shadow-2xl overflow-hidden">
            <div class="p-6 flex items-center border-b">
                <i class="fa-solid fa-magnifying-glass text-2xl text-gray-400 mr-4"></i>
                <input id="modalSearch" 
                       type="text" 
                       placeholder="Tìm kiếm sản phẩm..." 
                       class="flex-1 outline-none text-2xl placeholder-gray-300">
                <button onclick="toggleSearch()" class="text-xl">Đóng</button>
            </div>
            <div class="px-6 py-8 text-sm max-h-[420px] overflow-auto" id="search-results">
                <!-- JS suggestions -->
                <p class="text-gray-400 text-center py-12">Nhập từ khóa để tìm kiếm...</p>
            </div>
        </div>
    </div>

    <script>
        // Tailwind script already loaded via CDN
        function initializeTailwind() {
            // Already done in HTML
        }
        
        // Fake products data
        const products = [
            {
                id: 1,
                name: "iPhone 17 Pro Max",
                price: 38990000,
                oldPrice: 42990000,
                image: "https://picsum.photos/id/1015/400/400",
                badge: "MỚI"
            },
            {
                id: 2,
                name: "Samsung Galaxy S25 Ultra",
                price: 32990000,
                oldPrice: 35990000,
                image: "https://picsum.photos/id/1016/400/400",
                badge: "BÁN CHẠY"
            },
            {
                id: 3,
                name: "iPad Air 6 M3 2025",
                price: 18990000,
                oldPrice: null,
                image: "https://picsum.photos/id/201/400/400",
                badge: "GIẢM GIÁ"
            },
            {
                id: 4,
                name: "Xiaomi 15 Pro 5G",
                price: 16990000,
                oldPrice: 19990000,
                image: "https://picsum.photos/id/251/400/400",
                badge: ""
            },
            {
                id: 5,
                name: "Apple Watch Ultra 3",
                price: 24990000,
                oldPrice: null,
                image: "https://picsum.photos/id/1005/400/400",
                badge: "HOT"
            }
        ]
        
        // Render products
        function renderProducts() {
            const grid = document.getElementById('product-grid')
            grid.innerHTML = ''
            
            products.forEach(product => {
                const discount = product.oldPrice 
                    ? Math.round(((product.oldPrice - product.price) / product.oldPrice) * 100) 
                    : 0
                
                const html = `
                <div class="product-card bg-white rounded-3xl overflow-hidden border border-gray-100 group">
                    <div class="relative">
                        <img src="${product.image}" alt="${product.name}" class="w-full h-60 object-cover">
                        ${product.badge ? `<span class="absolute top-4 left-4 text-xs font-bold bg-[#0066FF] text-white px-4 py-1 rounded-3xl">${product.badge}</span>` : ''}
                        ${discount > 0 ? `<span class="absolute top-4 right-4 bg-red-500 text-white text-xs font-bold px-3 py-1 rounded-3xl">-${discount}%</span>` : ''}
                    </div>
                    <div class="p-6">
                        <h5 class="font-semibold text-lg leading-tight">${product.name}</h5>
                        <div class="flex items-baseline gap-x-3 mt-4">
                            <span class="text-2xl font-semibold">${product.price.toLocaleString('vi-VN')} ₫</span>
                            ${product.oldPrice ? `<span class="line-through text-gray-400 text-sm">${product.oldPrice.toLocaleString('vi-VN')} ₫</span>` : ''}
                        </div>
                        <button onclick="addToCart(${product.id}); event.stopImmediatePropagation()" 
                                class="mt-6 w-full py-4 bg-[#0066FF] hover:bg-[#0055DD] text-white font-medium rounded-3xl flex items-center justify-center gap-x-2 text-sm">
                            <i class="fa-solid fa-cart-plus"></i>
                            THÊM VÀO GIỎ
                        </button>
                    </div>
                </div>`
                grid.innerHTML += html
            })
        }
        
        // Cart logic
        let cart = []
        
        function addToCart(id) {
            const product = products.find(p => p.id === id)
            if (!product) return
            
            const existing = cart.find(item => item.id === id)
            if (existing) {
                existing.quantity = (existing.quantity || 1) + 1
            } else {
                cart.push({...product, quantity: 1})
            }
            
            updateCartCount()
            showToast(`${product.name} đã được thêm vào giỏ hàng!`)
        }
        
        function updateCartCount() {
            let count = 0
            cart.forEach(item => count += item.quantity || 1)
            document.getElementById('cart-count').textContent = count
            document.getElementById('mobile-cart-count').textContent = count
        }
        
        function toggleCart() {
            const modal = document.getElementById('cartModal')
            const itemsContainer = document.getElementById('cart-items')
            
            if (modal.classList.contains('hidden')) {
                // Show cart
                modal.classList.remove('hidden')
                modal.classList.add('flex')
                
                let html = ''
                let total = 0
                
                if (cart.length === 0) {
                    html = `<div class="text-center py-20"><i class="fa-solid fa-shopping-bag text-8xl text-gray-200 mb-6"></i><p class="text-2xl font-medium">Giỏ hàng trống</p></div>`
                } else {
                    cart.forEach((item, index) => {
                        const itemTotal = item.price * (item.quantity || 1)
                        total += itemTotal
                        
                        html += `
                        <div class="flex gap-4">
                            <img src="${item.image}" class="w-20 h-20 object-cover rounded-2xl">
                            <div class="flex-1">
                                <h6 class="font-medium">${item.name}</h6>
                                <p class="text-[#0066FF] text-xl font-semibold">${item.price.toLocaleString('vi-VN')} ₫</p>
                                <div class="flex justify-between mt-3">
                                    <div class="flex border rounded-3xl items-center text-sm">
                                        <button onclick="changeQuantity(${index}, -1)" class="px-4 py-2">-</button>
                                        <span class="px-4">${item.quantity || 1}</span>
                                        <button onclick="changeQuantity(${index}, 1)" class="px-4 py-2">+</button>
                                    </div>
                                    <button onclick="removeFromCart(${index})" class="text-red-500 text-sm">Xóa</button>
                                </div>
                            </div>
                        </div>`
                    })
                }
                
                itemsContainer.innerHTML = html
                document.getElementById('cart-total').innerHTML = `<span class="font-semibold">${total.toLocaleString('vi-VN')} ₫</span>`
            } else {
                modal.classList.add('hidden')
                modal.classList.remove('flex')
            }
        }
        
        function changeQuantity(index, change) {
            const item = cart[index]
            if (!item) return
            item.quantity = Math.max(1, (item.quantity || 1) + change)
            toggleCart() // refresh
        }
        
        function removeFromCart(index) {
            cart.splice(index, 1)
            toggleCart()
            updateCartCount()
        }
        
        function checkout() {
            if (cart.length === 0) return
            alert('🎉 Cảm ơn bạn đã mua hàng tại IMEX!\nĐơn hàng của bạn đang được xử lý...')
            cart = []
            toggleCart()
            updateCartCount()
        }
        
        // Search
        function toggleSearch() {
            const overlay = document.getElementById('searchOverlay')
            if (overlay.classList.contains('hidden')) {
                overlay.classList.remove('hidden')
                setTimeout(() => {
                    document.getElementById('modalSearch').focus()
                }, 300)
                generateFakeSuggestions()
            } else {
                overlay.classList.add('hidden')
            }
        }
        
        function generateFakeSuggestions() {
            const container = document.getElementById('search-results')
            container.innerHTML = `
            <div class="space-y-6">
                <div class="flex items-center gap-4 text-lg cursor-pointer" onclick="quickSearch('iPhone 17')">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <span>iPhone 17 Pro Max</span>
                </div>
                <div class="flex items-center gap-4 text-lg cursor-pointer" onclick="quickSearch('Galaxy S25')">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <span>Samsung Galaxy S25 Ultra</span>
                </div>
                <div class="flex items-center gap-4 text-lg cursor-pointer" onclick="quickSearch('AirPods')">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <span>AirPods Pro 3</span>
                </div>
                <div class="flex items-center gap-4 text-lg cursor-pointer" onclick="quickSearch('iPad')">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <span>iPad Air M3 2025</span>
                </div>
            </div>`
        }
        
        function quickSearch(term) {
            toggleSearch()
            alert(`🔍 Kết quả tìm kiếm cho "${term}"\n\n(Trong trang web thực tế sẽ hiển thị danh sách sản phẩm)`)
        }
        
        // Mobile menu
        function toggleMobileMenu() {
            const menu = document.getElementById('mobileMenu')
            menu.classList.toggle('hidden')
        }
        
        // Fake actions
        function fakeBuyNow() {
            alert('✅ Chuyển đến trang thanh toán iPhone 17 Pro Max...\nBạn đã chọn mua thành công!')
            addToCart(1)
        }
        
        function watchVideo() {
            alert('📽️ Đang mở video giới thiệu IMEX (demo)\n\nHãy tưởng tượng một video giới thiệu nền tảng siêu đẹp nhé!')
        }
        
        function goToCategory(n) {
            const names = ['Điện thoại', 'Máy tính bảng', 'Tai nghe', 'Đồng hồ', 'Phụ kiện sạc', 'Ốp lưng']
            alert(`📌 Bạn đang xem danh mục: ${names[n-1]}\n\nTrang danh mục sẽ hiển thị đầy đủ sản phẩm.`)
        }
        
        function viewAllProducts() {
            alert('🌟 Hiển thị tất cả sản phẩm nổi bật...\nBạn có thể thêm nhiều card sản phẩm hơn vào đây.')
        }
        
        function fakeDownloadApp() {
            alert('📲 Tải ứng dụng IMEX ngay!\n\n(Trong thực tế sẽ redirect đến App Store / Google Play)')
        }
        
        function showToast(message) {
            const toast = document.createElement('div')
            toast.style.cssText = `position:fixed; bottom:20px; right:20px; background:#0066FF; color:white; padding:16px 24px; border-radius:9999px; box-shadow:0 10px 15px -3px rgb(0 102 255); z-index:99999;`
            toast.innerHTML = `<i class="fa-solid fa-check-circle mr-2"></i> ${message}`
            document.body.appendChild(toast)
            
            setTimeout(() => {
                toast.style.transition = 'all 0.4s'
                toast.style.opacity = '0'
                toast.style.transform = 'translateY(20px)'
                setTimeout(() => toast.remove(), 400)
            }, 2800)
        }
        
        // Initialize everything
        window.onload = function() {
            renderProducts()
            updateCartCount()
            
            console.log('%c🚀 Trang web IMEX đã được khởi tạo thành công!', 'color:#0066FF; font-size:18px; font-family:Space Grotesk')
            console.log('Màu chủ đạo: Xanh dương (#0066FF) - Trắng')
            console.log('Bạn có thể copy toàn bộ code này để triển khai.')
        }
    </script>
</body>
</html>
