<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEX - Thiết bị di động chính hãng</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
        
        body { font-family: 'Inter', system_ui, sans-serif; }
        .logo-font { font-family: 'Inter', sans-serif; font-weight: 700; }
        
        .nav-active {
            color: #0066FF;
            border-bottom: 3px solid #0066FF;
        }
        
        .bottom-nav {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            border-top: 1px solid #e5e7eb;
            z-index: 1000;
        }
        
        .product-card {
            transition: all 0.3s;
        }
        .product-card:hover {
            transform: translateY(-4px);
            box-shadow: 0 10px 15px -3px rgba(0, 102, 255, 0.15);
        }
        
        .search-bar {
            background: #f1f5f9;
        }
    </style>
</head>
<body class="bg-gray-50 min-h-screen pb-20">

    <!-- TOP HEADER -->
    <header class="bg-white shadow-sm sticky top-0 z-50">
        <div class="max-w-screen-xl mx-auto">
            <!-- Logo + Search -->
            <div class="flex items-center justify-between px-4 py-3">
                <div class="flex items-center gap-2">
                    <div class="w-9 h-9 bg-[#0066FF] rounded-2xl flex items-center justify-center text-white text-3xl">📱</div>
                    <div>
                        <h1 class="logo-font text-2xl text-[#0066FF] tracking-tight">IMEX</h1>
                        <p class="text-[10px] text-gray-500 -mt-1">Mobile Mall</p>
                    </div>
                </div>
                
                <div class="flex-1 mx-4">
                    <div onclick="toggleSearch()" 
                         class="search-bar flex items-center gap-3 px-4 py-3 rounded-3xl text-sm text-gray-500 cursor-pointer">
                        <i class="fa-solid fa-magnifying-glass"></i>
                        <span>Tìm kiếm điện thoại, máy tính bảng...</span>
                    </div>
                </div>
                
                <div class="flex items-center gap-5 text-xl text-gray-700">
                    <i onclick="showNotifications()" class="fa-solid fa-bell cursor-pointer relative">
                        <span class="absolute -top-1 -right-1 w-4 h-4 bg-red-500 text-white text-[10px] rounded-full flex items-center justify-center">3</span>
                    </i>
                    <i onclick="toggleCart()" class="fa-solid fa-shopping-cart cursor-pointer relative">
                        <span id="cart-count-top" class="absolute -top-1 -right-1 w-4 h-4 bg-red-500 text-white text-[10px] rounded-full flex items-center justify-center">0</span>
                    </i>
                </div>
            </div>

            <!-- Category Tabs -->
            <div class="flex overflow-x-auto gap-6 px-4 py-3 bg-white border-t text-sm font-medium whitespace-nowrap scrollbar-hide">
                <a href="#" onclick="filterCategory('all')" class="nav-active pb-1">Trang chủ</a>
                <a href="#" onclick="filterCategory('phone')" class="hover:text-[#0066FF] pb-1">Điện thoại</a>
                <a href="#" onclick="filterCategory('tablet')" class="hover:text-[#0066FF] pb-1">Máy tính bảng</a>
                <a href="#" onclick="filterCategory('watch')" class="hover:text-[#0066FF] pb-1">Đồng hồ</a>
                <a href="#" onclick="filterCategory('accessory')" class="hover:text-[#0066FF] pb-1">Phụ kiện</a>
                <a href="#" onclick="filterCategory('sale')" class="text-red-500 pb-1">Flash Sale</a>
            </div>
        </div>
    </header>

    <!-- MAIN CONTENT -->
    <main class="max-w-screen-xl mx-auto px-4 pt-4">

        <!-- Banner Slider -->
        <div class="relative overflow-hidden rounded-3xl mb-6">
            <img id="main-banner" src="https://picsum.photos/id/1015/800/320" 
                 class="w-full h-40 object-cover" alt="Banner">
            <div class="absolute bottom-4 left-4 bg-black/60 text-white text-xs px-4 py-1 rounded-3xl">
                iPhone 17 Series - Giảm đến 15%
            </div>
        </div>

        <!-- Flash Sale -->
        <div class="mb-8">
            <div class="flex justify-between items-center mb-3">
                <div class="flex items-center gap-2">
                    <span class="text-red-500 text-xl">🔥</span>
                    <h3 class="font-semibold text-lg">Flash Sale</h3>
                </div>
                <span id="countdown" class="text-red-500 font-mono text-sm font-bold">02:45:12</span>
            </div>
            <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 gap-4" id="flash-grid"></div>
        </div>

        <!-- Gợi ý cho bạn -->
        <div>
            <h3 class="font-semibold text-lg mb-4">Gợi ý cho bạn</h3>
            <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-5 gap-4" id="product-grid"></div>
        </div>
    </main>

    <!-- BOTTOM NAVIGATION (giống Lazada) -->
    <nav class="bottom-nav">
        <div class="max-w-screen-xl mx-auto grid grid-cols-5 text-center text-xs py-2">
            <a href="#" onclick="navigateTo('home')" class="flex flex-col items-center text-[#0066FF]">
                <i class="fa-solid fa-house text-2xl mb-1"></i>
                <span>Trang chủ</span>
            </a>
            <a href="#" onclick="navigateTo('search')" class="flex flex-col items-center text-gray-500">
                <i class="fa-solid fa-magnifying-glass text-2xl mb-1"></i>
                <span>Tìm kiếm</span>
            </a>
            <a href="#" onclick="navigateTo('notifications')" class="flex flex-col items-center text-gray-500">
                <i class="fa-solid fa-bell text-2xl mb-1"></i>
                <span>Thông báo</span>
            </a>
            <a href="#" onclick="navigateTo('account')" class="flex flex-col items-center text-gray-500">
                <i class="fa-solid fa-user text-2xl mb-1"></i>
                <span>Tôi</span>
            </a>
            <a href="#" onclick="navigateTo('settings')" class="flex flex-col items-center text-gray-500">
                <i class="fa-solid fa-gear text-2xl mb-1"></i>
                <span>Cài đặt</span>
            </a>
        </div>
    </nav>

    <!-- CART MODAL -->
    <div id="cart-modal" class="hidden fixed inset-0 bg-black/70 z-[2000] flex items-end">
        <div class="bg-white w-full rounded-t-3xl max-h-[85vh] overflow-hidden">
            <div class="p-5 border-b flex justify-between items-center">
                <h3 class="text-xl font-semibold">Giỏ hàng</h3>
                <button onclick="toggleCart()" class="text-3xl">✕</button>
            </div>
            <div id="cart-content" class="p-5 overflow-auto" style="max-height: 65vh;"></div>
            <div class="p-5 border-t">
                <div class="flex justify-between text-lg mb-4">
                    <span>Tổng tiền:</span>
                    <span id="cart-total" class="font-bold text-[#0066FF]">0 ₫</span>
                </div>
                <button onclick="checkout()" 
                        class="w-full bg-[#0066FF] text-white py-5 rounded-3xl font-semibold text-lg">
                    Thanh toán ngay
                </button>
            </div>
        </div>
    </div>

    <script>
        // Dữ liệu sản phẩm
        const products = [
            { id: 1, name: "iPhone 17 Pro Max 256GB", price: 38990000, oldPrice: 42990000, image: "https://picsum.photos/id/1015/400/400", discount: 9 },
            { id: 2, name: "Samsung Galaxy S25 Ultra", price: 32990000, oldPrice: 35990000, image: "https://picsum.photos/id/1016/400/400", discount: 8 },
            { id: 3, name: "iPad Air 6 M3 11 inch", price: 18990000, oldPrice: null, image: "https://picsum.photos/id/201/400/400", discount: 0 },
            { id: 4, name: "Xiaomi 15 Pro 5G", price: 16990000, oldPrice: 19990000, image: "https://picsum.photos/id/251/400/400", discount: 15 },
            { id: 5, name: "Apple Watch Ultra 3", price: 24990000, oldPrice: null, image: "https://picsum.photos/id/1005/400/400", discount: 5 }
        ];

        let cart = [];

        // Render sản phẩm
        function renderProducts(filteredProducts = products) {
            const grid = document.getElementById('product-grid');
            grid.innerHTML = '';
            
            filteredProducts.forEach(product => {
                const discountHTML = product.discount > 0 
                    ? `<span class="absolute top-3 left-3 bg-red-500 text-white text-xs px-2 py-0.5 rounded">-${product.discount}%</span>` 
                    : '';
                
                const html = `
                <div class="product-card bg-white rounded-2xl overflow-hidden border border-gray-100">
                    <div class="relative">
                        <img src="${product.image}" class="w-full h-52 object-cover">
                        ${discountHTML}
                    </div>
                    <div class="p-3">
                        <p class="text-sm font-medium line-clamp-2 h-10">${product.name}</p>
                        <div class="mt-2 flex items-center gap-2">
                            <span class="text-lg font-bold text-[#0066FF]">${product.price.toLocaleString('vi-VN')} ₫</span>
                            ${product.oldPrice ? `<span class="text-xs line-through text-gray-400">${product.oldPrice.toLocaleString('vi-VN')} ₫</span>` : ''}
                        </div>
                        <button onclick="addToCart(${product.id}); event.stopImmediatePropagation()" 
                                class="mt-3 w-full py-3 bg-[#0066FF] hover:bg-[#0055dd] text-white text-sm rounded-2xl font-medium">
                            Thêm vào giỏ
                        </button>
                    </div>
                </div>`;
                grid.innerHTML += html;
            });
        }

        // Flash Sale (sản phẩm giảm mạnh)
        function renderFlashSale() {
            const flashGrid = document.getElementById('flash-grid');
            flashGrid.innerHTML = '';
            const flashItems = products.slice(0, 4);
            
            flashItems.forEach(product => {
                const html = `
                <div class="bg-white rounded-2xl overflow-hidden border border-red-100">
                    <div class="relative">
                        <img src="${product.image}" class="w-full h-40 object-cover">
                        <span class="absolute top-2 right-2 bg-red-500 text-white text-[10px] px-2 py-px rounded">Flash</span>
                    </div>
                    <div class="p-3">
                        <p class="text-xs font-medium line-clamp-2">${product.name}</p>
                        <p class="text-red-500 font-bold mt-1">${product.price.toLocaleString('vi-VN')} ₫</p>
                    </div>
                </div>`;
                flashGrid.innerHTML += html;
            });
        }

        // Đếm ngược Flash Sale
        function startCountdown() {
            let time = 2*3600 + 45*60 + 12; // 2 giờ 45 phút 12 giây
            setInterval(() => {
                time--;
                const h = Math.floor(time / 3600);
                const m = Math.floor((time % 3600) / 60);
                const s = time % 60;
                document.getElementById('countdown').textContent = 
                    `${h.toString().padStart(2,'0')}:${m.toString().padStart(2,'0')}:${s.toString().padStart(2,'0')}`;
            }, 1000);
        }

        // Thêm vào giỏ hàng
        function addToCart(id) {
            const product = products.find(p => p.id === id);
            const existing = cart.find(item => item.id === id);
            if (existing) existing.quantity++;
            else cart.push({...product, quantity: 1});
            
            updateCartCount();
            showToast(`Đã thêm ${product.name} vào giỏ hàng`);
        }

        function updateCartCount() {
            const count = cart.reduce((sum, item) => sum + item.quantity, 0);
            document.getElementById('cart-count-top').textContent = count;
        }

        function toggleCart() {
            const modal = document.getElementById('cart-modal');
            const content = document.getElementById('cart-content');
            
            if (modal.classList.contains('hidden')) {
                modal.classList.remove('hidden');
                let html = '';
                let total = 0;
                
                cart.forEach((item, index) => {
                    total += item.price * item.quantity;
                    html += `
                    <div class="flex gap-4 mb-6">
                        <img src="${item.image}" class="w-20 h-20 object-cover rounded-xl">
                        <div class="flex-1">
                            <p class="font-medium text-sm">${item.name}</p>
                            <p class="text-[#0066FF] font-bold">${item.price.toLocaleString('vi-VN')} ₫</p>
                            <div class="flex justify-between mt-3">
                                <div class="flex border rounded-xl">
                                    <button onclick="changeQuantity(${index}, -1)" class="px-3">-</button>
                                    <span class="px-4">${item.quantity}</span>
                                    <button onclick="changeQuantity(${index}, 1)" class="px-3">+</button>
                                </div>
                                <button onclick="removeFromCart(${index})" class="text-red-500 text-sm">Xóa</button>
                            </div>
                        </div>
                    </div>`;
                });
                
                content.innerHTML = html || '<p class="text-center py-12 text-gray-400">Giỏ hàng trống</p>';
                document.getElementById('cart-total').textContent = total.toLocaleString('vi-VN') + ' ₫';
            } else {
                modal.classList.add('hidden');
            }
        }

        function changeQuantity(index, delta) {
            cart[index].quantity += delta;
            if (cart[index].quantity < 1) cart[index].quantity = 1;
            toggleCart();
            updateCartCount();
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            toggleCart();
            updateCartCount();
        }

        function checkout() {
            if (cart.length === 0) return;
            alert('🎉 Cảm ơn bạn đã đặt hàng tại IMEX!\nĐơn hàng của bạn đang được xử lý.');
            cart = [];
            toggleCart();
            updateCartCount();
        }

        // Toast
        function showToast(message) {
            const toast = document.createElement('div');
            toast.style.cssText = `position:fixed; bottom:90px; left:50%; transform:translateX(-50%); background:#0066FF; color:white; padding:12px 24px; border-radius:9999px; box-shadow:0 10px 15px -3px rgba(0,0,0,0.3); z-index:9999; white-space:nowrap;`;
            toast.textContent = message;
            document.body.appendChild(toast);
            setTimeout(() => toast.remove(), 2500);
        }

        // Các hàm điều hướng bottom nav
        function navigateTo(page) {
            if (page === 'cart') {
                toggleCart();
            } else if (page === 'search') {
                toggleSearch();
            } else {
                alert(`Bạn đang xem trang: ${page.toUpperCase()} (đang phát triển)`);
            }
        }

        function toggleSearch() {
            const keyword = prompt("🔍 Tìm kiếm sản phẩm:");
            if (keyword) {
                alert(`Kết quả tìm kiếm cho "${keyword}"\n\n(Trong phiên bản thực sẽ hiển thị danh sách sản phẩm)`);
            }
        }

        function showNotifications() {
            alert("🛎️ Thông báo:\n• Đơn hàng #IMX3921 đang giao\n• Flash Sale iPhone 17 chỉ còn 2 giờ");
        }

        function filterCategory(category) {
            alert(`Đang hiển thị danh mục: ${category === 'all' ? 'Tất cả' : category}`);
            // Có thể lọc sản phẩm theo category ở đây
        }

        // Khởi tạo trang
        window.onload = function() {
            renderProducts();
            renderFlashSale();
            startCountdown();
            updateCartCount();
            
            console.log('%cIMEX Mobile - Giao diện giống Lazada đã sẵn sàng!', 'color:#0066FF; font-size:16px;');
        };
    </script>
</body>
</html>
