IMEX/
│
├── backend/
│   ├── server.js
│   ├── models/
│   │   └── Product.js
│   ├── routes/
│   │   └── productRoutes.js
│   └── .env
│
├── frontend/
│   ├── index.html
│   ├── styles.css
│   ├── script.js
│   └── images/
│       └── logo.png
│
└── package.json
require('dotenv').config();
const express = require('express');
const mongoose = require('mongoose');
const productRoutes = require('./routes/productRoutes');

const app = express();
const PORT = process.env.PORT || 5000;

// Kết nối tới MongoDB
mongoose.connect(process.env.MONGODB_URI, { useNewUrlParser: true, useUnifiedTopology: true })
    .then(() => console.log('MongoDB connected'))
    .catch(err => console.log(err));

// Middleware
app.use(express.json());

// Routes
app.use('/api/products', productRoutes);

// Khởi chạy server
app.listen(PORT, () => {
    console.log(`Server is running on port ${PORT}`);
});
const mongoose = require('mongoose');

const productSchema = new mongoose.Schema({
    name: String,
    specifications: Object,
    price: Number,
    image: String,
    reviews: [String],
});

module.exports = mongoose.model('Product', productSchema);
const express = require('express');
const Product = require('../models/Product');

const router = express.Router();

// Lấy danh sách sản phẩm
router.get('/', async (req, res) => {
    try {
        const products = await Product.find();
        res.json(products);
    } catch (error) {
        res.status(500).json({ message: error.message });
    }
});

// Thêm sản phẩm mới
router.post('/', async (req, res) => {
    const product = new Product(req.body);
    try {
        const savedProduct = await product.save();
        res.status(201).json(savedProduct);
    } catch (error) {
        res.status(400).json({ message: error.message });
    }
});

module.exports = router;
<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>IMEX - Nền tảng Thương mại điện tử</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>IMEX - Thương mại điện tử thiết bị di động</h1>
        <nav>
            <ul>
                <li><a href="#products">Sản phẩm</a></li>
                <li><a href="#community">Cộng đồng</a></li>
                <li><a href="#warranty">Bảo hành</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <section id="products">
            <h2>Sản phẩm nổi bật</h2>
            <div id="product-list"></div>
        </section>

        <section id="community">
            <h2>Cộng đồng người dùng công nghệ</h2>
            <p>Chia sẻ đánh giá và thảo luận về thiết bị di động</p>
        </section>

        <section id="warranty">
            <h2>Thông tin bảo hành</h2>
            <p>Tra cứu thông tin bảo hành thiết bị</p>
        </section>
    </main>

    <footer>
        <p>&copy; 2026 IMEX. Tất cả quyền được bảo lưu.</p>
    </footer>
    
    <script src="script.js"></script>
</body>
</html>
body {
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    color: #333;
}

header {
    background-color: #003366;
    color: white;
    padding: 20px;
}

h1 {
    margin: 0;
}

nav ul {
    list-style: none;
    display: flex;
    padding: 0;
}

nav ul li {
    margin-right: 20px;
}

nav ul li a {
    color: white;
    text-decoration: none;
}

section {
    padding: 20px;
    margin: 20px 0;
    background: white;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0,0,0,0.1);
}

footer {
    text-align: center;
    padding: 10px;
}
const productListDiv = document.getElementById('product-list');

fetch('/api/products')
    .then(response => response.json())
    .then(data => {
        data.forEach(product => {
            const productDiv = document.createElement('div');
            productDiv.innerHTML = `<h3>${product.name}</h3>
                                    <p>Giá: ${product.price} VNĐ</p>
                                    <img src="${product.image}" alt="${product.name}" style="width: 100px;"/><br>
                                    <p>${product.specifications.join(', ')}</p>`;
            productListDiv.appendChild(productDiv);
        });
    })
    .catch(error => console.error('Error:', error));
MONGODB_URI=mongodb://<username>:<password>@localhost:27017/imex
