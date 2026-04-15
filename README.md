<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEX - Nền tảng Thiết bị Di động</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;600;700&display=swap');
        
        .logo-font { font-family: 'Space Grotesk', sans-serif; }
        .hero-bg { background: linear-gradient(135deg, #0066FF 0%, #00A8FF 100%); }
        
        .product-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .product-card:hover {
            transform: translateY(-12px);
            box-shadow: 0 25px 50px -12px rgb(0 102 255 / 0.25);
        }
        
        .nav-link {
            position: relative;
        }
        .nav-link:after {
            content: '';
            position: absolute;
            width: 0;
            height: 3px;
            bottom: -4px;
            left: 0;
            background-color: #0066FF;
            transition: all 0.3s;
        }
        .nav-link:hover:after, .nav-link.active:after {
            width: 100%;
        }
    </style>
</head>
<body class="bg-gray-50">

<!-- NAVBAR -->
<nav class="bg-white border-b sticky top-0 z-50">
    <div class="max-w-screen-2xl mx-auto px-8 py-5">
        <div class="flex items-center justify-between">
            <!-- Logo -->
            <div class="flex items-center gap-3">
                <div class="w-12 h-12 bg-[#0066FF] rounded-3xl flex items-center justify-center text-4xl text-white shadow-inner">📱</div>
                <div>
                    <h1 class="logo-font text-4xl font-bold tracking-tighter text-[#0066FF]">IMEX</h1>
                    <p class="text-xs text-gray-500 -mt-1">Mobile Ecosystem</p>
                </div>
            </div>

            <!-- Menu -->
            <div class="hidden md:flex items-center gap-10 text-base font-medium">
                <a href="#" class="nav-link active text-gray-800">Trang chủ</a>
                <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Điện thoại</a>
                <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Máy tính bảng</a>
                <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Phụ kiện</a>
                <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">Đồng hồ</a>
                <a href="#" class="nav-link text-gray-700 hover:text-[#0066FF]">So sánh</a>
            </div>

            <!-- Right side -->
            <div class="flex items-center gap-6">
                <button onclick="toggleSearch()" class="flex items-center bg-gray-100 hover:bg-gray-200 px-6 py-3 rounded-3xl gap-3 text-gray-600">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <span class="hidden md:block">Tìm kiếm sản phẩm</span>
                </button>
                
                <button onclick="toggleCart()" class="relative text-2xl text-gray-700 hover:text-[#0066FF]">
                    <i class="fa-solid fa-bag-shopping"></i>
                    <span id="cart-count" class="absolute -top-2 -right-2 bg-red-500 text-white text-xs w-5 h-5 rounded-full flex items-center justify-center font-medium">0</span>
                </button>
                
                <div class="w-9 h-9 bg-[#0066FF] text-white rounded-2xl flex items-center justify-center font-semibold cursor-pointer">A</div>
            </div>
        </div>
    </div>
</nav>

<!-- HERO -->
<header class="hero-bg text-white py-24">
    <div class="max-w-screen-2xl mx-auto px-8 grid lg:grid-cols-2 gap-16 items-center">
        <div class="space-y-8">
            <div class="inline-flex items-center gap-2 bg-white/20 backdrop-blur-md px-6 py-3 rounded-3xl text-sm">
                <span class="relative flex h-3 w-3">
                    <span class="animate-ping absolute inline-flex h-full w-full rounded-full bg-green-400 opacity-75"></span>
                    <span class="relative inline-flex rounded-full h-3 w-3 bg-green-400"></span>
                </span>
                MỚI RA MẮT 2026
            </div>
            
            <h1 class="text-6xl lg:text-7xl font-bold leading-none tracking-tighter">
                Thiết bị di động<br>chính hãng • Trải nghiệm hoàn hảo
            </h1>
            
            <p class="text-xl text-white/90 max-w-md">
                Nền tảng thương mại điện tử chuyên sâu về điện thoại, máy tính bảng, đồng hồ và phụ kiện cao cấp.
            </p>
            
            <div class="flex gap-4">
                <button onclick="showProducts()" 
                        class="bg-white text-[#0066FF] px-10 py-6 rounded-3xl font-semibold text-lg flex items-center gap-3 hover:shadow-2xl">
                    Khám phá ngay
                </button>
                <button onclick="showCompare()" 
                        class="border-2 border-white/80 hover:border-white px-8 py-6 rounded-3xl font-semibold text-lg">
                    So sánh sản phẩm
                </button>
            </div>
        </div>
        
        <div class="flex justify-center">
            <img src="https://picsum.photos/id/1015/700/700" 
                 class="rounded-[4rem] shadow-2xl border-8 border-white/30" alt="iPhone 17 Pro">
        </div>
    </div>
</header>

<!-- SẢN PHẨM NỔI BẬT -->
<section class="max-w-screen-2xl mx-auto px-8 py-20">
    <div class="flex justify-between items-end mb-10">
        <h2 class="text-3xl font-semibold">Sản phẩm nổi bật</h2>
        <a href="#" onclick="showProducts()" class="text-[#0066FF] font-medium flex items-center gap-2">
            Xem tất cả <i class="fa-solid fa-arrow-right"></i>
        </a>
    </div>
    
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-8" id="product-grid"></div>
</section>

<!-- CART MODAL -->
<div id="cart-modal" class="hidden fixed inset-0 bg-black/70 z-[9999] flex items-center justify-center">
    <div class="bg-white w-full max-w-lg rounded-3xl max-h-[90vh] overflow-hidden">
        <div class="p-6 border-b flex justify-between items-center">
            <h3 class="text-2xl font-semibold">Giỏ hàng của bạn</h3>
            <button onclick="toggleCart()" class="text-3xl leading-none">×</button>
        </div>
        <div id="cart-items" class="p-6 overflow-auto" style="max-height: 55vh;"></div>
        <div class="p-6 border-t">
            <div class="flex justify-between text-xl mb-6">
                <span>Tổng tiền</span>
                <span id="cart-total" class="font-bold text-[#0066FF]">0 ₫</span>
            </div>
            <button onclick="checkout()" class="w-full py-6 bg-[#0066FF] text-white rounded-3xl text-xl font-semibold">
                Thanh toán ngay
            </button>
        </div>
    </div>
</div>

<script>
// Dữ liệu sản phẩm
const products = [
    {id:1, name:"iPhone 17 Pro Max 256GB", price:38990000, oldPrice:42990000, image:"https://picsum.photos/id/1015/400/400"},
    {id:2, name:"Samsung Galaxy S25 Ultra", price:32990000, oldPrice:35990000, image:"https://picsum.photos/id/1016/400/400"},
    {id:3, name:"iPad Air 6 2025", price:18990000, oldPrice:null, image:"https://picsum.photos/id/201/400/400"},
    {id:4, name:"Xiaomi 15 Pro", price:16990000, oldPrice:19990000, image:"https://picsum.photos/id/251/400/400"},
    {id:5, name:"Apple Watch Ultra 3", price:24990000, oldPrice:null, image:"https://picsum.photos/id/1005/400/400"}
];

let cart = [];

// Render sản phẩm
function renderProducts() {
    const grid = document.getElementById('product-grid');
    grid.innerHTML = '';
    
    products.forEach(p => {
        const discount = p.oldPrice ? Math.round(((p.oldPrice - p.price) / p.oldPrice) * 100) : 0;
        
        const html = `
        <div class="product-card bg-white rounded-3xl overflow-hidden border">
            <div class="relative">
                <img src="${p.image}" class="w-full h-64 object-cover">
                ${discount ? `<span class="absolute top-4 right-4 bg-red-500 text-white text-xs px-3 py-1 rounded-3xl">-${discount}%</span>` : ''}
            </div>
            <div class="p-6">
                <h5 class="font-semibold text-lg leading-tight">${p.name}</h5>
                <div class="mt-4">
                    <span class="text-2xl font-bold text-[#0066FF]">${p.price.toLocaleString('vi-VN')} ₫</span>
                    ${p.oldPrice ? `<span class="block text-sm line-through text-gray-400">${p.oldPrice.toLocaleString('vi-VN')} ₫</span>` : ''}
                </div>
                <button onclick="addToCart(${p.id}); event.stopImmediatePropagation()" 
                        class="mt-6 w-full py-4 bg-[#0066FF] text-white rounded-3xl font-medium">Thêm vào giỏ hàng</button>
            </div>
        </div>`;
        grid.innerHTML += html;
    });
}

// Cart functions
function addToCart(id) {
    const product = products.find(p => p.id === id);
    const existing = cart.find(item => item.id === id);
    if (existing) existing.quantity++;
    else cart.push({...product, quantity: 1});
    
    updateCartCount();
    showToast(`Đã thêm ${product.name} vào giỏ hàng`);
}

function updateCartCount() {
    const count = cart.reduce((sum, item) => sum + (item.quantity || 1), 0);
    document.getElementById('cart-count').textContent = count;
}

function toggleCart() {
    const modal = document.getElementById('cart-modal');
    const itemsContainer = document.getElementById('cart-items');
    
    if (modal.classList.contains('hidden')) {
        modal.classList.remove('hidden');
        let html = '';
        let total = 0;
        
        cart.forEach((item, index) => {
            const itemTotal = item.price * item.quantity;
            total += itemTotal;
            html += `
            <div class="flex gap-4 mb-6">
                <img src="${item.image}" class="w-24 h-24 object-cover rounded-2xl">
                <div class="flex-1">
                    <p class="font-medium">${item.name}</p>
                    <p class="text-[#0066FF] font-semibold">${item.price.toLocaleString('vi-VN')} ₫</p>
                    <div class="flex justify-between mt-4">
                        <div class="flex border rounded-3xl">
                            <button onclick="changeQty(${index}, -1)" class="px-4">-</button>
                            <span class="px-6">${item.quantity}</span>
                            <button onclick="changeQty(${index}, 1)" class="px-4">+</button>
                        </div>
                        <button onclick="removeFromCart(${index})" class="text-red-500">Xóa</button>
                    </div>
                </div>
            </div>`;
        });
        
        itemsContainer.innerHTML = html || '<p class="text-center py-16 text-gray-400">Giỏ hàng trống</p>';
        document.getElementById('cart-total').textContent = total.toLocaleString('vi-VN') + ' ₫';
    } else {
        modal.classList.add('hidden');
    }
}

function changeQty(index, delta) {
    cart[index].quantity = Math.max(1, cart[index].quantity + delta);
    toggleCart();
}

function removeFromCart(index) {
    cart.splice(index, 1);
    toggleCart();
    updateCartCount();
}

function checkout() {
    if (cart.length === 0) return;
    alert("✅ Thanh toán thành công!\nCảm ơn bạn đã mua sắm tại IMEX.");
    cart = [];
    toggleCart();
    updateCartCount();
}

function toggleSearch() {
    const query = prompt("🔍 Tìm kiếm sản phẩm trên IMEX:");
    if (query) alert(`Đang tìm kiếm: "${query}"\n(Kết quả sẽ hiển thị ở phiên bản đầy đủ)`);
}

function showToast(msg) {
    const toast = document.createElement('div');
    toast.style.cssText = 'position:fixed; bottom:30px; right:30px; background:#0066FF; color:white; padding:16px 28px; border-radius:9999px; box-shadow:0 10px 15px -3px rgb(0 102 255); z-index:99999;';
    toast.textContent = msg;
    document.body.appendChild(toast);
    setTimeout(() => toast.remove(), 2800);
}

function showProducts() {
    alert("Đang chuyển đến trang tất cả sản phẩm...");
}

function showCompare() {
    alert("Chức năng So sánh sản phẩm đang được phát triển...");
}

// Khởi tạo
window.onload = () => {
    renderProducts();
    updateCartCount();
    console.log('%cIMEX - Nền tảng Thương mại điện tử Thiết bị Di động đã sẵn sàng!', 'color:#0066FF; font-size:18px;');
};
</script>
</body>
</html>
