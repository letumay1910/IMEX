<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động. Chính hãng - Giá tốt - Dịch vụ chuyên nghiệp">
    <title>IMEX - Thiết Bị Di Động Chuyên Nghiệp</title>
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
            background: linear-gradient(92deg, #10b981 0%, #059669 100%);
        }
        
        .product-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-12px);
            box-shadow: 0 25px 50px -12px rgb(16 185 129);
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
        
        .nav-link:hover:after {
            width: 100%;
        }
        
        .section-header:after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background: #10b981;
            bottom: -8px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 9999px;
        }
        
        .modal {
            animation: modalPop 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
        }
        
        @keyframes modalPop {
            0% { opacity: 0; transform: scale(0.95) translateY(20px); }
            100% { opacity: 1; transform: scale(1) translateY(0); }
        }
        
        .spec-row:hover {
            background-color: #f0fdf4;
        }
        
        .status-dot {
            animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
        }
    </style>
</head>
<body class="tailwind-ready bg-white">

    <!-- NAVBAR -->
    <nav class="bg-white border-b-4 border-emerald-500 sticky top-0 z-50 shadow-lg">
        <div class="max-w-screen-2xl mx-auto">
            <div class="px-8 py-5 flex items-center justify-between">
                
                <!-- Logo -->
                <div class="flex items-center gap-x-3">
                    <div class="w-11 h-11 bg-emerald-500 rounded-3xl flex items-center justify-center text-white text-4xl shadow-inner">📱</div>
                    <h1 class="logo-font text-4xl font-bold tracking-[-1px] text-emerald-600">IMEX</h1>
                    <span class="text-emerald-600 font-semibold text-lg tracking-[1px] mt-1">MOBILE</span>
                </div>

                <!-- Desktop Menu -->
                <div class="hidden xl:flex items-center gap-x-10 text-base font-semibold text-gray-700">
                    <a onclick="navigateToSection('home')" class="nav-link">Trang chủ</a>
                    <a onclick="navigateToSection('shop')" class="nav-link">Cửa hàng</a>
                    <a onclick="navigateToSection('compare')" class="nav-link">So sánh</a>
                    <a onclick="navigateToSection('community')" class="nav-link">Cộng đồng</a>
                    <a onclick="navigateToSection('warranty')" class="nav-link">Bảo hành</a>
                    <a onclick="showOrders()" class="nav-link">Đơn hàng</a>
                </div>

                <div class="flex items-center gap-x-6">
                    <!-- Search -->
                    <div class="relative group">
                        <div onclick="toggleSearch()" class="flex items-center bg-emerald-50 border border-emerald-200 hover:border-emerald-300 rounded-3xl px-6 py-3.5 cursor-pointer">
                            <i class="fa-solid fa-magnifying-glass text-emerald-500 text-xl"></i>
                            <input id="search-input" 
                                   type="text" 
                                   placeholder="Tìm kiếm điện thoại, tablet, phụ kiện..." 
                                   class="hidden md:block bg-transparent outline-none w-80 ml-4 text-sm placeholder:text-emerald-400">
                        </div>
                    </div>

                    <!-- Cart -->
                    <div onclick="showCart()" class="relative cursor-pointer flex items-center justify-center w-12 h-12 hover:bg-emerald-50 rounded-3xl">
                        <i class="fa-solid fa-shopping-cart text-3xl text-gray-700"></i>
                        <span id="cart-count-badge" 
                              class="absolute -top-1 -right-1 bg-emerald-500 text-white text-xs font-bold w-6 h-6 rounded-2xl flex items-center justify-center shadow-md">0</span>
                    </div>

                    <!-- User -->
                    <div onclick="toggleUserMenu()" class="flex items-center gap-x-2 cursor-pointer">
                        <div class="w-9 h-9 bg-emerald-100 rounded-2xl flex items-center justify-center text-2xl text-emerald-600">👤</div>
                        <div class="hidden md:block">
                            <p id="user-name-display" class="text-sm font-semibold text-gray-800">Ánh</p>
                        </div>
                    </div>

                    <!-- Mobile Hamburger -->
                    <button onclick="toggleMobileMenu()" class="xl:hidden w-12 h-12 flex items-center justify-center text-4xl text-emerald-500">
                        <i id="hamburger-icon" class="fa-solid fa-bars"></i>
                    </button>
                </div>
            </div>
        </div>

        <!-- Mobile Menu -->
        <div id="mobile-menu" class="hidden xl:hidden bg-white border-t px-8 py-8 shadow-2xl">
            <div class="flex flex-col gap-y-6 text-lg font-medium text-gray-700">
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
    <section id="home" class="hero-bg text-white min-h-screen flex items-center relative overflow-hidden">
        <div class="max-w-screen-2xl mx-auto px-8 grid xl:grid-cols-2 gap-16 items-center">
            <div class="space-y-10">
                <div class="inline-flex items-center bg-white/20 backdrop-blur-xl px-8 py-3 rounded-3xl text-sm font-semibold tracking-wider">
                    <span class="w-3 h-3 bg-white rounded-full status-dot mr-2"></span>
                    CHÍNH HÃNG • BẢO HÀNH 24 THÁNG • GIAO SIÊU TỐC
                </div>
                
                <h1 class="text-6xl xl:text-7xl font-bold leading-none tracking-[-2px]">
                    IMEX<br>
                    <span class="text-emerald-100">Thiết bị di động</span><br>
                    chất lượng cao
                </h1>
                
                <p class="text-3xl text-emerald-100 max-w-lg">Điện thoại • Tablet • Phụ kiện • Smartwatch<br>Trải nghiệm mua sắm chuyên nghiệp</p>

                <div class="flex flex-wrap gap-4">
                    <button onclick="navigateToSection('shop')" 
                            class="bg-white text-emerald-600 hover:bg-emerald-50 px-10 py-6 rounded-3xl font-bold text-2xl flex items-center gap-x-4 shadow-2xl">
                        <i class="fa-solid fa-cart-shopping"></i>
                        KHÁM PHÁ CỬA HÀNG
                    </button>
                    <button onclick="navigateToSection('compare')" 
                            class="border-2 border-white hover:bg-white/10 px-10 py-6 rounded-3xl font-bold text-2xl flex items-center gap-x-4">
                        <i class="fa-solid fa-balance-scale"></i>
                        SO SÁNH NGAY
                    </button>
                </div>

                <div class="flex items-center gap-x-12 text-sm">
                    <div class="flex -space-x-6">
                        <div class="w-10 h-10 bg-white/90 text-emerald-600 rounded-2xl flex items-center justify-center ring-4 ring-emerald-500 text-xl">✓</div>
                        <div class="w-10 h-10 bg-white/90 text-emerald-600 rounded-2xl flex items-center justify-center ring-4 ring-emerald-500 text-xl">✓</div>
                    </div>
                    <div>
                        <p class="font-semibold">Hơn 85.000 khách hàng tin tưởng</p>
                        <p class="text-emerald-100">Đánh giá trung bình 4.96/5 • Chính hãng 100%</p>
                    </div>
                </div>
            </div>

            <!-- Hero visual -->
            <div class="relative hidden xl:flex justify-center items-center">
                <div class="absolute w-[460px] h-[460px] bg-white/10 backdrop-blur-3xl rounded-[4rem] rotate-12"></div>
                <img src="https://picsum.photos/id/1015/900/900" 
                     alt="iPhone 16 Pro Max" 
                     class="relative z-10 w-96 rounded-3xl shadow-2xl border-8 border-white rotate-[-8deg]">
                
                <div class="absolute top-12 left-12 bg-white text-emerald-600 text-sm font-semibold px-7 py-4 rounded-3xl shadow-2xl flex items-center gap-3">
                    <i class="fa-solid fa-shield-halved text-2xl"></i>
                    <div>Bảo hành điện tử<br><span class="text-xs text-gray-500">Tra cứu tức thì</span></div>
                </div>
                <div class="absolute bottom-12 right-12 bg-white text-emerald-600 text-sm font-semibold px-7 py-4 rounded-3xl shadow-2xl flex items-center gap-3">
                    <i class="fa-solid fa-truck-fast text-2xl"></i>
                    <div>Giao hàng 90 phút<br><span class="text-xs text-gray-500">Miễn phí từ 2 triệu</span></div>
                </div>
            </div>
        </div>
    </section>

    <!-- CATEGORIES -->
    <section class="max-w-screen-2xl mx-auto px-8 py-20">
        <div class="flex justify-between items-end mb-12">
            <div>
                <span class="px-6 py-2 bg-emerald-100 text-emerald-600 text-sm font-bold rounded-3xl">DANH MỤC SẢN PHẨM</span>
                <h2 class="section-header text-5xl font-semibold mt-3">Chọn thiết bị phù hợp</h2>
            </div>
            <a onclick="navigateToSection('shop')" class="text-emerald-600 font-semibold flex items-center gap-2">Xem tất cả <i class="fa-solid fa-arrow-right"></i></a>
        </div>
        
        <div class="grid grid-cols-2 md:grid-cols-4 gap-8">
            <div onclick="filterCategory('phone')" class="group bg-white border border-transparent hover:border-emerald-300 rounded-3xl p-10 cursor-pointer text-center">
                <div class="text-7xl mb-8 group-hover:scale-110 transition">📱</div>
                <h3 class="text-3xl font-semibold">Điện thoại</h3>
                <p class="text-emerald-500 text-sm mt-2">248 sản phẩm • iPhone, Samsung, Xiaomi</p>
            </div>
            <div onclick="filterCategory('tablet')" class="group bg-white border border-transparent hover:border-emerald-300 rounded-3xl p-10 cursor-pointer text-center">
                <div class="text-7xl mb-8 group-hover:scale-110 transition">📟</div>
                <h3 class="text-3xl font-semibold">Máy tính bảng</h3>
                <p class="text-emerald-500 text-sm mt-2">112 sản phẩm • iPad, Galaxy Tab</p>
            </div>
            <div onclick="filterCategory('accessory')" class="group bg-white border border-transparent hover:border-emerald-300 rounded-3xl p-10 cursor-pointer text-center">
                <div class="text-7xl mb-8 group-hover:scale-110 transition">🔌</div>
                <h3 class="text-3xl font-semibold">Phụ kiện</h3>
                <p class="text-emerald-500 text-sm mt-2">387 sản phẩm • Tai nghe, sạc, ốp lưng</p>
            </div>
            <div onclick="filterCategory('watch')" class="group bg-white border border-transparent hover:border-emerald-300 rounded-3xl p-10 cursor-pointer text-center">
                <div class="text-7xl mb-8 group-hover:scale-110 transition">⌚</div>
                <h3 class="text-3xl font-semibold">Smartwatch</h3>
                <p class="text-emerald-500 text-sm mt-2">89 sản phẩm • Apple Watch, Galaxy Watch</p>
            </div>
        </div>
    </section>

    <!-- SHOP SECTION -->
    <section id="shop" class="bg-emerald-50 py-20">
        <div class="max-w-screen-2xl mx-auto px-8">
            <h2 class="section-header text-5xl font-semibold text-center mb-14">Sản phẩm nổi bật</h2>
            <div id="products-grid" class="grid grid-cols-2 md:grid-cols-3 xl:grid-cols-4 gap-8">
                <!-- JS render -->
            </div>
        </div>
    </section>

    <!-- COMPARE -->
    <section id="compare" class="max-w-screen-2xl mx-auto px-8 py-20">
        <div class="flex justify-between items-end mb-12">
            <h2 class="text-5xl font-semibold">Hệ thống đối chiếu thông số kỹ thuật</h2>
            <button onclick="openCompareModal()" 
                    class="flex items-center gap-x-3 bg-emerald-500 hover:bg-emerald-600 text-white px-10 py-5 rounded-3xl font-semibold text-xl shadow-inner">
                <i class="fa-solid fa-balance-scale"></i>
                SO SÁNH (tối đa 4 sản phẩm)
            </button>
        </div>
        <div id="compare-preview" class="hidden grid grid-cols-4 gap-6 text-sm"></div>
    </section>

    <!-- COMMUNITY -->
    <section id="community" class="max-w-screen-2xl mx-auto px-8 py-20 bg-white">
        <h2 class="section-header text-5xl font-semibold text-center mb-12">Cộng đồng người dùng IMEX</h2>
        <div id="community-feed" class="grid md:grid-cols-3 gap-8">
            <!-- JS render -->
        </div>
        
        <div class="mt-16 bg-emerald-50 rounded-3xl p-10">
            <h3 class="font-semibold text-2xl mb-6 flex items-center gap-x-3"><i class="fa-solid fa-comment-dots"></i> Chia sẻ trải nghiệm của bạn</h3>
            <textarea id="community-input" rows="4" 
                      class="w-full rounded-3xl p-8 border border-emerald-200 focus:border-emerald-500 outline-none text-lg" 
                      placeholder="Bạn đang dùng thiết bị nào? Chia sẻ đánh giá, mẹo hay..."></textarea>
            <button onclick="postCommunity()" 
                    class="mt-8 bg-emerald-500 hover:bg-emerald-600 text-white px-12 py-6 rounded-3xl font-semibold text-xl">ĐĂNG BÀI NGAY</button>
        </div>
    </section>

    <!-- WARRANTY -->
    <section id="warranty" class="max-w-screen-2xl mx-auto px-8 py-20 bg-emerald-50">
        <div class="grid xl:grid-cols-12 gap-16 items-center">
            <div class="xl:col-span-5">
                <h2 class="text-5xl font-semibold leading-none">Bảo hành điện tử<br>chuyên nghiệp</h2>
                <p class="mt-8 text-xl text-gray-600">Tra cứu thông tin bảo hành chỉ trong 10 giây. Toàn bộ dữ liệu được lưu trữ an toàn trên hệ thống IMEX.</p>
                <div class="mt-12 bg-white rounded-3xl p-8 shadow-sm">
                    <input id="warranty-serial" type="text" placeholder="Nhập số serial / IMEI của thiết bị" 
                           class="w-full px-8 py-7 rounded-3xl border-2 border-emerald-300 focus:border-emerald-500 text-lg outline-none">
                    <button onclick="checkWarranty()" 
                            class="mt-8 w-full bg-emerald-500 hover:bg-emerald-600 text-white py-7 rounded-3xl text-2xl font-semibold">TRA CỨU NGAY</button>
                </div>
            </div>
            <div class="xl:col-span-7 bg-white rounded-3xl p-10">
                <h4 class="text-emerald-500 font-medium mb-6">Ví dụ kết quả tra cứu</h4>
                <div id="warranty-examples" class="space-y-8"></div>
            </div>
        </div>
    </section>

    <!-- PRODUCT DETAIL MODAL -->
    <div onclick="if(event.target.id==='product-modal')hideProductModal()" 
         id="product-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-6xl rounded-3xl modal overflow-hidden">
            
            <div class="px-10 py-6 border-b flex items-center justify-between sticky top-0 bg-white z-10">
                <h2 id="modal-product-name" class="text-4xl font-bold"></h2>
                <i onclick="hideProductModal()" class="fa-solid fa-xmark text-4xl cursor-pointer hover:text-emerald-500"></i>
            </div>
            
            <div class="grid xl:grid-cols-12 gap-10 p-10">
                <!-- Hình ảnh -->
                <div class="xl:col-span-5">
                    <img id="modal-image" src="" alt="" class="w-full rounded-3xl shadow-inner">
                    <div class="flex gap-4 mt-8">
                        <div onclick="switchImage(this)" class="flex-1 cursor-pointer border-2 border-emerald-500 rounded-2xl p-2"><img src="https://picsum.photos/id/1015/300/300" class="rounded-xl"></div>
                        <div onclick="switchImage(this)" class="flex-1 cursor-pointer border border-transparent rounded-2xl p-2"><img src="https://picsum.photos/id/201/300/300" class="rounded-xl"></div>
                        <div onclick="switchImage(this)" class="flex-1 cursor-pointer border border-transparent rounded-2xl p-2"><img src="https://picsum.photos/id/301/300/300" class="rounded-xl"></div>
                    </div>
                </div>
                
                <!-- Chi tiết -->
                <div class="xl:col-span-7 space-y-10">
                    <div class="flex justify-between items-end">
                        <div>
                            <p id="modal-price" class="text-5xl font-bold text-emerald-500"></p>
                            <p id="modal-old-price" class="text-gray-400 line-through text-xl"></p>
                        </div>
                        <button onclick="addCurrentToCart()" 
                                class="px-12 py-6 bg-emerald-500 hover:bg-emerald-600 text-white rounded-3xl text-2xl font-semibold flex items-center gap-x-4">
                            <i class="fa-solid fa-cart-plus"></i>
                            THÊM VÀO GIỎ HÀNG
                        </button>
                    </div>
                    
                    <!-- Tabs -->
                    <div class="flex border-b border-gray-200">
                        <button onclick="showTab(0)" id="tab-0" class="tab-btn px-10 py-4 font-semibold border-b-4 border-emerald-500 active">Thông số kỹ thuật</button>
                        <button onclick="showTab(1)" id="tab-1" class="tab-btn px-10 py-4 font-semibold">Mô tả sản phẩm</button>
                        <button onclick="showTab(2)" id="tab-2" class="tab-btn px-10 py-4 font-semibold">Đánh giá người dùng</button>
                        <button onclick="showTab(3)" id="tab-3" class="tab-btn px-10 py-4 font-semibold">Bảo hành</button>
                    </div>
                    
                    <!-- Tab contents -->
                    <div id="tab-content-0" class="tab-content">
                        <table class="w-full">
                            <tbody id="spec-table" class="divide-y text-sm"></tbody>
                        </table>
                    </div>
                    <div id="tab-content-1" class="tab-content hidden text-lg leading-relaxed"></div>
                    <div id="tab-content-2" class="tab-content hidden">
                        <div id="reviews-list" class="space-y-10"></div>
                        <div class="mt-10 p-8 bg-emerald-50 rounded-3xl">
                            <h4 class="font-semibold mb-4">Viết đánh giá của bạn</h4>
                            <textarea id="review-input" rows="3" class="w-full rounded-3xl p-6 border border-emerald-200" placeholder="Chia sẻ trải nghiệm..."></textarea>
                            <button onclick="submitReview()" class="mt-4 bg-emerald-500 text-white px-10 py-4 rounded-3xl">Gửi đánh giá</button>
                        </div>
                    </div>
                    <div id="tab-content-3" class="tab-content hidden text-lg"></div>
                    
                    <button onclick="addToCompareFromDetail()" 
                            class="w-full border-2 border-dashed border-emerald-500 text-emerald-600 py-7 rounded-3xl font-semibold flex items-center justify-center gap-3 text-xl">
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
             class="bg-white w-full max-w-7xl rounded-3xl modal max-h-[92vh] overflow-hidden flex flex-col">
            <div class="px-10 py-7 border-b flex justify-between items-center text-3xl font-semibold">
                <span>Đối chiếu thông số kỹ thuật</span>
                <i onclick="hideCompareModal()" class="fa-solid fa-xmark text-4xl cursor-pointer"></i>
            </div>
            <div class="flex-1 overflow-auto p-10">
                <table class="w-full text-left min-w-[800px]">
                    <thead>
                        <tr class="border-b-2">
                            <th class="py-5 font-medium text-lg">Thông số</th>
                            <th id="compare-col-1" class="py-5 font-semibold text-center"></th>
                            <th id="compare-col-2" class="py-5 font-semibold text-center"></th>
                            <th id="compare-col-3" class="py-5 font-semibold text-center"></th>
                            <th id="compare-col-4" class="py-5 font-semibold text-center"></th>
                        </tr>
                    </thead>
                    <tbody id="compare-table-body" class="text-base divide-y"></tbody>
                </table>
            </div>
        </div>
    </div>

    <!-- CART + CHECKOUT MODAL -->
    <div onclick="if(event.target.id==='cart-modal')hideCart()" 
         id="cart-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-4xl rounded-3xl modal flex flex-col max-h-[92vh]">
            
            <div class="px-10 py-7 border-b text-2xl font-semibold flex justify-between">
                <span>Giỏ hàng &amp; Thanh toán</span>
                <i onclick="hideCart()" class="fa-solid fa-xmark cursor-pointer text-4xl"></i>
            </div>
            
            <div id="cart-step-1" class="flex-1 overflow-auto p-10 space-y-10">
                <div id="cart-items-list" class="space-y-8"></div>
                
                <div class="pt-8 border-t">
                    <h4 class="font-semibold mb-6">Chọn hình thức vận chuyển</h4>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                        <label class="flex justify-between items-center border-2 border-transparent hover:border-emerald-400 rounded-3xl p-6 cursor-pointer">
                            <div>
                                <p class="font-medium">Giao nhanh 90 phút (Vinh &amp; khu vực lân cận)</p>
                                <p class="text-xs text-emerald-500">Miễn phí từ 2.000.000 ₫</p>
                            </div>
                            <input type="radio" name="shipping" checked class="accent-emerald-500">
                            <span class="font-bold text-xl">0 ₫</span>
                        </label>
                        <label class="flex justify-between items-center border-2 border-transparent hover:border-emerald-400 rounded-3xl p-6 cursor-pointer">
                            <div>
                                <p class="font-medium">Giao toàn quốc 1-2 ngày</p>
                                <p class="text-xs text-emerald-500">Phí cố định</p>
                            </div>
                            <input type="radio" name="shipping" class="accent-emerald-500">
                            <span class="font-bold text-xl">35.000 ₫</span>
                        </label>
                        <label class="flex justify-between items-center border-2 border-transparent hover:border-emerald-400 rounded-3xl p-6 cursor-pointer">
                            <div>
                                <p class="font-medium">Giao hỏa tốc (trong 4 giờ)</p>
                                <p class="text-xs text-emerald-500">Chỉ áp dụng nội thành Vinh</p>
                            </div>
                            <input type="radio" name="shipping" class="accent-emerald-500">
                            <span class="font-bold text-xl">99.000 ₫</span>
                        </label>
                    </div>
                </div>
                
                <button onclick="goToPaymentStep()" 
                        class="w-full py-8 bg-emerald-500 hover:bg-emerald-600 text-white text-2xl font-semibold rounded-3xl">TIẾP TỤC THANH TOÁN</button>
            </div>
            
            <!-- Payment step -->
            <div id="cart-step-2" class="flex-1 hidden p-10 space-y-8 overflow-auto">
                <h3 class="text-2xl font-semibold">Phương thức thanh toán</h3>
                <div class="space-y-6">
                    <label class="flex items-center gap-6 border-2 p-7 rounded-3xl cursor-pointer hover:border-emerald-400">
                        <i class="fa-brands fa-cc-visa text-5xl text-emerald-500"></i>
                        <div class="flex-1 font-medium">Thẻ tín dụng / Thẻ ghi nợ (Visa, Mastercard)</div>
                        <input type="radio" name="payment" checked class="accent-emerald-500 scale-125">
                    </label>
                    <label class="flex items-center gap-6 border-2 p-7 rounded-3xl cursor-pointer hover:border-emerald-400">
                        <i class="fa-brands fa-cc-mastercard text-5xl text-emerald-500"></i>
                        <div class="flex-1 font-medium">Ví điện tử Momo, ZaloPay, VNPAY</div>
                        <input type="radio" name="payment" class="accent-emerald-500 scale-125">
                    </label>
                    <label class="flex items-center gap-6 border-2 p-7 rounded-3xl cursor-pointer hover:border-emerald-400">
                        <i class="fa-solid fa-truck text-5xl text-emerald-500"></i>
                        <div class="flex-1 font-medium">Thanh toán khi nhận hàng (COD)</div>
                        <input type="radio" name="payment" class="accent-emerald-500 scale-125">
                    </label>
                </div>
                
                <button onclick="completeCheckout()" 
                        class="w-full py-8 bg-emerald-500 hover:bg-emerald-600 text-white text-2xl font-semibold rounded-3xl">XÁC NHẬN ĐƠN HÀNG &amp; THANH TOÁN</button>
            </div>
        </div>
    </div>

    <!-- ORDERS MODAL -->
    <div onclick="if(event.target.id==='orders-modal')hideOrders()" 
         id="orders-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center p-4">
        <div onclick="event.stopImmediatePropagation()" 
             class="bg-white w-full max-w-5xl rounded-3xl modal flex flex-col">
            <div class="px-10 py-7 border-b text-3xl font-semibold flex justify-between">
                <span>Đơn hàng của tôi</span>
                <i onclick="hideOrders()" class="fa-solid fa-xmark cursor-pointer"></i>
            </div>
            <div id="orders-list" class="flex-1 p-10 overflow-auto space-y-8"></div>
        </div>
    </div>

    <!-- USER DROPDOWN -->
    <div id="user-dropdown" onclick="if(event.target.id==='user-dropdown')this.classList.add('hidden')" 
         class="hidden fixed top-20 right-10 bg-white shadow-2xl rounded-3xl py-4 w-80 z-[9999]">
        <div class="px-8 py-6 border-b flex gap-4">
            <div class="text-5xl">👤</div>
            <div class="flex-1">
                <p class="font-semibold text-xl">Xin chào, Ánh!</p>
                <p class="text-emerald-600">anh.vinh@imex.vn</p>
            </div>
        </div>
        <a onclick="hideUserMenu();showOrders()" class="flex items-center gap-4 px-8 py-6 hover:bg-emerald-50 cursor-pointer">
            <i class="fa-solid fa-receipt w-6"></i>
            <span class="flex-1">Đơn hàng &amp; Theo dõi vận chuyển</span>
        </a>
        <a onclick="hideUserMenu();navigateToSection('warranty')" class="flex items-center gap-4 px-8 py-6 hover:bg-emerald-50 cursor-pointer">
            <i class="fa-solid fa-shield-halved w-6"></i>
            <span class="flex-1">Bảo hành của tôi</span>
        </a>
        <a onclick="hideUserMenu()" class="flex items-center gap-4 px-8 py-6 hover:bg-emerald-50 cursor-pointer text-red-500">
            <i class="fa-solid fa-sign-out-alt w-6"></i>
            <span class="flex-1">Đăng xuất</span>
        </a>
    </div>

    <script>
        // ==================== CẤU HÌNH CHÍNH ====================
        const PRIMARY_COLOR = '#10b981'
        
        // ==================== DỮ LIỆU SẢN PHẨM (chi tiết & chuyên nghiệp) ====================
        let products = [
            {
                id: 1,
                name: "iPhone 16 Pro Max 256GB",
                category: "phone",
                price: 32990000,
                oldPrice: 35990000,
                image: "https://picsum.photos/id/1015/900/900",
                description: "Thiết kế titan cao cấp, chip A18 Pro mạnh mẽ, camera 48MP Fusion, pin lớn 4680mAh. Trải nghiệm iOS 18 mượt mà.",
                specs: {
                    "Màn hình": "6.9 inch Super Retina XDR OLED, 120Hz, Always-On",
                    "Chipset": "Apple A18 Pro",
                    "RAM": "8 GB",
                    "Bộ nhớ trong": "256 GB",
                    "Pin": "4680 mAh, sạc nhanh 45W",
                    "Camera sau": "48MP Fusion + 48MP Ultra Wide + 12MP Tele",
                    "Camera trước": "12MP",
                    "Hệ điều hành": "iOS 18",
                    "Khác": "Face ID, IP68, eSIM"
                },
                rating: 5,
                reviews: [
                    { name: "Nguyễn Văn A", stars: 5, comment: "Pin cực trâu, camera đêm xuất sắc. Thiết kế sang trọng." },
                    { name: "Trần Thị B", stars: 5, comment: "Mua lần thứ 2 tại IMEX, luôn hài lòng về dịch vụ." }
                ]
            },
            {
                id: 2,
                name: "Samsung Galaxy S25 Ultra",
                category: "phone",
                price: 28990000,
                oldPrice: 31990000,
                image: "https://picsum.photos/id/201/900/900",
                description: "Màn hình Dynamic AMOLED 2X 6.8 inch, Snapdragon 8 Elite, camera 200MP, bút S Pen tích hợp.",
                specs: {
                    "Màn hình": "6.8 inch Dynamic AMOLED 2X, 120Hz",
                    "Chipset": "Snapdragon 8 Elite for Galaxy",
                    "RAM": "12 GB",
                    "Bộ nhớ trong": "256 GB",
                    "Pin": "5000 mAh, sạc nhanh 45W",
                    "Camera sau": "200MP chính + 50MP Ultra Wide + 10MP Tele x2",
                    "Camera trước": "12MP",
                    "Hệ điều hành": "One UI 7 (Android 15)",
                    "Khác": "S Pen, IP68, Wireless DeX"
                },
                rating: 4,
                reviews: [
                    { name: "Phạm Minh C", stars: 4, comment: "Bút S Pen cực tiện lợi cho công việc." }
                ]
            },
            {
                id: 3,
                name: "iPad Air 6 M2 128GB Wi-Fi",
                category: "tablet",
                price: 15990000,
                oldPrice: 17990000,
                image: "https://picsum.photos/id/301/900/900",
                description: "Màn hình Liquid Retina 11 inch, chip M2 mạnh mẽ, hỗ trợ Apple Pencil Pro.",
                specs: {
                    "Màn hình": "11 inch Liquid Retina, 120Hz",
                    "Chipset": "Apple M2",
                    "RAM": "8 GB",
                    "Bộ nhớ trong": "128 GB",
                    "Pin": "28.93 Wh",
                    "Camera": "12MP sau + 12MP trước",
                    "Hệ điều hành": "iPadOS 18"
                },
                rating: 5,
                reviews: []
            },
            {
                id: 4,
                name: "Xiaomi Redmi Note 14 Pro+ 5G",
                category: "phone",
                price: 6990000,
                oldPrice: 7990000,
                image: "https://picsum.photos/id/401/900/900",
                description: "Pin siêu lớn 6200mAh, camera 200MP, sạc nhanh 120W.",
                specs: {
                    "Màn hình": "6.67 inch AMOLED 120Hz",
                    "Chipset": "MediaTek Dimensity 7300 Ultra",
                    "RAM": "12 GB",
                    "Bộ nhớ trong": "512 GB",
                    "Pin": "6200 mAh, sạc 120W",
                    "Camera": "200MP chính",
                    "Hệ điều hành": "HyperOS 2.0"
                },
                rating: 4,
                reviews: []
            },
            {
                id: 5,
                name: "Apple Watch Ultra 2 Titanium",
                category: "watch",
                price: 18990000,
                oldPrice: 21990000,
                image: "https://picsum.photos/id/501/900/900",
                description: "Màn hình 49mm, pin 36 giờ, theo dõi sức khỏe chuyên sâu.",
                specs: {
                    "Màn hình": "49mm OLED Always-On",
                    "Chip": "S9 SiP",
                    "Pin": "36 giờ sử dụng",
                    "Chống nước": "100m (WR100)",
                    "Tính năng": "ECG, SpO2, Nhịp tim, Nhiệt độ"
                },
                rating: 5,
                reviews: []
            }
        ]
        
        let cart = []
        let compareList = []
        let orders = [
            { id: "IMX-240415-7842", product: "iPhone 16 Pro Max", status: "Đang giao hàng", date: "15/04/2026", tracking: "GHTK-987654321" },
            { id: "IMX-240410-3921", product: "iPad Air 6", status: "Đã nhận hàng", date: "10/04/2026", tracking: "GHN-1122334455" }
        ]
        let communityPosts = [
            { user: "Hùng iFan", time: "2 giờ trước", content: "iPhone 16 Pro Max pin dùng thoải mái 2 ngày chỉ sạc 1 lần. Camera đêm cực nét!", likes: 142 },
            { user: "Mai Tech", time: "6 giờ trước", content: "Redmi Note 14 Pro+ sạc 120W chỉ 18 phút đầy pin. Giá trị tiền bạc tuyệt vời!", likes: 91 }
        ]
        
        let currentProduct = null
        
        // ==================== RENDER SẢN PHẨM ====================
        function renderProducts(filteredProducts) {
            const grid = document.getElementById('products-grid')
            grid.innerHTML = ''
            
            filteredProducts.forEach(product => {
                const discount = product.oldPrice ? Math.round((1 - product.price / product.oldPrice) * 100) : 0
                const card = document.createElement('div')
                card.className = 'product-card bg-white rounded-3xl overflow-hidden cursor-pointer border border-transparent hover:border-emerald-200'
                card.innerHTML = `
                    <div class="relative">
                        <img src="${product.image}" class="w-full aspect-[4/3] object-cover">
                        ${discount ? `<div class="absolute top-4 left-4 bg-emerald-500 text-white text-xs font-bold px-4 py-1 rounded-3xl">-${discount}%</div>` : ''}
                    </div>
                    <div class="p-7">
                        <h4 class="font-semibold text-xl leading-tight">${product.name}</h4>
                        <div class="flex items-center gap-x-2 mt-4">
                            <div class="text-3xl font-bold text-emerald-500">${(product.price / 1000000).toFixed(1)}tr</div>
                            ${product.oldPrice ? `<span class="text-sm line-through text-gray-400">${(product.oldPrice / 1000000).toFixed(1)}tr</span>` : ''}
                        </div>
                        <div class="flex text-emerald-400 mt-3">${'★'.repeat(product.rating)}</div>
                    </div>
                `
                card.onclick = () => showProductDetail(product.id)
                grid.appendChild(card)
            })
            
            if (filteredProducts.length === 0) {
                grid.innerHTML = `<p class="col-span-full text-center py-20 text-gray-400 text-2xl">Không tìm thấy sản phẩm</p>`
            }
        }
        
        // ==================== CHI TIẾT SẢN PHẨM ====================
        function showProductDetail(id) {
            currentProduct = products.find(p => p.id === id)
            if (!currentProduct) return
            
            document.getElementById('modal-product-name').innerText = currentProduct.name
            document.getElementById('modal-image').src = currentProduct.image
            document.getElementById('modal-price').innerHTML = `<span class="text-5xl">${(currentProduct.price / 1000000).toFixed(1)}tr ₫</span>`
            document.getElementById('modal-old-price').innerHTML = currentProduct.oldPrice ? `<span class="line-through">${(currentProduct.oldPrice / 1000000).toFixed(1)}tr ₫</span>` : ''
            
            // Thông số
            let specHTML = ''
            Object.entries(currentProduct.specs).forEach(([key, value]) => {
                specHTML += `<tr class="spec-row"><td class="py-6 font-medium">${key}</td><td class="py-6 text-right text-gray-600">${value}</td></tr>`
            })
            document.getElementById('spec-table').innerHTML = specHTML
            
            // Mô tả
            document.getElementById('tab-content-1').innerHTML = `<p class="leading-relaxed text-gray-700">${currentProduct.description}</p>`
            
            // Đánh giá
            let reviewHTML = currentProduct.reviews.length 
                ? currentProduct.reviews.map(r => `
                    <div class="flex gap-6">
                        <div class="text-4xl">👤</div>
                        <div class="flex-1">
                            <div class="flex justify-between"><span class="font-semibold">${r.name}</span><span class="text-emerald-400">${'★'.repeat(r.stars)}</span></div>
                            <p class="mt-2 text-gray-600">${r.comment}</p>
                        </div>
                    </div>`).join('')
                : `<p class="text-gray-400">Chưa có đánh giá nào. Hãy là người đầu tiên!</p>`
            document.getElementById('reviews-list').innerHTML = reviewHTML
            
            // Bảo hành
            document.getElementById('tab-content-3').innerHTML = `
                <p class="font-medium">Bảo hành chính hãng 24 tháng • Đổi trả miễn phí trong 30 ngày</p>
                <p class="mt-6">Số serial: <span class="font-mono text-emerald-600">IMX-${Math.floor(100000000 + Math.random() * 900000000)}</span></p>
            `
            const modal = document.getElementById('product-modal')
            modal.classList.remove('hidden')
            modal.classList.add('flex')
            showTab(0)
        }
        
        function hideProductModal() {
            const modal = document.getElementById('product-modal')
            modal.classList.add('hidden')
            modal.classList.remove('flex')
            currentProduct = null
        }
        
        function switchImage(el) {
            const main = document.getElementById('modal-image')
            main.style.opacity = '0'
            setTimeout(() => {
                main.src = el.querySelector('img').src
                main.style.opacity = '1'
            }, 200)
        }
        
        function showTab(n) {
            document.querySelectorAll('.tab-btn').forEach(btn => btn.classList.remove('active', 'border-b-4', 'border-emerald-500'))
            document.getElementById(`tab-${n}`).classList.add('active', 'border-b-4', 'border-emerald-500')
            
            document.querySelectorAll('.tab-content').forEach(content => content.classList.add('hidden'))
            document.getElementById(`tab-content-${n}`).classList.remove('hidden')
        }
        
        function submitReview() {
            const input = document.getElementById('review-input')
            if (!input.value.trim() || !currentProduct) return
            currentProduct.reviews.unshift({
                name: "Bạn",
                stars: 5,
                comment: input.value
            })
            showProductDetail(currentProduct.id)
            input.value = ''
            showToast('Cảm ơn bạn! Đánh giá đã được đăng.')
        }
        
        // ==================== GIỎ HÀNG & THANH TOÁN ====================
        function addToCart(id) {
            const product = products.find(p => p.id === id)
            if (!product) return
            const exist = cart.find(item => item.id === id)
            if (exist) exist.quantity = (exist.quantity || 1) + 1
            else cart.push({ ...product, quantity: 1 })
            updateCartCount()
            showToast(`${product.name} đã được thêm vào giỏ hàng`)
        }
        
        function addCurrentToCart() {
            if (currentProduct) {
                addToCart(currentProduct.id)
                hideProductModal()
            }
        }
        
        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + (item.quantity || 1), 0)
            document.getElementById('cart-count-badge').textContent = count
        }
        
        function showCart() {
            const modal = document.getElementById('cart-modal')
            const container = document.getElementById('cart-items-list')
            container.innerHTML = ''
            
            if (cart.length === 0) {
                container.innerHTML = `<div class="text-center py-16"><i class="fa-solid fa-cart-shopping text-8xl text-gray-200"></i><p class="mt-6 text-2xl text-gray-400">Giỏ hàng trống</p></div>`
                document.getElementById('cart-step-1').classList.remove('hidden')
                document.getElementById('cart-step-2').classList.add('hidden')
                modal.classList.remove('hidden')
                modal.classList.add('flex')
                return
            }
            
            let subtotal = 0
            cart.forEach((item, index) => {
                const total = item.price * (item.quantity || 1)
                subtotal += total
                container.innerHTML += `
                <div class="flex gap-8 border-b pb-8 last:border-none">
                    <img src="${item.image}" class="w-24 h-24 object-cover rounded-2xl">
                    <div class="flex-1">
                        <h4 class="font-semibold">${item.name}</h4>
                        <p class="text-emerald-500">${(item.price / 1000000).toFixed(1)}tr ₫ × ${item.quantity || 1}</p>
                        <div class="flex items-center gap-x-4 mt-6">
                            <button onclick="changeCartQuantity(${index}, -1)" class="w-10 h-10 border rounded-2xl flex items-center justify-center text-2xl">-</button>
                            <span class="font-bold text-xl">${item.quantity || 1}</span>
                            <button onclick="changeCartQuantity(${index}, 1)" class="w-10 h-10 border rounded-2xl flex items-center justify-center text-2xl">+</button>
                            <button onclick="removeFromCart(${index});" class="ml-auto text-red-500 flex items-center gap-x-2"><i class="fa-solid fa-trash"></i> Xóa</button>
                        </div>
                    </div>
                    <div class="text-right text-3xl font-bold">${(total / 1000000).toFixed(1)}tr</div>
                </div>`
            })
            
            document.getElementById('cart-step-1').classList.remove('hidden')
            document.getElementById('cart-step-2').classList.add('hidden')
            modal.classList.remove('hidden')
            modal.classList.add('flex')
        }
        
        function changeCartQuantity(index, delta) {
            if (!cart[index]) return
            cart[index].quantity = Math.max(1, (cart[index].quantity || 1) + delta)
            showCart()
            updateCartCount()
        }
        
        function removeFromCart(index) {
            cart.splice(index, 1)
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
            const orderId = `IMX-${new Date().getFullYear()}${(new Date().getMonth()+1).toString().padStart(2,'0')}${Math.floor(1000 + Math.random() * 9000)}`
            orders.unshift({
                id: orderId,
                product: cart.map(i => i.name).join(', '),
                status: "Đang xử lý",
                date: "16/04/2026",
                tracking: `GHN-${Math.floor(100000 + Math.random() * 900000)}`
            })
            cart = []
            updateCartCount()
            
            setTimeout(() => {
                alert(`✅ Đơn hàng ${orderId} đã được xác nhận thành công!\n\nCảm ơn bạn đã mua sắm tại IMEX.\nBạn có thể theo dõi trạng thái trong phần Đơn hàng của tôi.`)
            }, 700)
        }
        
        // ==================== SO SÁNH ====================
        function openCompareModal() {
            if (compareList.length < 2) {
                showToast('Vui lòng chọn ít nhất 2 sản phẩm để so sánh')
                return
            }
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
            const keys = new Set()
            compareList.forEach(p => Object.keys(p.specs).forEach(k => keys.add(k)))
            
            let thead = `<th class="py-6 font-medium text-lg">Thông số</th>`
            compareList.forEach(p => {
                thead += `<th class="py-6 text-center font-semibold">${p.name}</th>`
            })
            document.querySelector('#compare-modal thead tr').innerHTML = thead
            
            let tbodyHTML = ''
            Array.from(keys).forEach(key => {
                tbodyHTML += `<tr><td class="py-6 font-medium">${key}</td>`
                compareList.forEach(p => {
                    tbodyHTML += `<td class="py-6 text-center">${p.specs[key] || '—'}</td>`
                })
                tbodyHTML += `</tr>`
            })
            document.getElementById('compare-table-body').innerHTML = tbodyHTML
        }
        
        function addToCompareFromDetail() {
            if (!currentProduct || compareList.length >= 4) {
                if (compareList.length >= 4) showToast('Chỉ được so sánh tối đa 4 sản phẩm')
                return
            }
            if (!compareList.find(p => p.id === currentProduct.id)) {
                compareList.push(currentProduct)
                showToast('Đã thêm vào danh sách so sánh')
            }
            hideProductModal()
        }
        
        // ==================== CỘNG ĐỒNG ====================
        function renderCommunity() {
            const container = document.getElementById('community-feed')
            container.innerHTML = communityPosts.map(post => `
                <div class="border border-emerald-200 hover:border-emerald-400 rounded-3xl p-8">
                    <div class="flex items-center gap-x-4">
                        <div class="w-12 h-12 bg-emerald-100 text-emerald-600 rounded-2xl flex items-center justify-center text-3xl">👤</div>
                        <div>
                            <p class="font-semibold">${post.user}</p>
                            <p class="text-xs text-gray-400">${post.time}</p>
                        </div>
                    </div>
                    <p class="mt-8 text-lg leading-relaxed">${post.content}</p>
                    <div class="mt-10 flex justify-between items-center text-emerald-500">
                        <i class="fa-solid fa-heart text-2xl"></i>
                        <span class="font-medium">${post.likes} lượt thích</span>
                    </div>
                </div>
            `).join('')
        }
        
        function postCommunity() {
            const input = document.getElementById('community-input')
            if (!input.value) return
            communityPosts.unshift({
                user: "Bạn",
                time: "Vừa xong",
                content: input.value,
                likes: 0
            })
            input.value = ''
            renderCommunity()
            showToast('Bài viết đã được đăng thành công!')
        }
        
        // ==================== BẢO HÀNH ====================
        function checkWarranty() {
            const serial = document.getElementById('warranty-serial').value.trim()
            if (!serial) {
                showToast('Vui lòng nhập số serial / IMEI')
                return
            }
            
            const examplesHTML = `
                <div class="flex justify-between items-center border-b pb-6">
                    <div>
                        <p class="font-semibold">${currentProduct ? currentProduct.name : 'iPhone 16 Pro Max'}</p>
                        <p class="text-xs text-gray-500">Serial: ${serial}</p>
                    </div>
                    <div class="text-right">
                        <span class="px-8 py-3 bg-emerald-100 text-emerald-600 font-medium rounded-3xl">Còn 22 tháng 14 ngày</span>
                    </div>
                </div>
                <p class="text-center text-emerald-600 mt-6">Bảo hành điện tử đã được kích hoạt • Hỗ trợ 24/7</p>
            `
            document.getElementById('warranty-examples').innerHTML = examplesHTML
            showToast('✅ Thông tin bảo hành đã được tra cứu thành công!')
        }
        
        // ==================== ĐƠN HÀNG ====================
        function showOrders() {
            hideUserMenu()
            const container = document.getElementById('orders-list')
            container.innerHTML = orders.map(order => `
                <div class="flex justify-between bg-white border border-emerald-100 rounded-3xl p-8 items-center">
                    <div>
                        <p class="font-mono font-semibold text-xl">${order.id}</p>
                        <p class="text-gray-600">${order.product}</p>
                        <p class="text-xs text-gray-400">${order.date}</p>
                    </div>
                    <div class="text-right">
                        <span class="inline-block px-8 py-3 text-sm rounded-3xl ${order.status.includes('Đang') ? 'bg-blue-100 text-blue-700' : 'bg-emerald-100 text-emerald-700'}">${order.status}</span>
                        <p onclick="trackOrder('${order.tracking}')" class="mt-4 text-emerald-500 cursor-pointer flex items-center justify-end gap-x-2">Theo dõi vận chuyển <i class="fa-solid fa-truck"></i></p>
                    </div>
                </div>
            `).join('') || `<div class="text-center py-16 text-gray-400 text-2xl">Bạn chưa có đơn hàng nào</div>`
            
            const modal = document.getElementById('orders-modal')
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
            showToast(`📦 Đang theo dõi đơn hàng: ${code} • Dự kiến giao hàng ngày mai lúc 14:30`)
        }
        
        // ==================== FILTER ====================
        function filterCategory(cat) {
            const filtered = products.filter(p => p.category === cat)
            renderProducts(filtered)
            navigateToSection('shop')
        }
        
        // ==================== UTILITIES ====================
        function toggleSearch() {
            const input = document.getElementById('search-input')
            input.classList.toggle('hidden')
            if (!input.classList.contains('hidden')) input.focus()
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
        
        function navigateToSection(section) {
            document.getElementById(section).scrollIntoView({ behavior: 'smooth' })
        }
        
        function showToast(message) {
            const toast = document.createElement('div')
            toast.style.cssText = `position:fixed; bottom:30px; right:30px; background:${PRIMARY_COLOR}; color:#fff; padding:20px 28px; border-radius:9999px; box-shadow:25px 25px 30px -10px rgb(16 185 129); z-index:99999; display:flex; align-items:center; gap:14px;`
            toast.innerHTML = `<i class="fa-solid fa-circle-check"></i> ${message}`
            document.body.appendChild(toast)
            
            setTimeout(() => {
                toast.style.transform = 'translateY(100px)'
                toast.style.opacity = '0'
                setTimeout(() => toast.remove(), 500)
            }, 3200)
        }
        
        // ==================== KHỞI ĐỘNG ====================
        window.onload = function () {
            renderProducts(products)
            renderCommunity()
            updateCartCount()
            
            console.log('%c✅ IMEX Mobile - Đã chuẩn hóa giao diện & chức năng chuyên nghiệp với màu xanh lá - trắng', 'background:#10b981;color:white;padding:2px 8px;border-radius:4px;font-weight:700')
        }
    </script>
</body>
</html>
