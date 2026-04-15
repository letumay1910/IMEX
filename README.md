<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEX - Thiết Bị Di Động Chính Hãng</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Roboto:wght@500;700&display=swap');
        
        :root { --primary: #eab308; }
        
        body { font-family: 'Inter', system_ui, sans-serif; }
        .logo-font { font-family: 'Roboto', sans-serif; }

        .hero-bg {
            background: linear-gradient(135deg, #eab308 0%, #ca8a04 100%);
        }

        .page { display: none; }
        .page.active { display: block; }

        .product-card {
            transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
        }
        .product-card:hover {
            transform: translateY(-15px);
            box-shadow: 0 30px 60px -15px rgb(234 179 8 / 0.4);
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
            background-color: #eab308;
            transition: width 0.3s ease;
        }
        .nav-link:hover:after { width: 100%; }

        .compare-table th, .compare-table td {
            padding: 18px 16px;
            text-align: center;
            border-bottom: 1px solid #f3e8c8;
        }
        .compare-table .best {
            background-color: #fefce8;
            font-weight: 600;
            position: relative;
        }
        .compare-table .best::after {
            content: "★";
            position: absolute;
            top: 12px;
            right: 12px;
            color: #eab308;
            font-size: 20px;
        }
    </style>
</head>
<body class="bg-white text-gray-900">

    <!-- NAVBAR -->
    <nav class="bg-white border-b border-amber-300 sticky top-0 z-50 shadow-sm">
        <div class="max-w-7xl mx-auto px-6 py-5 flex items-center justify-between">
            <div onclick="showPage('home')" class="flex items-center gap-x-4 cursor-pointer">
                <div class="w-12 h-12 bg-gradient-to-br from-amber-400 to-yellow-500 rounded-3xl flex items-center justify-center text-white text-4xl shadow-inner">📱</div>
                <div>
                    <h1 class="logo-font text-4xl font-bold text-amber-400 tracking-tight">IMEX</h1>
                    <p class="text-xs text-amber-600 -mt-1 tracking-widest">MOBILE</p>
                </div>
            </div>

            <div class="hidden md:flex items-center gap-x-10 text-base font-medium">
                <a onclick="showPage('home')" class="nav-link cursor-pointer">Trang chủ</a>
                <a onclick="showPage('shop')" class="nav-link cursor-pointer">Cửa hàng</a>
                <a onclick="showPage('flashsale')" class="nav-link text-red-600 cursor-pointer flex items-center gap-1"><i class="fa-solid fa-bolt"></i> Flash Sale</a>
                <a onclick="showPage('compare')" class="nav-link cursor-pointer">So sánh</a>
                <a onclick="showPage('community')" class="nav-link cursor-pointer">Cộng đồng</a>
                <a onclick="showPage('warranty')" class="nav-link cursor-pointer">Bảo hành</a>
            </div>

            <div class="flex items-center gap-x-6">
                <div onclick="toggleSearch()" class="cursor-pointer">
                    <i class="fa-solid fa-magnifying-glass text-2xl text-gray-600 hover:text-amber-400"></i>
                </div>
                <div onclick="showCart()" class="relative cursor-pointer">
                    <i class="fa-solid fa-shopping-cart text-2xl text-gray-600 hover:text-amber-400"></i>
                    <span id="cart-count-badge" class="absolute -top-2 -right-2 bg-red-500 text-white text-xs font-bold w-5 h-5 rounded-full flex items-center justify-center">0</span>
                </div>
                <div onclick="toggleUserMenu()" class="w-10 h-10 bg-amber-100 rounded-2xl flex items-center justify-center text-2xl cursor-pointer">👤</div>
            </div>
        </div>
    </nav>

    <!-- ==================== PAGE: SO SÁNH (CHI TIẾT HÓA + BỐ CỤC ĐẸP) ==================== -->
    <div id="page-compare" class="page active">
        <div class="max-w-7xl mx-auto px-6 py-12">
            
            <!-- Header -->
            <div class="text-center mb-12">
                <h1 class="text-5xl font-bold text-gray-900">So sánh thiết bị di động</h1>
                <p class="mt-3 text-lg text-gray-600 max-w-2xl mx-auto">
                    Chọn tối đa 4 sản phẩm để đối chiếu chi tiết thông số kỹ thuật. Hệ thống tự động đánh dấu giá trị tốt nhất.
                </p>
            </div>

            <!-- Chọn sản phẩm -->
            <div class="mb-16">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-2xl font-semibold">Chọn sản phẩm</h2>
                    <div class="text-sm text-amber-500 font-medium">
                        Đã chọn <span id="selected-count" class="font-bold text-amber-400">0</span>/4
                    </div>
                </div>
                
                <div id="compare-select-grid" class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 xl:grid-cols-5 gap-6">
                    <!-- Sản phẩm được render bằng JS -->
                </div>
            </div>

            <!-- Nút so sánh -->
            <div class="flex justify-center mb-20">
                <button onclick="performDetailedComparison()" 
                        class="bg-amber-400 hover:bg-amber-500 text-white px-16 py-6 rounded-3xl text-2xl font-semibold flex items-center gap-4 shadow-lg">
                    <i class="fa-solid fa-balance-scale"></i>
                    SO SÁNH CHI TIẾT
                </button>
            </div>

            <!-- Bảng so sánh -->
            <div id="compare-result" class="hidden">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-3xl font-semibold">Kết quả so sánh</h2>
                    <button onclick="clearComparison()" 
                            class="text-red-500 hover:text-red-600 text-sm font-medium flex items-center gap-2">
                        <i class="fa-solid fa-trash"></i> Xóa tất cả
                    </button>
                </div>
                
                <div class="overflow-x-auto rounded-3xl border border-amber-200 shadow">
                    <table id="compare-table" class="compare-table w-full min-w-[1000px] bg-white">
                        <!-- Header và body được render bằng JS -->
                    </table>
                </div>
            </div>
        </div>
    </div>

    <!-- Các trang khác (Home, Shop, Flashsale, ...) giữ nguyên hoặc rút gọn để tập trung vào phần So sánh -->
    <!-- Bạn có thể copy phần còn lại từ code trước nếu cần -->

    <script>
        // Dữ liệu sản phẩm (có nhiều thông số hơn để so sánh chi tiết)
        let allProducts = [
            {
                id: 1, name: "iPhone 16 Pro Max 256GB", category: "phone",
                image: "https://picsum.photos/id/1015/800/800",
                price: 32990000,
                specs: {
                    "Màn hình": "6.9 inch Super Retina XDR, 120Hz",
                    "Độ phân giải": "2868 x 1320 pixels",
                    "Chip": "A18 Pro",
                    "RAM": "8 GB",
                    "Bộ nhớ trong": "256 GB",
                    "Pin": "4680 mAh",
                    "Sạc nhanh": "45W",
                    "Camera chính": "48MP Fusion",
                    "Camera góc rộng": "48MP",
                    "Camera tele": "12MP 5x",
                    "Hệ điều hành": "iOS 18",
                    "Trọng lượng": "227g",
                    "Chất liệu": "Titan Grade 5"
                }
            },
            {
                id: 2, name: "Samsung Galaxy S25 Ultra", category: "phone",
                image: "https://picsum.photos/id/160/800/800",
                price: 28990000,
                specs: {
                    "Màn hình": "6.8 inch Dynamic AMOLED 2X, 120Hz",
                    "Độ phân giải": "3120 x 1440 pixels",
                    "Chip": "Snapdragon 8 Elite",
                    "RAM": "12 GB",
                    "Bộ nhớ trong": "512 GB",
                    "Pin": "5000 mAh",
                    "Sạc nhanh": "65W",
                    "Camera chính": "200MP",
                    "Camera góc rộng": "12MP",
                    "Camera tele": "50MP 5x",
                    "Hệ điều hành": "One UI 7",
                    "Trọng lượng": "232g",
                    "Chất liệu": "Titan"
                }
            },
            {
                id: 3, name: "iPad Air 6 M2 11\"", category: "tablet",
                image: "https://picsum.photos/id/1005/800/800",
                price: 15990000,
                specs: {
                    "Màn hình": "11 inch Liquid Retina",
                    "Độ phân giải": "2360 x 1640",
                    "Chip": "M2",
                    "RAM": "8 GB",
                    "Bộ nhớ trong": "128 GB",
                    "Pin": "28.93 Wh",
                    "Camera": "12MP",
                    "Hệ điều hành": "iPadOS 18",
                    "Trọng lượng": "462g"
                }
            }
        ];

        let selectedForCompare = [];

        function renderCompareSelection() {
            const container = document.getElementById('compare-select-grid');
            container.innerHTML = '';

            allProducts.forEach(product => {
                const isSelected = selectedForCompare.some(p => p.id === product.id);
                const card = document.createElement('div');
                card.className = `product-card bg-white border ${isSelected ? 'border-amber-400 shadow-md' : 'border-gray-200'} rounded-3xl overflow-hidden cursor-pointer`;
                card.innerHTML = `
                    <img src="${product.image}" class="w-full aspect-square object-cover">
                    <div class="p-5">
                        <h4 class="font-semibold text-lg">${product.name}</h4>
                        <p class="text-amber-400 font-medium mt-2">${(product.price/1000000).toFixed(1)} triệu</p>
                    </div>
                `;
                card.onclick = () => toggleSelectProduct(product, card);
                container.appendChild(card);
            });
        }

        function toggleSelectProduct(product, element) {
            const index = selectedForCompare.findIndex(p => p.id === product.id);
            
            if (index > -1) {
                selectedForCompare.splice(index, 1);
                element.classList.remove('border-amber-400', 'shadow-md');
            } else if (selectedForCompare.length < 4) {
                selectedForCompare.push(product);
                element.classList.add('border-amber-400', 'shadow-md');
            } else {
                alert("Chỉ được chọn tối đa 4 sản phẩm để so sánh!");
                return;
            }

            document.getElementById('selected-count').textContent = selectedForCompare.length;
        }

        function performDetailedComparison() {
            if (selectedForCompare.length < 2) {
                alert("Vui lòng chọn ít nhất 2 sản phẩm để so sánh!");
                return;
            }

            const table = document.getElementById('compare-table');
            table.innerHTML = '';

            // Header
            let headerHTML = `<thead><tr class="bg-amber-50"><th class="text-left font-medium">Thông số kỹ thuật</th>`;
            selectedForCompare.forEach(p => {
                headerHTML += `
                    <th class="text-center">
                        <img src="${p.image}" class="w-20 h-20 mx-auto rounded-2xl object-cover mb-3">
                        <p class="font-semibold text-sm">${p.name}</p>
                        <p class="text-amber-400 text-xs">${(p.price/1000000).toFixed(1)} triệu</p>
                    </th>`;
            });
            headerHTML += `</tr></thead>`;
            table.innerHTML += headerHTML;

            // Body
            let bodyHTML = `<tbody>`;
            const allSpecs = new Set();
            selectedForCompare.forEach(p => Object.keys(p.specs).forEach(key => allSpecs.add(key)));

            allSpecs.forEach(specKey => {
                bodyHTML += `<tr><td class="text-left font-medium">${specKey}</td>`;
                
                let values = selectedForCompare.map(p => p.specs[specKey] || "—");
                let maxValue = values[0];
                
                // Tìm giá trị "tốt nhất" (đơn giản: chuỗi dài hơn hoặc số lớn hơn)
                values.forEach(val => {
                    if (typeof val === 'string' && val.length > maxValue.length) maxValue = val;
                });

                values.forEach(val => {
                    const isBest = val === maxValue && val !== "—";
                    bodyHTML += `<td class="${isBest ? 'best' : ''}">${val}</td>`;
                });
                bodyHTML += `</tr>`;
            });

            bodyHTML += `</tbody>`;
            table.innerHTML += bodyHTML;

            document.getElementById('compare-result').classList.remove('hidden');
        }

        function clearComparison() {
            selectedForCompare = [];
            document.getElementById('selected-count').textContent = '0';
            document.getElementById('compare-result').classList.add('hidden');
            renderCompareSelection();
        }

        // Navigation
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
            const target = document.getElementById('page-' + pageId);
            if (target) target.classList.add('active');

            if (pageId === 'compare') {
                renderCompareSelection();
            }
        }

        function toggleSearch() {
            alert("Tính năng tìm kiếm sẽ được mở rộng trong phiên bản đầy đủ.");
        }

        function showCart() {
            alert("Giỏ hàng đang được phát triển. Hiện tại bạn có 0 sản phẩm.");
        }

        function toggleUserMenu() {
            alert("Xin chào Ánh! Tài khoản IMEX của bạn.");
        }

        function toggleMobileMenu() {
            alert("Menu di động - Đang phát triển.");
        }

        // Khởi tạo
        window.onload = () => {
            showPage('compare'); // Mở thẳng trang So sánh để kiểm tra
            console.log('%cIMEX - Trang So sánh đã được tối ưu bố cục và thiết kế đẹp hơn', 'color:#eab308; font-weight:bold');
        };
    </script>
</body>
</html>
