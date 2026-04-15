mobimex/
├── backend/                  # Node.js + Express
│   ├── config/
│   ├── controllers/
│   ├── models/
│   ├── routes/
│   ├── middleware/
│   ├── utils/
│   └── server.js
├── frontend/                 # Next.js 15 (App Router) - Mobile First
│   ├── app/
│   ├── components/
│   ├── lib/
│   ├── public/
│   └── package.json
├── mobile-app/               # React Native (Expo) - App di động native
│   ├── App.tsx
│   ├── screens/
│   ├── navigation/
│   └── ...
├── docker-compose.yml
└── README.md
{
  "name": "mobimex-backend",
  "version": "1.0.0",
  "main": "server.js",
  "scripts": {
    "start": "node server.js",
    "dev": "nodemon server.js"
  },
  "dependencies": {
    "express": "^4.19.2",
    "mongoose": "^8.5.0",
    "bcryptjs": "^3.0.0",
    "jsonwebtoken": "^9.0.2",
    "cors": "^2.8.5",
    "dotenv": "^16.4.5",
    "multer": "^1.4.5-lts.1",
    "stripe": "^16.0.0",
    "nodemailer": "^6.9.14",
    "cloudinary": "^2.0.0"
  }
}
const mongoose = require('mongoose');
require('dotenv').config();

const connectDB = async () => {
  try {
    await mongoose.connect(process.env.MONGO_URI);
    console.log('MongoDB connected successfully - MobIMEX IMEX Platform');
  } catch (err) {
    console.error(err);
    process.exit(1);
  }
};

module.exports = connectDB;
const mongoose = require('mongoose');

const ProductSchema = new mongoose.Schema({
  name: { type: String, required: true },
  category: { type: String, enum: ['Smartphone', 'Tablet', 'PhuKien', 'LinhKien', 'Case', 'SacDuPhong', 'TaiNghe'], required: true },
  brand: { type: String, required: true }, // iPhone, Samsung, Xiaomi, Oppo...
  model: String,
  priceVND: { type: Number, required: true },
  priceUSD: Number,
  importPrice: Number, // Giá nhập từ nước ngoài
  stock: { type: Number, default: 0 },
  stockImport: { type: Number, default: 0 }, // Kho nhập khẩu
  images: [String],
  description: String,
  specs: {
    screen: String,
    cpu: String,
    ram: String,
    storage: String,
    battery: String,
    camera: String
  },
  origin: { type: String, enum: ['Vietnam', 'China', 'USA', 'Korea', 'Others'] },
  hsCode: String, // Mã HS cho xuất nhập khẩu
  imexStatus: { type: String, enum: ['Imported', 'ExportReady', 'InTransit', 'CustomsCleared'] },
  createdAt: { type: Date, default: Date.now }
});

module.exports = mongoose.model('Product', ProductSchema);
const mongoose = require('mongoose');
const bcrypt = require('bcryptjs');

const UserSchema = new mongoose.Schema({
  name: String,
  email: { type: String, required: true, unique: true },
  password: { type: String, required: true },
  role: { type: String, enum: ['customer', 'seller', 'admin', 'imex_staff'], default: 'customer' },
  phone: String,
  address: String,
  companyName: String, // Dành cho doanh nghiệp IMEX
  taxCode: String,
  isVerified: { type: Boolean, default: false }
});

UserSchema.pre('save', async function(next) {
  if (!this.isModified('password')) return next();
  this.password = await bcrypt.hash(this.password, 12);
  next();
});

module.exports = mongoose.model('User', UserSchema);
const mongoose = require('mongoose');

const OrderSchema = new mongoose.Schema({
  user: { type: mongoose.Schema.Types.ObjectId, ref: 'User' },
  products: [{
    product: { type: mongoose.Schema.Types.ObjectId, ref: 'Product' },
    quantity: Number,
    price: Number
  }],
  totalAmount: Number,
  totalAmountUSD: Number,
  status: { type: String, enum: ['Pending', 'Confirmed', 'Processing', 'Shipped', 'Delivered', 'Cancelled'], default: 'Pending' },
  imexType: { type: String, enum: ['Domestic', 'Import', 'Export'] },
  shippingAddress: String,
  paymentMethod: { type: String, enum: ['COD', 'BankTransfer', 'Stripe', 'VNPay', 'PayPal'] },
  paymentStatus: { type: String, default: 'Unpaid' },
  trackingNumber: String,
  customsDocs: [String], // Chứng từ hải quan
  createdAt: { type: Date, default: Date.now }
});

module.exports = mongoose.model('Order', OrderSchema);
const mongoose = require('mongoose');

const OrderSchema = new mongoose.Schema({
  user: { type: mongoose.Schema.Types.ObjectId, ref: 'User' },
  products: [{
    product: { type: mongoose.Schema.Types.ObjectId, ref: 'Product' },
    quantity: Number,
    price: Number
  }],
  totalAmount: Number,
  totalAmountUSD: Number,
  status: { type: String, enum: ['Pending', 'Confirmed', 'Processing', 'Shipped', 'Delivered', 'Cancelled'], default: 'Pending' },
  imexType: { type: String, enum: ['Domestic', 'Import', 'Export'] },
  shippingAddress: String,
  paymentMethod: { type: String, enum: ['COD', 'BankTransfer', 'Stripe', 'VNPay', 'PayPal'] },
  paymentStatus: { type: String, default: 'Unpaid' },
  trackingNumber: String,
  customsDocs: [String], // Chứng từ hải quan
  createdAt: { type: Date, default: Date.now }
});

module.exports = mongoose.model('Order', OrderSchema);
const express = require('express');
const router = express.Router();
const User = require('../models/User');
const jwt = require('jsonwebtoken');
const bcrypt = require('bcryptjs');

router.post('/register', async (req, res) => {
  try {
    const { name, email, password, role, companyName, taxCode } = req.body;
    const existingUser = await User.findOne({ email });
    if (existingUser) return res.status(400).json({ msg: 'User already exists' });

    const user = new User({ name, email, password, role, companyName, taxCode });
    await user.save();

    const token = jwt.sign({ id: user._id, role: user.role }, process.env.JWT_SECRET, { expiresIn: '7d' });
    res.status(201).json({ token, user: { id: user._id, name, email, role } });
  } catch (err) {
    res.status(500).json({ msg: 'Server error' });
  }
});

router.post('/login', async (req, res) => {
  try {
    const { email, password } = req.body;
    const user = await User.findOne({ email });
    if (!user || !(await bcrypt.compare(password, user.password))) {
      return res.status(400).json({ msg: 'Invalid credentials' });
    }

    const token = jwt.sign({ id: user._id, role: user.role }, process.env.JWT_SECRET, { expiresIn: '7d' });
    res.json({ token, user: { id: user._id, name: user.name, email, role: user.role } });
  } catch (err) {
    res.status(500).json({ msg: 'Server error' });
  }
});

module.exports = router;
const express = require('express');
const router = express.Router();
const Product = require('../models/Product');
const authMiddleware = require('../middleware/auth');

// Get all products (mobile optimized - pagination + filter)
router.get('/', async (req, res) => {
  const { page = 1, limit = 20, category, brand, minPrice, maxPrice, origin } = req.query;
  const query = {};
  if (category) query.category = category;
  if (brand) query.brand = brand;
  if (origin) query.origin = origin;
  if (minPrice || maxPrice) {
    query.priceVND = {};
    if (minPrice) query.priceVND.$gte = Number(minPrice);
    if (maxPrice) query.priceVND.$lte = Number(maxPrice);
  }

  const products = await Product.find(query)
    .limit(Number(limit))
    .skip((Number(page) - 1) * Number(limit))
    .sort({ createdAt: -1 });

  const total = await Product.countDocuments(query);
  res.json({ products, total, pages: Math.ceil(total / limit) });
});

// Create product (only seller/admin)
router.post('/', authMiddleware, async (req, res) => {
  try {
    const product = new Product(req.body);
    await product.save();
    res.status(201).json(product);
  } catch (err) {
    res.status(500).json({ msg: err.message });
  }
});

// Update product (IMEX status)
router.put('/:id', authMiddleware, async (req, res) => {
  const product = await Product.findByIdAndUpdate(req.params.id, req.body, { new: true });
  res.json(product);
});

module.exports = router;
const express = require('express');
const router = express.Router();
const Order = require('../models/Order');
const authMiddleware = require('../middleware/auth');

// Create order with IMEX support
router.post('/', authMiddleware, async (req, res) => {
  try {
    const order = new Order({ ...req.body, user: req.user.id });
    await order.save();
    res.status(201).json(order);
  } catch (err) {
    res.status(500).json({ msg: err.message });
  }
});

router.get('/myorders', authMiddleware, async (req, res) => {
  const orders = await Order.find({ user: req.user.id }).populate('products.product');
  res.json(orders);
});

module.exports = router;
const express = require('express');
const cors = require('cors');
const connectDB = require('./config/db');
require('dotenv').config();

const app = express();
app.use(cors());
app.use(express.json());

connectDB();

app.use('/api/auth', require('./routes/auth'));
app.use('/api/products', require('./routes/products'));
app.use('/api/orders', require('./routes/orders'));

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`MobIMEX Backend running on port ${PORT} - Chuyên Thiết bị Di động & IMEX`));
const jwt = require('jsonwebtoken');

module.exports = (req, res, next) => {
  const token = req.header('x-auth-token');
  if (!token) return res.status(401).json({ msg: 'No token, authorization denied' });

  try {
    const decoded = jwt.verify(token, process.env.JWT_SECRET);
    req.user = decoded;
    next();
  } catch (err) {
    res.status(401).json({ msg: 'Token is not valid' });
  }
};
{
  "name": "mobimex-frontend",
  "version": "1.0.0",
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start"
  },
  "dependencies": {
    "next": "15.0.0",
    "react": "^18.3.0",
    "react-dom": "^18.3.0",
    "tailwindcss": "^3.4.0",
    "axios": "^1.7.0",
    "jwt-decode": "^4.0.0",
    "lucide-react": "^0.441.0"
  }
}
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.mobile-container {
  max-width: 480px;
  margin: 0 auto;
  min-height: 100vh;
  background: #f8fafc;
}
import './globals.css';
import { Inter } from 'next/font/google';

const inter = Inter({ subsets: ['latin', 'vietnamese'] });

export const metadata = {
  title: 'MobIMEX - Thương mại điện tử Thiết bị Di động & IMEX',
  description: 'Nền tảng chuyên biệt mua bán smartphone, tablet, phụ kiện với hỗ trợ xuất nhập khẩu toàn cầu.',
  icons: { icon: '/favicon.ico' }
};

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="vi">
      <body className={inter.className}>{children}</body>
    </html>
  );
}
'use client';

import { useState, useEffect } from 'react';
import axios from 'axios';
import { Smartphone, Tablet, Headphones, ShieldCheck, Truck, Globe } from 'lucide-react';

export default function Home() {
  const [products, setProducts] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    axios.get('http://localhost:5000/api/products?limit=8')
      .then(res => {
        setProducts(res.data.products);
        setLoading(false);
      })
      .catch(() => setLoading(false));
  }, []);

  return (
    <div className="mobile-container bg-white min-h-screen pb-20">
      {/* Header */}
      <header className="sticky top-0 bg-white border-b z-50 shadow-sm">
        <div className="flex items-center justify-between px-4 py-3">
          <div className="flex items-center gap-2">
            <div className="w-8 h-8 bg-blue-600 rounded-xl flex items-center justify-center text-white font-bold">M</div>
            <div>
              <h1 className="font-bold text-xl tracking-tight">MobIMEX</h1>
              <p className="text-[10px] text-gray-500 -mt-1">IMEX Mobile Devices</p>
            </div>
          </div>
          <div className="flex items-center gap-4">
            <Globe className="w-5 h-5 text-gray-600" />
            <div className="w-8 h-8 bg-gray-100 rounded-full flex items-center justify-center">👤</div>
          </div>
        </div>
      </header>

      {/* Hero Banner */}
      <div className="bg-gradient-to-r from-blue-600 to-indigo-600 text-white px-4 py-8">
        <h2 className="text-3xl font-bold leading-tight">Thiết bị di động chính hãng<br />Xuất Nhập khẩu Toàn cầu</h2>
        <p className="mt-3 text-blue-100">Giá tốt nhất • Hỗ trợ IMEX • Giao hàng nhanh</p>
        <button className="mt-6 bg-white text-blue-600 px-8 py-3 rounded-2xl font-semibold flex items-center gap-2">
          Khám phá ngay <Truck className="w-5 h-5" />
        </button>
      </div>

      {/* Categories */}
      <div className="px-4 py-6">
        <h3 className="font-semibold text-lg mb-4">Danh mục chuyên sâu</h3>
        <div className="grid grid-cols-4 gap-3">
          {[
            { icon: Smartphone, label: 'Smartphone' },
            { icon: Tablet, label: 'Tablet' },
            { icon: Headphones, label: 'Tai nghe' },
            { icon: ShieldCheck, label: 'Phụ kiện' }
          ].map((cat, i) => (
            <div key={i} className="flex flex-col items-center bg-white p-3 rounded-2xl shadow-sm border">
              <cat.icon className="w-8 h-8 text-blue-600 mb-2" />
              <span className="text-xs font-medium">{cat.label}</span>
            </div>
          ))}
        </div>
      </div>

      {/* Featured Products */}
      <div className="px-4 pb-8">
        <div className="flex justify-between items-center mb-4">
          <h3 className="font-semibold text-lg">Sản phẩm nổi bật</h3>
          <span className="text-blue-600 text-sm">Xem tất cả →</span>
        </div>

        {loading ? (
          <p>Đang tải...</p>
        ) : (
          <div className="grid grid-cols-2 gap-4">
            {products.map((product: any) => (
              <div key={product._id} className="bg-white rounded-3xl overflow-hidden shadow-sm border">
                <div className="h-48 bg-gray-100 relative">
                  {product.images?.[0] ? (
                    <img src={product.images[0]} alt={product.name} className="w-full h-full object-cover" />
                  ) : (
                    <div className="w-full h-full flex items-center justify-center text-5xl">📱</div>
                  )}
                  {product.origin === 'China' && <div className="absolute top-2 right-2 bg-orange-500 text-white text-[10px] px-2 py-0.5 rounded-full">Import</div>}
                </div>
                <div className="p-3">
                  <h4 className="font-medium text-sm line-clamp-2">{product.name}</h4>
                  <p className="text-xs text-gray-500 mt-1">{product.brand} • {product.model}</p>
                  <div className="mt-3 flex items-end justify-between">
                    <div>
                      <span className="text-lg font-bold text-blue-600">{product.priceVND.toLocaleString('vi-VN')}đ</span>
                      {product.priceUSD && <span className="text-xs block text-gray-500">${product.priceUSD}</span>}
                    </div>
                    <button className="bg-blue-600 text-white px-5 py-2 rounded-2xl text-sm font-medium active:scale-95 transition">
                      Mua
                    </button>
                  </div>
                </div>
              </div>
            ))}
          </div>
        )}
      </div>

      {/* IMEX Features */}
      <div className="px-4 py-8 bg-gray-50">
        <h3 className="font-semibold text-lg mb-4 text-center">Tính năng IMEX chuyên biệt</h3>
        <div className="space-y-4">
          <div className="bg-white p-5 rounded-3xl flex gap-4 items-start">
            <div className="w-12 h-12 bg-green-100 rounded-2xl flex-shrink-0 flex items-center justify-center">🌍</div>
            <div>
              <h4 className="font-semibold">Xuất Nhập khẩu minh bạch</h4>
              <p className="text-sm text-gray-600">Theo dõi lô hàng thời gian thực, chứng từ hải quan điện tử, HS Code tự động.</p>
            </div>
          </div>
          <div className="bg-white p-5 rounded-3xl flex gap-4 items-start">
            <div className="w-12 h-12 bg-amber-100 rounded-2xl flex-shrink-0 flex items-center justify-center">📦</div>
            <div>
              <h4 className="font-semibold">Kho đa quốc gia</h4>
              <p className="text-sm text-gray-600">Kho Việt Nam + Kho Trung Quốc + Fulfillment Mỹ/EU.</p>
            </div>
          </div>
        </div>
      </div>

      {/* Bottom Navigation (Mobile) */}
      <nav className="fixed bottom-0 left-0 right-0 bg-white border-t max-w-[480px] mx-auto">
        <div className="flex justify-around py-2">
          <div className="flex flex-col items-center text-blue-600">
            <span className="text-2xl">🏠</span>
            <span className="text-[10px]">Trang chủ</span>
          </div>
          <div className="flex flex-col items-center text-gray-500">
            <span className="text-2xl">🔍</span>
            <span className="text-[10px]">Tìm kiếm</span>
          </div>
          <div className="flex flex-col items-center text-gray-500">
            <span className="text-2xl">🛒</span>
            <span className="text-[10px]">Giỏ hàng</span>
          </div>
          <div className="flex flex-col items-center text-gray-500">
            <span className="text-2xl">👤</span>
            <span className="text-[10px]">Tài khoản</span>
          </div>
        </div>
      </nav>
    </div>
  );
}
// mobile-app/App.tsx
import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
import HomeScreen from './screens/HomeScreen';
import ProductsScreen from './screens/ProductsScreen';
import CartScreen from './screens/CartScreen';
import ProfileScreen from './screens/ProfileScreen';
import { Ionicons } from '@expo/vector-icons';

const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator
        screenOptions={({ route }) => ({
          tabBarIcon: ({ color, size }) => {
            let iconName: any;
            if (route.name === 'Home') iconName = 'home';
            else if (route.name === 'Products') iconName = 'phone-portrait';
            else if (route.name === 'Cart') iconName = 'cart';
            else if (route.name === 'Profile') iconName = 'person';
            return <Ionicons name={iconName} size={size} color={color} />;
          },
          tabBarActiveTintColor: '#2563eb',
          tabBarInactiveTintColor: 'gray',
        })}
      >
        <Tab.Screen name="Home" component={HomeScreen} />
        <Tab.Screen name="Products" component={ProductsScreen} />
        <Tab.Screen name="Cart" component={CartScreen} />
        <Tab.Screen name="Profile" component={ProfileScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}
