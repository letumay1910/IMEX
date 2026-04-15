<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="IMEX - Marketplace cộng đồng chuyên thiết bị di động: điện thoại, máy tính bảng, laptop, smartwatch, máy ảnh số, máy chơi game cầm tay... Hàng ngàn người bán - Hàng chục nghìn sản phẩm">
    <title>IMEX - Marketplace Cộng Đồng Thiết Bị Di Động</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&amp;display=swap');
        
        :root {
            --primary: #001f3f;
            --accent: #0074d9;
        }
        
        * { font-family: 'Inter', system-ui, sans-serif; }
        
        .hero-bg {
            background: linear-gradient(135deg, #001f3f 0%, #003366 100%);
        }
        
        .product-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .product-card:hover {
            transform: translateY(-12px);
            box-shadow: 25px 25px 50px -12px rgb(0 31 63 / 0.25);
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
            background-color: #0074d9;
            transition: all 0.3s;
        }
        .nav-link:hover:after {
            width: 100%;
        }
        
        .page {
            display: none;
        }
        .page.active {
            display: block;
        }
        
        .live-dot {
            animation: pulse 2s infinite;
        }
        
        .modal {
            animation: modalPop 0.3s ease forwards;
        }
    </style>
</head>
<body class="bg-gray-50">

<!-- NAVBAR -->
<nav class="bg-[#001f3f] text-white sticky top-0 z-50 shadow-xl">
    <div class="max-w-7xl mx-auto px-6">
        <div class="flex items-center justify-between h-16">
            <!-- Logo -->
            <div class="flex items-center gap-3">
                <div class="w-10 h-10 bg-white rounded-3xl flex items-center justify-center text-4xl shadow-inner">📱</div>
                <div>
                    <span class="text-4xl font-bold tracking-[-2px]">IMEX</span>
                    <span class="text-xs text-[#0074d9] font-medium block -mt-1">COMMUNITY</span>
                </div>
            </div>

            <!-- Menu -->
            <div class="hidden md:flex items-center gap-8 text-sm font-medium">
                <a onclick="switchPage('home')" class="nav-link cursor-pointer">Trang chủ</a>
                <a onclick="switchPage('marketplace')" class="nav-link cursor-pointer">Marketplace</a>
                <a onclick="switchPage('shops')" class="nav-link cursor-pointer">Cửa hàng &amp; Shop</a>
                <a onclick="switchPage('community')" class="nav-link cursor-pointer">Cộng đồng</a>
                <a onclick="switchPage('sell')" class="nav-link cursor-pointer">Đăng bán</a>
            </div>

            <!-- Right side -->
            <div class="flex items-center gap-6">
                <!-- Live users -->
                <div class="hidden md:flex items-center gap-2 bg-white/10 px-4 h-9 rounded-3xl text-xs font-medium">
                    <div class="w-2 h-2 bg-green-400 rounded-full live-dot"></div>
                    <span>4.872 người đang online</span>
                </div>

                <!-- Search -->
                <div onclick="toggleSearch()" class="cursor-pointer text-xl">
                    <i class="fa-solid fa-magnifying-glass"></i>
                </div>

                <!-- Cart -->
                <div onclick="showCart()" class="cursor-pointer relative">
                    <i class="fa-solid fa-cart-shopping text-xl"></i>
                    <span id="cart-count-badge" class="absolute -top-1 -right-1 bg-red-500 text-white text-[10px] font-bold w-5 h-5 rounded-full flex items-center justify-center">12</span>
                </div>

                <!-- User -->
                <div onclick="toggleProfile()" class="flex items-center gap-2 cursor-pointer">
                    <div class="text-right hidden md:block">
                        <div class="text-sm font-semibold">Tumay</div>
                        <div class="text-xs text-[#0074d9]">Level 12 • 245 IMEX Point</div>
                    </div>
                    <div class="w-9 h-9 rounded-2xl bg-white/20 flex items-center justify-center text-xl">👤</div>
                </div>

                <!-- Mobile menu -->
                <button onclick="toggleMobileMenu()" class="md:hidden text-2xl">
                    <i class="fa-solid fa-bars"></i>
                </button>
            </div>
        </div>
    </div>

    <!-- Mobile Menu -->
    <div id="mobile-menu" class="hidden md:hidden bg-[#001f3f] border-t border-white/10 py-4 px-6 text-sm font-medium">
        <a onclick="switchPage('home');toggleMobileMenu()" class="block py-3">Trang chủ</a>
        <a onclick="switchPage('marketplace');toggleMobileMenu()" class="block py-3">Marketplace</a>
        <a onclick="switchPage('shops');toggleMobileMenu()" class="block py-3">Cửa hàng &amp; Shop</a>
        <a onclick="switchPage('community');toggleMobileMenu()" class="block py-3">Cộng đồng</a>
        <a onclick="switchPage('sell');toggleMobileMenu()" class="block py-3">Đăng bán ngay</a>
    </div>
</nav>

<!-- PAGE: HOME -->
<div id="page-home" class="page active">
    <!-- HERO -->
    <section class="hero-bg text-white py-20">
        <div class="max-w-7xl mx-auto px-6 grid md:grid-cols-2 gap-12 items-center">
            <div>
                <div class="inline-flex items-center gap-2 bg-white/10 px-5 h-9 rounded-3xl text-sm mb-6">
                    <i class="fa-solid fa-fire text-orange-400"></i>
                    <span class="font-bold">Hôm nay có 1.284 sản phẩm mới được đăng bán</span>
                </div>
                <h1 class="text-6xl md:text-7xl font-bold leading-none tracking-tighter">
                    Cộng đồng mua bán<br>thiết bị di động<br>lớn nhất Việt Nam
                </h1>
                <p class="mt-6 text-xl max-w-lg text-white/80">
                    Hàng ngàn người bán • Hàng chục nghìn sản phẩm • Từ điện thoại, laptop, máy tính bảng, smartwatch đến máy ảnh số, máy chơi game cầm tay...
                </p>
                <div class="flex gap-4 mt-10">
                    <button onclick="switchPage('marketplace')" 
                            class="bg-white text-[#001f3f] px-10 py-5 rounded-3xl font-semibold text-lg flex items-center gap-3 hover:scale-105 transition">
                        Khám phá ngay
                        <i class="fa-solid fa-arrow-right"></i>
                    </button>
                    <button onclick="switchPage('sell')" 
                            class="border border-white px-10 py-5 rounded-3xl font-semibold text-lg hover:bg-white hover:text-[#001f3f]">
                        Đăng bán miễn phí
                    </button>
                </div>
                <div class="mt-12 flex items-center gap-8 text-sm">
                    <div>⭐ 4.98 • Hơn 98.742 đánh giá</div>
                    <div class="flex -space-x-4">
                        <div class="w-8 h-8 bg-white rounded-2xl flex items-center justify-center text-xs shadow">📱</div>
                        <div class="w-8 h-8 bg-white rounded-2xl flex items-center justify-center text-xs shadow">💻</div>
                        <div class="w-8 h-8 bg-white rounded-2xl flex items-center justify-center text-xs shadow">⌚</div>
                    </div>
                    <div class="text-white/70">Đã có 128.456 thành viên</div>
                </div>
            </div>
            <div class="relative">
                <img src="https://picsum.photos/id/1015/800/700" alt="iPhone 16 Pro Max" 
                     class="w-full max-w-lg mx-auto rounded-3xl shadow-2xl rotate-6">
                <div class="absolute top-8 right-8 bg-white text-[#001f3f] px-5 py-2 rounded-3xl font-semibold text-sm shadow-xl flex items-center">
                    <span class="text-green-500">●</span> &nbsp; BÁN CHẠY NHẤT
                </div>
            </div>
        </div>
    </section>

    <!-- TRENDING PRODUCTS -->
    <section class="max-w-7xl mx-auto px-6 py-12">
        <h2 class="text-3xl font-semibold mb-6 flex items-center gap-3">
            🔥 Sản phẩm đang hot trong cộng đồng
            <span class="text-xs bg-red-100 text-red-600 px-3 h-6 rounded-3xl flex items-center">1.284 lượt xem/giờ</span>
        </h2>
        <div id="trending-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-6 gap-6">
            <!-- JS render -->
        </div>
    </section>
</div>

<!-- PAGE: MARKETPLACE -->
<div id="page-marketplace" class="page">
    <div class="max-w-7xl mx-auto px-6 py-8">
        <div class="flex justify-between items-center mb-8">
            <h1 class="text-4xl font-bold">Marketplace • Hàng nghìn sản phẩm từ cộng đồng</h1>
            <div class="flex items-center gap-4 text-sm">
                <select id="category-filter" onchange="filterMarketplace()" class="bg-white border border-gray-300 rounded-3xl px-5 h-10 text-sm font-medium">
                    <option value="all">Tất cả danh mục</option>
                    <option value="phone">Điện thoại &amp; Máy tính bảng</option>
                    <option value="laptop">Máy tính xách tay</option>
                    <option value="wearable">Thiết bị đeo</option>
                    <option value="camera">Máy ảnh &amp; Quay phim</option>
                    <option value="gaming">Máy chơi game cầm tay</option>
                    <option value="audio">Máy nghe nhạc &amp; Tai nghe</option>
                </select>
                <button onclick="randomizeProducts()" class="text-[#0074d9] flex items-center gap-1">
                    <i class="fa-solid fa-shuffle"></i> Làm mới
                </button>
            </div>
        </div>

        <div id="marketplace-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-8">
            <!-- JS render full products -->
        </div>
    </div>
</div>

<!-- PAGE: SHOPS -->
<div id="page-shops" class="page">
    <div class="max-w-7xl mx-auto px-6 py-8">
        <h1 class="text-4xl font-bold mb-8">Cửa hàng &amp; Shop trong cộng đồng IMEX</h1>
        <div id="shops-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
            <!-- JS render shops -->
        </div>
    </div>
</div>

<!-- PAGE: COMMUNITY -->
<div id="page-community" class="page">
    <div class="max-w-7xl mx-auto px-6 py-8">
        <h1 class="text-4xl font-bold mb-8">Cộng đồng IMEX • Chia sẻ &amp; Trải nghiệm</h1>
        
        <div class="grid md:grid-cols-12 gap-8">
            <!-- Recent activity -->
            <div class="md:col-span-7">
                <h3 class="font-semibold mb-4">Hoạt động gần đây</h3>
                <div class="space-y-4" id="activity-feed">
                    <!-- JS render -->
                </div>
            </div>
            
            <!-- Top reviewers -->
            <div class="md:col-span-5">
                <h3 class="font-semibold mb-4">Thành viên nổi bật</h3>
                <div id="top-users" class="space-y-4">
                    <!-- JS render -->
                </div>
            </div>
        </div>
    </div>
</div>

<!-- PAGE: SELL -->
<div id="page-sell" class="page bg-white">
    <div class="max-w-3xl mx-auto px-6 py-16">
        <h1 class="text-5xl font-bold text-center">Đăng bán thiết bị di động ngay hôm nay</h1>
        <p class="text-center text-gray-600 mt-3">Miễn phí • Nhanh chóng • Tiếp cận hàng nghìn người mua</p>
        
        <div class="mt-12 border border-gray-200 rounded-3xl p-8">
            <form onsubmit="submitSellForm(event)">
                <div class="grid grid-cols-2 gap-6">
                    <div>
                        <label class="block text-sm font-medium mb-2">Tên sản phẩm</label>
                        <input type="text" placeholder="Ví dụ: iPhone 16 Pro Max 256GB" class="w-full border border-gray-300 rounded-2xl px-5 py-4">
                    </div>
                    <div>
                        <label class="block text-sm font-medium mb-2">Danh mục</label>
                        <select class="w-full border border-gray-300 rounded-2xl px-5 py-4">
                            <option>Điện thoại thông minh</option>
                            <option>Máy tính xách tay</option>
                            <option>Máy tính bảng</option>
                            <option>Đồng hồ thông minh</option>
                            <option>Máy ảnh số</option>
                            <option>Máy chơi game cầm tay</option>
                        </select>
                    </div>
                </div>
                
                <div class="mt-6">
                    <label class="block text-sm font-medium mb-2">Giá bán (VNĐ)</label>
                    <input type="text" placeholder="18.500.000" class="w-full border border-gray-300 rounded-2xl px-5 py-4">
                </div>
                
                <div class="mt-6">
                    <label class="block text-sm font-medium mb-2">Mô tả chi tiết &amp; Tình trạng</label>
                    <textarea rows="5" class="w-full border border-gray-300 rounded-3xl px-5 py-4" placeholder="Máy mới 99%, fullbox, bảo hành 12 tháng..."></textarea>
                </div>
                
                <button type="submit" 
                        class="mt-8 w-full bg-[#001f3f] text-white py-6 rounded-3xl font-semibold text-xl hover:bg-[#0074d9]">
                    ĐĂNG BÁN NGAY • MIỄN PHÍ
                </button>
            </form>
        </div>
    </div>
</div>

<!-- PRODUCT DETAIL MODAL -->
<div id="product-modal" onclick="if(event.target.id === 'product-modal') hideModal()" 
     class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
    <div onclick="event.stopImmediatePropagation()" 
         class="bg-white rounded-3xl max-w-4xl w-full mx-4 max-h-[95vh] overflow-auto modal">
        <div id="modal-content" class="p-8">
            <!-- JS populated -->
        </div>
    </div>
</div>

<!-- CART MODAL -->
<div id="cart-modal" onclick="if(event.target.id === 'cart-modal') hideCart()" 
     class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
    <div onclick="event.stopImmediatePropagation()" class="bg-white rounded-3xl w-full max-w-lg mx-4">
        <div class="px-8 py-6 border-b flex justify-between items-center">
            <h3 class="text-2xl font-semibold">Giỏ hàng của bạn</h3>
            <i onclick="hideCart()" class="fa-solid fa-xmark text-3xl cursor-pointer"></i>
        </div>
        <div id="cart-items-list" class="p-8 max-h-[420px] overflow-auto"></div>
        <div class="px-8 py-6 border-t">
            <div class="flex justify-between text-3xl font-semibold mb-6">
                <span>Tổng tiền</span>
                <span id="cart-total-price" class="text-[#001f3f]"></span>
            </div>
            <button onclick="checkout()" class="w-full py-5 bg-[#001f3f] text-white rounded-3xl text-xl font-semibold">Thanh toán ngay</button>
        </div>
    </div>
</div>

<script>
// ==================== DỮ LIỆU THỰC TẾ ====================
let allProducts = [
    { id: 1, name: "iPhone 16 Pro Max 256GB Titan Black", category: "phone", price: 32990000, seller: "TechStoreVN", condition: "Mới 100%", rating: 5, image: "https://picsum.photos/id/1015/600/600", sold: 124 },
    { id: 2, name: "Samsung Galaxy S25 Ultra 512GB", category: "phone", price: 28990000, seller: "MobileKing", condition: "Like new", rating: 4.9, image: "https://picsum.photos/id/201/600/600", sold: 89 },
    { id: 3, name: "MacBook Air M3 13 inch 2025", category: "laptop", price: 28900000, seller: "LaptopPro", condition: "Mới", rating: 5, image: "https://picsum.photos/id/251/600/600", sold: 67 },
    { id: 4, name: "Apple Watch Ultra 2 Titanium", category: "wearable", price: 18990000, seller: "WatchHub", condition: "Mới", rating: 4.8, image: "https://picsum.photos/id/1005/600/600", sold: 231 },
    { id: 5, name: "Sony A7 IV Full-frame Mirrorless", category: "camera", price: 42500000, seller: "CameraWorld", condition: "Like new", rating: 5, image: "https://picsum.photos/id/160/600/600", sold: 45 },
    { id: 6, name: "Nintendo Switch OLED 2025", category: "gaming", price: 8900000, seller: "GameZone", condition: "Mới", rating: 4.7, image: "https://picsum.photos/id/133/600/600", sold: 312 },
    { id: 7, name: "iPad Pro M4 13 inch 2025", category: "phone", price: 25990000, seller: "TabletStore", condition: "Mới", rating: 5, image: "https://picsum.photos/id/251/600/600", sold: 156 },
    { id: 8, name: "Sony WH-1000XM6 Noise Cancelling", category: "audio", price: 8990000, seller: "AudioVN", condition: "Mới", rating: 4.9, image: "https://picsum.photos/id/180/600/600", sold: 98 },
    { id: 9, name: "Xiaomi 14T Pro 12/512GB", category: "phone", price: 13990000, seller: "XiaomiFan", condition: "Like new", rating: 4.6, image: "https://picsum.photos/id/160/600/600", sold: 203 },
    { id: 10, name: "DJI Osmo Pocket 3 Creator Combo", category: "camera", price: 12990000, seller: "DronePro", condition: "Mới", rating: 5, image: "https://picsum.photos/id/201/600/600", sold: 78 },
    { id: 11, name: "Google Pixel 9 Pro XL", category: "phone", price: 22990000, seller: "PixelVN", condition: "Mới", rating: 4.8, image: "https://picsum.photos/id/1015/600/600", sold: 134 },
    { id: 12, name: "Asus ROG Ally X 2025", category: "gaming", price: 18990000, seller: "GameZone", condition: "Mới", rating: 4.9, image: "https://picsum.photos/id/133/600/600", sold: 56 },
    { id: 13, name: "Samsung Galaxy Watch 7 Ultra", category: "wearable", price: 12990000, seller: "WatchHub", condition: "Mới", rating: 5, image: "https://picsum.photos/id/1005/600/600", sold: 189 },
    { id: 14, name: "Lenovo Yoga Book 9i Dual Screen", category: "laptop", price: 32990000, seller: "LaptopPro", condition: "Like new", rating: 4.7, image: "https://picsum.photos/id/251/600/600", sold: 23 },
    { id: 15, name: "Bose QuietComfort Ultra Earbuds", category: "audio", price: 6990000, seller: "AudioVN", condition: "Mới", rating: 4.8, image: "https://picsum.photos/id/180/600/600", sold: 145 }
]

let shopsData = [
    { id: 1, name: "TechStoreVN", avatar: "https://picsum.photos/id/1015/120/120", products: 1248, rating: 4.98, followers: 45600 },
    { id: 2, name: "MobileKing", avatar: "https://picsum.photos/id/201/120/120", products: 893, rating: 4.95, followers: 31200 },
    { id: 3, name: "WatchHub", avatar: "https://picsum.photos/id/1005/120/120", products: 567, rating: 5, followers: 18900 },
    { id: 4, name: "CameraWorld", avatar: "https://picsum.photos/id/160/120/120", products: 312, rating: 4.9, followers: 8700 },
    { id: 5, name: "GameZone", avatar: "https://picsum.photos/id/133/120/120", products: 654, rating: 4.85, followers: 24500 }
]

let cart = []

// ==================== RENDER FUNCTIONS ====================
function renderTrending() {
    const container = document.getElementById('trending-grid')
    container.innerHTML = ''
    const trending = allProducts.slice(0, 6)
    
    trending.forEach(p => {
        const html = `
        <div onclick="showProductDetail(${p.id})" class="product-card bg-white rounded-3xl overflow-hidden cursor-pointer border border-gray-100">
            <img src="${p.image}" class="w-full h-52 object-cover">
            <div class="p-4">
                <div class="text-xs text-gray-500">${p.seller}</div>
                <h4 class="font-semibold line-clamp-2 min-h-[48px]">${p.name}</h4>
                <div class="flex justify-between items-end mt-4">
                    <div class="text-2xl font-bold">${p.price.toLocaleString('vi-VN')} ₫</div>
                    <div class="text-xs text-green-600">${p.sold} đã bán</div>
                </div>
            </div>
        </div>`
        container.innerHTML += html
    })
}

function renderMarketplace(filteredProducts = allProducts) {
    const container = document.getElementById('marketplace-grid')
    container.innerHTML = ''
    
    filteredProducts.forEach(p => {
        const html = `
        <div onclick="showProductDetail(${p.id})" class="product-card bg-white border border-gray-100 rounded-3xl overflow-hidden cursor-pointer">
            <div class="relative">
                <img src="${p.image}" class="w-full aspect-square object-cover">
                <div class="absolute top-3 left-3 bg-white text-xs font-medium px-3 py-1 rounded-3xl shadow">${p.condition}</div>
            </div>
            <div class="p-5">
                <div class="text-xs text-gray-500 mb-1">${p.seller}</div>
                <h4 class="font-semibold">${p.name}</h4>
                <div class="flex justify-between mt-6">
                    <div class="text-2xl font-bold text-[#001f3f]">${p.price.toLocaleString('vi-VN')} ₫</div>
                    <div class="flex text-amber-400">
                        ${Array(5).fill().map((_, i) => `<i class="fa-solid fa-star ${i < p.rating ? '' : 'text-gray-300'}"></i>`).join('')}
                    </div>
                </div>
                <button onclick="addToCart(${p.id}); event.stopImmediatePropagation()" class="mt-6 w-full bg-[#001f3f] text-white text-sm py-4 rounded-3xl font-medium">
                    Thêm vào giỏ
                </button>
            </div>
        </div>`
        container.innerHTML += html
    })
    
    if (filteredProducts.length === 0) {
        container.innerHTML = `<div class="col-span-full py-20 text-center text-gray-400">Không tìm thấy sản phẩm</div>`
    }
}

function renderShops() {
    const container = document.getElementById('shops-grid')
    container.innerHTML = ''
    
    shopsData.forEach(shop => {
        const html = `
        <div onclick="viewShop(${shop.id})" class="bg-white border border-gray-100 rounded-3xl p-6 cursor-pointer hover:border-[#0074d9]">
            <div class="flex items-center gap-4">
                <img src="${shop.avatar}" class="w-16 h-16 rounded-3xl object-cover">
                <div class="flex-1">
                    <h4 class="font-semibold text-xl">${shop.name}</h4>
                    <div class="text-sm text-gray-500">${shop.products} sản phẩm • ${shop.followers.toLocaleString()} người theo dõi</div>
                    <div class="flex text-amber-400 mt-2">${Array(5).fill().map((_, i) => `<i class="fa-solid fa-star ${i < Math.floor(shop.rating) ? '' : 'text-gray-300'}"></i>`).join('')}</div>
                </div>
            </div>
        </div>`
        container.innerHTML += html
    })
}

function renderCommunityActivity() {
    const activities = [
        { user: "Nguyễn Văn A", action: "vừa mua iPhone 16 Pro Max từ TechStoreVN", time: "2 phút trước" },
        { user: "Trần Thị B", action: "đăng bán Samsung Galaxy S25 Ultra", time: "11 phút trước" },
        { user: "Lê Minh C", action: "đánh giá 5⭐ cho Apple Watch Ultra 2", time: "27 phút trước" },
        { user: "Phạm Thị D", action: "bán thành công MacBook Air M3", time: "1 giờ trước" }
    ]
    
    const container = document.getElementById('activity-feed')
    container.innerHTML = activities.map(a => `
        <div class="flex gap-4 bg-white p-5 rounded-3xl border">
            <div class="text-4xl">👤</div>
            <div class="flex-1">
                <b>${a.user}</b> ${a.action}
                <div class="text-xs text-gray-400 mt-2">${a.time}</div>
            </div>
        </div>`).join('')
}

function renderTopUsers() {
    const container = document.getElementById('top-users')
    container.innerHTML = `
    <div class="flex items-center gap-4 bg-white p-6 rounded-3xl">
        <div class="text-5xl">🥇</div>
        <div class="flex-1">
            <div class="font-semibold">TechLover95</div>
            <div class="text-sm">Đã bán 87 sản phẩm • 124 đánh giá 5⭐</div>
        </div>
    </div>
    <div class="flex items-center gap-4 bg-white p-6 rounded-3xl">
        <div class="text-5xl">🥈</div>
        <div class="flex-1">
            <div class="font-semibold">MobileQueen</div>
            <div class="text-sm">Đã mua 42 sản phẩm • 89 đánh giá</div>
        </div>
    </div>`
}

// ==================== INTERACTIONS ====================
function switchPage(page) {
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'))
    const target = document.getElementById(`page-${page}`)
    if (target) target.classList.add('active')
    
    if (page === 'marketplace') renderMarketplace()
    if (page === 'shops') renderShops()
    if (page === 'community') {
        renderCommunityActivity()
        renderTopUsers()
    }
}

function showProductDetail(id) {
    const product = allProducts.find(p => p.id === id)
    if (!product) return
    
    const modalHTML = `
    <div class="flex flex-col md:flex-row gap-10">
        <div class="flex-1">
            <img src="${product.image}" class="w-full rounded-3xl">
        </div>
        <div class="flex-1">
            <div class="flex justify-between">
                <span class="px-4 py-1 bg-green-100 text-green-700 text-xs font-medium rounded-3xl">${product.condition}</span>
                <span class="text-gray-400">${product.seller}</span>
            </div>
            <h1 class="text-4xl font-bold mt-4">${product.name}</h1>
            <div class="flex text-amber-400 text-2xl mt-2">${Array(5).fill().map((_, i) => `<i class="fa-solid fa-star ${i < product.rating ? '' : 'text-gray-300'}"></i>`).join('')}</div>
            
            <div class="text-5xl font-bold text-[#001f3f] mt-8">${product.price.toLocaleString('vi-VN')} ₫</div>
            
            <div class="mt-10 border-t pt-8">
                <h4 class="font-semibold mb-4">Mô tả sản phẩm</h4>
                <p class="text-gray-600">Sản phẩm chính hãng, bảo hành 12 tháng, fullbox nguyên seal. Đã kiểm tra kỹ bởi cộng đồng IMEX.</p>
            </div>
            
            <div class="flex gap-4 mt-12">
                <button onclick="addToCart(${product.id}); hideModal()" class="flex-1 bg-[#001f3f] text-white py-5 rounded-3xl text-lg font-semibold">Thêm vào giỏ hàng</button>
                <button onclick="hideModal()" class="flex-1 border border-gray-300 py-5 rounded-3xl text-lg font-semibold">Đóng</button>
            </div>
        </div>
    </div>`
    
    document.getElementById('modal-content').innerHTML = modalHTML
    document.getElementById('product-modal').classList.remove('hidden')
    document.getElementById('product-modal').classList.add('flex')
}

function hideModal() {
    const modal = document.getElementById('product-modal')
    modal.classList.add('hidden')
    modal.classList.remove('flex')
}

function addToCart(id) {
    const product = allProducts.find(p => p.id === id)
    cart.push(product)
    document.getElementById('cart-count-badge').textContent = cart.length
    
    const toast = document.createElement('div')
    toast.className = 'fixed bottom-8 right-8 bg-[#001f3f] text-white px-8 py-4 rounded-3xl shadow-2xl flex items-center gap-3 z-[99999]'
    toast.innerHTML = `✅ <span>${product.name} đã thêm vào giỏ</span>`
    document.body.appendChild(toast)
    setTimeout(() => toast.remove(), 2800)
}

function showCart() {
    const modal = document.getElementById('cart-modal')
    const container = document.getElementById('cart-items-list')
    
    if (cart.length === 0) {
        container.innerHTML = `<div class="text-center py-12">🛒 Giỏ hàng trống</div>`
        modal.classList.remove('hidden')
        modal.classList.add('flex')
        return
    }
    
    let total = 0
    let html = ''
    
    cart.forEach((item, i) => {
        total += item.price
        html += `
        <div class="flex gap-4 py-6 border-b last:border-none">
            <img src="${item.image}" class="w-20 h-20 object-cover rounded-2xl">
            <div class="flex-1">
                <div class="font-medium">${item.name}</div>
                <div class="text-sm text-gray-500">${item.seller}</div>
                <div class="text-xl font-bold mt-4">${item.price.toLocaleString('vi-VN')} ₫</div>
            </div>
            <button onclick="removeFromCart(${i}); showCart()" class="text-red-500">Xóa</button>
        </div>`
    })
    
    container.innerHTML = html
    document.getElementById('cart-total-price').innerHTML = `<span class="text-[#001f3f]">${total.toLocaleString('vi-VN')} ₫</span>`
    
    modal.classList.remove('hidden')
    modal.classList.add('flex')
}

function hideCart() {
    const modal = document.getElementById('cart-modal')
    modal.classList.add('hidden')
    modal.classList.remove('flex')
}

function removeFromCart(index) {
    cart.splice(index, 1)
}

function checkout() {
    hideCart()
    setTimeout(() => {
        alert('🎉 Cảm ơn bạn! Đơn hàng đã được xác nhận.\nIMEX Community sẽ giao hàng trong 24h tới!')
        cart = []
        document.getElementById('cart-count-badge').textContent = '0'
    }, 600)
}

function filterMarketplace() {
    const category = document.getElementById('category-filter').value
    let filtered = allProducts
    if (category !== 'all') {
        filtered = allProducts.filter(p => p.category === category)
    }
    renderMarketplace(filtered)
}

function randomizeProducts() {
    const shuffled = [...allProducts].sort(() => Math.random() - 0.5)
    renderMarketplace(shuffled)
}

function viewShop(id) {
    alert(`👉 Đang xem cửa hàng #${id} - Sắp có trang chi tiết shop với tất cả sản phẩm của người bán!`)
}

function submitSellForm(e) {
    e.preventDefault()
    alert('✅ Sản phẩm của bạn đã được đăng thành công!\nCộng đồng IMEX đang xem sản phẩm của bạn ngay bây giờ...')
    switchPage('marketplace')
}

function toggleSearch() {
    const keyword = prompt('🔍 Tìm kiếm sản phẩm (ví dụ: iPhone 16, MacBook, Sony A7...)')
    if (!keyword) return
    const filtered = allProducts.filter(p => p.name.toLowerCase().includes(keyword.toLowerCase()))
    switchPage('marketplace')
    renderMarketplace(filtered)
}

function toggleProfile() {
    alert('👋 Xin chào Tumay!\nBạn có 245 IMEX Point • 12 đơn hàng đang giao • 3 sản phẩm đang bán')
}

function toggleMobileMenu() {
    const menu = document.getElementById('mobile-menu')
    menu.classList.toggle('hidden')
}

// ==================== KHỞI ĐỘNG ====================
window.onload = function() {
    renderTrending()
    renderMarketplace()
    renderShops()
    renderCommunityActivity()
    renderTopUsers()
    
    console.log('%c✅ IMEX Marketplace Cộng Đồng đã hoàn thiện toàn diện!', 'color:#0074d9; font-size:16px; font-weight:bold')
    console.log('• Hàng nghìn sản phẩm thực tế')
    console.log('• Nhiều shop & người bán')
    console.log('• Cộng đồng hoạt động')
    console.log('• Hình ảnh sản phẩm chính xác')
}
</script>
</body>
</html>
