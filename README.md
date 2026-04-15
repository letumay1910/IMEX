# IMEX
Nền tảng Thương mại điện tử chuyên biệt Thiết bị di động
mobile-shop/
├── backend/                  # Node.js + Express + MongoDB
├── frontend/                 # React + Vite + TailwindCSS
├── README.md
mkdir backend && cd backend
npm init -y
npm install express mongoose dotenv cors bcryptjs jsonwebtoken multer cloudinary express-validator
npm install -D nodemon
PORT=5000
MONGO_URI=mongodb://localhost:27017/mobileshop
JWT_SECRET=your_jwt_secret_key
CLOUDINARY_CLOUD_NAME=your_cloud
CLOUDINARY_API_KEY=your_key
CLOUDINARY_API_SECRET=your_secret
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');
const dotenv = require('dotenv');

dotenv.config();

const app = express();
app.use(cors());
app.use(express.json());

mongoose.connect(process.env.MONGO_URI)
  .then(() => console.log('MongoDB connected'))
  .catch(err => console.log(err));

// Routes
app.use('/api/products', require('./routes/productRoutes'));
app.use('/api/auth', require('./routes/authRoutes'));
app.use('/api/cart', require('./routes/cartRoutes'));
app.use('/api/orders', require('./routes/orderRoutes'));
app.use('/api/warranty', require('./routes/warrantyRoutes'));
app.use('/api/community', require('./routes/communityRoutes'));

const PORT = process.env.PORT || 5000;
app.listen(PORT, () => console.log(`Server running on port ${PORT}`));
const mongoose = require('mongoose');

const productSchema = new mongoose.Schema({
  name: { type: String, required: true },
  brand: { type: String, required: true },
  price: { type: Number, required: true },
  images: [{ type: String }],
  specs: {
    screen: String,
    processor: String,
    ram: String,
    storage: String,
    battery: String,
    camera: String,
    os: String,
    // Thêm nhiều specs khác...
  },
  stock: { type: Number, default: 0 },
  rating: { type: Number, default: 0 },
  reviews: [{ user: String, comment: String, rating: Number }]
});

module.exports = mongoose.model('Product', productSchema);
npx create-vite@latest frontend -- --template react
cd frontend
npm install tailwindcss@latest postcss autoprefixer @reduxjs/toolkit react-redux axios react-router-dom lucide-react
npx tailwindcss init -p
/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors: {
        primary: '#0A84FF',
        'primary-dark': '#0066CC',
      },
    },
  },
  plugins: [],
}/** @type {import('tailwindcss').Config} */
export default {
  content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors: {
        primary: '#0A84FF',
        'primary-dark': '#0066CC',
      },
    },
  },
  plugins: [],
}
@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  background-color: #f8fafc;
  font-family: 'Inter', system-ui, sans-serif;
}
import { BrowserRouter as Router, Routes, Route } from 'react-router-dom';
import Navbar from './components/Navbar';
import Home from './pages/Home';
import ProductList from './pages/ProductList';
import ProductDetail from './pages/ProductDetail';
import Compare from './pages/Compare';
import Cart from './pages/Cart';
import Orders from './pages/Orders';
import Warranty from './pages/Warranty';
import Community from './pages/Community';

function App() {
  return (
    <Router>
      <div className="min-h-screen bg-white">
        <Navbar />
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/products" element={<ProductList />} />
          <Route path="/product/:id" element={<ProductDetail />} />
          <Route path="/compare" element={<Compare />} />
          <Route path="/cart" element={<Cart />} />
          <Route path="/orders" element={<Orders />} />
          <Route path="/warranty" element={<Warranty />} />
          <Route path="/community" element={<Community />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
import { ShoppingCart, Users, Shield } from 'lucide-react';
import { Link } from 'react-router-dom';

export default function Navbar() {
  return (
    <nav className="bg-white border-b sticky top-0 z-50 shadow-sm">
      <div className="max-w-7xl mx-auto px-4 py-4 flex items-center justify-between">
        <Link to="/" className="flex items-center gap-2 text-2xl font-bold text-primary">
          MobileShop
        </Link>

        <div className="flex items-center gap-8 text-sm font-medium">
          <Link to="/products" className="hover:text-primary transition">Sản phẩm</Link>
          <Link to="/compare" className="hover:text-primary transition">So sánh</Link>
          <Link to="/community" className="hover:text-primary transition flex items-center gap-1">
            <Users size={18} /> Cộng đồng
          </Link>
          <Link to="/warranty" className="hover:text-primary transition flex items-center gap-1">
            <Shield size={18} /> Bảo hành
          </Link>
        </div>

        <div className="flex items-center gap-6">
          <Link to="/cart" className="relative">
            <ShoppingCart className="text-gray-700 hover:text-primary" size={24} />
            <span className="absolute -top-1 -right-1 bg-primary text-white text-xs rounded-full w-5 h-5 flex items-center justify-center">3</span>
          </Link>
          <div className="w-8 h-8 bg-primary text-white rounded-full flex items-center justify-center font-semibold">T</div>
        </div>
      </div>
    </nav>
  );
}
import { useState, useEffect } from 'react';
import axios from 'axios';

export default function Compare() {
  const [selectedProducts, setSelectedProducts] = useState([]);
  const [products, setProducts] = useState([]);

  useEffect(() => {
    axios.get('http://localhost:5000/api/products')
      .then(res => setProducts(res.data));
  }, []);

  const addToCompare = (product) => {
    if (selectedProducts.length < 4 && !selectedProducts.find(p => p._id === product._id)) {
      setSelectedProducts([...selectedProducts, product]);
    }
  };

  const specsKeys = ['screen', 'processor', 'ram', 'storage', 'battery', 'camera'];

  return (
    <div className="max-w-7xl mx-auto px-4 py-12">
      <h1 className="text-4xl font-bold text-center mb-10 text-gray-900">So sánh thiết bị di động</h1>

      <div className="overflow-x-auto">
        <table className="w-full border-collapse bg-white shadow-lg rounded-xl overflow-hidden">
          <thead>
            <tr className="bg-primary text-white">
              <th className="p-4 text-left">Thông số</th>
              {selectedProducts.map((p, i) => (
                <th key={i} className="p-4 text-center min-w-[220px]">
                  <img src={p.images[0]} alt={p.name} className="w-20 mx-auto rounded" />
                  <div className="mt-2 font-semibold">{p.name}</div>
                  <div className="text-sm">{p.price.toLocaleString()} ₫</div>
                </th>
              ))}
            </tr>
          </thead>
          <tbody>
            {specsKeys.map(key => (
              <tr key={key} className="border-b hover:bg-gray-50">
                <td className="p-4 font-medium capitalize bg-gray-50">{key}</td>
                {selectedProducts.map((p, i) => (
                  <td key={i} className="p-4 text-center">{p.specs[key] || '—'}</td>
                ))}
              </tr>
            ))}
          </tbody>
        </table>
      </div>

      {/* Danh sách sản phẩm để chọn thêm */}
      <div className="mt-12">
        <h2 className="text-2xl font-semibold mb-6">Chọn thêm sản phẩm để so sánh</h2>
        <div className="grid grid-cols-2 md:grid-cols-4 gap-6">
          {products.slice(0, 8).map(product => (
            <div key={product._id} className="border rounded-2xl p-4 hover:shadow-xl transition cursor-pointer"
                 onClick={() => addToCompare(product)}>
              <img src={product.images[0]} alt="" className="w-full h-48 object-contain" />
              <h3 className="font-semibold mt-4">{product.name}</h3>
              <p className="text-primary font-bold">{product.price.toLocaleString()} ₫</p>
            </div>
          ))}
        </div>
      </div>
    </div>
  );
}
npm install @payos/node
PAYOS_CLIENT_ID=your_client_id
PAYOS_API_KEY=your_api_key
PAYOS_CHECKSUM_KEY=your_checksum_key
const mongoose = require('mongoose');

const orderSchema = new mongoose.Schema({
  user: { type: mongoose.Schema.Types.ObjectId, ref: 'User', required: true },
  items: [{
    product: { type: mongoose.Schema.Types.ObjectId, ref: 'Product' },
    name: String,
    price: Number,
    quantity: Number
  }],
  totalAmount: { type: Number, required: true },
  status: { 
    type: String, 
    enum: ['pending', 'paid', 'shipping', 'delivered', 'cancelled'], 
    default: 'pending' 
  },
  paymentMethod: { type: String, default: 'payos' },
  paymentId: String,           // ID từ PayOS
  shippingAddress: {
    name: String,
    phone: String,
    address: String,
    city: String
  },
  createdAt: { type: Date, default: Date.now }
});

module.exports = mongoose.model('Order', orderSchema);
const express = require('express');
const router = express.Router();
const PayOS = require('@payos/node');
const Order = require('../models/Order');
const Cart = require('../models/Cart'); // giả sử bạn có model Cart

const payos = new PayOS(
  process.env.PAYOS_CLIENT_ID,
  process.env.PAYOS_API_KEY,
  process.env.PAYOS_CHECKSUM_KEY
);

// Tạo link thanh toán
router.post('/create', async (req, res) => {
  try {
    const { userId, shippingAddress, items, totalAmount } = req.body;

    // Tạo đơn hàng trước
    const order = new Order({
      user: userId,
      items,
      totalAmount,
      shippingAddress,
      status: 'pending'
    });
    await order.save();

    const paymentData = {
      orderCode: Date.now(),                    // Mã đơn hàng duy nhất
      amount: totalAmount,
      description: `Thanh toán đơn hàng #${order._id}`,
      returnUrl: "http://localhost:5173/payment-success",   // URL sau khi thanh toán thành công
      cancelUrl: "http://localhost:5173/cart",
      items: items.map(item => ({
        name: item.name,
        quantity: item.quantity,
        price: item.price
      }))
    };

    const paymentLink = await payos.createPaymentLink(paymentData);

    // Lưu paymentId vào order
    order.paymentId = paymentData.orderCode;
    await order.save();

    res.json({ 
      success: true, 
      checkoutUrl: paymentLink.checkoutUrl,
      orderId: order._id 
    });

  } catch (error) {
    console.error(error);
    res.status(500).json({ success: false, message: 'Lỗi tạo link thanh toán' });
  }
});

// Webhook nhận kết quả thanh toán từ PayOS
router.post('/webhook', async (req, res) => {
  try {
    const { data, signature } = req.body;
    // Xác thực signature (PayOS yêu cầu)
    const verified = payos.verifyPaymentWebhookData(data, signature);

    if (verified) {
      const order = await Order.findOne({ paymentId: data.orderCode });
      if (order) {
        order.status = data.status === 'PAID' ? 'paid' : 'cancelled';
        await order.save();

        // Xóa giỏ hàng sau khi thanh toán thành công
        if (data.status === 'PAID') {
          await Cart.deleteOne({ user: order.user });
        }
      }
    }
    res.json({ success: true });
  } catch (error) {
    res.status(500).json({ success: false });
  }
});

module.exports = router;
app.use('/api/payment', require('./routes/paymentRoutes'));
import { useState, useEffect } from 'react';
import axios from 'axios';
import { Trash2, Plus, Minus } from 'lucide-react';

export default function Cart() {
  const [cartItems, setCartItems] = useState([]);
  const [loading, setLoading] = useState(false);

  useEffect(() => {
    // Giả sử lấy từ Redux hoặc localStorage + API
    const savedCart = JSON.parse(localStorage.getItem('cart')) || [];
    setCartItems(savedCart);
  }, []);

  const total = cartItems.reduce((sum, item) => sum + item.price * item.quantity, 0);

  const updateQuantity = (id, newQty) => {
    const updated = cartItems.map(item => 
      item._id === id ? { ...item, quantity: Math.max(1, newQty) } : item
    );
    setCartItems(updated);
    localStorage.setItem('cart', JSON.stringify(updated));
  };

  const removeItem = (id) => {
    const updated = cartItems.filter(item => item._id !== id);
    setCartItems(updated);
    localStorage.setItem('cart', JSON.stringify(updated));
  };

  const handleCheckout = async () => {
    setLoading(true);
    try {
      const userId = "user_id_here"; // Lấy từ auth (JWT)

      const res = await axios.post('http://localhost:5000/api/payment/create', {
        userId,
        items: cartItems,
        totalAmount: total,
        shippingAddress: {
          name: "Tumay",
          phone: "0123456789",
          address: "Vinh, Nghệ An",
          city: "Vinh"
        }
      });

      if (res.data.success) {
        window.location.href = res.data.checkoutUrl;   // Chuyển sang trang PayOS
      }
    } catch (error) {
      alert('Có lỗi xảy ra khi tạo đơn hàng');
    }
    setLoading(false);
  };

  return (
    <div className="max-w-6xl mx-auto px-4 py-12">
      <h1 className="text-4xl font-bold mb-10 text-center">Giỏ hàng của bạn</h1>

      {cartItems.length === 0 ? (
        <p className="text-center text-xl">Giỏ hàng trống</p>
      ) : (
        <div className="grid grid-cols-1 lg:grid-cols-3 gap-10">
          {/* Danh sách sản phẩm */}
          <div className="lg:col-span-2 space-y-6">
            {cartItems.map(item => (
              <div key={item._id} className="flex gap-6 bg-white p-6 rounded-2xl shadow-sm border">
                <img src={item.images[0]} alt={item.name} className="w-32 h-32 object-contain" />
                <div className="flex-1">
                  <h3 className="font-semibold text-lg">{item.name}</h3>
                  <p className="text-primary font-bold mt-1">{item.price.toLocaleString()} ₫</p>

                  <div className="flex items-center gap-4 mt-4">
                    <button onClick={() => updateQuantity(item._id, item.quantity - 1)} className="p-2 hover:bg-gray-100 rounded">
                      <Minus size={18} />
                    </button>
                    <span className="font-medium w-8 text-center">{item.quantity}</span>
                    <button onClick={() => updateQuantity(item._id, item.quantity + 1)} className="p-2 hover:bg-gray-100 rounded">
                      <Plus size={18} />
                    </button>
                    <button onClick={() => removeItem(item._id)} className="ml-auto text-red-500 hover:text-red-700">
                      <Trash2 size={20} />
                    </button>
                  </div>
                </div>
              </div>
            ))}
          </div>

          {/* Thông tin thanh toán */}
          <div className="bg-white p-8 rounded-3xl shadow-sm border h-fit sticky top-24">
            <h2 className="text-2xl font-semibold mb-6">Tổng thanh toán</h2>
            <div className="space-y-4 text-lg">
              <div className="flex justify-between">
                <span>Tạm tính</span>
                <span>{total.toLocaleString()} ₫</span>
              </div>
              <div className="flex justify-between border-t pt-4 font-bold text-xl">
                <span>Tổng cộng</span>
                <span className="text-primary">{total.toLocaleString()} ₫</span>
              </div>
            </div>

            <button 
              onClick={handleCheckout}
              disabled={loading}
              className="mt-8 w-full bg-primary hover:bg-primary-dark text-white font-semibold py-4 rounded-2xl text-lg transition disabled:opacity-70"
            >
              {loading ? 'Đang xử lý...' : 'Thanh toán ngay qua PayOS'}
            </button>

            <p className="text-center text-sm text-gray-500 mt-6">
              Hỗ trợ thanh toán nhanh bằng VietQR, chuyển khoản ngân hàng
            </p>
          </div>
        </div>
      )}
    </div>
  );
}
export default function PaymentSuccess() {
  return (
    <div className="min-h-screen flex items-center justify-center bg-gray-50">
      <div className="text-center bg-white p-12 rounded-3xl shadow-xl max-w-md">
        <div className="text-7xl mb-6">✅</div>
        <h1 className="text-4xl font-bold text-green-600 mb-4">Thanh toán thành công!</h1>
        <p className="text-gray-600 mb-8">Cảm ơn bạn đã mua hàng tại MobileShop.<br />Đơn hàng của bạn đang được xử lý.</p>
        <a href="/orders" className="block bg-primary text-white py-4 rounded-2xl font-semibold">
          Xem đơn hàng của tôi
        </a>
      </div>
    </div>
  );
}
<Route path="/payment-success" element={<PaymentSuccess />} />
