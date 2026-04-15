# IMEX
Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động
imex-mobile-store/
├── app/
│   ├── layout.tsx
│   ├── page.tsx                 ← Trang chủ
│   ├── products/page.tsx
│   ├── product/[id]/page.tsx
│   ├── cart/page.tsx
│   └── checkout/page.tsx
├── components/
│   ├── Header.tsx
│   ├── Footer.tsx
│   ├── ProductCard.tsx
│   ├── CartDrawer.tsx
│   └── HeroBanner.tsx
├── data/products.ts             ← Dữ liệu sản phẩm mẫu
├── context/CartContext.tsx
├── lib/stripe.ts
└── tailwind.config.ts
npx create-next-app@latest imex-mobile-store --typescript --tailwind --eslint --app
cd imex-mobile-store
npm install @heroicons/react lucide-react
// tailwind.config.ts
import type { Config } from "tailwindcss";

const config: Config = {
  content: [
    "./app/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        imex: {
          blue: "#007BFF",      // Xanh dương chủ đạo
          "blue-dark": "#0056B3",
          light: "#F8FAFC",
        },
      },
      fontFamily: {
        sans: ["Inter", "system-ui", "sans-serif"],
      },
    },
  },
  plugins: [],
};

export default config;
export type Product = {
  id: number;
  name: string;
  category: string;
  price: number;
  originalPrice?: number;
  image: string;
  rating: number;
  inStock: boolean;
  description: string;
};

export const products: Product[] = [
  {
    id: 1,
    name: "IMEX Phone X Pro 256GB",
    category: "smartphone",
    price: 12490000,
    originalPrice: 13990000,
    image: "https://picsum.photos/id/1015/600/600",
    rating: 4.8,
    inStock: true,
    description: "Điện thoại cao cấp IMEX với camera 108MP, chip mạnh mẽ.",
  },
  {
    id: 2,
    name: "Ốp lưng IMEX 3D Carbon X Pro",
    category: "phu-kien",
    price: 289000,
    image: "https://picsum.photos/id/201/600/600",
    rating: 4.6,
    inStock: true,
    description: "Ốp lưng chống sốc, thiết kế 3D cao cấp.",
  },
  {
    id: 3,
    name: "Cường lực màn hình IMEX Gorilla Glass",
    category: "phu-kien",
    price: 159000,
    image: "https://picsum.photos/id/237/600/600",
    rating: 4.9,
    inStock: true,
    description: "Cường lực chống va đập, vân tay chống bám.",
  },
  // Thêm nhiều sản phẩm hơn...
];
"use client";
import Link from "next/link";
import { ShoppingCart, User, Search } from "lucide-react";
import { useCart } from "@/context/CartContext";

export default function Header() {
  const { cart } = useCart();

  return (
    <header className="bg-white shadow-sm sticky top-0 z-50">
      <div className="max-w-7xl mx-auto px-4 py-4 flex items-center justify-between">
        <div className="flex items-center gap-3">
          <div className="w-10 h-10 bg-imex-blue rounded-xl flex items-center justify-center">
            <span className="text-white font-bold text-2xl">I</span>
          </div>
          <div>
            <h1 className="text-2xl font-bold text-imex-blue">IMEX Mobile</h1>
            <p className="text-xs text-gray-500 -mt-1">Thiết bị di động chính hãng</p>
          </div>
        </div>

        <nav className="hidden md:flex gap-8 text-sm font-medium">
          <Link href="/" className="hover:text-imex-blue transition">Trang chủ</Link>
          <Link href="/products" className="hover:text-imex-blue transition">Sản phẩm</Link>
          <Link href="#" className="hover:text-imex-blue transition">Phụ kiện</Link>
          <Link href="#" className="hover:text-imex-blue transition">Khuyến mãi</Link>
        </nav>

        <div className="flex items-center gap-4">
          <div className="relative hidden md:block">
            <input
              type="text"
              placeholder="Tìm kiếm điện thoại, phụ kiện..."
              className="bg-gray-100 border border-gray-200 pl-10 py-2 w-80 rounded-full text-sm focus:outline-none focus:border-imex-blue"
            />
            <Search className="absolute left-4 top-3 text-gray-400" size={18} />
          </div>

          <Link href="/cart" className="relative">
            <ShoppingCart size={24} />
            {cart.length > 0 && (
              <span className="absolute -top-1 -right-1 bg-red-500 text-white text-[10px] w-5 h-5 flex items-center justify-center rounded-full">
                {cart.length}
              </span>
            )}
          </Link>
          <User size={24} />
        </div>
      </div>
    </header>
  );
}
import HeroBanner from "@/components/HeroBanner";
import ProductCard from "@/components/ProductCard";
import { products } from "@/data/products";

export default function Home() {
  return (
    <main className="min-h-screen bg-imex-light">
      <HeroBanner />

      <div className="max-w-7xl mx-auto px-4 py-12">
        <h2 className="text-3xl font-bold text-center mb-4">Sản phẩm nổi bật</h2>
        <p className="text-center text-gray-600 mb-10">Thiết bị di động và phụ kiện IMEX chính hãng</p>

        <div className="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6">
          {products.slice(0, 8).map((product) => (
            <ProductCard key={product.id} product={product} />
          ))}
        </div>
      </div>
    </main>
  );
}
export default function HeroBanner() {
  return (
    <div className="bg-gradient-to-r from-imex-blue to-imex-blue-dark text-white py-20">
      <div className="max-w-7xl mx-auto px-4 flex flex-col md:flex-row items-center gap-12">
        <div className="md:w-1/2 space-y-6">
          <h1 className="text-5xl font-bold leading-tight">
            IMEX Mobile<br />
            <span className="text-white/90">Công nghệ vượt trội</span>
          </h1>
          <p className="text-xl text-white/80">
            Điện thoại, phụ kiện và giải pháp bảo vệ thiết bị di động cao cấp.
          </p>
          <button className="bg-white text-imex-blue px-8 py-4 rounded-full font-semibold hover:bg-gray-100 transition">
            Khám phá ngay
          </button>
        </div>
        <div className="md:w-1/2">
          <img
            src="https://picsum.photos/id/1015/800/600"
            alt="IMEX Phone"
            className="rounded-3xl shadow-2xl"
          />
        </div>
      </div>
    </div>
  );
}
"use client";
import Image from "next/image";
import Link from "next/link";
import { Product } from "@/data/products";
import { useCart } from "@/context/CartContext";

export default function ProductCard({ product }: { product: Product }) {
  const { addToCart } = useCart();

  return (
    <div className="bg-white rounded-2xl overflow-hidden shadow-sm hover:shadow-xl transition group">
      <div className="relative h-64 bg-gray-100">
        <Image
          src={product.image}
          alt={product.name}
          fill
          className="object-cover group-hover:scale-105 transition"
        />
      </div>
      <div className="p-5">
        <div className="text-xs uppercase tracking-widest text-imex-blue mb-1">{product.category}</div>
        <h3 className="font-semibold line-clamp-2 h-14">{product.name}</h3>
        
        <div className="flex items-center gap-2 mt-3">
          <span className="text-2xl font-bold text-imex-blue">
            {(product.price / 1000000).toFixed(1)}tr
          </span>
          {product.originalPrice && (
            <span className="line-through text-gray-400 text-sm">
              {(product.originalPrice / 1000000).toFixed(1)}tr
            </span>
          )}
        </div>

        <button
          onClick={() => addToCart(product)}
          className="mt-5 w-full bg-imex-blue hover:bg-imex-blue-dark text-white py-3 rounded-xl font-medium transition"
        >
          Thêm vào giỏ
        </button>
      </div>
    </div>
  );
}
