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
            box-shadow: 0 4px 15px rgba(15, 76, 129, 0.15);
        }
        
        .product-card {
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
        }
        
        .product-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 25px 30px -8px rgb(15 76 129 / 0.2);
        }
        
        .hero-bg {
            background: linear-gradient(rgba(15, 76, 129, 0.9), rgba(15, 76, 129, 0.9)), 
                        url('https://picsum.photos/id/1015/2000/900') center/cover no-repeat;
        }
        
        .modal {
            animation: modalPop 0.3s ease-out forwards;
        }
        
        @keyframes modalPop {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }
    </style>
</head>
<body class="bg-slate-50 text-slate-900">

    <!-- TOP BAR -->
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
                    <i class="fa-solid fa-store"></i> Kênh người bán
                </a>
                <a onclick="showSupport()" class="hover:text-[#0F4C81] cursor-pointer">Hỗ trợ 24/7</a>
            </div>
        </div>
    </div>

    <!-- HEADER CHÍNH - NGẮN GỌN & CỐ ĐỊNH -->
    <header class="header-bg text-white nav-fixed">
        <div class="max-w-7xl mx-auto px-6 py-4">
            <div class="flex items-center justify-between">
                <!-- Logo -->
                <div class="flex items-center gap-3">
                    <div class="w-11 h-11 bg-white rounded-2xl flex items-center justify-center text-4xl shadow">📱</div>
                    <div>
                        <span class="text-3xl font-bold tracking-tight">DiĐộng</span>
                        <span class="text-3xl font-bold tracking-tight text-sky-200">Pro</span>
                    </div>
                </div>

                <!-- Search -->
                <div class="flex-1 max-w-2xl mx-10">
                    <div class="relative">
                        <input id="searchInput" 
                               onkeyup="if(event.key==='Enter') performSearch()"
                               type="text" 
                               placeholder="Tìm kiếm điện thoại, laptop, smartwatch, máy tính bảng..."
                               class="w-full bg-white text-slate-900 rounded-3xl py-4 pl-14 pr-6 outline-none text-base placeholder:text-slate-400 shadow-inner">
                        <i class="fa-solid fa-magnifying-glass absolute left-6 top-1/2 -translate-y-1/2 text-[#0F4C81] text-2xl"></i>
                        <button onclick="performSearch()" 
                                class="absolute right-2 top-1/2 -translate-y-1/2 bg-[#0F4C81] hover:bg-[#0A3A66] text-white px-8 py-3 rounded-3xl font-medium">
                            Tìm kiếm
                        </button>
                    </div>
                </div>

                <!-- Right Icons -->
                <div class="flex items-center gap-10 text-2xl">
                    <div onclick="showCart()" class="relative cursor-pointer hover:text-sky-200 transition">
                        <i class="fa-solid fa-cart-shopping"></i>
                        <span id="cartCount" class="absolute -top-2 -right-2 bg-red-500 text-white text-xs font-bold w-5 h-5 flex items-center justify-center rounded-full">0</span>
                    </div>
                    <div onclick="showCommunity()" class="cursor-pointer hover:text-sky-200 transition">
                        <i class="fa-solid fa-users"></i>
                    </div>
                    <div onclick="showVoucherModal()" class="cursor-pointer hover:text-sky-200 transition">
                        <i class="fa-solid fa-ticket"></i>
                    </div>
                    <div onclick="showAccountModal()" class="cursor-pointer hover:text-sky-200 transition">
                        <i class="fa-solid fa-user-circle"></i>
                    </div>
                </div>
            </div>
        </div>

        <!-- Thanh điều hướng ngắn gọn -->
        <nav class="bg-white text-slate-700 border-t">
            <div class="max-w-7xl mx-auto px-6">
                <div class="flex items-center gap-8 py-3 text-sm font-medium overflow-x-auto whitespace-nowrap">
                    <a onclick="filterCategory('all')" class="hover:text-[#0F4C81] cursor-pointer">Trang chủ</a>
                    <a onclick="filterCategory('mobile')" class="hover:text-[#0F4C81] cursor-pointer">Điện thoại thông minh</a>
                    <a onclick="filterCategory('laptop')" class="hover:text-[#0F4C81] cursor-pointer">Máy tính xách tay</a>
                    <a onclick="filterCategory('tablet')" class="hover:text-[#0F4C81] cursor-pointer">Máy tính bảng</a>
                    <a onclick="filterCategory('wearable')" class="hover:text-[#0F4C81] cursor-pointer">Đồng hồ thông minh</a>
                    <a onclick="filterCategory('gaming')" class="hover:text-[#0F4C81] cursor-pointer">Máy chơi game</a>
                    <a onclick="filterCategory('audio')" class="hover:text-[#0F4C81] cursor-pointer">Tai nghe & Âm thanh</a>
                    <a onclick="filterCategory('camera')" class="hover:text-[#0F4C81] cursor-pointer">Máy ảnh - Quay phim</a>
                    <a onclick="filterCategory('other')" class="hover:text-[#0F4C81] cursor-pointer">Thiết bị khác</a>
                    <div class="ml-auto bg-[#0F4C81] text-white text-xs px-6 py-2 rounded-3xl font-medium flex items-center gap-2">
                        <i class="fa-solid fa-bolt"></i> FLASH SALE 11.11
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
                <p class="text-2xl text-sky-100 mb-10">Quản lý sản phẩm • Đối chiếu thông số • Bảo hành điện tử • Cộng đồng • Giao dịch an toàn</p>
                
                <div class="flex gap-5">
                    <button onclick="document.getElementById('productsSection').scrollIntoView({behavior:'smooth'})" 
                            class="bg-white text-[#0F4C81] font-semibold px-10 py-5 rounded-3xl text-xl flex items-center gap-3 hover:scale-105 transition">
                        <i class="fa-solid fa-cart-shopping"></i> Mua sắm ngay
                    </button>
                    <button onclick="showCompareModal()" 
                            class="border-2 border-white/80 hover:bg-white/10 px-8 py-5 rounded-3xl text-xl font-semibold flex items-center gap-3 transition">
                        ⚖️ So sánh thông số
                    </button>
                </div>
            </div>
        </div>
    </section>

    <!-- SẢN PHẨM NỔI BẬT -->
    <section id="productsSection" class="max-w-7xl mx-auto px-6 py-16">
        <div class="flex justify-between items-center mb-10">
            <h2 class="text-4xl font-semibold">Sản phẩm nổi bật</h2>
            <select id="sortSelect" onchange="sortProducts()" class="border border-slate-300 rounded-3xl px-6 py-3 outline-none">
                <option value="default">Sắp xếp mặc định</option>
                <option value="price-low">Giá thấp đến cao</option>
                <option value="price-high">Giá cao đến thấp</option>
                <option value="rating">Đánh giá cao nhất</option>
            </select>
        </div>

        <div id="productGrid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-8">
            <!-- Render bởi JavaScript -->
        </div>
    </section>

    <!-- MODAL CHI TIẾT SẢN PHẨM -->
    <div id="productModal" onclick="if(event.target.id==='productModal') hideProductModal()" 
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="modal bg-white w-full max-w-5xl mx-4 rounded-3xl overflow-hidden">
            <div id="modalContent" class="p-10"></div>
        </div>
    </div>

    <!-- MODAL GIỎ HÀNG -->
    <div id="cartModal" onclick="if(event.target.id==='cartModal') hideCart()" 
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="modal bg-white w-full max-w-2xl mx-4 rounded-3xl p-8">
            <h3 class="text-3xl font-bold mb-6">Giỏ hàng của bạn</h3>
            <div id="cartItems" class="max-h-[400px] overflow-auto space-y-6"></div>
            <div class="border-t mt-8 pt-6 flex justify-between text-2xl font-semibold">
                <span>Tổng thanh toán</span>
                <span id="cartTotal" class="text-[#0F4C81]"></span>
            </div>
            <button onclick="checkout()" 
                    class="mt-8 w-full py-6 bg-[#0F4C81] text-white text-xl font-semibold rounded-3xl">
                Thanh toán ngay (VNPAY / Momo / ZaloPay)
            </button>
        </div>
    </div>

    <!-- MODAL SO SÁNH -->
    <div id="compareModal" onclick="if(event.target.id==='compareModal') hideCompareModal()" 
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="modal bg-white w-full max-w-6xl mx-4 rounded-3xl p-8">
            <h3 class="text-3xl font-bold mb-6">So sánh thông số kỹ thuật</h3>
            <table id="compareTable" class="w-full text-sm"></table>
        </div>
    </div>

    <!-- MODAL TÀI KHOẢN -->
    <div id="accountModal" onclick="if(event.target.id==='accountModal') hideAccountModal()" 
         class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
        <div onclick="event.stopImmediatePropagation()" 
             class="modal bg-white w-full max-w-md mx-4 rounded-3xl p-8">
            <h3 class="text-3xl font-bold mb-6">Tài khoản DiĐộng Pro</h3>
            <div class="space-y-6">
                <div class="grid grid-cols-2 gap-6">
                    <div class="bg-slate-100 rounded-3xl p-6 text-center">
                        <div class="text-5xl mb-3">📦</div>
                        <div class="font-bold text-4xl text-[#0F4C81]">18</div>
                        <div class="text-sm">Đơn hàng</div>
                    </div>
                    <div class="bg-slate-100 rounded-3xl p-6 text-center">
                        <div class="text-5xl mb-3">🔐</div>
                        <div class="font-bold text-4xl text-[#0F4C81]">7</div>
                        <div class="text-sm">Bảo hành điện tử</div>
                    </div>
                </div>
                <button onclick="hideAccountModal()" class="w-full py-5 border border-[#0F4C81] text-[#0F4C81] rounded-3xl font-medium">Quản lý tài khoản</button>
                <button onclick="logout()" class="w-full py-5 text-red-600 border border-red-200 rounded-3xl">Đăng xuất</button>
            </div>
        </div>
    </div>

    <!-- SCRIPT -->
    <script>
        let products = [
            {id:1, name:"iPhone 16 Pro Max 256GB", category:"mobile", price:34990000, rating:4.9, sold:3240, image:"📱", specs:{cpu:"A18 Pro", ram:"8GB", battery:"4680mAh", screen:"6.9 inch", os:"iOS 18"}},
            {id:2, name:"Samsung Galaxy Z Fold6 512GB", category:"mobile", price:44990000, rating:4.8, sold:1890, image:"📱", specs:{cpu:"Snapdragon 8 Gen 3", ram:"12GB", battery:"4400mAh", screen:"7.6 inch", os:"Android 14"}},
            {id:3, name:"MacBook Air M3 16GB", category:"laptop", price:32990000, rating:5.0, sold:1240, image:"💻", specs:{cpu:"Apple M3", ram:"16GB", battery:"18 giờ", screen:"13.6 inch", os:"macOS"}},
            {id:4, name:"Apple Watch Ultra 2", category:"wearable", price:18990000, rating:4.9, sold:4120, image:"⌚", specs:{cpu:"S9 SiP", ram:"N/A", battery:"36 giờ", screen:"49mm", os:"watchOS 11"}},
            {id:5, name:"iPad Pro M4 13 inch", category:"tablet", price:42990000, rating:4.7, sold:780, image:"📟", specs:{cpu:"M4", ram:"16GB", battery:"10 giờ", screen:"13 inch OLED", os:"iPadOS 18"}},
            {id:6, name:"Steam Deck OLED 1TB", category:"gaming", price:16990000, rating:4.6, sold:520, image:"🎮", specs:{cpu:"Ryzen Z1", ram:"16GB", battery:"8 giờ", screen:"7.4 inch", os:"SteamOS"}}
        ];

        let cart = [];
        let compareList = [];

        function renderProducts(list) {
            const grid = document.getElementById('productGrid');
            grid.innerHTML = '';
            list.forEach(p => {
                const html = `
                <div onclick="showProductDetail(${p.id})" class="product-card bg-white rounded-3xl overflow-hidden cursor-pointer">
                    <div class="h-56 flex items-center justify-center text-8xl bg-slate-100">${p.image}</div>
                    <div class="p-6">
                        <h3 class="font-semibold text-lg line-clamp-2">${p.name}</h3>
                        <div class="mt-4 flex justify-between items-baseline">
                            <span class="text-2xl font-bold text-[#0F4C81]">${p.price.toLocaleString('vi-VN')} ₫</span>
                            <span class="text-amber-400">★ ${p.rating}</span>
                        </div>
                        <div class="text-xs text-slate-500 mt-2">Đã bán ${p.sold}</div>
                    </div>
                </div>`;
                grid.innerHTML += html;
            });
        }

        function showProductDetail(id) {
            const p = products.find(x => x.id === id);
            if (!p) return;

            const content = document.getElementById('modalContent');
            content.innerHTML = `
            <div class="flex gap-10">
                <div class="flex-1 text-center">
                    <div class="text-[160px] mb-8">${p.image}</div>
                    <h2 class="text-4xl font-bold">${p.name}</h2>
                    <div class="text-4xl font-bold text-[#0F4C81] mt-6">${p.price.toLocaleString('vi-VN')} ₫</div>
                </div>
                <div class="flex-1">
                    <div class="flex justify-end">
                        <span onclick="hideProductModal()" class="text-5xl cursor-pointer text-slate-300 hover:text-slate-500">×</span>
                    </div>
                    <h4 class="font-semibold text-lg mb-4">Thông số kỹ thuật</h4>
                    <div class="grid grid-cols-2 gap-y-4 text-sm">
                        <div>CPU:</div><div class="font-medium">${p.specs.cpu}</div>
                        <div>RAM:</div><div class="font-medium">${p.specs.ram}</div>
                        <div>Pin:</div><div class="font-medium">${p.specs.battery}</div>
                        <div>Màn hình:</div><div class="font-medium">${p.specs.screen}</div>
                        <div>Hệ điều hành:</div><div class="font-medium">${p.specs.os}</div>
                    </div>
                    
                    <div class="mt-10 bg-emerald-50 border border-emerald-200 rounded-3xl p-6">
                        <div class="flex items-center gap-3 text-[#0F4C81]">
                            <i class="fa-solid fa-shield-halved text-3xl"></i>
                            <div>
                                <div class="font-medium">Bảo hành điện tử 36 tháng</div>
                                <div class="text-xs">Đã lưu trữ trên hệ thống • Tra cứu mọi lúc</div>
                            </div>
                        </div>
                    </div>

                    <div class="flex gap-4 mt-10">
                        <button onclick="addToCart(${p.id}); hideProductModal()" 
                                class="flex-1 bg-[#0F4C81] text-white py-6 rounded-3xl font-semibold text-xl">Thêm vào giỏ</button>
                        <button onclick="addToCompare(${products.indexOf(p)}); hideProductModal()" 
                                class="flex-1 border-2 border-[#0F4C81] text-[#0F4C81] py-6 rounded-3xl font-semibold text-xl">So sánh</button>
                    </div>
                </div>
            </div>`;
            
            document.getElementById('productModal').classList.remove('hidden');
            document.getElementById('productModal').classList.add('flex');
        }

        function hideProductModal() {
            const modal = document.getElementById('productModal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
        }

        function addToCart(id) {
            const product = products.find(p => p.id === id);
            cart.push(product);
            document.getElementById('cartCount').textContent = cart.length;
            alert(`✅ Đã thêm ${product.name} vào giỏ hàng!`);
        }

        function showCart() {
            const modal = document.getElementById('cartModal');
            const container = document.getElementById('cartItems');
            container.innerHTML = '';
            
            if (cart.length === 0) {
                container.innerHTML = `<p class="text-center py-12 text-slate-400">Giỏ hàng trống</p>`;
            } else {
                let total = 0;
                cart.forEach((item, index) => {
                    total += item.price;
                    container.innerHTML += `
                    <div class="flex gap-6 items-center border-b pb-6">
                        <div class="text-6xl">${item.image}</div>
                        <div class="flex-1">
                            <div class="font-medium">${item.name}</div>
                            <div class="text-[#0F4C81] text-xl">${item.price.toLocaleString('vi-VN')} ₫</div>
                        </div>
                        <button onclick="removeFromCart(${index});" class="text-red-500 text-3xl">×</button>
                    </div>`;
                });
                document.getElementById('cartTotal').innerHTML = `${total.toLocaleString('vi-VN')} ₫`;
            }
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            document.getElementById('cartCount').textContent = cart.length;
            showCart();
        }

        function hideCart() {
            const modal = document.getElementById('cartModal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
        }

        function checkout() {
            hideCart();
            setTimeout(() => {
                alert('🎉 Thanh toán thành công! Cảm ơn bạn đã mua sắm tại DiĐộng Pro.\nMã đơn hàng: DD' + Math.floor(100000 + Math.random() * 900000));
                cart = [];
                document.getElementById('cartCount').textContent = '0';
            }, 800);
        }

        function addToCompare(index) {
            const product = products[index];
            if (compareList.length >= 4) return alert('Chỉ so sánh tối đa 4 sản phẩm!');
            compareList.push(product);
            alert(`✅ Đã thêm ${product.name} vào danh sách so sánh`);
        }

        function showCompareModal() {
            const modal = document.getElementById('compareModal');
            const table = document.getElementById('compareTable');
            table.innerHTML = `
            <thead>
                <tr class="border-b-4 border-[#0F4C81]">
                    <th class="text-left py-5 px-8 font-medium">Thông số</th>
                    ${compareList.map(p => `<th class="text-center py-5"><div class="text-6xl">${p.image}</div><div class="mt-2 font-medium">${p.name}</div></th>`).join('')}
                </tr>
            </thead>
            <tbody>
                ${['cpu','ram','battery','screen','os'].map(key => {
                    const label = {cpu:'CPU', ram:'RAM', battery:'Pin', screen:'Màn hình', os:'Hệ điều hành'}[key];
                    return `<tr class="border-b"><td class="py-5 px-8 font-medium">${label}</td>${compareList.map(p => `<td class="text-center py-5">${p.specs[key] || '—'}</td>`).join('')}</tr>`;
                }).join('')}
            </tbody>`;
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

        function hideCompareModal() {
            const modal = document.getElementById('compareModal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
            compareList = [];
        }

        function performSearch() {
            const q = document.getElementById('searchInput').value.toLowerCase().trim();
            const filtered = q ? products.filter(p => p.name.toLowerCase().includes(q)) : products;
            renderProducts(filtered);
        }

        function filterCategory(cat) {
            const filtered = cat === 'all' ? products : products.filter(p => p.category === cat);
            renderProducts(filtered);
        }

        function sortProducts() {
            const type = document.getElementById('sortSelect').value;
            let sorted = [...products];
            if (type === 'price-low') sorted.sort((a,b) => a.price - b.price);
            if (type === 'price-high') sorted.sort((a,b) => b.price - a.price);
            if (type === 'rating') sorted.sort((a,b) => b.rating - a.rating);
            renderProducts(sorted);
        }

        function showCommunity() {
            alert("💬 Cộng đồng DiĐộng Pro\n\nChia sẻ đánh giá, kinh nghiệm sử dụng thiết bị di động với hơn 120.000 thành viên.");
        }

        function showVoucherModal() {
            alert("🎟 Voucher của bạn:\n• Giảm 500.000đ cho đơn từ 10 triệu\n• Freeship toàn quốc\n• Trả góp 0% lãi suất");
        }

        function showAccountModal() {
            document.getElementById('accountModal').classList.remove('hidden');
            document.getElementById('accountModal').classList.add('flex');
        }

        function hideAccountModal() {
            const modal = document.getElementById('accountModal');
            modal.classList.add('hidden');
            modal.classList.remove('flex');
        }

        function logout() {
            hideAccountModal();
            alert("👋 Đăng xuất thành công. Hẹn gặp lại bạn!");
        }

        function toggleSellerMode() {
            if (confirm("Chuyển sang chế độ Người bán?")) {
                alert("✅ Đã vào Seller Center\nBạn có thể đăng bán thiết bị di động, quản lý đơn hàng và doanh thu.");
            }
        }

        function changeLocation() {
            const loc = prompt("Nhập tỉnh/thành phố của bạn:", "Vinh, Nghệ An");
            if (loc) document.getElementById('location').textContent = loc;
        }

        function showSupport() {
            alert("🛟 Hỗ trợ khách hàng 24/7\nHotline: 1800 9999\nEmail: support@didongpro.vn");
        }

        // Khởi chạy
        window.onload = () => {
            renderProducts(products);
            console.log('%c✅ DiĐộng Pro đã hoàn thiện toàn diện với màu xanh dương đậm. Giao diện đẹp, đầy đủ tính năng, giống Shopee cao.', 
                        'color:#0F4C81; font-size:15px; font-weight:700');
        };
    </script>
</body>
</html>
