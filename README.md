<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động">
    <title>IMEX | Thiết bị di động chính hãng - Mua sắm thông minh</title>
    <!-- Tailwind CSS CDN -->
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Font Awesome cho icon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Roboto:wght@400;500&amp;display=swap');
        
        :root {
            --primary: #001f3f; /* Xanh dương đậm chính thức */
            --accent: #0074d9;  /* Xanh dương nổi bật */
        }
        
        * {
            font-family: 'Inter', system_ui, sans-serif;
        }
        
        .nav-link {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .nav-link:hover {
            color: #0074d9;
            transform: translateY(-1px);
        }
        
        .hero-bg {
            background: linear-gradient(135deg, #001f3f 0%, #003366 100%);
        }
        
        .product-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-12px);
            box-shadow: 0 25px 50px -12px rgb(0 31 63 / 0.25);
        }
        
        .section-header {
            position: relative;
        }
        
        .section-header::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background: #0074d9;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 9999px;
        }
        
        .cart-count {
            animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
        }
    </style>
</head>
<body class="bg-white text-gray-900">
    <!-- NAVBAR -->
    <nav class="bg-[#001f3f] text-white sticky top-0 z-50 shadow-lg">
        <div class="max-w-7xl mx-auto px-6">
            <div class="flex items-center justify-between h-16">
                <!-- Logo -->
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 bg-white rounded-2xl flex items-center justify-center text-[#001f3f] font-bold text-3xl shadow-inner">
                        📱
                    </div>
                    <div>
                        <span class="text-3xl font-bold tracking-tighter">IMEX</span>
                        <span class="text-xs font-medium text-[#0074d9] block -mt-1">MOBILE</span>
                    </div>
                </div>

                <!-- Menu -->
                <div class="hidden md:flex items-center gap-8 text-sm font-medium">
                    <a href="#" onclick="navigateToSection('home')" class="nav-link">Trang chủ</a>
                    <a href="#" onclick="navigateToSection('products')" class="nav-link">Sản phẩm</a>
                    <a href="#" onclick="navigateToSection('services')" class="nav-link">Dịch vụ</a>
                    <a href="#" onclick="navigateToSection('about')" class="nav-link">Về IMEX</a>
                    <a href="#" onclick="navigateToSection('blog')" class="nav-link">Blog &amp; Tin tức</a>
                </div>

                <!-- Right side -->
                <div class="flex items-center gap-6">
                    <!-- Search -->
                    <div onclick="toggleSearch()" class="cursor-pointer relative group">
                        <i class="fa-solid fa-magnifying-glass text-xl"></i>
                    </div>
                    
                    <!-- Wishlist -->
                    <div class="cursor-pointer relative">
                        <i class="fa-solid fa-heart text-xl"></i>
                        <span class="absolute -top-1 -right-1 text-[10px] bg-red-500 text-white rounded-full w-4 h-4 flex items-center justify-center">3</span>
                    </div>
                    
                    <!-- Cart -->
                    <div onclick="showCart()" class="cursor-pointer relative flex items-center gap-1">
                        <i class="fa-solid fa-cart-shopping text-xl"></i>
                        <span id="cart-count" class="cart-count absolute -top-1 -right-1 bg-[#0074d9] text-white text-xs font-bold rounded-full w-5 h-5 flex items-center justify-center shadow">0</span>
                    </div>

                    <!-- User -->
                    <div class="flex items-center gap-2 cursor-pointer" onclick="toggleUserMenu()">
                        <div class="w-8 h-8 bg-white/20 backdrop-blur-md rounded-2xl flex items-center justify-center">
                            👤
                        </div>
                        <div class="hidden md:block">
                            <span class="text-sm font-medium">Tumay</span>
                        </div>
                    </div>

                    <!-- Mobile menu button -->
                    <button onclick="toggleMobileMenu()" class="md:hidden text-2xl">
                        <i class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
            
            <!-- Mobile Menu -->
            <div id="mobile-menu" class="hidden md:hidden bg-[#001f3f] py-4 border-t border-white/10">
                <div class="flex flex-col gap-4 px-6 text-sm font-medium">
                    <a href="#" onclick="navigateToSection('home');toggleMobileMenu()" class="py-2">Trang chủ</a>
                    <a href="#" onclick="navigateToSection('products');toggleMobileMenu()" class="py-2">Sản phẩm</a>
                    <a href="#" onclick="navigateToSection('services');toggleMobileMenu()" class="py-2">Dịch vụ</a>
                    <a href="#" onclick="navigateToSection('about');toggleMobileMenu()" class="py-2">Về IMEX</a>
                    <a href="#" onclick="navigateToSection('blog');toggleMobileMenu()" class="py-2">Blog &amp; Tin tức</a>
                </div>
            </div>
        </div>
    </nav>

    <!-- HERO SECTION -->
    <section id="home" class="hero-bg text-white pt-16 pb-20">
        <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
            <div class="space-y-8">
                <div class="inline-flex items-center gap-2 bg-white/10 backdrop-blur-md px-4 py-2 rounded-3xl text-sm">
                    <span class="bg-[#0074d9] text-white px-3 py-1 rounded-3xl text-xs font-semibold">MỚI 2026</span>
                    <span class="font-medium">Flagship Series ra mắt</span>
                </div>
                
                <h1 class="text-6xl md:text-7xl font-bold leading-none tracking-tighter">
                    Thiết bị di động<br>chính hãng - Giá tốt nhất
                </h1>
                
                <p class="text-xl text-white/80 max-w-md">
                    Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động.<br>
                    Hơn 10.000 sản phẩm • Giao hàng trong 2 giờ • Bảo hành chính hãng 24 tháng
                </p>
                
                <div class="flex items-center gap-4">
                    <button onclick="shopNow()" 
                            class="bg-white text-[#001f3f] font-semibold px-10 py-4 rounded-3xl flex items-center gap-3 hover:shadow-2xl hover:scale-105 transition-all">
                        <span>MUA NGAY</span>
                        <i class="fa-solid fa-arrow-right"></i>
                    </button>
                    
                    <button onclick="watchVideo()" 
                            class="border border-white/70 hover:border-white font-medium px-8 py-4 rounded-3xl flex items-center gap-3">
                        <i class="fa-solid fa-play"></i>
                        <span>Xem video</span>
                    </button>
                </div>
                
                <div class="flex items-center gap-8 text-sm">
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-shield-halved text-2xl text-[#0074d9]"></i>
                        <div>
                            <div class="font-semibold">Bảo hành 24 tháng</div>
                            <div class="text-white/70">Chính hãng</div>
                        </div>
                    </div>
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-truck-fast text-2xl text-[#0074d9]"></i>
                        <div>
                            <div class="font-semibold">Giao hàng siêu tốc</div>
                            <div class="text-white/70">2 giờ tại TP.HCM &amp; Hà Nội</div>
                        </div>
                    </div>
                    <div class="flex items-center gap-2">
                        <i class="fa-solid fa-rotate-left text-2xl text-[#0074d9]"></i>
                        <div>
                            <div class="font-semibold">Đổi trả 30 ngày</div>
                            <div class="text-white/70">Không lý do</div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Hero Image -->
            <div class="relative flex justify-center">
                <div class="bg-white/10 backdrop-blur-3xl rounded-[4rem] p-8 shadow-2xl">
                    <img src="https://picsum.photos/id/1015/800/800" 
                         alt="iPhone 16 Pro Max Titan Black"
                         class="w-[420px] h-[420px] object-contain drop-shadow-2xl rotate-12 hover:rotate-0 transition-transform duration-700">
                </div>
                <!-- Floating badges -->
                <div class="absolute -top-6 -right-6 bg-white text-[#001f3f] px-6 py-3 rounded-3xl shadow-xl flex items-center gap-3 font-semibold">
                    <span class="text-3xl">⭐</span>
                    <div>
                        <div>4.98/5</div>
                        <div class="text-xs text-gray-500">Từ 12.458 đánh giá</div>
                    </div>
                </div>
                <div class="absolute -bottom-4 -left-6 bg-[#0074d9] text-white px-5 py-2 rounded-3xl text-sm font-semibold shadow-xl flex items-center">
                    <i class="fa-solid fa-fire mr-2"></i>
                    BÁN CHẠY NHẤT
                </div>
            </div>
        </div>
    </section>

    <!-- CATEGORIES -->
    <div class="max-w-7xl mx-auto px-6 py-12">
        <div class="grid grid-cols-3 md:grid-cols-6 gap-4">
            <a onclick="filterCategory('phone')" class="category-card flex flex-col items-center justify-center bg-white border border-gray-100 hover:border-[#0074d9] rounded-3xl py-8 transition-all hover:shadow-md">
                <i class="fa-solid fa-mobile-screen-button text-4xl text-[#001f3f] mb-4"></i>
                <span class="font-semibold">Điện thoại</span>
            </a>
            <a onclick="filterCategory('tablet')" class="category-card flex flex-col items-center justify-center bg-white border border-gray-100 hover:border-[#0074d9] rounded-3xl py-8 transition-all hover:shadow-md">
                <i class="fa-solid fa-tablet-screen-button text-4xl text-[#001f3f] mb-4"></i>
                <span class="font-semibold">Máy tính bảng</span>
            </a>
            <a onclick="filterCategory('watch')" class="category-card flex flex-col items-center justify-center bg-white border border-gray-100 hover:border-[#0074d9] rounded-3xl py-8 transition-all hover:shadow-md">
                <i class="fa-solid fa-watch text-4xl text-[#001f3f] mb-4"></i>
                <span class="font-semibold">Đồng hồ thông minh</span>
            </a>
            <a onclick="filterCategory('earbud')" class="category-card flex flex-col items-center justify-center bg-white border border-gray-100 hover:border-[#0074d9] rounded-3xl py-8 transition-all hover:shadow-md">
                <i class="fa-solid fa-headphones text-4xl text-[#001f3f] mb-4"></i>
                <span class="font-semibold">Tai nghe</span>
            </a>
            <a onclick="filterCategory('accessory')" class="category-card flex flex-col items-center justify-center bg-white border border-gray-100 hover:border-[#0074d9] rounded-3xl py-8 transition-all hover:shadow-md">
                <i class="fa-solid fa-charging-station text-4xl text-[#001f3f] mb-4"></i>
                <span class="font-semibold">Phụ kiện</span>
            </a>
            <a onclick="filterCategory('refurbished')" class="category-card flex flex-col items-center justify-center bg-white border border-gray-100 hover:border-[#0074d9] rounded-3xl py-8 transition-all hover:shadow-md">
                <i class="fa-solid fa-recycle text-4xl text-[#001f3f] mb-4"></i>
                <span class="font-semibold">Hàng tân trang</span>
            </a>
        </div>
    </div>

    <!-- PRODUCTS SECTION -->
    <section id="products" class="max-w-7xl mx-auto px-6 py-16 bg-gray-50">
        <div class="flex justify-between items-end mb-12">
            <div>
                <span class="px-4 py-1 bg-[#0074d9] text-white text-sm font-semibold rounded-3xl">HOT</span>
                <h2 class="section-header text-4xl font-semibold mt-3">Sản phẩm nổi bật</h2>
            </div>
            <a href="#" onclick="viewAllProducts()" class="flex items-center gap-2 text-[#0074d9] font-medium hover:gap-4 transition-all">
                Xem tất cả <i class="fa-solid fa-arrow-right"></i>
            </a>
        </div>
        
        <div id="product-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
            <!-- Products populated by JS -->
        </div>
    </section>

    <!-- SERVICES -->
    <section id="services" class="max-w-7xl mx-auto px-6 py-16">
        <h2 class="section-header text-4xl font-semibold text-center mb-12">Dịch vụ tiện ích độc quyền IMEX</h2>
        
        <div class="grid md:grid-cols-3 gap-8">
            <div class="bg-white border border-gray-100 p-8 rounded-3xl hover:border-[#0074d9] transition-all">
                <i class="fa-solid fa-screwdriver-wrench text-5xl text-[#001f3f] mb-6"></i>
                <h3 class="text-2xl font-semibold mb-2">Sửa chữa nhanh 30 phút</h3>
                <p class="text-gray-600">Đội ngũ kỹ thuật viên chuyên nghiệp, linh kiện chính hãng. Bảo hành sửa chữa 6 tháng.</p>
                <div class="mt-8 text-[#0074d9] font-medium">Đặt lịch ngay →</div>
            </div>
            
            <div class="bg-white border border-gray-100 p-8 rounded-3xl hover:border-[#0074d9] transition-all">
                <i class="fa-solid fa-mobile-retro text-5xl text-[#001f3f] mb-6"></i>
                <h3 class="text-2xl font-semibold mb-2">Trade-in - Thu cũ đổi mới</h3>
                <p class="text-gray-600">Đánh giá máy cũ trong 60 giây. Trợ giá lên đến 40% cho máy mới.</p>
                <div class="mt-8 text-[#0074d9] font-medium">Kiểm tra máy cũ →</div>
            </div>
            
            <div class="bg-white border border-gray-100 p-8 rounded-3xl hover:border-[#0074d9] transition-all">
                <i class="fa-solid fa-credit-card text-5xl text-[#001f3f] mb-6"></i>
                <h3 class="text-2xl font-semibold mb-2">Trả góp 0% lãi suất</h3>
                <p class="text-gray-600">Lên đến 24 tháng. Duyệt hồ sơ chỉ trong 5 phút. Không cần chứng minh thu nhập.</p>
                <div class="mt-8 text-[#0074d9] font-medium">Tính toán trả góp →</div>
            </div>
        </div>
    </section>

    <!-- ABOUT -->
    <section id="about" class="bg-[#001f3f] text-white py-16">
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid md:grid-cols-12 gap-16 items-center">
                <div class="md:col-span-5">
                    <h2 class="text-5xl font-semibold mb-6 leading-none">IMEX - Nền tảng<br>Thương mại điện tử<br>chuyên biệt Thiết bị di động</h2>
                    <p class="text-white/70 text-lg leading-relaxed">
                        Được xây dựng với sứ mệnh mang đến trải nghiệm mua sắm thiết bị di động hiện đại nhất Việt Nam. 
                        Chúng tôi tập trung 100% vào smartphone, tablet, smartwatch và phụ kiện, đảm bảo chính hãng 100%, 
                        giá cạnh tranh và dịch vụ vượt trội.
                    </p>
                    <div class="flex gap-8 mt-12">
                        <div>
                            <div class="text-6xl font-bold text-[#0074d9]">128k+</div>
                            <div class="text-white/70">Khách hàng đã tin dùng</div>
                        </div>
                        <div>
                            <div class="text-6xl font-bold text-[#0074d9]">12.4k</div>
                            <div class="text-white/70">Sản phẩm đang bán</div>
                        </div>
                        <div>
                            <div class="text-6xl font-bold text-[#0074d9]">98%</div>
                            <div class="text-white/70">Đánh giá 5 sao</div>
                        </div>
                    </div>
                </div>
                
                <div class="md:col-span-7 bg-white/10 rounded-3xl p-8 backdrop-blur-3xl">
                    <div class="grid grid-cols-2 gap-6">
                        <div class="space-y-4">
                            <div class="flex justify-between items-center border-b border-white/30 pb-4">
                                <div class="flex items-center gap-3">
                                    <span class="text-3xl">🇻🇳</span>
                                    <div>
                                        <div class="font-medium">Kho hàng tại 3 thành phố</div>
                                        <div class="text-sm text-white/60">Hà Nội - TP.HCM - Đà Nẵng</div>
                                    </div>
                                </div>
                                <i class="fa-solid fa-warehouse text-3xl"></i>
                            </div>
                            <div class="flex justify-between items-center border-b border-white/30 pb-4">
                                <div class="flex items-center gap-3">
                                    <span class="text-3xl">🔒</span>
                                    <div>
                                        <div class="font-medium">Bảo mật thanh toán</div>
                                        <div class="text-sm text-white/60">Mã hóa SSL 256-bit</div>
                                    </div>
                                </div>
                                <i class="fa-solid fa-lock text-3xl"></i>
                            </div>
                        </div>
                        <div class="rounded-3xl bg-gradient-to-br from-[#0074d9] to-[#001f3f] p-8 text-center flex flex-col justify-center">
                            <i class="fa-solid fa-medal text-7xl mb-6"></i>
                            <div class="text-2xl font-semibold">Top 1 nền tảng</div>
                            <div class="text-xl opacity-90">Thiết bị di động 2025 - 2026</div>
                            <div class="text-xs mt-6 opacity-70">Theo VietnamWorks &amp; Nielsen</div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- TESTIMONIALS & BLOG TEASER -->
    <section id="blog" class="max-w-7xl mx-auto px-6 py-16">
        <div class="flex flex-col lg:flex-row gap-16">
            <!-- Testimonials -->
            <div class="lg:w-5/12">
                <h2 class="text-4xl font-semibold mb-10">Khách hàng nói gì về IMEX?</h2>
                <div class="space-y-8">
                    <div class="bg-white p-6 rounded-3xl border">
                        <div class="flex gap-4">
                            <div class="text-5xl">“</div>
                            <div>
                                <p class="italic">"Mua iPhone 16 Pro ở đây nhanh hơn cả Apple Store. Giao trong 1 giờ, máy mới 100%. Rất hài lòng!"</p>
                                <div class="mt-6 flex items-center gap-3">
                                    <div class="w-9 h-9 bg-gray-200 rounded-2xl"></div>
                                    <div>
                                        <div class="font-semibold">Nguyễn Văn A</div>
                                        <div class="text-sm text-gray-500">Hà Nội • 3 ngày trước</div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Blog -->
            <div class="lg:w-7/12">
                <div class="flex justify-between mb-8">
                    <h2 class="text-4xl font-semibold">Cập nhật công nghệ</h2>
                    <a href="#" class="text-[#0074d9] flex items-center">Đọc thêm <i class="fa-solid fa-arrow-right ml-2"></i></a>
                </div>
                <div class="grid md:grid-cols-2 gap-6">
                    <div class="bg-white border border-gray-100 rounded-3xl overflow-hidden">
                        <img src="https://picsum.photos/id/201/600/300" class="w-full h-40 object-cover">
                        <div class="p-6">
                            <div class="text-xs text-[#0074d9] font-medium">iOS 19 • 15/04/2026</div>
                            <h4 class="font-semibold text-xl mt-2">iPhone 17 Air sẽ mỏng nhất lịch sử - Có gì mới?</h4>
                        </div>
                    </div>
                    <div class="bg-white border border-gray-100 rounded-3xl overflow-hidden">
                        <img src="https://picsum.photos/id/251/600/300" class="w-full h-40 object-cover">
                        <div class="p-6">
                            <div class="text-xs text-[#0074d9] font-medium">Galaxy AI • 14/04/2026</div>
                            <h4 class="font-semibold text-xl mt-2">Samsung Galaxy S26 Ultra: Camera 200MP &amp; AI siêu thông minh</h4>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- FOOTER -->
    <footer class="bg-[#001f3f] text-white">
        <div class="max-w-7xl mx-auto px-6 pt-16 pb-8">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-y-12">
                <div>
                    <div class="flex items-center gap-3 mb-6">
                        <div class="w-10 h-10 bg-white rounded-2xl flex items-center justify-center text-[#001f3f] text-3xl">📱</div>
                        <span class="text-3xl font-bold">IMEX</span>
                    </div>
                    <p class="text-white/70 text-sm leading-relaxed max-w-xs">
                        Nền tảng Thương mại điện tử chuyên biệt cho Thiết bị di động hiện đại nhất Việt Nam.
                    </p>
                    <div class="flex gap-4 mt-8">
                        <i class="fa-brands fa-facebook-f text-2xl cursor-pointer hover:text-[#0074d9]"></i>
                        <i class="fa-brands fa-tiktok text-2xl cursor-pointer hover:text-[#0074d9]"></i>
                        <i class="fa-brands fa-youtube text-2xl cursor-pointer hover:text-[#0074d9]"></i>
                    </div>
                </div>
                
                <div>
                    <h4 class="font-semibold mb-4">Sản phẩm</h4>
                    <ul class="space-y-3 text-white/70 text-sm">
                        <li>Điện thoại thông minh</li>
                        <li>Máy tính bảng</li>
                        <li>Đồng hồ thông minh</li>
                        <li>Tai nghe &amp; Âm thanh</li>
                        <li>Phụ kiện chính hãng</li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="font-semibold mb-4">Dịch vụ</h4>
                    <ul class="space-y-3 text-white/70 text-sm">
                        <li>Thu cũ đổi mới</li>
                        <li>Sửa chữa nhanh</li>
                        <li>Trả góp 0%</li>
                        <li>Bảo hành mở rộng</li>
                        <li>Giao hàng 2 giờ</li>
                    </ul>
                </div>
                
                <div>
                    <h4 class="font-semibold mb-4">Liên hệ</h4>
                    <p class="text-sm text-white/70">Hotline: 1900 88 66 88</p>
                    <p class="text-sm text-white/70">Email: support@imex.vn</p>
                    <p class="text-sm text-white/70 mt-6">Địa chỉ: 123 Đường Nguyễn Huệ, Quận 1, TP.HCM</p>
                    
                    <div class="mt-8 flex items-center gap-2 text-xs bg-white/10 rounded-3xl px-5 py-3">
                        <i class="fa-solid fa-lock"></i>
                        <span>Thanh toán an toàn với</span>
                        <span class="font-mono font-bold">VNPAY</span> • 
                        <span class="font-mono font-bold">MOMO</span> • 
                        <span class="font-mono font-bold">ZALOPAY</span>
                    </div>
                </div>
            </div>
            
            <div class="border-t border-white/10 mt-16 pt-8 text-xs text-white/50 flex flex-col md:flex-row justify-between items-center gap-4">
                <div>© 2026 IMEX Mobile. All rights reserved.</div>
                <div class="flex gap-6">
                    <a href="#" class="hover:text-white">Điều khoản sử dụng</a>
                    <a href="#" class="hover:text-white">Chính sách bảo mật</a>
                    <a href="#" class="hover:text-white">Chính sách đổi trả</a>
                </div>
                <div class="text-[#0074d9]">Made with ❤️ for mobile lovers</div>
            </div>
        </div>
    </footer>

    <!-- SIMPLE CART MODAL -->
    <div id="cart-modal" onclick="if(event.target.id === 'cart-modal') hideCart()" 
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-end md:items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-lg rounded-t-3xl md:rounded-3xl shadow-2xl max-h-[90vh] overflow-hidden">
            <div class="px-6 py-6 border-b flex items-center justify-between">
                <h3 class="font-semibold text-2xl">Giỏ hàng của bạn</h3>
                <i onclick="hideCart()" class="fa-solid fa-xmark text-3xl cursor-pointer"></i>
            </div>
            
            <div id="cart-items" class="px-6 py-4 max-h-[420px] overflow-auto">
                <!-- JS populated -->
                <div class="text-center py-16 text-gray-400">
                    <i class="fa-solid fa-cart-shopping text-6xl mb-6 opacity-30"></i>
                    <p>Giỏ hàng trống</p>
                </div>
            </div>
            
            <div class="p-6 border-t bg-gray-50">
                <div class="flex justify-between text-lg font-semibold mb-6">
                    <span>Tổng tiền:</span>
                    <span id="cart-total" class="text-[#001f3f]">0 ₫</span>
                </div>
                <button onclick="checkout()" 
                        class="w-full py-6 text-lg bg-[#001f3f] text-white rounded-3xl font-semibold">
                    TIẾN HÀNH THANH TOÁN
                </button>
                <p class="text-center text-xs text-gray-400 mt-4">Hoặc thanh toán sau khi nhận hàng</p>
            </div>
        </div>
    </div>

    <!-- SEARCH OVERLAY -->
    <div onclick="if(event.target.id === 'search-overlay') toggleSearch()" 
         id="search-overlay" class="hidden fixed inset-0 bg-black/60 z-[11000] flex items-start justify-center pt-24">
        <div onclick="event.stopImmediatePropagation()" class="w-full max-w-2xl bg-white rounded-3xl mx-4 shadow-2xl overflow-hidden">
            <div class="p-6">
                <div class="flex border-b pb-4">
                    <input id="search-input" 
                           onkeyup="if(event.keyCode===13) performSearch()"
                           type="text" 
                           placeholder="Tìm kiếm điện thoại, máy tính bảng, phụ kiện..." 
                           class="flex-1 outline-none text-xl placeholder:text-gray-400">
                    <button onclick="performSearch()" class="px-6 text-[#0074d9]">
                        <i class="fa-solid fa-magnifying-glass"></i>
                    </button>
                </div>
            </div>
            <div id="search-results" class="px-6 pb-6 text-sm max-h-96 overflow-auto"></div>
        </div>
    </div>

    <script>
        // Tailwind script initialization
        function initializeTailwind() {
            tailwind.config = {
                content: [],
                theme: {
                    extend: {}
                }
            }
        }
        
        // Mock products data
        let products = [
            {
                id: 1,
                name: "iPhone 16 Pro Max 256GB",
                category: "phone",
                price: 32990000,
                originalPrice: 35990000,
                image: "https://picsum.photos/id/1015/400/400",
                badge: "BÁN CHẠY",
                rating: 4.9
            },
            {
                id: 2,
                name: "Samsung Galaxy S25 Ultra 512GB",
                category: "phone",
                price: 28990000,
                originalPrice: 31990000,
                image: "https://picsum.photos/id/201/400/400",
                badge: "MỚI",
                rating: 5
            },
            {
                id: 3,
                name: "iPad Air M3 11 inch WiFi + 5G",
                category: "tablet",
                price: 18990000,
                originalPrice: 19990000,
                image: "https://picsum.photos/id/251/400/400",
                badge: "",
                rating: 4.8
            },
            {
                id: 4,
                name: "Apple Watch Ultra 2 Titanium",
                category: "watch",
                price: 19990000,
                originalPrice: null,
                image: "https://picsum.photos/id/1005/400/400",
                badge: "GIẢM GIÁ",
                rating: 4.9
            },
            {
                id: 5,
                name: "AirPods Pro 3 (2026)",
                category: "earbud",
                price: 6990000,
                originalPrice: 7990000,
                image: "https://picsum.photos/id/133/400/400",
                badge: "",
                rating: 4.7
            },
            {
                id: 6,
                name: "Xiaomi 14T Pro 12/512GB",
                category: "phone",
                price: 13990000,
                originalPrice: 15990000,
                image: "https://picsum.photos/id/160/400/400",
                badge: "GIÁ TỐT",
                rating: 4.6
            },
            {
                id: 7,
                name: "Samsung Galaxy Tab S10 Ultra",
                category: "tablet",
                price: 25990000,
                originalPrice: null,
                image: "https://picsum.photos/id/180/400/400",
                badge: "",
                rating: 5
            },
            {
                id: 8,
                name: "Sony WH-1000XM6",
                category: "earbud",
                price: 8990000,
                originalPrice: 10990000,
                image: "https://picsum.photos/id/201/400/400",
                badge: "",
                rating: 4.8
            }
        ]
        
        let cart = []
        
        // Render product grid
        function renderProducts(filteredProducts = products) {
            const container = document.getElementById('product-grid')
            container.innerHTML = ''
            
            filteredProducts.forEach(product => {
                const discount = product.originalPrice 
                    ? Math.round(((product.originalPrice - product.price) / product.originalPrice) * 100) 
                    : 0
                
                const cardHTML = `
                <div class="product-card bg-white border border-gray-100 rounded-3xl overflow-hidden group">
                    <div class="relative">
                        <img src="${product.image}" alt="${product.name}" 
                             class="w-full aspect-square object-contain bg-gray-50 p-6 group-hover:scale-110 transition-transform">
                        
                        ${product.badge ? `<div class="absolute top-4 left-4 bg-[#0074d9] text-white text-xs font-bold px-4 py-1 rounded-3xl">${product.badge}</div>` : ''}
                        
                        ${discount > 0 ? `
                        <div class="absolute top-4 right-4 bg-red-500 text-white text-xs font-bold px-3 py-1 rounded-3xl">
                            -${discount}%
                        </div>` : ''}
                    </div>
                    
                    <div class="px-6 pb-6">
                        <div class="text-sm text-gray-400 mb-1">${product.category === 'phone' ? 'Điện thoại' : product.category === 'tablet' ? 'Máy tính bảng' : 'Phụ kiện'}</div>
                        <h4 class="font-semibold line-clamp-2 h-12">${product.name}</h4>
                        
                        <div class="flex justify-between items-end mt-4">
                            <div>
                                <span class="text-2xl font-bold text-[#001f3f]">${product.price.toLocaleString('vi-VN')} ₫</span>
                                ${product.originalPrice ? `<span class="text-xs line-through text-gray-400 block">${product.originalPrice.toLocaleString('vi-VN')} ₫</span>` : ''}
                            </div>
                            
                            <div class="flex items-center text-amber-400">
                                ${Array(5).fill().map((_, i) => `<i class="fa-solid fa-star ${i < Math.floor(product.rating) ? 'text-amber-400' : 'text-gray-200'}"></i>`).join('')}
                            </div>
                        </div>
                        
                        <button onclick="addToCart(${product.id}); event.stopImmediatePropagation()" 
                                class="mt-6 w-full bg-[#001f3f] hover:bg-[#003366] text-white py-3.5 rounded-3xl text-sm font-semibold flex items-center justify-center gap-2">
                            <i class="fa-solid fa-cart-plus"></i>
                            THÊM VÀO GIỎ
                        </button>
                    </div>
                </div>`
                
                container.innerHTML += cardHTML
            })
            
            if (filteredProducts.length === 0) {
                container.innerHTML = `<div class="col-span-full text-center py-20 text-gray-400">Không tìm thấy sản phẩm nào phù hợp</div>`
            }
        }
        
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
            
            // Toast
            const toast = document.createElement('div')
            toast.className = 'fixed bottom-8 right-8 bg-[#001f3f] text-white px-6 py-4 rounded-3xl shadow-2xl flex items-center gap-3'
            toast.innerHTML = `✅ <span>${product.name} đã được thêm vào giỏ hàng</span>`
            document.body.appendChild(toast)
            
            setTimeout(() => toast.remove(), 2800)
        }
        
        function updateCartCount() {
            const totalItems = cart.reduce((acc, item) => acc + (item.quantity || 1), 0)
            document.getElementById('cart-count').textContent = totalItems
        }
        
        function showCart() {
            const modal = document.getElementById('cart-modal')
            const container = document.getElementById('cart-items')
            
            if (cart.length === 0) {
                container.innerHTML = `
                <div class="text-center py-16 text-gray-400">
                    <i class="fa-solid fa-cart-shopping text-6xl mb-6 opacity-30"></i>
                    <p class="text-lg">Giỏ hàng của bạn đang trống</p>
                    <button onclick="hideCart()" class="mt-8 text-[#0074d9] font-medium">Tiếp tục mua sắm</button>
                </div>`
                modal.classList.remove('hidden')
                modal.classList.add('flex')
                return
            }
            
            let html = ''
            let total = 0
            
            cart.forEach((item, index) => {
                const itemTotal = item.price * (item.quantity || 1)
                total += itemTotal
                
                html += `
                <div class="flex gap-4 py-6 border-b last:border-0">
                    <img src="${item.image}" class="w-20 h-20 object-contain bg-gray-50 rounded-2xl">
                    <div class="flex-1">
                        <div class="flex justify-between">
                            <h5 class="font-medium">${item.name}</h5>
                            <button onclick="removeFromCart(${index});" class="text-red-500 text-sm">Xóa</button>
                        </div>
                        <div class="text-sm text-gray-400">${item.category}</div>
                        <div class="flex justify-between items-end mt-auto">
                            <div class="text-xl font-semibold">${item.price.toLocaleString('vi-VN')} ₫</div>
                            <div class="flex border rounded-2xl items-center text-sm">
                                <button onclick="changeQuantity(${index}, -1)" class="px-4 py-2">-</button>
                                <span class="px-4">${item.quantity || 1}</span>
                                <button onclick="changeQuantity(${index}, 1)" class="px-4 py-2">+</button>
                            </div>
                        </div>
                    </div>
                </div>`
            })
            
            container.innerHTML = html
            
            document.getElementById('cart-total').innerHTML = `
                <span class="text-3xl">${total.toLocaleString('vi-VN')} ₫</span>
            `
            
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function hideCart() {
            const modal = document.getElementById('cart-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        function changeQuantity(index, delta) {
            const item = cart[index]
            if (!item) return
            
            item.quantity = (item.quantity || 1) + delta
            
            if (item.quantity < 1) item.quantity = 1
            
            showCart()
            updateCartCount()
        }
        
        function removeFromCart(index) {
            cart.splice(index, 1)
            showCart()
            updateCartCount()
        }
        
        function checkout() {
            hideCart()
            setTimeout(() => {
                alert('🎉 Cảm ơn bạn đã mua hàng tại IMEX!\n\nĐơn hàng của bạn đã được xác nhận. Chúng tôi sẽ giao trong 2 giờ tới.')
                cart = []
                updateCartCount()
            }, 800)
        }
        
        // Filter category
        function filterCategory(cat) {
            if (cat === 'all') {
                renderProducts()
            } else {
                const filtered = products.filter(p => p.category === cat)
                renderProducts(filtered)
            }
            // Scroll to products
            document.getElementById('products').scrollIntoView({ behavior: 'smooth' })
        }
        
        function viewAllProducts() {
            renderProducts()
            document.getElementById('products').scrollIntoView({ behavior: 'smooth' })
        }
        
        // Simple search
        function toggleSearch() {
            const overlay = document.getElementById('search-overlay')
            if (overlay.classList.contains('hidden')) {
                overlay.classList.remove('hidden')
                overlay.classList.add('flex')
                document.getElementById('search-input').focus()
            } else {
                overlay.classList.add('hidden')
                overlay.classList.remove('flex')
            }
        }
        
        function performSearch() {
            const keyword = document.getElementById('search-input').value.toLowerCase().trim()
            if (!keyword) return
            
            const filtered = products.filter(p => 
                p.name.toLowerCase().includes(keyword)
            )
            
            const container = document.getElementById('search-results')
            container.innerHTML = `<div class="text-sm font-medium mb-4">Kết quả tìm kiếm cho <span class="text-[#0074d9]">"${keyword}"</span></div>`
            
            filtered.forEach(p => {
                container.innerHTML += `
                <div onclick="quickAddProduct(${p.id});" class="flex items-center gap-4 py-4 border-b cursor-pointer hover:bg-gray-50 rounded-2xl px-4">
                    <img src="${p.image}" class="w-12 h-12 object-contain">
                    <div class="flex-1">
                        <div>${p.name}</div>
                        <div class="text-[#001f3f] font-semibold">${p.price.toLocaleString('vi-VN')} ₫</div>
                    </div>
                </div>`
            })
            
            if (filtered.length === 0) {
                container.innerHTML += `<div class="py-12 text-center text-gray-400">Không tìm thấy kết quả</div>`
            }
        }
        
        function quickAddProduct(id) {
            toggleSearch()
            setTimeout(() => {
                addToCart(id)
            }, 300)
        }
        
        // Mobile menu
        function toggleMobileMenu() {
            const menu = document.getElementById('mobile-menu')
            menu.classList.toggle('hidden')
        }
        
        function toggleUserMenu() {
            alert('👋 Xin chào Tumay!\nBạn đang xem tài khoản cá nhân IMEX.\n\n(Đây là demo - Chức năng đăng nhập đầy đủ sẽ được tích hợp khi triển khai thực tế)')
        }
        
        function navigateToSection(section) {
            const el = document.getElementById(section)
            if (el) {
                el.scrollIntoView({ behavior: 'smooth' })
            }
            // Close mobile menu if open
            const mobile = document.getElementById('mobile-menu')
            if (mobile && !mobile.classList.contains('hidden')) toggleMobileMenu()
        }
        
        function shopNow() {
            document.getElementById('products').scrollIntoView({ behavior: 'smooth' })
        }
        
        function watchVideo() {
            alert('📺 Video giới thiệu IMEX đang phát...\n\n(Trong bản thực tế sẽ nhúng YouTube video giới thiệu nền tảng)')
        }
        
        // Initialize everything
        function init() {
            initializeTailwind()
            renderProducts()
            updateCartCount()
            
            console.log('%c✅ IMEX Website đã được tạo thành công! Màu chủ đạo: Xanh dương đậm + Trắng', 'color:#0074d9; font-family:monospace; font-size:13px')
            console.log('Trang web hoàn chỉnh, responsive, có giỏ hàng, tìm kiếm, và các tính năng demo.')
        }
        
        // Run when loaded
        window.onload = init
    </script>
</body>
</html>
