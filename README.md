<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động">
    <title>IMEX - Mua sắm Điện thoại, Laptop, Tai nghe, Máy chơi game</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;family=Roboto:wght@400;500&amp;display=swap');
        
        :root {
            --primary-blue: #007BFF;
        }
        
        * {
            font-family: 'Inter', system_ui, sans-serif;
        }
        
        .header {
            background: linear-gradient(90deg, #007BFF, #00A2FF);
            box-shadow: 0 4px 12px rgba(0, 123, 255, 0.3);
        }
        
        .shopee-like-search {
            transition: all 0.3s ease;
        }
        
        .shopee-like-search:focus {
            box-shadow: 0 0 0 4px rgba(0, 123, 255, 0.3);
        }
        
        .product-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 20px 25px -5px rgb(0 123 255 / 0.1), 0 8px 10px -6px rgb(0 123 255 / 0.1);
        }
        
        .banner-slide {
            animation: slideBanner 15s infinite linear;
        }
        
        @keyframes slideBanner {
            0% { transform: translateX(0); }
            33% { transform: translateX(-100%); }
            66% { transform: translateX(-200%); }
            100% { transform: translateX(0); }
        }
        
        .cart-count {
            animation: ping 2s cubic-bezier(0, 0, 0.2, 1) infinite;
        }
    </style>
</head>
<body class="bg-gray-50">
    <!-- HEADER - Giống Shopee -->
    <header class="header sticky top-0 z-50">
        <div class="max-w-7xl mx-auto px-4">
            <div class="flex items-center justify-between py-3">
                
                <!-- Logo -->
                <div class="flex items-center gap-2">
                    <div class="w-10 h-10 bg-white rounded-2xl flex items-center justify-center text-[#007BFF] text-3xl font-bold shadow-inner">
                        📱
                    </div>
                    <h1 class="text-4xl font-bold text-white tracking-tighter">IMEX</h1>
                    <span class="text-white/90 text-sm font-medium mt-1">Thiết bị di động</span>
                </div>

                <!-- Search Bar - Giống Shopee -->
                <div class="flex-1 max-w-2xl mx-8">
                    <div class="relative">
                        <input 
                            id="search-input"
                            type="text" 
                            placeholder="Tìm kiếm điện thoại, laptop, tai nghe, máy chơi game..."
                            class="shopee-like-search w-full bg-white text-gray-800 placeholder-gray-400 rounded-3xl py-3 px-6 pl-12 text-lg focus:outline-none border border-transparent">
                        <i onclick="performSearch()" class="fa-solid fa-magnifying-glass absolute left-5 top-1/2 -translate-y-1/2 text-[#007BFF] text-xl cursor-pointer"></i>
                        
                        <!-- Gợi ý nhanh -->
                        <div class="absolute right-4 top-1/2 -translate-y-1/2 flex gap-2 text-xs">
                            <div onclick="quickSearch('iPhone')" class="bg-white/90 text-[#007BFF] px-3 py-1 rounded-3xl cursor-pointer hover:bg-white">iPhone 16</div>
                            <div onclick="quickSearch('Galaxy')" class="bg-white/90 text-[#007BFF] px-3 py-1 rounded-3xl cursor-pointer hover:bg-white">Galaxy S25</div>
                            <div onclick="quickSearch('AirPods')" class="bg-white/90 text-[#007BFF] px-3 py-1 rounded-3xl cursor-pointer hover:bg-white">AirPods Pro</div>
                        </div>
                    </div>
                </div>

                <!-- Right side icons -->
                <div class="flex items-center gap-6 text-white">
                    <!-- Tài khoản -->
                    <div onclick="toggleAccountMenu()" class="flex items-center gap-2 cursor-pointer hover:bg-white/20 px-4 py-2 rounded-3xl">
                        <i class="fa-solid fa-user-circle text-3xl"></i>
                        <div class="hidden md:block">
                            <p class="text-sm font-medium">Xin chào, Ánh</p>
                            <p class="text-xs text-white/80">Tài khoản</p>
                        </div>
                    </div>

                    <!-- Giỏ hàng -->
                    <div onclick="showCart()" class="relative cursor-pointer hover:bg-white/20 px-4 py-2 rounded-3xl flex items-center gap-2">
                        <i class="fa-solid fa-shopping-cart text-3xl"></i>
                        <span id="cart-count" class="cart-count absolute -top-1 -right-1 bg-red-500 text-white text-xs font-bold rounded-full h-5 w-5 flex items-center justify-center">0</span>
                        <span class="hidden md:block text-sm font-medium">Giỏ hàng</span>
                    </div>

                    <!-- Thông báo -->
                    <div class="relative cursor-pointer hover:bg-white/20 p-3 rounded-3xl">
                        <i class="fa-solid fa-bell text-3xl"></i>
                        <span class="absolute top-2 right-2 bg-red-500 text-[10px] font-bold rounded-full h-4 w-4 flex items-center justify-center">3</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Danh mục ngang (giống Shopee) -->
        <div class="bg-white border-t border-b text-[#007BFF] py-2 shadow-sm">
            <div class="max-w-7xl mx-auto px-4">
                <div class="flex items-center gap-8 text-sm font-medium overflow-x-auto whitespace-nowrap pb-1 scrollbar-hide">
                    <a onclick="filterByCategory('all')" class="flex items-center gap-1 hover:text-blue-600 transition-colors cursor-pointer">
                        <i class="fa-solid fa-house"></i>
                        <span>Trang chủ</span>
                    </a>
                    <a onclick="filterByCategory('Điện thoại')" class="flex items-center gap-2 hover:text-blue-600 transition-colors cursor-pointer">
                        <span class="text-xl">📱</span>
                        <span>Điện thoại</span>
                    </a>
                    <a onclick="filterByCategory('Máy tính')" class="flex items-center gap-2 hover:text-blue-600 transition-colors cursor-pointer">
                        <span class="text-xl">💻</span>
                        <span>Laptop & Máy tính</span>
                    </a>
                    <a onclick="filterByCategory('Tai nghe')" class="flex items-center gap-2 hover:text-blue-600 transition-colors cursor-pointer">
                        <span class="text-xl">🎧</span>
                        <span>Tai nghe</span>
                    </a>
                    <a onclick="filterByCategory('Game')" class="flex items-center gap-2 hover:text-blue-600 transition-colors cursor-pointer">
                        <span class="text-xl">🎮</span>
                        <span>Máy chơi game</span>
                    </a>
                    <a onclick="filterByCategory('Phụ kiện')" class="flex items-center gap-2 hover:text-blue-600 transition-colors cursor-pointer">
                        <span class="text-xl">🔌</span>
                        <span>Phụ kiện di động</span>
                    </a>
                    <div class="ml-auto flex items-center gap-2 text-xs bg-blue-100 text-[#007BFF] px-4 py-1 rounded-3xl">
                        <i class="fa-solid fa-truck-fast"></i>
                        <span>FREE SHIP toàn quốc từ 500k</span>
                    </div>
                    <div class="text-xs bg-amber-100 text-amber-600 px-4 py-1 rounded-3xl flex items-center gap-1">
                        <i class="fa-solid fa-fire"></i>
                        <span>Flash Sale hôm nay</span>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- HERO BANNER - Carousel giống Shopee -->
    <div class="max-w-7xl mx-auto px-4 mt-4 relative overflow-hidden rounded-3xl shadow-xl">
        <div id="banner-container" class="flex w-[300%] banner-slide">
            <!-- Slide 1 -->
            <div class="w-1/3 bg-gradient-to-r from-[#007BFF] to-[#00A2FF] flex items-center px-12 py-14 text-white">
                <div class="max-w-md">
                    <div class="uppercase tracking-widest text-sm font-medium mb-3">MỚI RA MẮT</div>
                    <h2 class="text-6xl font-bold leading-none mb-4">iPhone 16 Pro<br>Max chính hãng</h2>
                    <p class="text-xl mb-8">Giá chỉ từ 28.990.000đ • Bảo hành 12 tháng</p>
                    <button onclick="buyNow(1)" 
                            class="bg-white text-[#007BFF] font-semibold px-10 py-4 rounded-3xl text-lg flex items-center gap-3 hover:scale-105 transition">
                        Mua ngay <i class="fa-solid fa-arrow-right"></i>
                    </button>
                </div>
                <img src="https://picsum.photos/id/1015/620/420" alt="iPhone 16 Pro" 
                     class="absolute right-12 bottom-0 h-96 object-contain drop-shadow-2xl">
            </div>
            
            <!-- Slide 2 -->
            <div class="w-1/3 bg-gradient-to-r from-purple-600 to-[#007BFF] flex items-center px-12 py-14 text-white">
                <div class="max-w-md">
                    <div class="uppercase tracking-widest text-sm font-medium mb-3">GIẢM SỐC</div>
                    <h2 class="text-6xl font-bold leading-none mb-4">MacBook Air M3<br>Chỉ còn 32.990.000đ</h2>
                    <p class="text-xl mb-8">Tiết kiệm ngay 5 triệu • Hàng chính hãng Apple</p>
                    <button onclick="buyNow(3)" 
                            class="bg-white text-[#007BFF] font-semibold px-10 py-4 rounded-3xl text-lg flex items-center gap-3 hover:scale-105 transition">
                        Mua ngay <i class="fa-solid fa-arrow-right"></i>
                    </button>
                </div>
                <img src="https://picsum.photos/id/201/620/420" alt="MacBook Air" 
                     class="absolute right-12 bottom-0 h-96 object-contain drop-shadow-2xl rotate-[-8deg]">
            </div>
            
            <!-- Slide 3 -->
            <div class="w-1/3 bg-gradient-to-r from-[#007BFF] to-cyan-500 flex items-center px-12 py-14 text-white">
                <div class="max-w-md">
                    <div class="uppercase tracking-widest text-sm font-medium mb-3">BEST SELLER</div>
                    <h2 class="text-6xl font-bold leading-none mb-4">AirPods Pro 2<br>& Sony WH-1000XM5</h2>
                    <p class="text-xl mb-8">Giảm đến 40% • Âm thanh đỉnh cao</p>
                    <button onclick="buyNow(4)" 
                            class="bg-white text-[#007BFF] font-semibold px-10 py-4 rounded-3xl text-lg flex items-center gap-3 hover:scale-105 transition">
                        Mua ngay <i class="fa-solid fa-arrow-right"></i>
                    </button>
                </div>
                <img src="https://picsum.photos/id/1005/620/420" alt="Tai nghe" 
                     class="absolute right-12 bottom-0 h-96 object-contain drop-shadow-2xl">
            </div>
        </div>
        
        <!-- Dots -->
        <div class="absolute bottom-6 left-1/2 flex gap-2 z-10">
            <div onclick="changeBanner(0)" class="w-3 h-3 bg-white rounded-full cursor-pointer"></div>
            <div onclick="changeBanner(1)" class="w-3 h-3 bg-white/50 rounded-full cursor-pointer"></div>
            <div onclick="changeBanner(2)" class="w-3 h-3 bg-white/50 rounded-full cursor-pointer"></div>
        </div>
    </div>

    <!-- FLASH SALE -->
    <div class="max-w-7xl mx-auto px-4 mt-10">
        <div class="flex items-center justify-between mb-6">
            <div class="flex items-center gap-3">
                <i class="fa-solid fa-fire text-3xl text-red-500"></i>
                <h2 class="text-3xl font-bold text-gray-900">🔥 FLASH SALE HÔM NAY</h2>
                <div class="bg-red-500 text-white text-sm font-medium px-4 py-1 rounded-3xl flex items-center">
                    <span id="countdown" class="font-mono">03:15:42</span>
                </div>
            </div>
            <a onclick="viewAll()" class="text-[#007BFF] font-medium flex items-center gap-1 hover:underline">
                Xem tất cả <i class="fa-solid fa-chevron-right text-xs"></i>
            </a>
        </div>
        
        <!-- Product Grid -->
        <div id="product-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-6 gap-6">
            <!-- Sẽ được render bằng JavaScript -->
        </div>
    </div>

    <!-- DANH MỤC SẢN PHẨM -->
    <div class="max-w-7xl mx-auto px-4 mt-16">
        <h2 class="text-3xl font-bold mb-8 flex items-center gap-3">
            <span>📂</span> Danh mục chuyên biệt
        </h2>
        <div class="grid grid-cols-3 md:grid-cols-6 gap-4">
            <div onclick="filterByCategory('Điện thoại')" class="bg-white rounded-3xl p-6 text-center shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all cursor-pointer border border-transparent hover:border-[#007BFF]">
                <div class="text-6xl mb-4">📱</div>
                <h3 class="font-semibold text-xl">Điện thoại</h3>
                <p class="text-sm text-gray-500 mt-1">iPhone, Samsung, Xiaomi...</p>
            </div>
            <div onclick="filterByCategory('Máy tính')" class="bg-white rounded-3xl p-6 text-center shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all cursor-pointer border border-transparent hover:border-[#007BFF]">
                <div class="text-6xl mb-4">💻</div>
                <h3 class="font-semibold text-xl">Laptop &amp; Máy tính</h3>
                <p class="text-sm text-gray-500 mt-1">MacBook, Dell, Asus...</p>
            </div>
            <div onclick="filterByCategory('Tai nghe')" class="bg-white rounded-3xl p-6 text-center shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all cursor-pointer border border-transparent hover:border-[#007BFF]">
                <div class="text-6xl mb-4">🎧</div>
                <h3 class="font-semibold text-xl">Tai nghe</h3>
                <p class="text-sm text-gray-500 mt-1">AirPods, Sony, JBL...</p>
            </div>
            <div onclick="filterByCategory('Game')" class="bg-white rounded-3xl p-6 text-center shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all cursor-pointer border border-transparent hover:border-[#007BFF]">
                <div class="text-6xl mb-4">🎮</div>
                <h3 class="font-semibold text-xl">Máy chơi game</h3>
                <p class="text-sm text-gray-500 mt-1">Nintendo, PS5, Xbox...</p>
            </div>
            <div onclick="filterByCategory('Phụ kiện')" class="bg-white rounded-3xl p-6 text-center shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all cursor-pointer border border-transparent hover:border-[#007BFF]">
                <div class="text-6xl mb-4">🔋</div>
                <h3 class="font-semibold text-xl">Phụ kiện</h3>
                <p class="text-sm text-gray-500 mt-1">Sạc, ốp lưng, cáp...</p>
            </div>
            <div onclick="filterByCategory('all')" class="bg-gradient-to-br from-[#007BFF] to-cyan-500 text-white rounded-3xl p-6 text-center shadow-sm hover:shadow-xl hover:-translate-y-1 transition-all cursor-pointer">
                <div class="text-6xl mb-4">🌐</div>
                <h3 class="font-semibold text-xl">Tất cả thiết bị</h3>
                <p class="text-sm mt-1 opacity-90">Hơn 500+ sản phẩm</p>
            </div>
        </div>
    </div>

    <!-- FOOTER -->
    <footer class="bg-gray-900 text-white mt-20">
        <div class="max-w-7xl mx-auto px-4 py-12 grid grid-cols-2 md:grid-cols-5 gap-8">
            <div>
                <div class="flex items-center gap-2 mb-6">
                    <div class="w-8 h-8 bg-white rounded-2xl flex items-center justify-center text-[#007BFF] text-3xl">📱</div>
                    <h2 class="text-3xl font-bold">IMEX</h2>
                </div>
                <p class="text-gray-400 text-sm">Nền tảng thương mại điện tử chuyên biệt cho thiết bị di động.<br>Chỉ bán sản phẩm công nghệ chính hãng.</p>
                <div class="flex gap-4 mt-8">
                    <i class="fa-brands fa-facebook text-2xl cursor-pointer hover:text-[#007BFF]"></i>
                    <i class="fa-brands fa-tiktok text-2xl cursor-pointer hover:text-[#007BFF]"></i>
                    <i class="fa-brands fa-youtube text-2xl cursor-pointer hover:text-[#007BFF]"></i>
                </div>
            </div>
            <div>
                <h4 class="font-semibold mb-4">Về IMEX</h4>
                <ul class="space-y-2 text-sm text-gray-400">
                    <li>Giới thiệu</li>
                    <li>Chính sách bảo hành</li>
                    <li>Quy chế hoạt động</li>
                    <li>Blog công nghệ</li>
                </ul>
            </div>
            <div>
                <h4 class="font-semibold mb-4">Hỗ trợ khách hàng</h4>
                <ul class="space-y-2 text-sm text-gray-400">
                    <li>Hotline: 1900 6868</li>
                    <li>Chat trực tuyến 24/7</li>
                    <li>Trung tâm hỗ trợ</li>
                    <li>Gửi yêu cầu bảo hành</li>
                </ul>
            </div>
            <div>
                <h4 class="font-semibold mb-4">Thanh toán</h4>
                <div class="flex gap-4 text-4xl">
                    <i class="fa-brands fa-cc-visa"></i>
                    <i class="fa-brands fa-cc-mastercard"></i>
                    <i class="fa-brands fa-cc-paypal"></i>
                    <i class="fa-solid fa-money-bill-wave"></i>
                </div>
                <p class="text-xs text-gray-400 mt-6">Miễn phí vận chuyển cho đơn từ 500.000đ</p>
            </div>
            <div>
                <h4 class="font-semibold mb-4">Tải app IMEX</h4>
                <div class="flex gap-3">
                    <div class="bg-gray-800 text-xs px-6 py-3 rounded-2xl flex-1 text-center cursor-pointer">📱 App Store</div>
                    <div class="bg-gray-800 text-xs px-6 py-3 rounded-2xl flex-1 text-center cursor-pointer">▶️ Google Play</div>
                </div>
                <p class="text-xs text-gray-400 mt-8">© 2026 IMEX Vietnam. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <!-- CART MODAL -->
    <div onclick="if(event.target.id === 'cart-modal') hideCart()" id="cart-modal" class="hidden fixed inset-0 bg-black/60 z-[100] flex items-end md:items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" class="bg-white w-full max-w-lg md:rounded-3xl md:max-h-[90vh] overflow-hidden">
            <div class="px-6 py-4 border-b flex items-center justify-between">
                <h3 class="text-2xl font-semibold">Giỏ hàng của bạn (<span id="modal-cart-count">0</span>)</h3>
                <i onclick="hideCart()" class="fa-solid fa-xmark text-3xl cursor-pointer"></i>
            </div>
            
            <div id="cart-items" class="max-h-[420px] overflow-auto px-6 py-2">
                <!-- JS render items -->
            </div>
            
            <div class="px-6 py-6 border-t">
                <div class="flex justify-between text-lg mb-6">
                    <span class="font-medium">Tổng tiền:</span>
                    <span id="cart-total" class="font-bold text-2xl text-[#007BFF]">0 ₫</span>
                </div>
                <button onclick="checkout()" 
                        class="w-full bg-[#007BFF] text-white font-semibold text-xl py-5 rounded-3xl">
                    Thanh toán ngay
                </button>
                <p class="text-center text-xs text-gray-400 mt-4">Hoặc thanh toán khi nhận hàng • Bảo mật 100%</p>
            </div>
        </div>
    </div>

    <!-- ACCOUNT MENU (mini) -->
    <div onclick="if(event.target.id === 'account-menu') toggleAccountMenu()" id="account-menu" class="hidden fixed top-20 right-8 bg-white shadow-2xl rounded-3xl py-4 px-2 w-72 z-[110]">
        <div class="px-6 py-4 border-b">
            <div class="flex items-center gap-4">
                <i class="fa-solid fa-user-circle text-6xl text-[#007BFF]"></i>
                <div>
                    <p class="font-semibold text-lg">Ánh Nguyễn</p>
                    <p class="text-sm text-gray-500">anhnguyen.imex@gmail.com</p>
                </div>
            </div>
        </div>
        <div class="py-2">
            <a href="#" class="flex items-center gap-4 px-6 py-4 hover:bg-gray-100 rounded-2xl"><i class="fa-solid fa-heart w-6"></i> Sản phẩm yêu thích</a>
            <a href="#" class="flex items-center gap-4 px-6 py-4 hover:bg-gray-100 rounded-2xl"><i class="fa-solid fa-history w-6"></i> Đơn hàng đã mua</a>
            <a href="#" class="flex items-center gap-4 px-6 py-4 hover:bg-gray-100 rounded-2xl"><i class="fa-solid fa-ticket w-6"></i> Voucher của tôi</a>
            <a href="#" class="flex items-center gap-4 px-6 py-4 hover:bg-gray-100 rounded-2xl"><i class="fa-solid fa-gear w-6"></i> Cài đặt tài khoản</a>
        </div>
        <div class="px-6 pt-4 border-t text-red-500 cursor-pointer text-center font-medium" onclick="logout()">Đăng xuất</div>
    </div>

    <script>
        // Tailwind config
        function initializeTailwind() {
            return {
                config(userConfig = {}) {
                    return {
                        configUser: userConfig,
                        theme: {
                            extend: {
                                colors: {
                                    primary: '#007BFF',
                                }
                            }
                        }
                    }
                },
                theme: {
                    extend: {},
                },
            }
        }
        const config = initializeTailwind().config
        document.documentElement.setAttribute('data-tailwind-config', JSON.stringify(config))

        // Danh sách sản phẩm (chỉ bán thiết bị di động)
        let products = [
            {
                id: 1,
                name: "iPhone 16 Pro Max 256GB",
                category: "Điện thoại",
                price: 28990000,
                oldPrice: 32990000,
                rating: 4.9,
                sold: 1243,
                image: "https://picsum.photos/id/1015/300/300"
            },
            {
                id: 2,
                name: "Samsung Galaxy S25 Ultra",
                category: "Điện thoại",
                price: 26990000,
                oldPrice: 29990000,
                rating: 4.8,
                sold: 987,
                image: "https://picsum.photos/id/160/300/300"
            },
            {
                id: 3,
                name: "MacBook Air M3 13 inch",
                category: "Máy tính",
                price: 32990000,
                oldPrice: 37990000,
                rating: 5.0,
                sold: 654,
                image: "https://picsum.photos/id/201/300/300"
            },
            {
                id: 4,
                name: "AirPods Pro 2 (2024)",
                category: "Tai nghe",
                price: 5990000,
                oldPrice: 7990000,
                rating: 4.9,
                sold: 3421,
                image: "https://picsum.photos/id/1005/300/300"
            },
            {
                id: 5,
                name: "Sony WH-1000XM5",
                category: "Tai nghe",
                price: 7990000,
                oldPrice: 9990000,
                rating: 4.7,
                sold: 876,
                image: "https://picsum.photos/id/133/300/300"
            },
            {
                id: 6,
                name: "Nintendo Switch OLED",
                category: "Game",
                price: 8990000,
                oldPrice: 10990000,
                rating: 4.8,
                sold: 1543,
                image: "https://picsum.photos/id/251/300/300"
            },
            {
                id: 7,
                name: "Dell XPS 14 2025",
                category: "Máy tính",
                price: 45990000,
                oldPrice: 49990000,
                rating: 4.6,
                sold: 312,
                image: "https://picsum.photos/id/870/300/300"
            },
            {
                id: 8,
                name: "PS5 Slim + 2 tay cầm",
                category: "Game",
                price: 13990000,
                oldPrice: 15990000,
                rating: 5.0,
                sold: 543,
                image: "https://picsum.photos/id/1009/300/300"
            },
            {
                id: 9,
                name: "Xiaomi 14T Pro",
                category: "Điện thoại",
                price: 13990000,
                oldPrice: 15990000,
                rating: 4.5,
                sold: 2314,
                image: "https://picsum.photos/id/1016/300/300"
            },
            {
                id: 10,
                name: "JBL Flip 6 Bluetooth",
                category: "Tai nghe",
                price: 2490000,
                oldPrice: 3290000,
                rating: 4.8,
                sold: 1876,
                image: "https://picsum.photos/id/133/300/300"
            }
        ]

        let cart = []

        // Format giá VND
        function formatPrice(price) {
            return price.toLocaleString('vi-VN') + ' ₫'
        }

        // Render sản phẩm
        function renderProducts(filteredProducts) {
            const container = document.getElementById('product-grid')
            container.innerHTML = ''
            
            filteredProducts.forEach(product => {
                const discount = product.oldPrice ? Math.round(((product.oldPrice - product.price) / product.oldPrice) * 100) : 0
                
                const cardHTML = `
                <div class="product-card bg-white rounded-3xl overflow-hidden border border-gray-100">
                    <div class="relative">
                        <img src="${product.image}" alt="${product.name}" class="w-full aspect-square object-cover">
                        ${discount > 0 ? `<div class="absolute top-3 left-3 bg-red-500 text-white text-xs font-bold px-3 py-1 rounded-3xl">-${discount}%</div>` : ''}
                    </div>
                    <div class="p-4">
                        <div class="text-xs font-medium text-[#007BFF]">${product.category}</div>
                        <h4 class="font-semibold text-base leading-tight mt-1 line-clamp-2 h-12">${product.name}</h4>
                        
                        <div class="flex items-center gap-1 mt-3">
                            ${Array(5).fill().map((_, i) => `<i class="fa-solid fa-star ${i < Math.floor(product.rating) ? 'text-yellow-400' : 'text-gray-300'}"></i>`).join('')}
                            <span class="text-xs text-gray-500 ml-1">(${product.rating})</span>
                        </div>
                        
                        <div class="mt-3 flex items-baseline gap-2">
                            <span class="text-xl font-bold text-[#007BFF]">${formatPrice(product.price)}</span>
                            ${product.oldPrice ? `<span class="line-through text-xs text-gray-400">${formatPrice(product.oldPrice)}</span>` : ''}
                        </div>
                        
                        <div class="text-xs text-gray-400 mt-1">${product.sold} đã bán</div>
                        
                        <button onclick="addToCart(${product.id}); event.stopImmediatePropagation()" 
                                class="mt-4 w-full bg-[#007BFF] hover:bg-blue-700 transition text-white py-3 rounded-3xl text-sm font-medium flex items-center justify-center gap-2">
                            <i class="fa-solid fa-cart-plus"></i>
                            THÊM VÀO GIỎ
                        </button>
                    </div>
                </div>`
                
                container.innerHTML += cardHTML
            })
            
            if (filteredProducts.length === 0) {
                container.innerHTML = `<div class="col-span-full text-center py-12 text-gray-400">Không tìm thấy sản phẩm nào 😢</div>`
            }
        }

        // Thêm vào giỏ
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
            
            // Toast thông báo
            const toast = document.createElement('div')
            toast.style.cssText = 'position:fixed; bottom:20px; right:20px; background:#007BFF; color:white; padding:16px 24px; border-radius:9999px; box-shadow:0 10px 15px -3px rgb(0 123 255); display:flex; align-items:center; gap:12px;'
            toast.innerHTML = `✅ <span>${product.name} đã được thêm vào giỏ!</span>`
            document.body.appendChild(toast)
            
            setTimeout(() => toast.remove(), 2800)
        }

        // Cập nhật số lượng giỏ
        function updateCartCount() {
            const countEl = document.getElementById('cart-count')
            const totalItems = cart.reduce((sum, item) => sum + (item.quantity || 1), 0)
            countEl.textContent = totalItems
        }

        // Hiển thị giỏ hàng
        function showCart() {
            const modal = document.getElementById('cart-modal')
            const itemsContainer = document.getElementById('cart-items')
            const totalEl = document.getElementById('cart-total')
            const countEl = document.getElementById('modal-cart-count')
            
            itemsContainer.innerHTML = ''
            
            if (cart.length === 0) {
                itemsContainer.innerHTML = `
                <div class="py-12 text-center">
                    <div class="text-7xl mb-6">🛒</div>
                    <p class="text-xl font-medium text-gray-300">Giỏ hàng trống</p>
                    <p class="text-sm text-gray-400 mt-2">Hãy thêm một số thiết bị di động yêu thích nhé!</p>
                </div>`
                totalEl.textContent = '0 ₫'
                countEl.textContent = '0'
                modal.classList.remove('hidden')
                return
            }
            
            let total = 0
            cart.forEach((item, index) => {
                const itemTotal = item.price * (item.quantity || 1)
                total += itemTotal
                
                const html = `
                <div class="flex gap-4 py-4 border-b last:border-0">
                    <img src="${item.image}" class="w-20 h-20 object-cover rounded-2xl">
                    <div class="flex-1">
                        <div class="flex justify-between">
                            <p class="font-medium">${item.name}</p>
                            <i onclick="removeFromCart(${index});" class="fa-solid fa-trash text-red-400 cursor-pointer"></i>
                        </div>
                        <p class="text-xs text-gray-500">${item.category}</p>
                        <div class="flex justify-between items-end mt-4">
                            <div>
                                <span class="font-bold">${formatPrice(item.price)}</span>
                                ${item.quantity > 1 ? `<span class="text-xs ml-2">x${item.quantity}</span>` : ''}
                            </div>
                            <span class="text-lg font-semibold text-[#007BFF]">${formatPrice(itemTotal)}</span>
                        </div>
                    </div>
                </div>`
                itemsContainer.innerHTML += html
            })
            
            totalEl.textContent = formatPrice(total)
            countEl.textContent = cart.length
            modal.classList.remove('hidden')
        }

        function hideCart() {
            document.getElementById('cart-modal').classList.add('hidden')
        }

        function removeFromCart(index) {
            cart.splice(index, 1)
            showCart()
            updateCartCount()
        }

        // Thanh toán giả lập
        function checkout() {
            if (cart.length === 0) return
            hideCart()
            
            setTimeout(() => {
                alert('🎉 Cảm ơn bạn đã mua hàng tại IMEX!\nĐơn hàng của bạn đã được xác nhận.\nMã đơn: IMX-' + Math.floor(100000 + Math.random() * 900000))
                cart = []
                updateCartCount()
            }, 600)
        }

        // Lọc theo danh mục
        function filterByCategory(category) {
            let filtered = products
            
            if (category !== 'all') {
                filtered = products.filter(p => p.category === category)
            }
            
            renderProducts(filtered)
            
            // Scroll lên top grid
            document.getElementById('product-grid').scrollIntoView({ behavior: 'smooth' })
        }

        // Tìm kiếm
        function performSearch() {
            const keyword = document.getElementById('search-input').value.toLowerCase().trim()
            if (!keyword) {
                renderProducts(products)
                return
            }
            
            const filtered = products.filter(p => 
                p.name.toLowerCase().includes(keyword) || 
                p.category.toLowerCase().includes(keyword)
            )
            renderProducts(filtered)
        }

        function quickSearch(term) {
            document.getElementById('search-input').value = term
            performSearch()
        }

        // Đếm ngược flash sale
        function startCountdown() {
            let time = 3 * 3600 + 15 * 60 + 42 // 3h15p42s
            const countdownEl = document.getElementById('countdown')
            
            setInterval(() => {
                if (time <= 0) return
                time--
                const hours = Math.floor(time / 3600)
                const minutes = Math.floor((time % 3600) / 60)
                const seconds = time % 60
                countdownEl.textContent = `${hours.toString().padStart(2, '0')}:${minutes.toString().padStart(2, '0')}:${seconds.toString().padStart(2, '0')}`
            }, 1000)
        }

        // Thay đổi banner
        let currentBanner = 0
        function changeBanner(n) {
            currentBanner = n
            const container = document.getElementById('banner-container')
            container.style.animation = 'none'
            container.offsetHeight
            container.style.transform = `translateX(-${n * 100}%)`
        }
        
        function buyNow(id) {
            const product = products.find(p => p.id === id)
            if (product) {
                cart.push({...product, quantity: 1})
                updateCartCount()
                showCart()
            }
        }
        
        function toggleAccountMenu() {
            const menu = document.getElementById('account-menu')
            menu.classList.toggle('hidden')
        }
        
        function logout() {
            toggleAccountMenu()
            setTimeout(() => alert('👋 Đã đăng xuất. Hẹn gặp lại bạn tại IMEX!'), 400)
        }
        
        function viewAll() {
            renderProducts(products)
            document.getElementById('product-grid').scrollIntoView({ behavior: 'smooth' })
        }

        // Khởi tạo trang web
        window.onload = function () {
            renderProducts(products)
            updateCartCount()
            startCountdown()
            
            // Nhấn Enter trong ô tìm kiếm
            document.getElementById('search-input').addEventListener('keypress', function(e) {
                if (e.key === 'Enter') performSearch()
            })
            
            console.log('%c✅ Trang IMEX đã được tạo thành công! Gần giống Shopee, chỉ bán thiết bị di động, màu chủ đạo xanh dương - trắng.', 'color:#007BFF; font-size:13px; font-weight:600')
        }
    </script>
</body>
</html>
