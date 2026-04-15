// server.js
const express = require('express');
const mongoose = require('mongoose');
const cors = require('cors');

const app = express();
app.use(cors());
app.use(express.json());

// Kết nối với MongoDB
mongoose.connect('mongodb://localhost:27017/ecommerce', { useNewUrlParser: true, useUnifiedTopology: true });

// Định nghĩa mô hình sản phẩm
const ProductSchema = new mongoose.Schema({
    name: String,
    description: String,
    price: Number,
    category: String,
    imageUrl: String,
});

const Product = mongoose.model('Product', ProductSchema);

// API để lấy danh sách sản phẩm
app.get('/api/products', async (req, res) => {
    const products = await Product.find();
    res.json(products);
});

// API để thêm sản phẩm mới
app.post('/api/products', async (req, res) => {
    const newProduct = new Product(req.body);
    await newProduct.save();
    res.status(201).json(newProduct);
});

// Bắt đầu server
const PORT = process.env.PORT || 5000;
app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
});
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cửa Hàng Thiết Bị Di Động</title>
    <style>
        body { font-family: Arial, sans-serif; }
        .product { border: 1px solid #ccc; margin: 10px; padding: 10px; }
        img { max-width: 100px; }
    </style>
</head>
<body>
    <h1>Danh Sách Sản Phẩm</h1>
    <div id="products"></div>
    
    <script>
        async function fetchProducts() {
            const response = await fetch('http://localhost:5000/api/products');
            const products = await response.json();
            const productsDiv = document.getElementById('products');

            products.forEach(product => {
                const productDiv = document.createElement('div');
                productDiv.className = 'product';
                productDiv.innerHTML = `
                    <h2>${product.name}</h2>
                    <p>${product.description}</p>
                    <p>Giá: ${product.price} VND</p>
                    <img src="${product.imageUrl}" alt="${product.name}" />
                `;
                productsDiv.appendChild(productDiv);
            });
        }

        fetchProducts();
    </script>
</body>
</html>
mongod
node server.js
{
    "name": "iPhone 13",
    "description": "Điện thoại thông minh từ Apple",
    "price": 15000000,
    "category": "Điện thoại",
    "imageUrl": "https://link-to-image.com/iphone13.jpg"
}
