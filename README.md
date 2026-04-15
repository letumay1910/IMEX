<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEX - Nền tảng Thiết bị Di động</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Space+Grotesk:wght@500;600;700&display=swap');
        .logo-font { font-family: 'Space Grotesk', sans-serif; }
        .product-card:hover { transform: translateY(-10px); box-shadow: 0 20px 25px -5px rgb(0 102 255 / 0.15); }
        .spec-row:hover { background-color: #f0f7ff; }
        .compare-table td, .compare-table th { padding: 14px 12px; border-bottom: 1px solid #e5e7eb; }
    </style>
</head>
<body class="bg-gray-50 text-gray-900">

<!-- NAVBAR -->
<nav class="bg-white shadow sticky top-0 z-50">
    <div class="max-w-screen-2xl mx-auto px-8 py-5 flex items-center justify-between">
        <div class="flex items-center gap-3">
            <div class="w-11 h-11 bg-[#0066FF] rounded-3xl flex items-center justify-center text-white text-4xl">📱</div>
            <h1 class="logo-font text-4xl font-bold tracking-tighter text-[#0066FF]">IMEX</h1>
        </div>
        
        <div class="hidden lg:flex gap-8 font-medium">
            <a href="#" class="hover:text-[#0066FF]">Trang chủ</a>
            <a href="#" onclick="showProducts()" class="hover:text-[#0066FF]">Sản phẩm</a>
            <a href="#" onclick="showCompare()" class="hover:text-[#0066FF]">So sánh</a>
            <a href="#" onclick="showCommunity()" class="hover:text-[#0066FF]">Cộng đồng</a>
            <a href="#" onclick="showWarranty()" class="hover:text-[#0066FF]">Bảo hành</a>
        </div>
        
        <div class="flex items-center gap-6">
            <button onclick="toggleSearch()" class="text-2xl"><i class="fa-solid fa-magnifying-glass"></i></button>
            <button onclick="toggleWishlist()" class="relative text-2xl"><i class="fa-solid fa-heart"></i><span id="wishlist-count" class="absolute -top-1 -right-1 bg-red-500 text-white text-xs w-5 h-5 rounded-full flex items-center justify-center">0</span></button>
            <button onclick="toggleCart()" class="relative text-2xl"><i class="fa-solid fa-bag-shopping"></i><span id="cart-count" class="absolute -top-1 -right-1 bg-red-500 text-white text-xs w-5 h-5 rounded-full flex items-center justify-center">0</span></button>
            <button onclick="showAccount()" class="flex items-center gap-2">
                <div class="w-8 h-8 bg-[#0066FF] text-white rounded-2xl flex items-center justify-center">A</div>
            </button>
        </div>
    </div>
</nav>

<!-- HERO -->
<header class="hero-bg text-white py-20">
    <div class="max-w-screen-2xl mx-auto px-8 grid lg:grid-cols-2 gap-12 items-center">
        <div>
            <h2 class="text-6xl font-bold leading-none">Hệ sinh thái thiết bị di động<br>toàn diện nhất Việt Nam</h2>
            <p class="mt-6 text-xl">Tìm kiếm • So sánh • Mua hàng • Bảo hành • Cộng đồng</p>
            <div class="mt-10 flex gap-4">
                <button onclick="showProducts()" class="bg-white text-[#0066FF] px-10 py-5 rounded-3xl font-semibold">Khám phá sản phẩm</button>
                <button onclick="showCompare()" class="border-2 border-white px-10 py-5 rounded-3xl font-semibold">So sánh ngay</button>
            </div>
        </div>
        <img src="https://picsum.photos/id/1015/800/600" class="rounded-3xl shadow-2xl" alt="IMEX Hero">
    </div>
</header>

<!-- PRODUCT SECTION -->
<section id="products-section" class="max-w-screen-2xl mx-auto px-8 py-16">
    <h3 class="text-3xl font-semibold mb-8">Sản phẩm nổi bật</h3>
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8" id="product-grid"></div>
</section>

<!-- COMPARE SECTION -->
<section id="compare-section" class="hidden max-w-screen-2xl mx-auto px-8 py-16 bg-white">
    <h3 class="text-3xl font-semibold mb-6 flex items-center gap-3">
        <i class="fa-solid fa-scale-balanced"></i> So sánh thiết bị
    </h3>
    <div class="flex gap-4 mb-8">
        <select id="compare-select" class="border rounded-3xl px-6 py-3" onchange="addToCompare()">
            <option value="">Chọn sản phẩm để so sánh...</option>
        </select>
        <button onclick="clearCompare()" class="text-red-500">Xóa tất cả</button>
    </div>
    <div class="overflow-x-auto">
        <table id="compare-table" class="compare-table min-w-full bg-white border-collapse"></table>
    </div>
</section>

<!-- WARRANTY SECTION -->
<section id="warranty-section" class="hidden max-w-screen-2xl mx-auto px-8 py-16">
    <h3 class="text-3xl font-semibold mb-8">Bảo hành điện tử</h3>
    <div class="bg-white rounded-3xl p-10 max-w-2xl mx-auto">
        <input id="warranty-code" type="text" placeholder="Nhập mã IMEI / Số serial" class="w-full border rounded-3xl px-8 py-6 text-lg">
        <button onclick="checkWarranty()" class="mt-6 w-full bg-[#0066FF] text-white py-6 rounded-3xl font-semibold">Tra cứu bảo hành</button>
        <div id="warranty-result" class="mt-8"></div>
    </div>
</section>

<!-- COMMUNITY SECTION -->
<section id="community-section" class="hidden max-w-screen-2xl mx-auto px-8 py-16 bg-gray-50">
    <h3 class="text-3xl font-semibold mb-8">Cộng đồng IMEX</h3>
    <div class="grid md:grid-cols-2 gap-8">
        <div class="bg-white rounded-3xl p-8">
            <h4 class="font-semibold mb-4">Đánh giá sản phẩm</h4>
            <div id="reviews-list" class="space-y-6"></div>
        </div>
        <div class="bg-white rounded-3xl p-8">
            <h4 class="font-semibold mb-4">Thảo luận mới nhất</h4>
            <div class="space-y-4 text-sm">
                <div class="border-l-4 border-[#0066FF] pl-4">"iPhone 17 Pro Max có đáng nâng cấp từ 16 không?"</div>
                <div class="border-l-4 border-[#0066FF] pl-4">"So sánh pin Galaxy S25 Ultra và Xiaomi 15 Pro"</div>
            </div>
            <button onclick="postReview()" class="mt-8 w-full py-4 border border-[#0066FF] text-[#0066FF] rounded-3xl">Đăng bài thảo luận</button>
        </div>
    </div>
</section>

<!-- CART MODAL -->
<div id="cart-modal" class="hidden fixed inset-0 bg-black/60 flex items-center justify-center z-[100]">
    <div class="bg-white w-full max-w-lg rounded-3xl max-h-[90vh] overflow-hidden">
        <div class="p-6 border-b flex justify-between">
            <h3 class="text-2xl font-semibold">Giỏ hàng</h3>
            <button onclick="toggleCart()" class="text-3xl">✕</button>
        </div>
        <div id="cart-items" class="p-6 overflow-auto" style="max-height: 60vh;"></div>
        <div class="p-6 border-t">
            <div class="flex justify-between text-xl mb-6">
                <span>Tổng cộng</span>
                <span id="cart-total" class="font-bold">0 ₫</span>
            </div>
            <button onclick="checkout()" class="w-full py-6 bg-[#0066FF] text-white rounded-3xl text-xl font-semibold">Thanh toán ngay</button>
        </div>
    </div>
</div>

<script>
// Dữ liệu sản phẩm mẫu (có thông số kỹ thuật chi tiết)
const products = [
    {
        id: 1,
        name: "iPhone 17 Pro Max",
        brand: "Apple",
        price: 38990000,
        image: "https://picsum.photos/id/1015/400/400",
        specs: { "Màn hình": "6.9 inch Super Retina XDR", "Chip": "A19 Pro", "RAM": "12GB", "Bộ nhớ": "256GB", "Pin": "4800mAh", "Camera": "48MP Chính" },
        rating: 4.9
    },
    {
        id: 2,
        name: "Samsung Galaxy S25 Ultra",
        brand: "Samsung",
        price: 32990000,
        image: "https://picsum.photos/id/1016/400/400",
        specs: { "Màn hình": "6.8 inch Dynamic AMOLED 2X", "Chip": "Snapdragon 8 Elite", "RAM": "16GB", "Bộ nhớ": "512GB", "Pin": "5000mAh", "Camera": "200MP Chính" },
        rating: 4.8
    },
    {
        id: 3,
        name: "Xiaomi 15 Pro",
        brand: "Xiaomi",
        price: 16990000,
        image: "https://picsum.photos/id/251/400/400",
        specs: { "Màn hình": "6.73 inch LTPO OLED", "Chip": "Dimensity 9400", "RAM": "16GB", "Bộ nhớ": "512GB", "Pin": "6100mAh", "Camera": "50MP Leica" },
        rating: 4.7
    }
];

let cart = [];
let compareList = [];
let wishlist = [];

// Render sản phẩm
function renderProducts() {
    const grid = document.getElementById('product-grid');
    grid.innerHTML = '';
    products.forEach(p => {
        const card = document.createElement('div');
        card.className = 'product-card bg-white rounded-3xl overflow-hidden';
        card.innerHTML = `
            <img src="${p.image}" class="w-full h-64 object-cover">
            <div class="p-6">
                <h4 class="font-semibold">${p.name}</h4>
                <p class="text-[#0066FF] text-2xl font-bold mt-2">${p.price.toLocaleString('vi-VN')} ₫</p>
                <div class="flex justify-between mt-6">
                    <button onclick="addToCart(${p.id}); event.stopImmediatePropagation()" class="flex-1 py-4 bg-[#0066FF] text-white rounded-3xl text-sm font-medium">Thêm giỏ</button>
                    <button onclick="addToCompare(${p.id}); event.stopImmediatePropagation()" class="flex-1 ml-3 py-4 border border-[#0066FF] text-[#0066FF] rounded-3xl text-sm font-medium">So sánh</button>
                </div>
            </div>
        `;
        grid.appendChild(card);
    });
}

// Thêm vào giỏ
function addToCart(id) {
    const product = products.find(p => p.id === id);
    const existing = cart.find(item => item.id === id);
    if (existing) existing.quantity++;
    else cart.push({ ...product, quantity: 1 });
    updateCartCount();
    showToast(`Đã thêm ${product.name} vào giỏ hàng`);
}

function updateCartCount() {
    let count = cart.reduce((a, b) => a + b.quantity, 0);
    document.getElementById('cart-count').textContent = count;
}

function toggleCart() {
    const modal = document.getElementById('cart-modal');
    const itemsDiv = document.getElementById('cart-items');
    if (modal.classList.contains('hidden')) {
        modal.classList.remove('hidden');
        let html = '';
        let total = 0;
        cart.forEach((item, i) => {
            const itemTotal = item.price * item.quantity;
            total += itemTotal;
            html += `
                <div class="flex gap-4 mb-6">
                    <img src="${item.image}" class="w-20 h-20 object-cover rounded-2xl">
                    <div class="flex-1">
                        <p class="font-medium">${item.name}</p>
                        <p class="text-[#0066FF]">${item.price.toLocaleString('vi-VN')} ₫ × ${item.quantity}</p>
                    </div>
                    <button onclick="removeFromCart(${i});" class="text-red-500">Xóa</button>
                </div>`;
        });
        itemsDiv.innerHTML = html || '<p class="text-center py-12 text-gray-400">Giỏ hàng trống</p>';
        document.getElementById('cart-total').textContent = total.toLocaleString('vi-VN') + ' ₫';
    } else {
        modal.classList.add('hidden');
    }
}

function removeFromCart(index) {
    cart.splice(index, 1);
    toggleCart();
    updateCartCount();
}

function checkout() {
    if (cart.length === 0) return;
    alert('✅ Thanh toán thành công! Cảm ơn bạn đã mua hàng tại IMEX.\nĐơn hàng đang được xử lý.');
    cart = [];
    toggleCart();
    updateCartCount();
}

// So sánh
function addToCompare(id) {
    if (compareList.length >= 4) {
        alert("Chỉ so sánh tối đa 4 sản phẩm!");
        return;
    }
    const product = products.find(p => p.id === id);
    if (compareList.some(p => p.id === id)) return;
    compareList.push(product);
    renderCompareTable();
    document.getElementById('compare-section').classList.remove('hidden');
    showToast(`Đã thêm ${product.name} vào bảng so sánh`);
}

function renderCompareTable() {
    const table = document.getElementById('compare-table');
    let html = `<thead><tr><th class="text-left">Thông số</th>`;
    compareList.forEach(p => {
        html += `<th class="text-center"><img src="${p.image}" class="mx-auto h-20 object-contain"><p class="font-medium mt-2">${p.name}</p></th>`;
    });
    html += `</tr></thead><tbody>`;
    
    const allKeys = Object.keys(compareList[0].specs || {});
    allKeys.forEach(key => {
        html += `<tr class="spec-row"><td class="font-medium">${key}</td>`;
        compareList.forEach(p => {
            html += `<td class="text-center">${p.specs[key] || '—'}</td>`;
        });
        html += `</tr>`;
    });
    html += `</tbody>`;
    table.innerHTML = html;
}

function clearCompare() {
    compareList = [];
    document.getElementById('compare-table').innerHTML = '';
    document.getElementById('compare-section').classList.add('hidden');
}

// Bảo hành
function showWarranty() {
    hideAllSections();
    document.getElementById('warranty-section').classList.remove('hidden');
}

function checkWarranty() {
    const code = document.getElementById('warranty-code').value.trim();
    const result = document.getElementById('warranty-result');
    if (!code) {
        result.innerHTML = `<p class="text-red-500">Vui lòng nhập mã IMEI / Serial</p>`;
        return;
    }
    result.innerHTML = `
        <div class="bg-green-50 border border-green-200 p-6 rounded-3xl">
            <p class="font-semibold text-green-700">Bảo hành hợp lệ</p>
            <p>Sản phẩm: iPhone 17 Pro Max</p>
            <p>Thời hạn: Còn 28 tháng (đến 15/08/2028)</p>
            <p class="mt-4 text-sm">Bạn có thể mang máy đến trung tâm bảo hành gần nhất hoặc yêu cầu hỗ trợ online.</p>
        </div>`;
}

// Cộng đồng
function showCommunity() {
    hideAllSections();
    document.getElementById('community-section').classList.remove('hidden');
    
    const reviews = [
        { name: "Nguyễn Văn A", product: "iPhone 17 Pro Max", text: "Màn hình đẹp, pin trâu, camera cực nét!", rating: 5 },
        { name: "Trần Thị B", product: "Galaxy S25 Ultra", text: "Bút S-Pen rất tiện lợi cho công việc.", rating: 4 }
    ];
    
    let html = '';
    reviews.forEach(r => {
        html += `<div class="border-b pb-6"><p class="font-medium">${r.name} • ${r.product}</p><p class="text-yellow-500">★${r.rating}</p><p class="mt-2">"${r.text}"</p></div>`;
    });
    document.getElementById('reviews-list').innerHTML = html;
}

function postReview() {
    alert("Cảm ơn bạn! Bài đăng của bạn đã được gửi đến cộng đồng IMEX.");
}

// Helper functions
function hideAllSections() {
    document.querySelectorAll('section[id$="-section"]').forEach(s => s.classList.add('hidden'));
}

function showProducts() {
    hideAllSections();
    document.getElementById('products-section').classList.remove('hidden');
}

function showCompare() {
    hideAllSections();
    document.getElementById('compare-section').classList.remove('hidden');
}

function toggleSearch() {
    const term = prompt("Tìm kiếm sản phẩm (demo):");
    if (term) alert(`Kết quả tìm kiếm cho "${term}"`);
}

function toggleWishlist() {
    alert("Danh sách yêu thích đang được phát triển (demo).");
}

function showAccount() {
    alert("Xin chào Ánh!\nVIP Member • Điểm thưởng: 12.450");
}

function showToast(message) {
    const toast = document.createElement('div');
    toast.style.cssText = `position: fixed; bottom: 80px; right: 20px; background: #0066FF; color: white; padding: 14px 24px; border-radius: 9999px; box-shadow: 0 10px 15px -3px rgb(0 0 0 / 0.3); z-index: 99999;`;
    toast.textContent = message;
    document.body.appendChild(toast);
    setTimeout(() => toast.remove(), 2800);
}

// Khởi tạo
window.onload = () => {
    renderProducts();
    updateCartCount();
    console.log('%c✅ IMEX - Hệ sinh thái thương mại điện tử thiết bị di động đã sẵn sàng!', 'color:#0066FF; font-size:18px;');
};
</script>
</body>
</html>
