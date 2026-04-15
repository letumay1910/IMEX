<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động">
    <title>IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Roboto:wght@700&amp;display=swap');
        
        :root {
            --red: #e30613;
        }
        
        * {
            transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
            transition-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
            transition-duration: 150ms;
        }
        
        .tailwind-ready .bg-primary { background-color: #e30613; }
        .tailwind-ready .text-primary { color: #e30613; }
        .tailwind-ready .border-primary { border-color: #e30613; }
        
        .hero-bg {
            background: linear-gradient(135deg, #e30613 0%, #b2000f 100%);
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
            background-color: #e30613;
        }
        
        .nav-link:hover:after {
            width: 100%;
        }
        
        .card-hover:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 25px -5px rgb(227 6 19 / 0.1), 0 8px 10px -6px rgb(227 6 19 / 0.1);
        }
        
        .section-title {
            position: relative;
        }
        
        .section-title:after {
            content: '';
            position: absolute;
            width: 60px;
            height: 3px;
            background-color: #e30613;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
        }
        
        .phone-float {
            animation: float 3s ease-in-out infinite;
        }
    </style>
</head>
<body class="tailwind-ready font-sans">
    <!-- NAVBAR -->
    <nav class="bg-white border-b border-gray-200 sticky top-0 z-50 shadow-sm">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex justify-between items-center h-16">
                <!-- Logo -->
                <div class="flex items-center gap-x-3">
                    <div class="w-9 h-9 bg-[#e30613] rounded-2xl flex items-center justify-center text-white text-2xl font-bold shadow-inner">📱</div>
                    <h1 class="text-3xl font-bold tracking-[-1px]">
                        <span class="text-[#e30613]">IMEX</span>
                    </h1>
                    <span class="text-xs font-medium bg-[#e30613] text-white px-2.5 py-0.5 rounded-full mt-1">Thiết bị di động</span>
                </div>

                <!-- Menu Desktop -->
                <div class="hidden md:flex items-center gap-x-8 text-sm font-medium">
                    <a href="#" onclick="navigateToSection('home')" class="nav-link text-gray-700 hover:text-[#e30613]">Trang chủ</a>
                    <a href="#" onclick="navigateToSection('san-pham')" class="nav-link text-gray-700 hover:text-[#e30613]">Sản phẩm</a>
                    <a href="#" onclick="navigateToSection('tinh-nang')" class="nav-link text-gray-700 hover:text-[#e30613]">Tính năng</a>
                    <a href="#" onclick="navigateToSection('he-sinh-thai')" class="nav-link text-gray-700 hover:text-[#e30613]">Hệ sinh thái</a>
                    <a href="#" onclick="navigateToSection('cong-dong')" class="nav-link text-gray-700 hover:text-[#e30613]">Cộng đồng</a>
                    <a href="#" onclick="navigateToSection('bao-hanh')" class="nav-link text-gray-700 hover:text-[#e30613]">Bảo hành</a>
                </div>

                <div class="flex items-center gap-x-4">
                    <!-- Search -->
                    <div class="relative hidden sm:block">
                        <input 
                            type="text" 
                            id="search-input"
                            placeholder="Tìm điện thoại, máy tính bảng..." 
                            class="w-72 bg-gray-100 border border-gray-200 focus:border-[#e30613] focus:bg-white rounded-full py-2 pl-10 pr-4 text-sm outline-none">
                        <i class="fa-solid fa-magnifying-glass absolute left-4 top-3 text-gray-400"></i>
                    </div>

                    <!-- Icons -->
                    <button onclick="toggleCart()" class="relative p-2 hover:bg-gray-100 rounded-2xl">
                        <i class="fa-solid fa-shopping-cart text-xl text-gray-700"></i>
                        <span id="cart-count" class="absolute -top-1 -right-1 bg-[#e30613] text-white text-[10px] font-bold rounded-full h-5 w-5 flex items-center justify-center">3</span>
                    </button>
                    
                    <button onclick="showLogin()" class="flex items-center gap-x-2 bg-white border border-[#e30613] hover:bg-[#e30613] hover:text-white text-[#e30613] px-5 py-2 rounded-3xl text-sm font-semibold">
                        <i class="fa-solid fa-user"></i>
                        <span>Đăng nhập</span>
                    </button>

                    <!-- Mobile menu button -->
                    <button onclick="toggleMobileMenu()" class="md:hidden p-3 text-2xl text-gray-700">
                        <i id="mobile-icon" class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t px-6 py-4">
            <div class="flex flex-col gap-y-4 text-sm font-medium">
                <a href="#" onclick="navigateToSection('home');toggleMobileMenu()" class="py-2">Trang chủ</a>
                <a href="#" onclick="navigateToSection('san-pham');toggleMobileMenu()" class="py-2">Sản phẩm</a>
                <a href="#" onclick="navigateToSection('tinh-nang');toggleMobileMenu()" class="py-2">Tính năng</a>
                <a href="#" onclick="navigateToSection('he-sinh-thai');toggleMobileMenu()" class="py-2">Hệ sinh thái</a>
                <a href="#" onclick="navigateToSection('cong-dong');toggleMobileMenu()" class="py-2">Cộng đồng</a>
                <a href="#" onclick="navigateToSection('bao-hanh');toggleMobileMenu()" class="py-2">Bảo hành điện tử</a>
                <div class="pt-4 border-t flex justify-between">
                    <button onclick="showLogin();toggleMobileMenu()" class="flex-1 bg-[#e30613] text-white py-3 rounded-3xl font-semibold">Đăng nhập / Đăng ký</button>
                </div>
            </div>
        </div>
    </nav>

    <!-- HERO SECTION -->
    <header id="home" class="hero-bg text-white">
        <div class="max-w-7xl mx-auto px-6 pt-16 pb-20 grid md:grid-cols-2 gap-12 items-center">
            <div class="space-y-8">
                <div class="inline-flex items-center bg-white/20 backdrop-blur-md text-white text-sm font-medium px-5 py-2 rounded-3xl">
                    <i class="fa-solid fa-rocket mr-2"></i>
                    NỀN TẢNG THƯƠNG MẠI ĐIỆN TỬ CHUYÊN BIỆT THIẾT BỊ DI ĐỘNG
                </div>
                
                <h1 class="text-5xl md:text-6xl font-bold leading-none tracking-[-2px]">
                    IMEX<br>Thiết bị di động<br><span class="text-white/90">Mua sắm thông minh – Kết nối toàn diện</span>
                </h1>
                
                <p class="text-xl text-white/90 max-w-md">
                    Cầu nối giữa nhà sản xuất, nhà phân phối và người tiêu dùng. 
                    Tìm kiếm – So sánh – Mua hàng – Bảo hành – Hỗ trợ chỉ trong 1 nền tảng.
                </p>
                
                <div class="flex flex-wrap gap-4">
                    <button onclick="exploreNow()" 
                            class="bg-white text-[#e30613] hover:bg-yellow-300 font-semibold px-8 py-4 rounded-3xl text-lg flex items-center gap-x-3 shadow-xl">
                        <span>Khám phá ngay</span>
                        <i class="fa-solid fa-arrow-right"></i>
                    </button>
                    
                    <button onclick="watchVideo()" 
                            class="border-2 border-white hover:bg-white hover:text-[#e30613] font-semibold px-8 py-4 rounded-3xl text-lg flex items-center gap-x-3">
                        <i class="fa-solid fa-play"></i>
                        <span>Xem video giới thiệu</span>
                    </button>
                </div>
                
                <div class="flex items-center gap-x-8 text-sm">
                    <div class="flex items-center">
                        <div class="flex -space-x-4">
                            <div class="w-6 h-6 bg-white rounded-2xl flex items-center justify-center text-xs">📱</div>
                            <div class="w-6 h-6 bg-white rounded-2xl flex items-center justify-center text-xs">💻</div>
                        </div>
                        <span class="ml-3">+50.000 sản phẩm</span>
                    </div>
                    <div>⭐ 4.98/5 từ 28.451 đánh giá</div>
                    <div class="flex items-center gap-x-1">
                        <i class="fa-solid fa-truck text-yellow-300"></i>
                        <span>Giao hàng toàn quốc trong 24h</span>
                    </div>
                </div>
            </div>
            
            <!-- Hero visual -->
            <div class="relative flex justify-center">
                <div class="relative">
                    <!-- Floating phones -->
                    <div class="phone-float absolute -left-6 top-8 bg-white rounded-3xl shadow-2xl p-3 w-36 rotate-[-12deg]">
                        <div class="bg-black rounded-2xl p-1">
                            <div class="bg-gradient-to-br from-blue-400 to-purple-500 h-64 rounded-2xl flex items-center justify-center text-white text-4xl">iPhone 16</div>
                        </div>
                        <div class="text-center text-xs font-bold text-[#e30613] mt-2">16 Pro Max • 256GB</div>
                    </div>
                    
                    <div class="phone-float absolute -right-8 bottom-12 bg-white rounded-3xl shadow-2xl p-3 w-36 rotate-[12deg]">
                        <div class="bg-black rounded-2xl p-1">
                            <div class="bg-gradient-to-br from-emerald-400 to-teal-500 h-64 rounded-2xl flex items-center justify-center text-white text-4xl">Galaxy S25</div>
                        </div>
                        <div class="text-center text-xs font-bold text-[#e30613] mt-2">Ultra • 512GB</div>
                    </div>
                    
                    <!-- Center main phone -->
                    <div class="relative z-10 bg-white rounded-[3rem] shadow-2xl p-4 w-80 mx-auto">
                        <div class="bg-black rounded-3xl overflow-hidden">
                            <div class="h-96 bg-gradient-to-br from-orange-400 via-red-500 to-pink-500 flex flex-col items-center justify-center text-white">
                                <div class="text-7xl mb-4">📱</div>
                                <div class="text-center">
                                    <div class="text-2xl font-bold">IMEX Store</div>
                                    <div class="text-sm opacity-75">Thiết bị di động chính hãng</div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- TRUST BAR -->
    <div class="bg-white py-4 border-b">
        <div class="max-w-7xl mx-auto px-6 flex flex-wrap justify-center md:justify-between items-center gap-x-8 gap-y-3 text-sm text-gray-500">
            <div class="flex items-center gap-x-2"><i class="fa-solid fa-shield-halved text-[#e30613]"></i> Bảo hành chính hãng 24 tháng</div>
            <div class="flex items-center gap-x-2"><i class="fa-solid fa-truck-fast text-[#e30613]"></i> Giao hàng miễn phí từ 5 triệu</div>
            <div class="flex items-center gap-x-2"><i class="fa-solid fa-headset text-[#e30613]"></i> Hỗ trợ 24/7 qua chat &amp; hotline</div>
            <div class="flex items-center gap-x-2"><i class="fa-solid fa-rotate-left text-[#e30613]"></i> Đổi trả trong 30 ngày</div>
            <div class="flex items-center gap-x-2"><i class="fa-solid fa-lock text-[#e30613]"></i> Thanh toán an toàn 100%</div>
        </div>
    </div>

    <!-- TỔNG QUAN DỰ ÁN -->
    <section class="max-w-7xl mx-auto px-6 py-20">
        <div class="text-center mb-12">
            <span class="px-4 py-1 bg-red-100 text-[#e30613] text-sm font-semibold rounded-3xl">1. TỔNG QUAN DỰ ÁN</span>
            <h2 class="section-title text-4xl font-bold mt-3">IMEX – Cầu nối hoàn hảo cho thế giới di động</h2>
        </div>
        
        <div class="grid md:grid-cols-12 gap-12 items-center">
            <div class="md:col-span-7">
                <p class="text-lg text-gray-700 leading-relaxed">
                    Nền tảng đóng vai trò là cầu nối giữa các nhà cung cấp, doanh nghiệp và người tiêu dùng, giúp quá trình tìm kiếm, giao dịch, thanh toán và giao nhận sản phẩm được thực hiện một cách nhanh chóng, thuận tiện và an toàn. 
                    Hệ thống còn tích hợp nhiều dịch vụ hỗ trợ như tư vấn, bảo hành và chăm sóc khách hàng, góp phần nâng cao trải nghiệm người dùng và thúc đẩy sự phát triển của thị trường thương mại điện tử trong lĩnh vực thiết bị di động.
                </p>
                <div class="mt-8 flex items-center gap-x-6">
                    <div class="text-center">
                        <div class="text-4xl font-bold text-[#e30613]">1.2M+</div>
                        <div class="text-sm text-gray-500">Người dùng hoạt động</div>
                    </div>
                    <div class="text-center">
                        <div class="text-4xl font-bold text-[#e30613]">8.500+</div>
                        <div class="text-sm text-gray-500">Cửa hàng &amp; đối tác</div>
                    </div>
                    <div class="text-center">
                        <div class="text-4xl font-bold text-[#e30613]">320.000+</div>
                        <div class="text-sm text-gray-500">Đơn hàng/tháng</div>
                    </div>
                </div>
            </div>
            
            <div class="md:col-span-5 bg-gray-50 rounded-3xl p-8 border border-gray-100">
                <h3 class="font-semibold mb-4 flex items-center gap-x-2 text-[#e30613]"><i class="fa-solid fa-circle-nodes"></i> Hệ sinh thái IMEX</h3>
                <ul class="space-y-4 text-gray-700">
                    <li class="flex items-center gap-x-3"><span class="text-2xl">🏭</span> Nhà sản xuất thiết bị</li>
                    <li class="flex items-center gap-x-3"><span class="text-2xl">🚚</span> Nhà phân phối ủy quyền</li>
                    <li class="flex items-center gap-x-3"><span class="text-2xl">🛒</span> Các nhà bán lẻ thiết bị</li>
                    <li class="flex items-center gap-x-3"><span class="text-2xl">📦</span> Đơn vị logistics</li>
                    <li class="flex items-center gap-x-3"><span class="text-2xl">🔧</span> Trung tâm sửa chữa và bảo hành</li>
                    <li class="flex items-center gap-x-3"><span class="text-2xl">👤</span> Người tiêu dùng cuối cùng</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- SẢN PHẨM NỔI BẬT -->
    <section id="san-pham" class="bg-gray-50 py-20">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex justify-between items-end mb-12">
                <div>
                    <span class="text-[#e30613] font-semibold">SẢN PHẨM HOT</span>
                    <h2 class="text-4xl font-bold">Thiết bị di động mới nhất</h2>
                </div>
                <a href="#" onclick="viewAllProducts()" class="text-[#e30613] flex items-center gap-x-2 font-medium">Xem tất cả <i class="fa-solid fa-arrow-right"></i></a>
            </div>
            
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-6">
                <!-- Product Card 1 -->
                <div class="bg-white rounded-3xl overflow-hidden border card-hover">
                    <div class="h-48 bg-gradient-to-br from-slate-900 to-black flex items-center justify-center text-7xl">📱</div>
                    <div class="p-4">
                        <div class="text-xs bg-green-100 text-green-700 w-fit px-3 py-px rounded-full">iOS 18</div>
                        <h4 class="font-semibold mt-2">iPhone 16 Pro Max 256GB</h4>
                        <div class="flex justify-between items-baseline mt-4">
                            <div>
                                <span class="line-through text-xs text-gray-400">32.990.000 ₫</span>
                                <span class="text-2xl font-bold text-[#e30613]">29.990.000 ₫</span>
                            </div>
                            <button onclick="addToCart(this)" class="bg-[#e30613] text-white px-5 py-2 rounded-2xl text-sm">Mua ngay</button>
                        </div>
                    </div>
                </div>
                
                <!-- Product Card 2 -->
                <div class="bg-white rounded-3xl overflow-hidden border card-hover">
                    <div class="h-48 bg-gradient-to-br from-blue-600 to-cyan-500 flex items-center justify-center text-7xl">📱</div>
                    <div class="p-4">
                        <div class="text-xs bg-blue-100 text-blue-700 w-fit px-3 py-px rounded-full">Android 15</div>
                        <h4 class="font-semibold mt-2">Samsung Galaxy S25 Ultra</h4>
                        <div class="flex justify-between items-baseline mt-4">
                            <div>
                                <span class="line-through text-xs text-gray-400">34.990.000 ₫</span>
                                <span class="text-2xl font-bold text-[#e30613]">31.490.000 ₫</span>
                            </div>
                            <button onclick="addToCart(this)" class="bg-[#e30613] text-white px-5 py-2 rounded-2xl text-sm">Mua ngay</button>
                        </div>
                    </div>
                </div>
                
                <!-- Product Card 3 -->
                <div class="bg-white rounded-3xl overflow-hidden border card-hover">
                    <div class="h-48 bg-gradient-to-br from-purple-600 to-violet-500 flex items-center justify-center text-7xl">📱</div>
                    <div class="p-4">
                        <div class="text-xs bg-purple-100 text-purple-700 w-fit px-3 py-px rounded-full">5G</div>
                        <h4 class="font-semibold mt-2">Xiaomi 14T Pro 12/512GB</h4>
                        <div class="flex justify-between items-baseline mt-4">
                            <div>
                                <span class="text-2xl font-bold text-[#e30613]">15.990.000 ₫</span>
                            </div>
                            <button onclick="addToCart(this)" class="bg-[#e30613] text-white px-5 py-2 rounded-2xl text-sm">Mua ngay</button>
                        </div>
                    </div>
                </div>
                
                <!-- Product Card 4 -->
                <div class="bg-white rounded-3xl overflow-hidden border card-hover">
                    <div class="h-48 bg-gradient-to-br from-red-500 to-orange-500 flex items-center justify-center text-7xl">📱</div>
                    <div class="p-4">
                        <div class="text-xs bg-red-100 text-red-700 w-fit px-3 py-px rounded-full">Pin 7000mAh</div>
                        <h4 class="font-semibold mt-2">OPPO Reno12 5G</h4>
                        <div class="flex justify-between items-baseline mt-4">
                            <div>
                                <span class="text-2xl font-bold text-[#e30613]">12.490.000 ₫</span>
                            </div>
                            <button onclick="addToCart(this)" class="bg-[#e30613] text-white px-5 py-2 rounded-2xl text-sm">Mua ngay</button>
                        </div>
                    </div>
                </div>
                
                <!-- Product Card 5 -->
                <div class="bg-white rounded-3xl overflow-hidden border card-hover">
                    <div class="h-48 bg-gradient-to-br from-emerald-500 to-teal-500 flex items-center justify-center text-7xl">💻</div>
                    <div class="p-4">
                        <div class="text-xs bg-emerald-100 text-emerald-700 w-fit px-3 py-px rounded-full">Tablet</div>
                        <h4 class="font-semibold mt-2">iPad Air M3 11 inch</h4>
                        <div class="flex justify-between items-baseline mt-4">
                            <div>
                                <span class="line-through text-xs text-gray-400">19.990.000 ₫</span>
                                <span class="text-2xl font-bold text-[#e30613]">17.990.000 ₫</span>
                            </div>
                            <button onclick="addToCart(this)" class="bg-[#e30613] text-white px-5 py-2 rounded-2xl text-sm">Mua ngay</button>
                        </div>
                    </div>
                </div>
                
                <!-- Product Card 6 -->
                <div class="bg-white rounded-3xl overflow-hidden border card-hover">
                    <div class="h-48 bg-gradient-to-br from-amber-400 to-yellow-500 flex items-center justify-center text-7xl">⌚</div>
                    <div class="p-4">
                        <div class="text-xs bg-amber-100 text-amber-700 w-fit px-3 py-px rounded-full">Smartwatch</div>
                        <h4 class="font-semibold mt-2">Apple Watch Ultra 2</h4>
                        <div class="flex justify-between items-baseline mt-4">
                            <div>
                                <span class="text-2xl font-bold text-[#e30613]">21.990.000 ₫</span>
                            </div>
                            <button onclick="addToCart(this)" class="bg-[#e30613] text-white px-5 py-2 rounded-2xl text-sm">Mua ngay</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- TÍNH NĂNG CHÍNH -->
    <section id="tinh-nang" class="max-w-7xl mx-auto px-6 py-20">
        <div class="text-center mb-12">
            <span class="px-4 py-1 bg-red-100 text-[#e30613] text-sm font-semibold rounded-3xl">1.2. CÁC TÍNH NĂNG CHÍNH</span>
            <h2 class="section-title text-4xl font-bold mt-3">Hệ sinh thái thương mại điện tử toàn diện</h2>
        </div>
        
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
            <!-- Feature 1 -->
            <div class="bg-white border rounded-3xl p-8 card-hover">
                <div class="w-14 h-14 flex items-center justify-center bg-red-100 text-[#e30613] rounded-2xl text-4xl mb-6">📦</div>
                <h3 class="text-2xl font-semibold mb-2">Quản lý sản phẩm</h3>
                <p class="text-gray-600">Hiển thị thông tin chi tiết thiết bị di động, thông số kỹ thuật, hình ảnh, giá bán và đánh giá người dùng.</p>
                <div class="mt-8 text-[#e30613] font-medium flex items-center">Khám phá ngay <i class="fa-solid fa-arrow-right ml-2"></i></div>
            </div>
            
            <!-- Feature 2 -->
            <div class="bg-white border rounded-3xl p-8 card-hover">
                <div class="w-14 h-14 flex items-center justify-center bg-red-100 text-[#e30613] rounded-2xl text-4xl mb-6">⚖️</div>
                <h3 class="text-2xl font-semibold mb-2">Hệ thống đối chiếu thông số</h3>
                <p class="text-gray-600">So sánh nhiều thiết bị theo cấu hình, hiệu năng, pin, camera, giá bán… giúp bạn chọn được sản phẩm phù hợp nhất.</p>
                <div onclick="openCompareModal()" class="mt-8 text-[#e30613] font-medium flex items-center cursor-pointer">Bắt đầu so sánh <i class="fa-solid fa-arrow-right ml-2"></i></div>
            </div>
            
            <!-- Feature 3 -->
            <div class="bg-white border rounded-3xl p-8 card-hover">
                <div class="w-14 h-14 flex items-center justify-center bg-red-100 text-[#e30613] rounded-2xl text-4xl mb-6">🛒</div>
                <h3 class="text-2xl font-semibold mb-2">Giao dịch &amp; Thanh toán trực tuyến</h3>
                <p class="text-gray-600">Giỏ hàng, đặt hàng, thanh toán điện tử, quản lý đơn hàng và theo dõi giao hàng thời gian thực.</p>
                <div class="mt-8 text-[#e30613] font-medium flex items-center">Mua sắm ngay <i class="fa-solid fa-arrow-right ml-2"></i></div>
            </div>
            
            <!-- Feature 4 -->
            <div class="bg-white border rounded-3xl p-8 card-hover">
                <div class="w-14 h-14 flex items-center justify-center bg-red-100 text-[#e30613] rounded-2xl text-4xl mb-6">🔐</div>
                <h3 class="text-2xl font-semibold mb-2">Bảo hành điện tử</h3>
                <p class="text-gray-600">Lưu trữ và quản lý thông tin bảo hành trên hệ thống. Tra cứu nhanh, sử dụng dịch vụ hỗ trợ chỉ với 1 click.</p>
                <div onclick="navigateToSection('bao-hanh')" class="mt-8 text-[#e30613] font-medium flex items-center cursor-pointer">Kiểm tra bảo hành <i class="fa-solid fa-arrow-right ml-2"></i></div>
            </div>
            
            <!-- Feature 5 -->
            <div class="bg-white border rounded-3xl p-8 card-hover">
                <div class="w-14 h-14 flex items-center justify-center bg-red-100 text-[#e30613] rounded-2xl text-4xl mb-6">👥</div>
                <h3 class="text-2xl font-semibold mb-2">Cộng đồng người dùng công nghệ</h3>
                <p class="text-gray-600">Chia sẻ đánh giá, kinh nghiệm sử dụng, hỏi đáp và kết nối với hàng ngàn tín đồ công nghệ.</p>
                <div onclick="navigateToSection('cong-dong')" class="mt-8 text-[#e30613] font-medium flex items-center cursor-pointer">Tham gia ngay <i class="fa-solid fa-arrow-right ml-2"></i></div>
            </div>
            
            <!-- Feature 6 -->
            <div class="bg-white border rounded-3xl p-8 card-hover flex flex-col">
                <div class="w-14 h-14 flex items-center justify-center bg-red-100 text-[#e30613] rounded-2xl text-4xl mb-6">📍</div>
                <h3 class="text-2xl font-semibold mb-2">Tư vấn &amp; Hỗ trợ cá nhân hóa</h3>
                <p class="text-gray-600 flex-1">AI gợi ý sản phẩm phù hợp với nhu cầu, ngân sách và phong cách sử dụng của bạn.</p>
                <button onclick="talkToAI()" class="mt-auto border border-[#e30613] text-[#e30613] hover:bg-[#e30613] hover:text-white py-3 rounded-3xl font-semibold flex justify-center items-center gap-x-2">
                    <i class="fa-solid fa-robot"></i> Nói chuyện với IMEX AI
                </button>
            </div>
        </div>
    </section>

    <!-- SO SÁNH THÔNG SỐ (Demo Modal Trigger) -->
    <div onclick="openCompareModal()" class="max-w-7xl mx-auto px-6 py-12 bg-gradient-to-r from-red-50 to-white border-y flex flex-col md:flex-row items-center justify-between cursor-pointer hover:from-red-100">
        <div class="flex items-center gap-x-6">
            <i class="fa-solid fa-chart-simple text-5xl text-[#e30613]"></i>
            <div>
                <span class="uppercase tracking-widest text-xs font-bold text-[#e30613]">Công cụ độc quyền</span>
                <h3 class="text-3xl font-bold">So sánh thông số kỹ thuật nhanh chóng</h3>
            </div>
        </div>
        <div class="text-[#e30613] text-2xl font-semibold flex items-center mt-6 md:mt-0">
            Thử ngay <i class="fa-solid fa-arrow-right ml-4"></i>
        </div>
    </div>

    <!-- HỆ SINH THÁI -->
    <section id="he-sinh-thai" class="max-w-7xl mx-auto px-6 py-20">
        <div class="text-center mb-12">
            <h2 class="section-title text-4xl font-bold">Hệ sinh thái IMEX kết nối toàn chuỗi giá trị</h2>
        </div>
        <div class="flex flex-wrap justify-center gap-6">
            <div class="bg-white shadow-sm px-8 py-6 rounded-3xl flex items-center gap-x-4 w-64 text-center border border-transparent hover:border-[#e30613]">
                <span class="text-5xl">🏭</span>
                <div class="text-left">
                    <strong>Nhà sản xuất</strong>
                    <div class="text-xs text-gray-500">Apple • Samsung • Xiaomi • Oppo</div>
                </div>
            </div>
            <div class="bg-white shadow-sm px-8 py-6 rounded-3xl flex items-center gap-x-4 w-64 text-center border border-transparent hover:border-[#e30613]">
                <span class="text-5xl">📦</span>
                <div class="text-left">
                    <strong>Nhà phân phối</strong>
                    <div class="text-xs text-gray-500">FPT Shop • The Gioi Di Dong • CellphoneS</div>
                </div>
            </div>
            <div class="bg-white shadow-sm px-8 py-6 rounded-3xl flex items-center gap-x-4 w-64 text-center border border-transparent hover:border-[#e30613]">
                <span class="text-5xl">🛍️</span>
                <div class="text-left">
                    <strong>Nhà bán lẻ</strong>
                    <div class="text-xs text-gray-500">Hơn 2.800 cửa hàng trên toàn quốc</div>
                </div>
            </div>
            <div class="bg-white shadow-sm px-8 py-6 rounded-3xl flex items-center gap-x-4 w-64 text-center border border-transparent hover:border-[#e30613]">
                <span class="text-5xl">🚚</span>
                <div class="text-left">
                    <strong>Logistics</strong>
                    <div class="text-xs text-gray-500">GHN • GHTK • Viettel Post</div>
                </div>
            </div>
            <div class="bg-white shadow-sm px-8 py-6 rounded-3xl flex items-center gap-x-4 w-64 text-center border border-transparent hover:border-[#e30613]">
                <span class="text-5xl">🔧</span>
                <div class="text-left">
                    <strong>Bảo hành &amp; Sửa chữa</strong>
                    <div class="text-xs text-gray-500">Hơn 450 trung tâm ủy quyền</div>
                </div>
            </div>
        </div>
    </section>

    <!-- CỘNG ĐỒNG -->
    <section id="cong-dong" class="bg-[#e30613] text-white py-20">
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid md:grid-cols-2 gap-12 items-center">
                <div>
                    <h2 class="text-4xl font-bold mb-6">Cộng đồng IMEX – Nơi tín đồ công nghệ gặp gỡ</h2>
                    <p class="text-white/90 text-lg">Chia sẻ đánh giá thực tế, kinh nghiệm sử dụng, hỏi đáp chuyên sâu và cùng nhau khám phá những sản phẩm di động mới nhất.</p>
                    <div class="mt-10 flex gap-4">
                        <button onclick="joinCommunity()" class="bg-white text-[#e30613] px-10 py-4 rounded-3xl font-semibold flex-1 md:flex-none">Tham gia cộng đồng miễn phí</button>
                        <button onclick="navigateToSection('tinh-nang')" class="border border-white px-10 py-4 rounded-3xl flex-1 md:flex-none">Xem bài viết nổi bật</button>
                    </div>
                </div>
                <div class="grid grid-cols-2 gap-4">
                    <div class="bg-white/10 backdrop-blur-md rounded-3xl p-5 text-sm">
                        “Mình mua iPhone 16 qua IMEX, giao hàng siêu nhanh và bảo hành điện tử rất tiện!”<br>
                        <span class="block mt-4 text-xs opacity-75">@techvinh123</span>
                    </div>
                    <div class="bg-white/10 backdrop-blur-md rounded-3xl p-5 text-sm">
                        “Công cụ so sánh thông số giúp mình chọn được Galaxy S25 Ultra đúng nhu cầu trong 2 phút.”<br>
                        <span class="block mt-4 text-xs opacity-75">@gadgetlover</span>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- BẢO HÀNH -->
    <section id="bao-hanh" class="max-w-7xl mx-auto px-6 py-20">
        <div class="rounded-3xl bg-gradient-to-r from-[#e30613] to-red-700 text-white p-12 md:p-16 flex flex-col md:flex-row items-center gap-12">
            <div class="flex-1">
                <h2 class="text-4xl font-bold">Bảo hành điện tử – Chỉ 1 click là kiểm tra được</h2>
                <p class="mt-4 text-white/90">Nhập IMEI hoặc số serial → Xem ngay thời hạn bảo hành, lịch sử sửa chữa và đặt lịch hỗ trợ.</p>
                <div class="mt-8 flex gap-x-3">
                    <input type="text" id="imei-input" placeholder="Nhập IMEI / Serial number" class="flex-1 bg-white/20 placeholder:text-white/60 text-white border border-white/30 rounded-3xl px-6 py-4 outline-none">
                    <button onclick="checkWarranty()" class="bg-white text-[#e30613] px-10 font-semibold rounded-3xl">Kiểm tra</button>
                </div>
            </div>
            <div class="flex-1 text-center">
                <div class="inline-flex flex-col items-center bg-white/10 backdrop-blur-md rounded-3xl px-12 py-8">
                    <i class="fa-solid fa-qrcode text-8xl mb-4"></i>
                    <p class="text-xl font-medium">Hoặc quét mã QR trên hộp sản phẩm</p>
                    <div class="mt-6 text-xs opacity-70">Đã hỗ trợ 128.459 thiết bị • Cập nhật realtime</div>
                </div>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-gray-900 text-white">
        <div class="max-w-7xl mx-auto px-6 pt-16 pb-8">
            <div class="grid grid-cols-2 md:grid-cols-5 gap-y-10">
                <div>
                    <div class="flex items-center gap-x-3 mb-6">
                        <div class="w-9 h-9 bg-white rounded-2xl flex items-center justify-center text-[#e30613] text-3xl">📱</div>
                        <h1 class="text-3xl font-bold">IMEX</h1>
                    </div>
                    <p class="text-sm text-gray-400">Nền tảng thương mại điện tử chuyên biệt thiết bị di động hàng đầu Việt Nam.</p>
                    <div class="mt-6 flex gap-x-4 text-2xl">
                        <i class="fa-brands fa-facebook"></i>
                        <i class="fa-brands fa-youtube"></i>
                        <i class="fa-brands fa-tiktok"></i>
                        <i class="fa-brands fa-zalo"></i>
                    </div>
                </div>
                
                <div>
                    <strong class="text-sm block mb-4">Sản phẩm</strong>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li>Điện thoại</li>
                        <li>Máy tính bảng</li>
                        <li>Đồng hồ thông minh</li>
                        <li>Phụ kiện chính hãng</li>
                    </ul>
                </div>
                
                <div>
                    <strong class="text-sm block mb-4">Tính năng</strong>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li>So sánh thông số</li>
                        <li>Bảo hành điện tử</li>
                        <li>Cộng đồng IMEX</li>
                        <li>IMEX AI tư vấn</li>
                    </ul>
                </div>
                
                <div>
                    <strong class="text-sm block mb-4">Công ty</strong>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li>Về IMEX</li>
                        <li>Tuyển dụng</li>
                        <li>Blog công nghệ</li>
                        <li>Liên hệ</li>
                    </ul>
                </div>
                
                <div>
                    <strong class="text-sm block mb-4">Hỗ trợ</strong>
                    <ul class="space-y-2 text-sm text-gray-400">
                        <li>Hotline: 1900 68 68 68</li>
                        <li>Chat trực tiếp</li>
                        <li>Chính sách đổi trả</li>
                        <li>Điều khoản dịch vụ</li>
                    </ul>
                    <div class="mt-8 bg-white/10 rounded-2xl p-4 text-xs">
                        © 2026 IMEX Corporation. All Rights Reserved.<br>
                        <span class="text-[#e30613]">Được xây dựng dựa trên tài liệu dự án</span>
                    </div>
                </div>
            </div>
        </div>
    </footer>

    <!-- COMPARE MODAL -->
    <div onclick="if(event.target.id === 'compare-modal')hideCompareModal()" id="compare-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" class="bg-white rounded-3xl max-w-4xl w-full mx-4 max-h-[90vh] overflow-hidden">
            <div class="p-6 border-b flex justify-between items-center">
                <h3 class="font-bold text-2xl">So sánh thiết bị di động</h3>
                <button onclick="hideCompareModal()" class="text-3xl text-gray-400">×</button>
            </div>
            <div class="p-6">
                <p class="text-center text-gray-500 mb-6">Chọn tối đa 4 sản phẩm để so sánh thông số</p>
                <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                    <div class="border rounded-2xl p-4 text-center cursor-pointer hover:border-[#e30613]" onclick="selectProduct(this)">
                        iPhone 16 Pro Max
                    </div>
                    <div class="border rounded-2xl p-4 text-center cursor-pointer hover:border-[#e30613]" onclick="selectProduct(this)">
                        Galaxy S25 Ultra
                    </div>
                    <div class="border rounded-2xl p-4 text-center cursor-pointer hover:border-[#e30613]" onclick="selectProduct(this)">
                        Xiaomi 14T Pro
                    </div>
                    <div class="border rounded-2xl p-4 text-center cursor-pointer hover:border-[#e30613]" onclick="selectProduct(this)">
                        OPPO Reno12 Pro
                    </div>
                </div>
                <button onclick="simulateComparison()" class="mt-8 w-full py-4 bg-[#e30613] text-white rounded-3xl font-semibold">BẮT ĐẦU SO SÁNH NGAY</button>
            </div>
        </div>
    </div>

    <script>
        // Tailwind script initialization
        function initializeTailwind() {
            return {
                config(userConfig = {}) {
                    return {
                        configUser: userConfig,
                        defaultTheme: {
                            extend: {
                                colors: {
                                    primary: '#e30613'
                                }
                            }
                        }
                    }
                },
                theme(userConfig = {}) {
                    return {
                        ...this.defaultTheme,
                        ...this.config(userConfig).theme
                    }
                }
            }
        }
        
        // Main script
        function init() {
            initializeTailwind().theme()
            
            // Fake live cart count
            let count = 3
            setInterval(() => {
                count++
                if (count > 9) count = 3
                const el = document.getElementById('cart-count')
                if (el) el.textContent = count
            }, 8000)
            
            console.log('%c✅ Trang web IMEX đã được khởi tạo thành công!', 'background:#e30613;color:#fff;padding:2px 6px;border-radius:4px')
        }
        
        // Navigation
        function navigateToSection(section) {
            const el = document.getElementById(section)
            if (el) {
                el.scrollIntoView({ behavior: 'smooth' })
            }
        }
        
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu')
            const icon = document.getElementById('mobile-icon')
            menu.classList.toggle('hidden')
            icon.classList.toggle('fa-bars')
            icon.classList.toggle('fa-xmark')
        }
        
        function toggleCart() {
            alert('🛒 Giỏ hàng của bạn có 3 sản phẩm. Bạn sẽ được chuyển đến trang giỏ hàng trong phiên bản đầy đủ!')
        }
        
        function showLogin() {
            alert('🔑 Chào mừng đến với IMEX!\n\nĐăng nhập / Đăng ký bằng số điện thoại hoặc Google/Apple ID.\n(Tính năng demo)')
        }
        
        function exploreNow() {
            navigateToSection('san-pham')
        }
        
        function watchVideo() {
            alert('🎥 Video giới thiệu IMEX (1 phút 48 giây)\n\nBạn đang xem demo. Trong phiên bản thực tế sẽ nhúng video YouTube.')
        }
        
        function addToCart(btn) {
            btn.innerHTML = '✅ Đã thêm'
            setTimeout(() => {
                btn.innerHTML = 'Mua ngay'
                alert('✅ Sản phẩm đã được thêm vào giỏ hàng!')
            }, 1200)
        }
        
        function openCompareModal() {
            document.getElementById('compare-modal').classList.remove('hidden')
            document.getElementById('compare-modal').classList.add('flex')
        }
        
        function hideCompareModal() {
            const modal = document.getElementById('compare-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        function selectProduct(el) {
            el.classList.toggle('border-[#e30613]')
            el.classList.toggle('bg-red-50')
        }
        
        function simulateComparison() {
            hideCompareModal()
            setTimeout(() => {
                alert('📊 Kết quả so sánh đã được hiển thị!\n\niPhone 16 Pro Max vs Galaxy S25 Ultra vs Xiaomi 14T Pro\n\nBạn có thể xem bảng so sánh chi tiết trong phiên bản đầy đủ của website.')
            }, 800)
        }
        
        function checkWarranty() {
            const input = document.getElementById('imei-input').value
            if (input.length > 5) {
                alert('✅ Bảo hành hợp lệ!\nThiết bị: iPhone 16 Pro Max\nThời hạn: Còn 18 tháng 12 ngày\nTrung tâm gần nhất: Vinh, Nghệ An')
            } else {
                alert('Vui lòng nhập IMEI / Serial number hợp lệ')
            }
        }
        
        function talkToAI() {
            alert('🤖 IMEX AI: Chào bạn! Bạn đang tìm mua điện thoại nào? Mình có thể gợi ý dựa trên nhu cầu của bạn (pin trâu, camera đẹp, chơi game...). Hãy chat với mình nhé!')
        }
        
        function joinCommunity() {
            alert('👋 Chào mừng bạn đến với Cộng đồng IMEX!\nBạn đã được cấp tài khoản thử nghiệm ngay lập tức.')
            navigateToSection('cong-dong')
        }
        
        function viewAllProducts() {
            navigateToSection('san-pham')
        }
        
        // Start the app
        window.onload = init
    </script>
</body>
</html>
