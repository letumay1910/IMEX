```html
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
            --primary: #eab308;
        }
        
        * {
            transition-property: color, background-color, border-color, text-decoration-color, fill, stroke;
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
            background: linear-gradient(90deg, #eab308 0%, #ca8a04 100%);
        }
        
        .product-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-12px) scale(1.03);
            box-shadow: 0 25px 50px -12px rgb(234 179 8);
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
            background-color: #eab308;
        }
        
        .nav-link:hover:after {
            width: 100%;
        }
        
        .modal {
            animation: modalPop 0.3s ease-out;
        }
        
        @keyframes modalPop {
            0% { opacity: 0; transform: scale(0.95); }
            100% { opacity: 1; transform: scale(1); }
        }
        
        .spec-row:hover {
            background-color: #fefce8;
        }
        
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
        <div class="max-w-7xl mx-auto">
            <div class="px-6 py-5 flex items-center justify-between">
                
                <!-- Logo -->
                <div class="flex items-center gap-x-3">
                    <div class="w-11 h-11 bg-gradient-to-br from-amber-400 to-yellow-500 rounded-3xl flex items-center justify-center shadow-inner text-white text-4xl">📱</div>
                    <h1 class="logo-font text-4xl font-bold tracking-[-2px] text-amber-400">IMEX</h1>
                    <span class="text-amber-600 font-semibold text-lg mt-1 tracking-widest">MOBILE</span>
                </div>

                <!-- Desktop Menu -->
                <div class="hidden md:flex items-center gap-x-9 text-base font-semibold">
                    <a onclick="navigateToSection('home')" class="nav-link text-gray-800 hover:text-amber-400">Trang chủ</a>
                    <a onclick="navigateToSection('shop')" class="nav-link text-gray-800 hover:text-amber-400">Cửa hàng</a>
                    <a onclick="navigateToSection('compare')" class="nav-link text-gray-800 hover:text-amber-400">So sánh</a>
                    <a onclick="navigateToSection('community')" class="nav-link text-gray-800 hover:text-amber-400">Cộng đồng</a>
                    <a onclick="navigateToSection('warranty')" class="nav-link text-gray-800 hover:text-amber-400">Bảo hành</a>
                    <a onclick="showOrders()" class="nav-link text-gray-800 hover:text-amber-400">Đơn hàng</a>
                </div>

                <div class="flex items-center gap-x-5">
                    <!-- Search -->
                    <div onclick="toggleSearch()" class="relative cursor-pointer">
                        <div class="flex items-center bg-amber-50 hover:bg-amber-100 border border-amber-200 rounded-3xl px-6 py-3 text-sm font-medium gap-x-3">
                            <i class="fa-solid fa-magnifying-glass text-amber-400"></i>
                            <input id="search-input" type="text" placeholder="Tìm iPhone, Galaxy, phụ kiện..." 
                                   class="bg-transparent outline-none w-64 hidden md:block placeholder:text-amber-400/70">
                        </div>
                    </div>

                    <!-- Cart -->
                    <div onclick="showCart()" class="relative cursor-pointer flex items-center justify-center w-12 h-12 hover:bg-amber-50 rounded-3xl">
                        <i class="fa-solid fa-shopping-cart text-3xl text-gray-700"></i>
                        <span id="cart-count-badge" class="absolute -top-1 -right-1 bg-amber-400 text-white text-xs font-bold w-6 h-6 rounded-2xl flex items-center justify-center shadow-md">0</span>
                    </div>

                    <!-- User -->
                    <div onclick="toggleUserMenu()" class="flex items-center gap-x-2 cursor-pointer">
                        <div class="w-9 h-9 bg-amber-100 text-amber-400 rounded-2xl flex items-center justify-center text-2xl">👤</div>
                        <div class="hidden md:block">
                            <p id="user-name" class="text-sm font-semibold text-gray-800">Ánh</p>
                        </div>
                    </div>

                    <!-- Mobile Hamburger -->
                    <button onclick="toggleMobileMenu()" class="md:hidden w-12 h-12 flex items-center justify-center text-4xl text-amber-400">
                        <i id="hamburger-icon" class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden md:hidden bg-white border-t px-6 py-8 shadow-2xl">
            <div class="flex flex-col gap-y-6 text-lg font-medium">
                <a onclick="navigateToSection('home');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-house w-8"></i> Trang chủ</a>
                <a onclick="navigateToSection('shop');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-store w-8"></i> Cửa hàng</a>
                <a onclick="navigateToSection('compare');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-balance-scale w-8"></i> So sánh sản phẩm</a>
                <a onclick="navigateToSection('community');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-users w-8"></i> Cộng đồng</a>
                <a onclick="navigateToSection('warranty');toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-shield-halved w-8"></i> Bảo hành điện tử</a>
                <a onclick="showOrders();toggleMobileMenu()" class="flex items-center gap-4"><i class="fa-solid fa-receipt w-8"></i> Đơn hàng của tôi</a>
            </div>
        </div>
    </nav>

    <!-- HERO -->
    <section id="home" class="hero-bg text-white min-h-screen flex items-center relative">
        <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
            <div class="space-y-8">
                <div class="inline-flex bg-white/20 backdrop-blur-xl text-white text-sm font-semibold px-8 py-3 rounded-3xl items-center gap-3 shadow-inner">
                    <i class="fa-solid fa-medal"></i>
                    THIẾT BỊ DI ĐỘNG CHÍNH HÃNG 100%
                </div>
                
                <h1 class="text-6xl md:text-7xl font-bold leading-none tracking-[-2px]">
                    IMEX<br>
                    <span class="text-amber-100">Thế giới di động</span><br>
                    vàng rực rỡ
                </h1>
                
                <p class="text-3xl text-amber-100 max-w-lg">Điện thoại • Tablet • Phụ kiện<br>Giá tốt nhất • Giao ngay • Bảo hành vàng</p>

                <div class="flex gap-6">
                    <button onclick="navigateToSection('shop')" 
                            class="bg-white text-amber-400 hover:scale-105 px-10 py-6 rounded-3xl font-bold text-2xl flex items-center gap-x-4 shadow-2xl">
                        <i class="fa-solid fa-cart-shopping"></i>
                        MUA NGAY
                    </button>
                    <button onclick="navigateToSection('compare')" 
                            class="border-2 border-white/90 hover:bg-white/10 px-10 py-6 rounded-3xl font-bold text-2xl flex items-center gap-x-4">
                        <i class="fa-solid fa-balance-scale"></i>
                        SO SÁNH NGAY
                    </button>
                </div>

                <div class="flex items-center gap-x-12">
                    <div class="flex items-center">
                        <div class="text-5xl font-bold">4.98</div>
                        <div class="ml-3">
                            <div class="flex text-amber-300">★★★★★</div>
                            <p class="text-xs tracking-widest">Hơn 68.420 đánh giá</p>
                        </div>
                    </div>
                    <div>
                        <i class="fa-solid fa-truck text-4xl"></i>
                        <p class="font-medium mt-1">Giao hàng trong 90 phút tại Vinh &amp; Toàn quốc</p>
                    </div>
                </div>
            </div>

            <!-- Hero visual -->
            <div class="relative flex justify-center">
                <div class="absolute w-[420px] h-[420px] bg-white/10 backdrop-blur-3xl rounded-[4rem] -rotate-12 shadow-2xl"></div>
                <img src="https://picsum.photos/id/1015/800/800" alt="iPhone 16 Pro" 
                     class="relative z-10 w-80 md:w-96 rounded-3xl shadow-2xl rotate-[-6deg] border-8 border-white">
                
                <!-- Floating badges -->
                <div class="absolute top-12 -left-6 bg-white text-amber-400 text-sm font-bold px-7 py-4 rounded-3xl shadow-2xl flex items-center gap-3">
                    <i class="fa-solid fa-shield-halved text-2xl"></i>
                    <div>
                        <p>Bảo hành điện tử</p>
                        <p class="text-xs text-gray-500">24 tháng chính hãng</p>
                    </div>
                </div>
                <div class="absolute bottom-16 right-6 bg-white text-amber-400 text-sm font-bold px-7 py-4 rounded-3xl shadow-2xl flex items-center gap-3">
                    <i class="fa-solid fa-truck-fast text-2xl"></i>
                    <div>
                        <p>Giao nhanh 90 phút</p>
                        <p class="text-xs text-gray-500">Miễn phí từ 3 triệu</p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- CATEGORIES -->
    <section class="max-w-7xl mx-auto px-6 py-20">
        <div class="text-center mb-12">
            <span class="px-6 py-2 bg-amber-100 text-amber-400 rounded-3xl text-sm font-bold">DANH MỤC</span>
            <h2 class="section-header text-5xl font-semibold mt-4">Chọn thiết bị hoàn hảo cho bạn</h2>
        </div>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
            <div onclick="filterCategory('phone')" class="group bg-white border-2 border-transparent hover:border-amber-300 rounded-3xl p-8 cursor-pointer text-center">
                <div class="text-7xl mb-6 group-hover:scale-110">📱</div>
                <h3 class="text-3xl font-semibold">Điện thoại</h3>
                <p class="text-amber-400 text-sm mt-2">iPhone, Samsung, Xiaomi • 248 sản phẩm</p>
            </div>
            <div onclick="filterCategory('tablet')" class="group bg-white border-2 border-transparent hover:border-amber-300 rounded-3xl p-8 cursor-pointer text-center">
                <div class="text-7xl mb-6 group-hover:scale-110">📟</div>
                <h3 class="text-3xl font-semibold">Máy tính bảng</h3>
                <p class="text-amber-400 text-sm mt-2">iPad, Galaxy Tab • 112 sản phẩm</p>
            </div>
            <div onclick="filterCategory('accessory')" class="group bg-white border-2 border-transparent hover:border-amber-300 rounded-3xl p-8 cursor-pointer text-center">
                <div class="text-7xl mb-6 group-hover:scale-110">🔌</div>
                <h3 class="text-3xl font-semibold">Phụ kiện</h3>
                <p class="text-amber-400 text-sm mt-2">Ốp lưng, tai nghe, sạc • 387 sản phẩm</p>
            </div>
            <div onclick="filterCategory('watch')" class="group bg-white border-2 border-transparent hover:border-amber-300 rounded-3xl p-8 cursor-pointer text-center">
                <div class="text-7xl mb-6 group-hover:scale-110">⌚</div>
                <h3 class="text-3xl font-semibold">Smartwatch</h3>
                <p class="text-amber-400 text-sm mt-2">Apple Watch, Galaxy Watch • 89 sản phẩm</p>
            </div>
        </div>
    </section>

    <!-- SHOP + PRODUCT GRID -->
    <section id="shop" class="bg-amber-50 py-20">
        <div class="max-w-7xl mx-auto px-6">
            <h2 class="section-header text-5xl font-semibold text-center mb-12">Sản phẩm nổi bật</h2>
            
            <div id="products-grid" class="grid grid-cols-2 lg:grid-cols-4 gap-8">
                <!-- JS render -->
            </div>
        </div>
    </section>

    <!-- COMPARISON SECTION -->
    <section id="compare" class="max-w-7xl mx-auto px-6 py-20">
        <div class="flex justify-between items-end mb-10">
            <h2 class="text-5xl font-semibold">Hệ thống so sánh thông số kỹ thuật</h2>
            <button onclick="openCompareModal()" 
                    class="flex items-center gap-x-3 bg-amber-400 hover:bg-yellow-500 text-white px-8 py-4 rounded-3xl font-semibold text-lg">
                <i class="fa-solid fa-balance-scale"></i>
                SO SÁNH NGAY (tối đa 4 thiết bị)
            </button>
        </div>
        <p class="text-amber-500 text-lg mb-8">Chọn nhiều sản phẩm để đối chiếu cấu hình, pin, hiệu năng, giá bán...</p>
        
        <div id="compare-preview" class="grid grid-cols-4 gap-6 text-sm hidden">
            <!-- JS sẽ render preview các sản phẩm đã chọn -->
        </div>
    </section>

    <!-- COMMUNITY -->
    <section id="community" class="max-w-7xl mx-auto px-6 py-20 bg-white">
        <h2 class="section-header text-5xl font-semibold text-center mb-12">Cộng đồng người dùng công nghệ</h2>
        
        <div class="grid md:grid-cols-3 gap-8" id="community-feed">
            <!-- JS render posts -->
        </div>
        
        <!-- Post form -->
        <div class="mt-16 bg-amber-50 rounded-3xl p-8">
            <h3 class="font-semibold text-2xl mb-6 flex items-center"><i class="fa-solid fa-comment-dots mr-4"></i> Chia sẻ kinh nghiệm của bạn</h3>
            <textarea id="community-input" rows="3" 
                      class="w-full rounded-3xl p-6 border border-amber-200 focus:border-amber-400 outline-none" 
                      placeholder="Bạn đang dùng iPhone 16 Pro Max? Chia sẻ đánh giá..."></textarea>
            <button onclick="postCommunity()" 
                    class="mt-6 bg-amber-400 hover:bg-amber-500 text-white px-10 py-5 rounded-3xl font-semibold">ĐĂNG BÀI</button>
        </div>
    </section>

    <!-- WARRANTY -->
    <section id="warranty" class="max-w-7xl mx-auto px-6 py-20 bg-amber-50">
        <div class="grid md:grid-cols-2 gap-16 items-center">
            <div>
                <h2 class="text-5xl font-semibold">Bảo hành điện tử</h2>
                <p class="text-xl mt-6 text-gray-600">Tra cứu thời hạn bảo hành chỉ trong 10 giây. Toàn bộ thông tin được lưu trữ an toàn trên hệ thống IMEX.</p>
                
                <div class="mt-10">
                    <input id="warranty-serial" type="text" placeholder="Nhập số serial / IMEI" 
                           class="w-full px-8 py-6 rounded-3xl border-2 border-amber-300 focus:border-amber-400 text-xl">
                    <button onclick="checkWarranty()" 
                            class="mt-6 w-full bg-gradient-to-r from-amber-400 to-yellow-500 text-white py-6 rounded-3xl text-2xl font-semibold">TRA CỨU BẢO HÀNH</button>
                </div>
            </div>
            
            <div class="bg-white rounded-3xl p-10 shadow-xl">
                <h4 class="font-medium text-amber-400">Ví dụ kết quả tra cứu</h4>
                <div class="mt-8 space-y-6">
                    <div class="flex justify-between items-center border-b pb-4">
                        <div>
                            <p class="font-semibold">iPhone 16 Pro Max</p>
                            <p class="text-sm text-gray-500">Serial: 1234567890ABC</p>
                        </div>
                        <div class="text-right">
                            <span class="px-6 py-2 bg-green-100 text-green-700 rounded-3xl text-sm font-medium">Còn 18 tháng</span>
                        </div>
                    </div>
                    <div class="flex justify-between items-center border-b pb-4">
                        <div>
                            <p class="font-semibold">Galaxy Tab S10 Ultra</p>
                            <p class="text-sm text-gray-500">Serial: GTAB20251234</p>
                        </div>
                        <div class="text-right">
                            <span class="px-6 py-2 bg-green-100 text-green-700 rounded-3xl text-sm font-medium">Còn 22 tháng</span>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- PRODUCT DETAIL MODAL -->
    <div onclick="if(event.target.id==='product-modal')hideProductModal()" 
         id="product-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-5xl rounded-3xl modal overflow-hidden">
            
            <div class="flex justify-between px-8 py-6 border-b">
                <h2 id="modal-product-name" class="text-4xl font-bold"></h2>
                <i onclick="hideProductModal()" class="fa-solid fa-xmark text-4xl cursor-pointer"></i>
            </div>
            
            <div class="grid md:grid-cols-2 gap-10 p-8">
                <!-- Image -->
                <div>
                    <img id="modal-image" src="" class="w-full rounded-3xl shadow-inner">
                    <div class="flex gap-4 mt-8">
                        <div onclick="switchImage(this)" class="flex-1 cursor-pointer border-2 border-amber-300 rounded-2xl p-2"><img src="https://picsum.photos/id/1015/200/200" class="rounded-xl"></div>
                        <div onclick="switchImage(this)" class="flex-1 cursor-pointer border border-transparent rounded-2xl p-2"><img src="https://picsum.photos/id/201/200/200" class="rounded-xl"></div>
                        <div onclick="switchImage(this)" class="flex-1 cursor-pointer border border-transparent rounded-2xl p-2"><img src="https://picsum.photos/id/301/200/200" class="rounded-xl"></div>
                    </div>
                </div>
                
                <!-- Info -->
                <div class="space-y-8">
                    <div class="flex justify-between items-baseline">
                        <div>
                            <p id="modal-price" class="text-5xl font-bold text-amber-400"></p>
                            <p id="modal-old-price" class="text-gray-400 line-through"></p>
                        </div>
                        <button onclick="addCurrentToCart()" 
                                class="px-10 py-5 bg-amber-400 hover:bg-yellow-500 text-white text-xl rounded-3xl font-semibold flex items-center">
                            <i class="fa-solid fa-cart-plus mr-3"></i> THÊM VÀO GIỎ
                        </button>
                    </div>
                    
                    <!-- Tabs -->
                    <div class="flex border-b">
                        <button onclick="showTab(0)" id="tab-0" class="tab-btn active px-8 py-4 font-semibold border-b-4 border-amber-400">Thông số kỹ thuật</button>
                        <button onclick="showTab(1)" id="tab-1" class="tab-btn px-8 py-4 font-semibold">Đánh giá</button>
                        <button onclick="showTab(2)" id="tab-2" class="tab-btn px-8 py-4 font-semibold">Bảo hành</button>
                    </div>
                    
                    <!-- Tab content -->
                    <div id="tab-content-0" class="tab-content">
                        <table class="w-full text-sm">
                            <tbody id="spec-table" class="divide-y"></tbody>
                        </table>
                    </div>
                    <div id="tab-content-1" class="tab-content hidden">
                        <div id="reviews-list" class="space-y-8"></div>
                    </div>
                    <div id="tab-content-2" class="tab-content hidden text-lg">
                        <p class="font-medium">Bảo hành chính hãng 24 tháng • Hỗ trợ đổi mới trong 30 ngày</p>
                        <p class="text-amber-400 mt-4">Bạn có thể tra cứu bảo hành điện tử bất kỳ lúc nào qua số serial.</p>
                    </div>
                    
                    <!-- Compare button -->
                    <button onclick="addToCompareFromDetail()" 
                            class="w-full border-2 border-dashed border-amber-400 text-amber-400 hover:bg-amber-50 py-5 rounded-3xl font-semibold flex items-center justify-center gap-3">
                        <i class="fa-solid fa-balance-scale"></i> THÊM VÀO DANH SÁCH SO SÁNH
                    </button>
                </div>
            </div>
        </div>
    </div>

    <!-- COMPARE MODAL -->
    <div onclick="if(event.target.id==='compare-modal')hideCompareModal()" 
         id="compare-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-7xl rounded-3xl modal max-h-[90vh] overflow-hidden">
            <div class="px-8 py-6 border-b flex items-center justify-between">
                <h3 class="text-4xl font-bold">So sánh thông số kỹ thuật</h3>
                <i onclick="hideCompareModal()" class="fa-solid fa-xmark text-4xl cursor-pointer"></i>
            </div>
            
            <div class="p-8 overflow-auto" style="max-height: calc(90vh - 120px)">
                <table class="w-full text-left">
                    <thead>
                        <tr class="border-b">
                            <th class="py-4 font-medium">Thông số</th>
                            <th id="compare-col-1" class="py-4 font-semibold text-center"></th>
                            <th id="compare-col-2" class="py-4 font-semibold text-center"></th>
                            <th id="compare-col-3" class="py-4 font-semibold text-center"></th>
                            <th id="compare-col-4" class="py-4 font-semibold text-center"></th>
                        </tr>
                    </thead>
                    <tbody id="compare-table-body" class="text-sm divide-y"></tbody>
                </table>
            </div>
            
            <div class="p-8 border-t flex justify-end">
                <button onclick="hideCompareModal()" class="px-12 py-5 rounded-3xl border text-lg">Đóng</button>
            </div>
        </div>
    </div>

    <!-- CART + CHECKOUT MODAL -->
    <div onclick="if(event.target.id==='cart-modal')hideCart()" 
         id="cart-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-3xl rounded-3xl modal">
            <div class="px-8 py-6 border-b flex items-center justify-between text-2xl font-semibold">
                <span>Giỏ hàng • Thanh toán &amp; vận chuyển</span>
                <i onclick="hideCart()" class="fa-solid fa-xmark cursor-pointer"></i>
            </div>
            
            <div class="p-8" id="cart-step-1">
                <div id="cart-items-list" class="max-h-80 overflow-auto space-y-8"></div>
                
                <div class="mt-8 flex justify-between text-xl font-medium">
                    <span>Tạm tính</span>
                    <span id="cart-subtotal" class="font-bold"></span>
                </div>
                
                <div class="mt-12">
                    <h4 class="font-semibold mb-4">Chọn phương thức vận chuyển</h4>
                    <div class="grid grid-cols-2 gap-4">
                        <label class="flex items-center gap-4 border-2 border-transparent hover:border-amber-400 rounded-3xl p-6 cursor-pointer">
                            <input type="radio" name="shipping" checked class="accent-amber-400">
                            <div class="flex-1">
                                <p class="font-medium">Giao nhanh 90 phút (Vinh &amp; lân cận)</p>
                                <p class="text-sm text-gray-500">Miễn phí từ 3 triệu</p>
                            </div>
                            <span class="font-bold">0 ₫</span>
                        </label>
                        <label class="flex items-center gap-4 border-2 border-transparent hover:border-amber-400 rounded-3xl p-6 cursor-pointer">
                            <input type="radio" name="shipping" class="accent-amber-400">
                            <div class="flex-1">
                                <p class="font-medium">Giao toàn quốc 1-2 ngày</p>
                                <p class="text-sm text-gray-500">Phí cố định</p>
                            </div>
                            <span class="font-bold">35.000 ₫</span>
                        </label>
                    </div>
                </div>
                
                <button onclick="goToPaymentStep()" 
                        class="mt-12 w-full bg-gradient-to-r from-amber-400 to-yellow-500 text-white py-7 rounded-3xl text-2xl font-semibold">TIẾP TỤC THANH TOÁN</button>
            </div>
            
            <!-- Payment step -->
            <div id="cart-step-2" class="hidden p-8">
                <h3 class="text-2xl font-semibold mb-8">Chọn hình thức thanh toán</h3>
                <div class="space-y-6">
                    <label class="flex items-center gap-6 border-2 p-6 rounded-3xl cursor-pointer">
                        <i class="fa-brands fa-cc-visa text-4xl"></i>
                        <div class="flex-1">Thẻ Visa / Mastercard</div>
                        <input type="radio" name="payment" checked class="accent-amber-400">
                    </label>
                    <label class="flex items-center gap-6 border-2 p-6 rounded-3xl cursor-pointer">
                        <i class="fa-brands fa-cc-mastercard text-4xl"></i>
                        <div class="flex-1">Momo / ZaloPay</div>
                        <input type="radio" name="payment" class="accent-amber-400">
                    </label>
                    <label class="flex items-center gap-6 border-2 p-6 rounded-3xl cursor-pointer">
                        <i class="fa-solid fa-truck text-4xl"></i>
                        <div class="flex-1">Thanh toán khi nhận hàng (COD)</div>
                        <input type="radio" name="payment" class="accent-amber-400">
                    </label>
                </div>
                
                <button onclick="completeCheckout()" 
                        class="mt-12 w-full bg-gradient-to-r from-amber-400 to-yellow-500 text-white py-7 rounded-3xl text-2xl font-semibold">XÁC NHẬN ĐƠN HÀNG</button>
            </div>
        </div>
    </div>

    <!-- ORDERS MODAL -->
    <div onclick="if(event.target.id==='orders-modal')hideOrders()" 
         id="orders-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" class="bg-white rounded-3xl modal w-full max-w-4xl">
            <div class="p-8 border-b flex justify-between items-center">
                <h3 class="text-3xl font-bold">Đơn hàng của tôi</h3>
                <i onclick="hideOrders()" class="fa-solid fa-xmark text-4xl cursor-pointer"></i>
            </div>
            <div id="orders-list" class="p-8 space-y-6 max-h-[70vh] overflow-auto"></div>
        </div>
    </div>

    <!-- USER MENU (dropdown) -->
    <div id="user-dropdown" onclick="if(event.target.id==='user-dropdown')this.classList.add('hidden')" 
         class="hidden fixed top-20 right-8 bg-white shadow-2xl rounded-3xl py-4 w-72 z-[9999]">
        <div class="px-6 py-4 border-b flex items-center gap-4">
            <div class="text-5xl">👤</div>
            <div>
                <p class="font-semibold">Xin chào, Ánh!</p>
                <p class="text-sm text-gray-500">anh.vinh@imex.vn</p>
            </div>
        </div>
        <a onclick="hideUserMenu();showOrders()" class="flex px-6 py-5 hover:bg-amber-50 items-center gap-4 cursor-pointer">
            <i class="fa-solid fa-receipt w-6"></i>
            <span>Đơn hàng &amp; theo dõi vận chuyển</span>
        </a>
        <a onclick="hideUserMenu()" class="flex px-6 py-5 hover:bg-amber-50 items-center gap-4 cursor-pointer">
            <i class="fa-solid fa-shield-halved w-6"></i>
            <span>Bảo hành của tôi</span>
        </a>
        <a onclick="hideUserMenu()" class="flex px-6 py-5 hover:bg-amber-50 items-center gap-4 cursor-pointer">
            <i class="fa-solid fa-sign-out-alt w-6"></i>
            <span>Đăng xuất</span>
        </a>
    </div>

    <script>
        // ==================== CẤU HÌNH MÀU VÀNG TRẮNG ====================
        const PRIMARY = '#eab308'
        
        // ==================== DỮ LIỆU SẢN PHẨM (có thông số chi tiết) ====================
        let products = [
            {
                id: 1,
                name: "iPhone 16 Pro Max 256GB",
                category: "phone",
                price: 32990000,
                oldPrice: 35990000,
                image: "https://picsum.photos/id/1015/800/800",
                specs: {
                    "Màn hình": "6.9\" Super Retina XDR OLED, 120Hz",
                    "Chip": "A18 Pro",
                    "RAM": "8 GB",
                    "Bộ nhớ": "256 GB",
                    "Pin": "4680 mAh",
                    "Camera": "48MP Fusion + 48MP Ultra Wide",
                    "Hệ điều hành": "iOS 18"
                },
                rating: 5,
                reviews: [
                    { name: "Nguyễn Văn A", comment: "Màn hình đẹp xuất sắc, pin trâu hơn hẳn đời trước!", stars: 5 },
                    { name: "Trần Thị B", comment: "Thiết kế titan siêu nhẹ, camera đêm cực nét.", stars: 5 }
                ]
            },
            {
                id: 2,
                name: "Samsung Galaxy S25 Ultra",
                category: "phone",
                price: 28990000,
                oldPrice: 31990000,
                image: "https://picsum.photos/id/201/800/800",
                specs: {
                    "Màn hình": "6.8\" Dynamic AMOLED 2X, 120Hz",
                    "Chip": "Snapdragon 8 Elite",
                    "RAM": "12 GB",
                    "Bộ nhớ": "256 GB",
                    "Pin": "5000 mAh",
                    "Camera": "200MP chính",
                    "Hệ điều hành": "One UI 7"
                },
                rating: 4,
                reviews: [
                    { name: "Phạm Minh C", comment: "Bút S Pen siêu tiện, chụp ảnh cực đỉnh.", stars: 4 }
                ]
            },
            {
                id: 3,
                name: "iPad Air 6 M2 128GB",
                category: "tablet",
                price: 15990000,
                oldPrice: 17990000,
                image: "https://picsum.photos/id/301/800/800",
                specs: {
                    "Màn hình": "11\" Liquid Retina",
                    "Chip": "M2",
                    "RAM": "8 GB",
                    "Bộ nhớ": "128 GB",
                    "Pin": "28.93 Wh",
                    "Camera": "12MP",
                    "Hệ điều hành": "iPadOS 18"
                },
                rating: 5,
                reviews: []
            },
            {
                id: 4,
                name: "Xiaomi Redmi Note 14 Pro+",
                category: "phone",
                price: 6990000,
                oldPrice: 7990000,
                image: "https://picsum.photos/id/401/800/800",
                specs: {
                    "Màn hình": "6.67\" AMOLED 120Hz",
                    "Chip": "Dimensity 7300 Ultra",
                    "RAM": "12 GB",
                    "Bộ nhớ": "512 GB",
                    "Pin": "6200 mAh",
                    "Camera": "200MP",
                    "Hệ điều hành": "HyperOS"
                },
                rating: 4,
                reviews: []
            },
            {
                id: 5,
                name: "Apple Watch Ultra 2",
                category: "watch",
                price: 18990000,
                oldPrice: 21990000,
                image: "https://picsum.photos/id/501/800/800",
                specs: {
                    "Màn hình": "49mm Titanium",
                    "Chip": "S9 SiP",
                    "Pin": "36 giờ",
                    "Chống nước": "100m",
                    "Tính năng": "GPS, ECG, Blood Oxygen"
                },
                rating: 5,
                reviews: []
            }
        ]
        
        let cart = []
        let compareList = []
        let orders = [
            { id: "IMX-20260415-7842", product: "iPhone 16 Pro Max", status: "Đang giao", date: "15/04/2026", tracking: "GHTK-987654" },
            { id: "IMX-20260410-3921", product: "Galaxy Tab S10", status: "Đã nhận", date: "10/04/2026", tracking: "GHN-112233" }
        ]
        let communityPosts = [
            { user: "Hùng iFan", time: "2 giờ trước", content: "iPhone 16 Pro Max pin dùng 2 ngày chỉ sạc 1 lần. Quá đáng tiền!", likes: 124 },
            { user: "Mai Tech", time: "5 giờ trước", content: "Galaxy S25 Ultra chụp đêm đẹp hơn hẳn iPhone luôn!", likes: 87 }
        ]
        
        let currentProduct = null
        
        // Render sản phẩm
        function renderProducts(filtered) {
            const grid = document.getElementById('products-grid')
            grid.innerHTML = ''
            filtered.forEach(p => {
                const html = `
                <div onclick="showProductDetail(${p.id})" class="product-card bg-white rounded-3xl overflow-hidden cursor-pointer">
                    <img src="${p.image}" class="w-full h-64 object-cover">
                    <div class="p-6">
                        <h4 class="font-semibold text-xl">${p.name}</h4>
                        <div class="flex justify-between mt-4">
                            <div class="text-3xl font-bold text-amber-400">${(p.price/1000000).toFixed(1)}tr</div>
                            ${p.oldPrice ? `<div class="text-sm line-through text-gray-400">${(p.oldPrice/1000000).toFixed(1)}tr</div>` : ''}
                        </div>
                        <div class="flex text-amber-300 mt-2">${'★'.repeat(p.rating)}</div>
                    </div>
                </div>`
                grid.innerHTML += html
            })
        }
        
        function showProductDetail(id) {
            currentProduct = products.find(p => p.id === id)
            if (!currentProduct) return
            
            document.getElementById('modal-product-name').innerText = currentProduct.name
            document.getElementById('modal-image').src = currentProduct.image
            document.getElementById('modal-price').innerHTML = `<span class="text-5xl">${(currentProduct.price/1000000).toFixed(1)}tr ₫</span>`
            document.getElementById('modal-old-price').innerHTML = currentProduct.oldPrice ? `<span class="line-through text-xl">${(currentProduct.oldPrice/1000000).toFixed(1)}tr ₫</span>` : ''
            
            // Specs table
            let tableHTML = ''
            for (let [key, value] of Object.entries(currentProduct.specs)) {
                tableHTML += `<tr class="spec-row"><td class="py-4 font-medium">${key}</td><td class="py-4 text-right">${value}</td></tr>`
            }
            document.getElementById('spec-table').innerHTML = tableHTML
            
            // Reviews
            let reviewsHTML = `<p class="text-gray-400 mb-6">Chưa có đánh giá nào. Hãy là người đầu tiên!</p>`
            if (currentProduct.reviews && currentProduct.reviews.length) {
                reviewsHTML = currentProduct.reviews.map(r => `
                <div class="border-l-4 border-amber-300 pl-6">
                    <div class="flex justify-between"><span class="font-medium">${r.name}</span><span class="text-amber-300">${'★'.repeat(r.stars)}</span></div>
                    <p class="text-gray-600 mt-2">${r.comment}</p>
                </div>`).join('')
            }
            document.getElementById('reviews-list').innerHTML = reviewsHTML
            
            // Show modal
            document.getElementById('product-modal').classList.remove('hidden')
            document.getElementById('product-modal').classList.add('flex')
            showTab(0)
        }
        
        function hideProductModal() {
            const modal = document.getElementById('product-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
            currentProduct = null
        }
        
        function switchImage(el) {
            // Demo chuyển ảnh (có thể mở rộng)
            const mainImg = document.getElementById('modal-image')
            mainImg.style.opacity = 0
            setTimeout(() => {
                mainImg.src = el.querySelector('img').src
                mainImg.style.opacity = 1
            }, 150)
        }
        
        function showTab(n) {
            document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active', 'border-b-4', 'border-amber-400'))
            document.getElementById('tab-' + n).classList.add('active', 'border-b-4', 'border-amber-400')
            
            document.querySelectorAll('.tab-content').forEach(el => el.classList.add('hidden'))
            document.getElementById('tab-content-' + n).classList.remove('hidden')
        }
        
        // Thêm vào giỏ từ chi tiết
        function addCurrentToCart() {
            if (!currentProduct) return
            addToCart(currentProduct.id)
            hideProductModal()
        }
        
        // ==================== GIỎ HÀNG + THANH TOÁN ====================
        function addToCart(id) {
            const product = products.find(p => p.id === id)
            if (!product) return
            const exist = cart.find(item => item.id === id)
            if (exist) exist.quantity = (exist.quantity || 1) + 1
            else cart.push({...product, quantity: 1})
            updateCartCount()
            showToast(`${product.name} đã thêm vào giỏ hàng!`)
        }
        
        function updateCartCount() {
            const count = cart.reduce((acc, item) => acc + (item.quantity || 1), 0)
            document.getElementById('cart-count-badge').innerText = count
        }
        
        function showCart() {
            const modal = document.getElementById('cart-modal')
            const list = document.getElementById('cart-items-list')
            list.innerHTML = ''
            
            if (cart.length === 0) {
                list.innerHTML = `<div class="text-center py-16 text-gray-400 text-2xl">Giỏ hàng trống</div>`
                document.getElementById('cart-step-1').classList.remove('hidden')
                document.getElementById('cart-step-2').classList.add('hidden')
                modal.classList.remove('hidden')
                modal.classList.add('flex')
                return
            }
            
            let subtotal = 0
            cart.forEach((item, i) => {
                const total = item.price * (item.quantity || 1)
                subtotal += total
                list.innerHTML += `
                <div class="flex gap-6">
                    <img src="${item.image}" class="w-24 h-24 object-cover rounded-2xl">
                    <div class="flex-1">
                        <p class="font-semibold">${item.name}</p>
                        <p class="text-amber-400">${(item.price/1000000).toFixed(1)}tr ₫ × ${item.quantity || 1}</p>
                        <div class="mt-4 flex items-center">
                            <button onclick="changeCartQty(${i}, -1)" class="w-9 h-9 border rounded-2xl text-xl">-</button>
                            <span class="px-6 font-bold">${item.quantity || 1}</span>
                            <button onclick="changeCartQty(${i}, 1)" class="w-9 h-9 border rounded-2xl text-xl">+</button>
                            <button onclick="removeFromCart(${i})" class="ml-auto text-red-500 text-sm">Xóa</button>
                        </div>
                    </div>
                    <div class="text-3xl font-bold text-right">${(total/1000000).toFixed(1)}tr</div>
                </div>`
            })
            
            document.getElementById('cart-subtotal').innerText = `${(subtotal/1000000).toFixed(1)}tr ₫`
            document.getElementById('cart-step-1').classList.remove('hidden')
            document.getElementById('cart-step-2').classList.add('hidden')
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function changeCartQty(i, delta) {
            if (!cart[i]) return
            cart[i].quantity = Math.max(1, (cart[i].quantity || 1) + delta)
            showCart()
            updateCartCount()
        }
        
        function removeFromCart(i) {
            cart.splice(i, 1)
            showCart()
            updateCartCount()
        }
        
        function hideCart() {
            const modal = document.getElementById('cart-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        function goToPaymentStep() {
            document.getElementById('cart-step-1').classList.add('hidden')
            document.getElementById('cart-step-2').classList.remove('hidden')
        }
        
        function completeCheckout() {
            hideCart()
            const orderId = 'IMX-' + Date.now().toString().slice(-8)
            orders.unshift({
                id: orderId,
                product: cart.map(c => c.name).join(', '),
                status: "Đang xử lý",
                date: "15/04/2026",
                tracking: "GHN-" + Math.floor(100000 + Math.random() * 900000)
            })
            cart = []
            updateCartCount()
            
            setTimeout(() => {
                alert(`✅ Đơn hàng ${orderId} đã được xác nhận!\n\nBạn có thể theo dõi vận chuyển trong phần "Đơn hàng của tôi".\nCảm ơn bạn đã mua sắm tại IMEX!`)
            }, 600)
        }
        
        // ==================== SO SÁNH ====================
        function openCompareModal() {
            if (compareList.length === 0) {
                showToast('Chưa có sản phẩm nào trong danh sách so sánh. Hãy thêm từ trang chi tiết!')
                return
            }
            hideCompareModal()
            renderCompareTable()
            const modal = document.getElementById('compare-modal')
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function hideCompareModal() {
            const modal = document.getElementById('compare-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        function renderCompareTable() {
            // Lấy tất cả keys specs
            const allKeys = new Set()
            compareList.forEach(p => {
                Object.keys(p.specs).forEach(k => allKeys.add(k))
            })
            
            let theadHTML = `<th class="py-4 font-medium">Thông số</th>`
            compareList.forEach((p, i) => {
                theadHTML += `<th class="text-center font-semibold">${p.name}</th>`
            })
            document.querySelector('thead tr').innerHTML = theadHTML
            
            let bodyHTML = ''
            allKeys.forEach(key => {
                bodyHTML += `<tr class="spec-row"><td class="py-4 font-medium">${key}</td>`
                compareList.forEach(p => {
                    bodyHTML += `<td class="py-4 text-center">${p.specs[key] || '—'}</td>`
                })
                bodyHTML += `</tr>`
            })
            document.getElementById('compare-table-body').innerHTML = bodyHTML
        }
        
        function addToCompareFromDetail() {
            if (!currentProduct) return
            if (compareList.length >= 4) {
                showToast('Chỉ được so sánh tối đa 4 sản phẩm!')
                return
            }
            if (!compareList.find(p => p.id === currentProduct.id)) {
                compareList.push(currentProduct)
                showToast('Đã thêm vào danh sách so sánh!')
            }
            hideProductModal()
        }
        
        // ==================== CỘNG ĐỒNG ====================
        function renderCommunity() {
            const container = document.getElementById('community-feed')
            container.innerHTML = communityPosts.map(post => `
            <div class="border border-amber-200 rounded-3xl p-8">
                <div class="flex items-center gap-3">
                    <div class="w-10 h-10 bg-amber-100 rounded-2xl flex items-center justify-center text-2xl">👤</div>
                    <div>
                        <p class="font-medium">${post.user}</p>
                        <p class="text-xs text-gray-400">${post.time}</p>
                    </div>
                </div>
                <p class="mt-6 text-lg">${post.content}</p>
                <div class="flex justify-between mt-8 text-amber-400">
                    <i class="fa-solid fa-heart"></i>
                    <span class="text-sm">${post.likes} lượt thích</span>
                </div>
            </div>`).join('')
        }
        
        function postCommunity() {
            const input = document.getElementById('community-input')
            if (!input.value.trim()) return
            communityPosts.unshift({
                user: "Bạn",
                time: "Vừa xong",
                content: input.value,
                likes: 0
            })
            input.value = ''
            renderCommunity()
            showToast('Bài viết đã được đăng lên cộng đồng!')
        }
        
        // ==================== BẢO HÀNH ====================
        function checkWarranty() {
            const serial = document.getElementById('warranty-serial').value.trim()
            if (!serial) {
                showToast('Vui lòng nhập số serial / IMEI')
                return
            }
            showToast(`✅ Bảo hành của thiết bị ${serial} còn hiệu lực đến 12/2027. Bạn có thể đến trung tâm IMEX bất kỳ lúc nào!`)
        }
        
        // ==================== ĐƠN HÀNG ====================
        function showOrders() {
            hideUserMenu()
            const modal = document.getElementById('orders-modal')
            const container = document.getElementById('orders-list')
            
            let html = ''
            orders.forEach(order => {
                html += `
                <div class="flex justify-between border border-amber-200 rounded-3xl p-8">
                    <div>
                        <p class="font-semibold text-xl">${order.id}</p>
                        <p class="text-gray-500">${order.product}</p>
                        <p class="text-sm mt-2">${order.date}</p>
                    </div>
                    <div class="text-right">
                        <span class="px-6 py-3 text-sm rounded-3xl ${order.status === 'Đang giao' ? 'bg-blue-100 text-blue-600' : 'bg-green-100 text-green-700'}">${order.status}</span>
                        <p onclick="trackOrder('${order.tracking}')" class="mt-6 text-amber-400 cursor-pointer flex items-center justify-end">Theo dõi <i class="fa-solid fa-truck ml-2"></i></p>
                    </div>
                </div>`
            })
            container.innerHTML = html || `<p class="text-center py-12 text-gray-400 text-2xl">Bạn chưa có đơn hàng nào</p>`
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function hideOrders() {
            const modal = document.getElementById('orders-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
        }
        
        function trackOrder(code) {
            hideOrders()
            showToast(`📦 Đang theo dõi vận chuyển: ${code} • Dự kiến giao ngày mai lúc 14:30`)
        }
        
        // ==================== FILTER & SEARCH ====================
        function filterCategory(cat) {
            const filtered = products.filter(p => p.category === cat)
            renderProducts(filtered)
            navigateToSection('shop')
        }
        
        function toggleSearch() {
            const input = document.getElementById('search-input')
            input.classList.toggle('hidden')
            if (!input.classList.contains('hidden')) input.focus()
        }
        
        // ==================== UTILS ====================
        function showToast(msg) {
            const toast = document.createElement('div')
            toast.style.cssText = `position:fixed; bottom:30px; right:30px; background:#eab308; color:#fff; padding:18px 26px; border-radius:9999px; box-shadow:20px 20px 30px -10px #f59e0b; z-index:99999; display:flex; align-items:center; gap:12px;`
            toast.innerHTML = `<i class="fa-solid fa-check-circle"></i> ${msg}`
            document.body.append(toast)
            setTimeout(() => {
                toast.style.transform = 'translateY(80px)'
                toast.style.opacity = 0
                setTimeout(() => toast.remove(), 400)
            }, 3200)
        }
        
        function navigateToSection(id) {
            document.getElementById(id).scrollIntoView({ behavior: 'smooth' })
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
        
        function toggleUserMenu() {
            const dd = document.getElementById('user-dropdown')
            dd.classList.toggle('hidden')
        }
        
        function hideUserMenu() {
            document.getElementById('user-dropdown').classList.add('hidden')
        }
        
        // ==================== KHỞI ĐỘNG ====================
        window.onload = () => {
            renderProducts(products)
            renderCommunity()
            updateCartCount()
            
            console.log('%c🚀 IMEX Mobile đã được nâng cấp hoàn toàn: Màu vàng trắng sang trọng • Trang chi tiết • So sánh thông số • Thanh toán & vận chuyển • Bảo hành điện tử • Cộng đồng người dùng', 'background:#eab308;color:#fff;padding:4px 8px;border-radius:4px;font-weight:bold')
        }
    </script>
</body>
</html>
```
