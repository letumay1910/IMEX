// models/Product.js
const mongoose = require('mongoose');

const productSchema = new mongoose.Schema({
  name: { type: String, required: true },           // Tên điện thoại (iPhone 16 Pro, Samsung S25...)
  brand: { type: String, required: true },          // Apple, Samsung, Xiaomi, Oppo...
  category: { type: String, enum: ['smartphone', 'tablet', 'accessory'] },
  price: { type: Number, required: true },          // Giá bán (VND)
  originalPrice: Number,                            // Giá gốc (để hiển thị giảm giá)
  stock: { type: Number, default: 0 },
  variants: [{                                      // Biến thể: màu sắc, RAM, ROM
    color: String,
    ram: String,
    storage: String,
    priceVariant: Number,
    stockVariant: Number
  }],
  specifications: {                                 // Thông số kỹ thuật
    screen: String,
    camera: String,
    battery: String,
    processor: String,
    os: String
  },
  images: [String],                                 // URL ảnh (Cloudinary)
  description: String,
  warranty: { type: Number, default: 12 },          // Bảo hành (tháng)
  isFeatured: { type: Boolean, default: false },
  rating: { type: Number, default: 0 },
  reviewCount: { type: Number, default: 0 },
  createdAt: { type: Date, default: Date.now }
});

module.exports = mongoose.model('Product', productSchema);
// models/Order.js
const orderSchema = new mongoose.Schema({
  user: { type: mongoose.Schema.Types.ObjectId, ref: 'User' },
  items: [{
    product: { type: mongoose.Schema.Types.ObjectId, ref: 'Product' },
    variant: Object,
    quantity: Number,
    price: Number
  }],
  totalAmount: Number,
  status: { 
    type: String, 
    enum: ['pending', 'confirmed', 'shipping', 'delivered', 'cancelled'],
    default: 'pending' 
  },
  paymentMethod: { type: String, enum: ['COD', 'VNPay', 'Momo'] },
  shippingAddress: {
    fullName: String,
    phone: String,
    address: String,
    city: String,
    district: String
  },
  createdAt: { type: Date, default: Date.now }
});

module.exports = mongoose.model('Order', orderSchema);
const express = require('express');
const router = express.Router();
const Product = require('../models/Product');

// Lấy danh sách sản phẩm (có filter theo brand, giá, category)
router.get('/', async (req, res) => {
  const { brand, minPrice, maxPrice, category, page = 1, limit = 20 } = req.query;
  
  let filter = {};
  if (brand) filter.brand = brand;
  if (category) filter.category = category;
  if (minPrice || maxPrice) {
    filter.price = {};
    if (minPrice) filter.price.$gte = minPrice;
    if (maxPrice) filter.price.$lte = maxPrice;
  }

  const products = await Product.find(filter)
    .skip((page - 1) * limit)
    .limit(parseInt(limit))
    .sort({ createdAt: -1 });

  res.json(products);
});

// Chi tiết sản phẩm
router.get('/:id', async (req, res) => {
  const product = await Product.findById(req.params.id);
  if (!product) return res.status(404).json({ msg: 'Không tìm thấy sản phẩm' });
  res.json(product);
});

// Admin: Thêm sản phẩm mới
router.post('/', async (req, res) => {
  // ... validation & auth middleware
  const newProduct = new Product(req.body);
  await newProduct.save();
  res.status(201).json(newProduct);
});

module.exports = router;
// src/pages/Products.js
import React, { useState, useEffect } from 'react';
import axios from 'axios';

const Products = () => {
  const [products, setProducts] = useState([]);
  const [filters, setFilters] = useState({ brand: '', minPrice: '', maxPrice: '' });

  useEffect(() => {
    fetchProducts();
  }, [filters]);

  const fetchProducts = async () => {
    const res = await axios.get('/api/products', { params: filters });
    setProducts(res.data);
  };

  return (
    <div className="container mx-auto p-4">
      <h1 className="text-3xl font-bold mb-6">IMEX Mobile - Thiết bị di động chính hãng</h1>
      
      {/* Bộ lọc */}
      <div className="flex gap-4 mb-8">
        <select onChange={(e) => setFilters({...filters, brand: e.target.value})}>
          <option value="">Tất cả thương hiệu</option>
          <option value="Apple">Apple</option>
          <option value="Samsung">Samsung</option>
          <option value="Xiaomi">Xiaomi</option>
        </select>
        {/* Thêm filter giá, category... */}
      </div>

      <div className="grid grid-cols-1 md:grid-cols-3 lg:grid-cols-4 gap-6">
        {products.map(product => (
          <div key={product._id} className="border rounded-lg overflow-hidden shadow hover:shadow-lg transition">
            <img src={product.images[0]} alt={product.name} className="w-full h-64 object-cover" />
            <div className="p-4">
              <h3 className="font-semibold text-lg">{product.name}</h3>
              <p className="text-red-600 font-bold text-xl">
                {product.price.toLocaleString('vi-VN')} ₫
              </p>
              {product.originalPrice && (
                <p className="line-through text-gray-500">
                  {product.originalPrice.toLocaleString('vi-VN')} ₫
                </p>
              )}
              <button 
                onClick={() => addToCart(product)}
                className="mt-4 w-full bg-blue-600 text-white py-2 rounded hover:bg-blue-700"
              >
                Thêm vào giỏ
              </button>
            </div>
          </div>
        ))}
      </div>
    </div>
  );
};

export default Products;
npm install vnpay
import { VNPay } from 'vnpay';

const vnpay = new VNPay({
  tmnCode: process.env.VNP_TMN_CODE!,
  secureSecret: process.env.VNP_HASH_SECRET!,
  vnpayHost: 'https://sandbox.vnpayment.vn', // production thì đổi sang https://vnpayment.vn
  testMode: true,
});

export async function POST(req: Request) {
  const { orderId, amount, orderInfo } = await req.json();

  const paymentUrl = vnpay.buildPaymentUrl({
    vnp_Amount: amount * 100,           // nhân 100 vì VNPay dùng đơn vị nhỏ nhất
    vnp_TxnRef: orderId,
    vnp_OrderInfo: orderInfo || 'Thanh toán đơn hàng IMEX',
    vnp_ReturnUrl: `${process.env.NEXT_PUBLIC_BASE_URL}/payment/vnpay-return`,
    vnp_IpAddr: '127.0.0.1', // lấy từ headers thực tế
  });

  return Response.json({ paymentUrl });
}
