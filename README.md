# IMEX
Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động
mobile-ecommerce/
├── app/
│   ├── Models/              # Product, Category, Order, Warranty, Review, Comparison...
│   ├── Http/Controllers/
│   ├── Services/            # ProductComparisonService, WarrantyService...
├── resources/
│   ├── views/               # Blade (nếu dùng hybrid) hoặc Vue SPA
│   └── js/                  # Vue 3 app
├── routes/
│   ├── web.php
│   └── api.php
├── database/
│   ├── migrations/
│   └── seeders/
├── public/
└── composer.json
// database/migrations/xxxx_xx_xx_create_products_table.php
Schema::create('products', function (Blueprint $table) {
    $table->id();
    $table->string('name');
    $table->string('brand');                    // Apple, Samsung, Xiaomi...
    $table->string('model');
    $table->decimal('price', 15, 2);
    $table->text('description');
    $table->json('specifications');             // {"screen": "6.7 inch", "ram": "8GB", "battery": "5000mAh", ...}
    $table->json('images');                     // array URL hình ảnh
    $table->integer('stock');
    $table->foreignId('category_id')->constrained();
    $table->boolean('is_active')->default(true);
    $table->timestamps();
});
// app/Models/Product.php
class Product extends Model
{
    protected $casts = [
        'specifications' => 'array',
        'images' => 'array',
    ];

    public function category()
    {
        return $this->belongsTo(Category::class);
    }

    public function reviews()
    {
        return $this->hasMany(Review::class);
    }
}
// app/Http/Controllers/ProductComparisonController.php
public function compare(Request $request)
{
    $productIds = $request->input('products', []); // array id sản phẩm

    if (count($productIds) < 2 || count($productIds) > 4) {
        return response()->json(['error' => 'Chọn từ 2 đến 4 sản phẩm'], 400);
    }

    $products = Product::whereIn('id', $productIds)
        ->select('id', 'name', 'brand', 'price', 'specifications', 'images')
        ->get();

    // Chuẩn bị dữ liệu so sánh (lấy các key specs chung)
    $comparison = [];
    if ($products->isNotEmpty()) {
        $allKeys = collect($products->pluck('specifications'))->flatMap(fn($spec) => array_keys($spec))->unique();

        foreach ($allKeys as $key) {
            $comparison[$key] = $products->map(function ($product) use ($key) {
                return $product->specifications[$key] ?? 'N/A';
            });
        }
    }

    return response()->json([
        'products' => $products,
        'comparison_table' => $comparison
    ]);
}
<!-- resources/js/components/ProductComparison.vue -->
<template>
  <div class="overflow-x-auto">
    <table class="min-w-full border">
      <thead>
        <tr>
          <th>Thông số</th>
          <th v-for="product in products" :key="product.id">{{ product.name }}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(values, spec) in comparison" :key="spec">
          <td class="font-medium">{{ spec }}</td>
          <td v-for="(val, i) in values" :key="i">{{ val }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
Schema::create('warranties', function (Blueprint $table) {
    $table->id();
    $table->foreignId('product_id')->constrained();
    $table->foreignId('user_id')->constrained();
    $table->string('warranty_code')->unique();
    $table->date('start_date');
    $table->date('end_date');
    $table->string('status'); // active, expired, claimed
    $table->timestamps();
});
# 1. Tạo project mới
composer create-project bagisto/bagisto mobile-ecommerce
cd mobile-ecommerce

# 2. Cài đặt
php artisan bagisto:install

# 3. Thêm package VNPay (mới nhất 2026)
composer require tringuyenduc2903/vnpay-vietnam-laravel:^2.0

# 4. Publish & migrate
php artisan vendor:publish --tag=vnpay-config
php artisan migrate
// 2026_04_15_000001_create_product_specifications_table.php
Schema::create('product_specifications', function (Blueprint $table) {
    $table->id();
    $table->foreignId('product_id')->constrained()->cascadeOnDelete();
    $table->string('key');           // screen, ram, camera, battery...
    $table->text('value');
    $table->timestamps();
    
    $table->unique(['product_id', 'key']);
});

// 2026_04_15_000002_create_warranties_table.php
Schema::create('warranties', function (Blueprint $table) {
    $table->id();
    $table->foreignId('product_id')->constrained();
    $table->foreignId('user_id')->constrained();
    $table->foreignId('order_id')->nullable()->constrained();
    $table->string('warranty_code')->unique();
    $table->date('start_date');
    $table->date('end_date');
    $table->enum('status', ['active', 'expired', 'claimed', 'cancelled'])->default('active');
    $table->text('claim_note')->nullable();
    $table->timestamps();
});

// 2026_04_15_000003_create_community_posts_table.php
Schema::create('community_posts', function (Blueprint $table) {
    $table->id();
    $table->foreignId('user_id')->constrained();
    $table->string('title');
    $table->longText('content');
    $table->string('image')->nullable();
    $table->enum('type', ['review', 'question', 'tip', 'news'])->default('review');
    $table->integer('likes')->default(0);
    $table->timestamps();
});

// 2026_04_15_000004_create_community_comments_table.php
Schema::create('community_comments', function (Blueprint $table) {
    $table->id();
    $table->foreignId('post_id')->constrained()->cascadeOnDelete();
    $table->foreignId('user_id')->constrained();
    $table->longText('content');
    $table->timestamps();
});
php artisan migrate
<?php
namespace App\Models;

use Illuminate\Database\Eloquent\Relations\HasMany;

class Product extends \Webkul\Product\Models\Product
{
    protected $casts = ['specifications' => 'array']; // dùng JSON chính

    public function specifications(): HasMany
    {
        return $this->hasMany(ProductSpecification::class);
    }

    public function warranties(): HasMany
    {
        return $this->hasMany(Warranty::class);
    }
}
<?php
namespace App\Services;

class ProductComparisonService
{
    public function compare(array $productIds)
    {
        if (count($productIds) < 2 || count($productIds) > 4) {
            throw new \Exception('Chỉ được so sánh từ 2 đến 4 sản phẩm');
        }

        $products = Product::with('specifications')
            ->whereIn('id', $productIds)
            ->get();

        $allKeys = $products->flatMap(fn($p) => $p->specifications->pluck('key'))->unique();

        $comparison = [];
        foreach ($allKeys as $key) {
            $comparison[$key] = $products->map(function ($product) use ($key) {
                $spec = $product->specifications->firstWhere('key', $key);
                return $spec ? $spec->value : '—';
            })->values();
        }

        return [
            'products' => $products,
            'comparison' => $comparison,
            'keys' => $allKeys
        ];
    }
}
public function compare(Request $request)
{
    $result = app(ProductComparisonService::class)->compare($request->products);
    return response()->json($result);
}
public function vnpayCheckout(Request $request)
{
    $order = Order::findOrFail($request->order_id);
    
    $vnpay = new \Tringuyenduc2903\VNPay\VNPay();
    $paymentUrl = $vnpay->createPayment([
        'amount' => $order->grand_total * 100,
        'order_id' => $order->id,
        'order_info' => "Đơn hàng #" . $order->id,
        'return_url' => route('payment.vnpay.return'),
    ]);

    return redirect($paymentUrl);
}

public function vnpayReturn(Request $request)
{
    $vnpay = new \Tringuyenduc2903\VNPay\VNPay();
    if ($vnpay->verifyPayment($request->all())) {
        $order = Order::find($request->vnp_TxnRef);
        $order->update(['status' => 'processing']);
        // Gửi mail + notification
        return redirect()->route('checkout.success');
    }
    return redirect()->route('checkout.fail');
}
public function generate(Request $request)
{
    $order = Order::findOrFail($request->order_id);
    
    $warrantyCode = 'BH-' . strtoupper(Str::random(10));
    
    Warranty::create([
        'product_id' => $order->items->first()->product_id,
        'user_id' => auth()->id(),
        'order_id' => $order->id,
        'warranty_code' => $warrantyCode,
        'start_date' => now(),
        'end_date' => now()->addMonths(12), // tùy model
    ]);

    // Tạo QR code (sử dụng SimpleQrcode)
    $qr = QrCode::size(300)->generate(route('warranty.check', $warrantyCode));

    return response()->json(['code' => $warrantyCode, 'qr' => $qr]);
}

public function check($code)
{
    $warranty = Warranty::where('warranty_code', $code)->firstOrFail();
    return view('warranty.detail', compact('warranty'));
}
Route::middleware('auth:sanctum')->group(function () {
    Route::post('/compare', [ComparisonController::class, 'compare']);
    Route::post('/warranty/generate', [WarrantyController::class, 'generate']);
    Route::get('/community/posts', [CommunityPostController::class, 'index']);
    // ... tất cả API khác
});
composer require filament/filament
php artisan filament:install --panels
