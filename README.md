<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>ESSENCE - Mode & Parfums de Luxe</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Helvetica', sans-serif;
        }

        nav {
            background: #111;
            color: white;
            padding: 1rem;
            position: fixed;
            width: 100%;
            z-index: 100;
        }

        .nav-content {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 2rem;
            font-weight: bold;
        }

        .nav-links {
            display: flex;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            color: white;
            text-decoration: none;
        }

        .dropdown {
            position: relative;
            display: inline-block;
        }

        .dropdown-content {
            display: none;
            position: absolute;
            background: white;
            min-width: 200px;
            box-shadow: 0 8px 16px rgba(0,0,0,0.2);
            z-index: 1;
            border-radius: 5px;
        }

        .dropdown:hover .dropdown-content {
            display: block;
        }

        .dropdown-content a {
            color: black;
            padding: 12px 16px;
            text-decoration: none;
            display: block;
        }

        .dropdown-content a:hover {
            background: #f1f1f1;
        }

        .cart-icon {
            position: relative;
            cursor: pointer;
        }

        .cart-count {
            position: absolute;
            top: -10px;
            right: -10px;
            background: red;
            color: white;
            border-radius: 50%;
            padding: 2px 6px;
            font-size: 12px;
        }

        .cart-panel {
            position: fixed;
            right: -400px;
            top: 0;
            width: 400px;
            height: 100vh;
            background: white;
            box-shadow: -2px 0 10px rgba(0,0,0,0.1);
            transition: right 0.3s;
            z-index: 1000;
            padding: 20px;
        }

        .cart-panel.open {
            right: 0;
        }

        .cart-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }

        .close-cart {
            cursor: pointer;
            font-size: 1.5rem;
        }

        .cart-items {
            max-height: calc(100vh - 200px);
            overflow-y: auto;
        }

        .cart-item {
            display: flex;
            gap: 1rem;
            margin-bottom: 1rem;
            padding-bottom: 1rem;
            border-bottom: 1px solid #eee;
        }

        .cart-item img {
            width: 80px;
            height: 80px;
            object-fit: cover;
        }

        .cart-total {
            position: absolute;
            bottom: 20px;
            left: 20px;
            right: 20px;
            padding-top: 20px;
            border-top: 1px solid #eee;
        }

        .hero {
            height: 100vh;
            background: linear-gradient(rgba(0,0,0,0.5), rgba(0,0,0,0.5)), url('/api/placeholder/1200/800');
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            text-align: center;
            padding-top: 60px;
        }

        .hero-content h1 {
            font-size: 4rem;
            margin-bottom: 1rem;
        }

        .btn {
            background: white;
            color: black;
            padding: 1rem 2rem;
            border: none;
            border-radius: 30px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .btn:hover {
            transform: scale(1.05);
        }

        .categories {
            max-width: 1200px;
            margin: 4rem auto;
            padding: 0 1rem;
        }

        .category-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 2rem;
            margin-bottom: 4rem;
        }

        .category-card {
            position: relative;
            height: 300px;
            overflow: hidden;
            border-radius: 10px;
        }

        .category-card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .category-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: rgba(0,0,0,0.7);
            color: white;
            padding: 1rem;
            text-align: center;
        }

        .products {
            max-width: 1200px;
            margin: 4rem auto;
            padding: 0 1rem;
        }

        .products h2 {
            text-align: center;
            margin-bottom: 2rem;
            font-size: 2.5rem;
        }

        .product-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .product-card {
            background: white;
            padding: 1rem;
            border-radius: 10px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }

        .product-card:hover {
            transform: translateY(-5px);
        }

        .product-image {
            width: 100%;
            height: 300px;
            background: #f5f5f5;
            margin-bottom: 1rem;
            border-radius: 5px;
            overflow: hidden;
        }

        .product-image img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        .product-info h3 {
            margin-bottom: 0.5rem;
        }

        .price {
            font-weight: bold;
            font-size: 1.2rem;
            color: #111;
            margin-bottom: 1rem;
        }
    </style>
</head>
<body>
    <nav>
        <div class="nav-content">
            <div class="logo">ESSENCE</div>
            <div class="nav-links">
                <div class="dropdown">
                    <a href="#parfums">Parfums</a>
                    <div class="dropdown-content">
                        <a href="#parfums-homme">Homme</a>
                        <a href="#parfums-femme">Femme</a>
                        <a href="#parfums-enfant">Enfant</a>
                    </div>
                </div>
                <div class="dropdown">
                    <a href="#vetements">Vêtements</a>
                    <div class="dropdown-content">
                        <a href="#vetements-homme">Homme</a>
                        <a href="#vetements-femme">Femme</a>
                        <a href="#vetements-enfant">Enfant</a>
                    </div>
                </div>
                <a href="#nouveautes">Nouveautés</a>
                <a href="#collections">Collections</a>
                <div class="cart-icon" onclick="toggleCart()">
                    🛒 <span class="cart-count">0</span>
                </div>
            </div>
        </div>
    </nav>

    <div class="cart-panel">
        <div class="cart-header">
            <h2>Panier</h2>
            <span class="close-cart" onclick="toggleCart()">×</span>
        </div>
        <div class="cart-items">
            <!-- Les articles du panier seront ajoutés ici dynamiquement -->
        </div>
        <div class="cart-total">
            <h3>Total : <span id="cart-total-amount">0,00 €</span></h3>
            <button class="btn" style="width: 100%; margin-top: 1rem;">Commander</button>
        </div>
    </div>

    <section class="hero">
        <div class="hero-content">
            <h1>ESSENCE & STYLE</h1>
            <p>Mode et Parfums de Luxe</p>
            <button class="btn">Découvrir la Collection</button>
        </div>
    </section>

    <section class="categories">
        <h2>Nos Catégories</h2>
        <div class="category-grid">
            <div class="category-card">
                <img src="/api/placeholder/400/300" alt="Parfums">
                <div class="category-overlay">
                    <h3>Parfums</h3>
                </div>
            </div>
            <div class="category-card">
                <img src="/api/placeholder/400/300" alt="Vêtements">
                <div class="category-overlay">
                    <h3>Vêtements</h3>
                </div>
            </div>
            <div class="category-card">
                <img src="/api/placeholder/400/300" alt="Accessoires">
                <div class="category-overlay">
                    <h3>Accessoires</h3>
                </div>
            </div>
        </div>
    </section>

    <section class="products">
        <h2>Nouveautés</h2>
        <div class="product-grid">
            <div class="product-card">
                <div class="product-image">
                    <img src="/api/placeholder/300/300" alt="Parfum Mystique">
                </div>
                <div class="product-info">
                    <h3>Mystique Noir</h3>
                    <p>Une fragrance envoûtante aux notes boisées</p>
                    <p class="price">89,99 €</p>
                    <button class="btn" onclick="addToCart('Mystique Noir', 89.99)">Ajouter au panier</button>
                </div>
            </div>

            <div class="product-card">
                <div class="product-image">
                    <img src="/api/placeholder/300/300" alt="T-shirt Premium">
                </div>
                <div class="product-info">
                    <h3>T-shirt Premium</h3>
                    <p>100% coton bio</p>
                    <p class="price">49,99 €</p>
                    <button class="btn" onclick="addToCart('T-shirt Premium', 49.99)">Ajouter au panier</button>
                </div>
            </div>

            <div class="product-card">
                <div class="product-image">
                    <img src="/api/placeholder/300/300" alt="Veste Élégance">
                </div>
                <div class="product-info">
                    <h3>Veste Élégance</h3>
                    <p>Coupe moderne et matériaux premium</p>
                    <p class="price">149,99 €</p>
                    <button class="btn" onclick="addToCart('Veste Élégance', 149.99)">Ajouter au panier</button>
                </div>
            </div>
        </div>
    </section>

    <script>
        let cart = [];
        let cartOpen = false;

        function toggleCart() {
            const cartPanel = document.querySelector('.cart-panel');
            cartOpen = !cartOpen;
            cartPanel.style.right = cartOpen ? '0' : '-400px';
        }

        function addToCart(name, price) {
            cart.push({ name, price });
            updateCart();
        }

        function removeFromCart(index) {
            cart.splice(index, 1);
            updateCart();
        }

        function updateCart() {
            const cartItems = document.querySelector('.cart-items');
            const cartCount = document.querySelector('.cart-count');
            const totalAmount = document.getElementById('cart-total-amount');
            
            // Mise à jour du nombre d'articles
            cartCount.textContent = cart.length;
            
            // Mise à jour du contenu du panier
            cartItems.innerHTML = cart.map((item, index) => `
                <div class="cart-item">
                    <img src="/api/placeholder/80/80" alt="${item.name}">
                    <div>
                        <h4>${item.name}</h4>
                        <p>${item.price.toFixed(2)} €</p>
                    </div>
                    <button onclick="removeFromCart(${index})">×</button>
                </div>
            `).join('');
            
            // Calcul et mise à jour du total
            const total = cart.reduce((sum, item) => sum + item.price, 0);
            totalAmount.textContent = `${total.toFixed(2)} €`;
        }
    </script>
</body>
</html>
