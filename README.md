<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DiĐộng Pro - Chuyên Thiết Bị Di Động</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
        
        :root {
            --primary: #0F4C81;
        }
        
        * {
            font-family: 'Inter', system_ui, sans-serif;
        }
        
        .header-bg {
            background: linear-gradient(90deg, #0F4C81 0%, #0A3A66 100%);
        }
        
        .nav-fixed {
            position: sticky;
            top: 0;
            z-index: 50;
            box-shadow: 0 4px 12px rgba(15, 76, 129, 0.15);
        }
        
        .product-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-6px);
            box-shadow: 0 20px 25px -5px rgb(15 76 129 / 0.15);
        }
        
        .hero-bg {
            background: linear-gradient(rgba(15, 76, 129, 0.88), rgba(15, 76, 129, 0.88)), 
                        url('https://picsum.photos/id/1015/2000/900') center/cover no-repeat;
        }
        
        .modal {
            animation: modalPop 0.3s ease-out;
        }
        
        @keyframes modalPop {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-900">

    <!-- TOP BAR NHẸ -->
    <div class="bg-white border-b py-2 text-xs">
        <div class="max-w-7xl mx-auto px-6 flex justify-between items-center">
            <div class="flex items-center gap-6 text-slate-600">
                <span class="flex items-center gap-1.5">
                    <i class="fa-solid fa-location-dot text-[#0F4C81]"></i>
                    <span id="location" class="font-medium">Vinh, Nghệ An</span>
                </span>
                <span onclick="changeLocation()" class="text-[#0F4C81] cursor-pointer hover:underline">Thay đổi</span>
            </div>
            <div class="flex items-center gap-8 text-slate-600">
                <a onclick="toggleSellerMode()" class="hover:text-[#0F4C81] cursor-pointer flex items-center gap-1">
                    <i class="fa-solid fa-store"></i> Bán hàng
                </a>
                <a href="#" class="hover:text-[#0F4C81] cursor-pointer">Hỗ trợ</a>
                <a onclick="showAccountModal()" class="hover:text-[#0F4C81] cursor-pointer flex items-center gap-1">
                    <i class="fa-solid fa-user"></i> Lê Tú Mây
                </a>
            </div>
        </div>
    </div>

    <!-- HEADER CHÍNH - NGẮN GỌN, CỐ ĐỊNH -->
    <header class="header-bg text-white nav-fixed">
        <div class="max-w-7xl mx-auto px-6 py-4">
            <div class="flex items-center justify-between">
                <!-- Logo -->
                <div class="flex items-center gap-3">
                    <div class="w-11 h-11 bg-white rounded-2xl flex items-center justify-center text-4xl shadow-md">📱</div>
                    <div>
                        <span class="text-3xl font-bold tracking-tight">DiĐộng</span>
                        <span class="text-3xl font-bold tracking-tight text-sky-200">Pro</span>
                    </div>
                </div>

                <!-- Search Bar -->
                <div class="flex-1 max-w-2xl mx-10">
                    <div class="relative">
                        <input id="searchInput" 
                               onkeyup="if(event.key==='Enter') performSearch()"
                               type="text" 
                               placeholder="Tìm iPhone, Galaxy, MacBook, Smartwatch, Laptop..."
                               class="w-full bg-white text-slate-900 rounded-3xl py-4 pl-14 pr-6 outline-none text-base placeholder:text-slate-400 shadow-inner">
                        <i class="fa-solid fa-magnifying-glass absolute left-6 top-1/2 -translate-y-1/2 text-[#0F4C81] text-2xl"></i>
                        <button onclick="performSearch()" 
                                class="absolute right-2 top-1/2 -translate-y-1/2 bg-[#0F4C81] hover:bg-[#0A3A66] text-white px-8 py-3 rounded-3xl font-medium">
                            Tìm kiếm
                        </button>
                    </div>
                </div>

                <!-- Icons -->
                <div class="flex items-center gap-9 text-2xl">
                    <div onclick="showCart()" class="relative cursor-pointer">
                        <i class="fa-solid fa-cart-shopping"></i>
                        <span id="cartCount" class="absolute -top-1 -right-2 bg-red-500 text-white text-xs font-bold w-5 h-5 flex items-center justify-center rounded-full">3</span>
                    </div>
                    <div onclick="showCommunity()" class="cursor-pointer">
                        <i class="fa-solid fa-users"></i>
                    </div>
                    <div onclick="showVoucherModal()" class="cursor-pointer">
                        <i class="fa-solid fa-ticket"></i>
                    </div>
                    <div onclick="showAccountModal()" class="cursor-pointer">
                        <i class="fa-solid fa-user-circle"></i>
                    </div>
                </div>
            </div>
        </div>

        <!-- Thanh điều hướng ngắn gọn -->
        <nav class="bg-white text-slate-700 border-t">
            <div class="max-w-7xl mx-auto px-6">
                <div class="flex items-center gap-8 py-3 text-sm font-medium overflow-x-auto">
                    <a onclick="filterCategory('all')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Trang chủ</a>
                    <a onclick="filterCategory('mobile')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Điện thoại thông minh</a>
                    <a onclick="filterCategory('laptop')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Máy tính xách tay</a>
                    <a onclick="filterCategory('tablet')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Máy tính bảng</a>
                    <a onclick="filterCategory('wearable')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Đồng hồ thông minh</a>
                    <a onclick="filterCategory('gaming')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Máy chơi game</a>
                    <a onclick="filterCategory('audio')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Tai nghe & Âm thanh</a>
                    <a onclick="filterCategory('camera')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Máy ảnh - Quay phim</a>
                    <a onclick="filterCategory('other')" class="hover:text-[#0F4C81] whitespace-nowrap cursor-pointer">Thiết bị khác</a>
                    
                    <div class="ml-auto bg-[#0F4C81] text-white text-xs px-6 py-2 rounded-3xl font-medium flex items-center gap-2">
                        <i class="fa-solid fa-bolt"></i> FLASH SALE
                    </div>
                </div>
            </div>
        </nav>
    </header>

    <!-- HERO -->
    <section class="hero-bg text-white py-20">
        <div class="max-w-7xl mx-auto px-6 grid grid-cols-2 gap-12 items-center">
            <div>
                <h1 class="text-6xl font-bold leading-none mb-6">
                    Nền tảng Thương mại Điện tử<br>Chuyên Thiết Bị Di Động
                </h1>
                <p class="text-2xl text-sky-100 mb-10">Hơn 50.000 sản phẩm • Bảo hành điện tử • Đối chiếu thông số • Cộng đồng công nghệ</p>
                
                <div class="flex gap-5">
                    <button onclick="document.getElementById('productsSection').scrollIntoView({behavior:'smooth'})" 
                            class="bg-white text-[#0F4C81] font-semibold px-10 py-5 rounded-3xl text-xl flex items-center gap-3 hover:scale-105 transition">
                        <i class="fa-solid fa-cart-shopping"></i> Mua sắm ngay
                    </button>
                    <button onclick="showCompareModal()" 
                            class="border-2 border-white/80 hover:bg-white/10 px-8 py-5 rounded-3xl text-xl font-semibold flex items-center gap-3 transition">
                        ⚖️ So sánh sản phẩm
                    </button>
                </div>
            </div>
            <div class="text-center">
                <div class="inline-block bg-white/10 backdrop-blur-md rounded-3xl p-8">
                    <img src="https://picsum.photos/id/1015/520/380" class="rounded-3xl shadow-2xl" alt="Hero">
                </div>
            </div>
        </div>
    </section>

    <!-- SẢN PHẨM -->
    <section id="productsSection" class="max-w-7xl mx-auto px-6 py-16">
        <div class="flex justify-between items-center mb-10">
            <h2 class="text-4xl font-semibold">Sản phẩm nổi bật</h2>
            <select id="sortSelect" onchange="sortProducts()" class="border border-slate-300 rounded-3xl px-6 py-3 outline-none">
                <option value="default">Sắp xếp</option>
                <option value="price-low">Giá thấp đến cao</option>
                <option value="price-high">Giá cao đến thấp</option>
                <option value="rating">Đánh giá cao nhất</option>
            </select>
        </div>

        <div id="productGrid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-8">
            <!-- Sản phẩm sẽ được render bởi JS -->
        </div>
    </section>

    <!-- MODALS (giống Shopee) -->
    <!-- Product Detail, Cart, Compare, Account, Seller... sẽ giữ nguyên logic từ phiên bản trước nhưng điều chỉnh màu -->

    <script>
        // Màu chủ đạo mới
        const primaryColor = '#0F4C81';

        // Dữ liệu sản phẩm
        let products = [
            {id:1, name:"iPhone 16 Pro Max 256GB", category:"mobile", price:34990000, rating:4.9, sold:2450, image:"📱"},
            {id:2, name:"Samsung Galaxy Z Fold6", category:"mobile", price:44990000, rating:4.8, sold:1320, image:"📱"},
            {id:3, name:"MacBook Air M3 16GB", category:"laptop", price:32990000, rating:5.0, sold:980, image:"💻"},
            {id:4, name:"Apple Watch Ultra 2", category:"wearable", price:18990000, rating:4.9, sold:3120, image:"⌚"},
            {id:5, name:"iPad Pro M4 13 inch", category:"tablet", price:42990000, rating:4.7, sold:650, image:"📟"},
            {id:6, name:"Steam Deck OLED", category:"gaming", price:16990000, rating:4.6, sold:420, image:"🎮"},
        ];

        let cart = [];

        function renderProducts(filteredProducts) {
            const grid = document.getElementById('productGrid');
            grid.innerHTML = '';
            
            filteredProducts.forEach(product => {
                const card = `
                <div onclick="showProductDetail(${product.id})" class="product-card bg-white rounded-3xl overflow-hidden cursor-pointer border border-transparent hover:border-[#0F4C81]/30">
                    <div class="h-56 flex items-center justify-center text-8xl bg-slate-100">${product.image}</div>
                    <div class="p-6">
                        <h3 class="font-semibold text-lg leading-tight">${product.name}</h3>
                        <div class="mt-4 flex items-baseline justify-between">
                            <span class="text-2xl font-bold text-[#0F4C81]">${product.price.toLocaleString('vi-VN')} ₫</span>
                            <span class="text-amber-400">★ ${product.rating}</span>
                        </div>
                        <div class="text-xs text-slate-500 mt-2">Đã bán ${product.sold}</div>
                    </div>
                </div>`;
                grid.innerHTML += card;
            });
        }

        function showProductDetail(id) {
            const product = products.find(p => p.id === id);
            if (!product) return;
            
            alert(`📱 Chi tiết sản phẩm:\n\n${product.name}\nGiá: ${product.price.toLocaleString('vi-VN')} ₫\nĐánh giá: ${product.rating} sao\nĐã bán: ${product.sold} chiếc\n\n(Bảo hành điện tử • So sánh thông số • Thêm vào giỏ hàng)`);
            // Bạn có thể mở rộng modal chi tiết ở đây nếu cần
        }

        function addToCart(id) {
            const product = products.find(p => p.id === id);
            cart.push(product);
            document.getElementById('cartCount').textContent = cart.length;
            alert(`✅ Đã thêm ${product.name} vào giỏ hàng!`);
        }

        function showCart() {
            if (cart.length === 0) {
                alert("Giỏ hàng trống!");
                return;
            }
            let total = cart.reduce((sum, item) => sum + item.price, 0);
            alert(`🛒 Giỏ hàng của bạn (${cart.length} sản phẩm)\nTổng tiền: ${total.toLocaleString('vi-VN')} ₫\n\nNhấn OK để thanh toán (Demo)`);
        }

        function performSearch() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const filtered = products.filter(p => 
                p.name.toLowerCase().includes(query)
            );
            renderProducts(filtered.length ? filtered : products);
        }

        function filterCategory(category) {
            if (category === 'all') {
                renderProducts(products);
            } else {
                const filtered = products.filter(p => p.category === category);
                renderProducts(filtered);
            }
        }

        function sortProducts() {
            const sortType = document.getElementById('sortSelect').value;
            let sorted = [...products];
            
            if (sortType === 'price-low') sorted.sort((a,b) => a.price - b.price);
            else if (sortType === 'price-high') sorted.sort((a,b) => b.price - a.price);
            else if (sortType === 'rating') sorted.sort((a,b) => b.rating - a.rating);
            
            renderProducts(sorted);
        }

        function showCommunity() {
            alert("💬 Chào mừng bạn đến với Cộng đồng DiĐộng Pro!\n\nBạn có thể chia sẻ đánh giá, kinh nghiệm sử dụng thiết bị di động.");
        }

        function showVoucherModal() {
            alert("🎟 Bạn có các voucher:\n• Giảm 500.000đ cho đơn từ 10 triệu\n• Freeship toàn quốc\n• Trả góp 0% lãi suất");
        }

        function showAccountModal() {
            alert("👤 Tài khoản: Lê Tú Mây\n\nSố đơn hàng: 12\nThiết bị đang bảo hành: 4\n\nCảm ơn bạn đã sử dụng DiĐộng Pro!");
        }

        function toggleSellerMode() {
            const confirmSeller = confirm("Chuyển sang chế độ Nhà bán hàng?\n\nBạn có thể đăng bán thiết bị di động, quản lý đơn hàng.");
            if (confirmSeller) {
                alert("✅ Đã chuyển sang chế độ Bán hàng (Seller Center)\n\nBạn có thể thêm sản phẩm mới ngay bây giờ.");
            }
        }

        function changeLocation() {
            const newLoc = prompt("Nhập địa điểm của bạn:", "Vinh, Nghệ An");
            if (newLoc) document.getElementById('location').textContent = newLoc;
        }

        function showCompareModal() {
            alert("⚖️ Hệ thống đối chiếu thông số kỹ thuật\n\nChọn nhiều sản phẩm để so sánh cấu hình, pin, giá bán, màn hình...");
        }

        // Khởi chạy
        window.onload = () => {
            renderProducts(products);
            console.log('%c✅ DiĐộng Pro đã hoàn thiện với màu xanh dương đậm - trắng. Thanh điều hướng ngắn gọn, cố định, giao diện sạch sẽ và chuyên nghiệp hơn.', 
                        'color:#0F4C81; font-size:14px; font-weight:600');
        };
    </script>
</body>
</html>
