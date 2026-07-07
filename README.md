<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>كافيه مصطفى - الطلب أونلاين</title>
    <style>
        :root {
            --gold: #c8a45c;
            --gold-light: #d4b87a;
            --dark: #1a1a1a;
            --darker: #0d0d0d;
            --brown: #2c1810;
            --brown-light: #3d2b1f;
            --cream: #f0e6d2;
            --red: #e74c3c;
            --green: #27ae60;
            --blue: #3498db;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: var(--dark);
            color: var(--cream);
            min-height: 100vh;
            overflow-x: hidden;
        }

        /* جسيمات الخلفية */
        #particles {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
        }

        .particle {
            position: absolute;
            background: var(--gold);
            border-radius: 50%;
            animation: floatUp linear infinite;
            opacity: 0;
        }

        @keyframes floatUp {
            0% { transform: translateY(100vh) scale(0); opacity: 0; }
            10% { opacity: 0.8; }
            90% { opacity: 0.2; }
            100% { transform: translateY(-10vh) scale(1.5); opacity: 0; }
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        @keyframes slideInDown {
            from { transform: translateY(-100px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideInUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        @keyframes bounceIn {
            0% { transform: scale(0.3); opacity: 0; }
            50% { transform: scale(1.05); }
            70% { transform: scale(0.9); }
            100% { transform: scale(1); opacity: 1; }
        }

        @keyframes shake {
            0%, 100% { transform: translateX(0); }
            25% { transform: translateX(-5px); }
            75% { transform: translateX(5px); }
        }

        @keyframes glow {
            0%, 100% { box-shadow: 0 0 5px var(--gold); }
            50% { box-shadow: 0 0 25px var(--gold), 0 0 50px var(--gold-light); }
        }

        @keyframes spin {
            from { transform: rotate(0deg); }
            to { transform: rotate(360deg); }
        }

        @keyframes ripple {
            0% { transform: scale(0); opacity: 1; }
            100% { transform: scale(4); opacity: 0; }
        }

        .slide-in { animation: slideInUp 0.6s ease-out; }
        .fade-in { animation: fadeIn 0.8s ease-out; }
        .bounce-in { animation: bounceIn 0.6s ease-out; }

        /* شريط التنقل */
        .navbar {
            background: linear-gradient(135deg, rgba(44,24,16,0.95), rgba(74,44,23,0.95));
            backdrop-filter: blur(20px);
            padding: 15px 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border-bottom: 2px solid var(--gold);
            position: sticky;
            top: 0;
            z-index: 1000;
            animation: slideInDown 0.5s ease-out;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
        }

        .navbar .logo {
            display: flex;
            align-items: center;
            gap: 10px;
            cursor: pointer;
        }

        .navbar .logo-icon {
            font-size: 2.5em;
            animation: pulse 2s infinite;
        }

        .navbar .logo-text {
            font-size: 1.8em;
            color: var(--gold);
            font-weight: bold;
            text-shadow: 0 0 20px rgba(200,164,92,0.5);
            letter-spacing: 2px;
        }

        .navbar .nav-links {
            display: flex;
            gap: 20px;
            align-items: center;
        }

        .nav-btn {
            background: transparent;
            border: 2px solid var(--gold);
            color: var(--gold);
            padding: 10px 25px;
            border-radius: 50px;
            cursor: pointer;
            font-size: 1em;
            font-weight: bold;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .nav-btn:hover {
            background: var(--gold);
            color: var(--brown);
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(200,164,92,0.4);
        }

        .nav-btn .ripple-effect {
            position: absolute;
            border-radius: 50%;
            background: rgba(255,255,255,0.5);
            animation: ripple 0.6s linear;
        }

        .cart-btn {
            background: var(--gold);
            color: var(--brown);
            border: none;
            padding: 12px 25px;
            border-radius: 50px;
            cursor: pointer;
            font-weight: bold;
            font-size: 1.1em;
            transition: all 0.3s;
            animation: pulse 2s infinite;
            position: relative;
        }

        .cart-btn:hover {
            background: var(--gold-light);
            transform: scale(1.05);
            box-shadow: 0 10px 30px rgba(200,164,92,0.5);
        }

        .cart-badge {
            background: var(--red);
            color: white;
            border-radius: 50%;
            padding: 3px 8px;
            font-size: 0.75em;
            position: absolute;
            top: -8px;
            right: -8px;
            animation: bounceIn 0.5s;
        }

        /* المحتوى الرئيسي */
        .main-container {
            position: relative;
            z-index: 1;
            max-width: 1300px;
            margin: 0 auto;
            padding: 20px;
        }

        .section-title {
            text-align: center;
            color: var(--gold);
            font-size: 2.2em;
            margin: 50px 0 30px;
            position: relative;
            animation: fadeIn 0.8s ease-out;
        }

        .section-title::after {
            content: '';
            display: block;
            width: 100px;
            height: 3px;
            background: linear-gradient(90deg, transparent, var(--gold), transparent);
            margin: 15px auto;
            border-radius: 10px;
        }

        /* شبكة المنتجات */
        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 25px;
            padding: 10px;
        }

        .product-card {
            background: linear-gradient(145deg, #2c2420, #1f1a16);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid #3a2f25;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            box-shadow: 0 8px 25px rgba(0,0,0,0.3);
            cursor: pointer;
            position: relative;
        }

        .product-card:hover {
            transform: translateY(-12px) scale(1.02);
            border-color: var(--gold);
            box-shadow: 0 20px 50px rgba(200,164,92,0.3), 0 0 30px rgba(200,164,92,0.1);
            animation: glow 2s infinite;
        }

        .product-card .badge {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--red);
            color: white;
            padding: 5px 15px;
            border-radius: 20px;
            font-size: 0.8em;
            z-index: 2;
            animation: pulse 2s infinite;
        }

        .product-image {
            width: 100%;
            height: 220px;
            object-fit: cover;
            transition: all 0.5s;
        }

        .product-card:hover .product-image {
            transform: scale(1.1);
        }

        .product-image-placeholder {
            width: 100%;
            height: 220px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 5em;
            background: linear-gradient(135deg, #3d2b1f, #5a3d2b);
        }

        .product-info {
            padding: 20px;
            position: relative;
        }

        .product-name {
            font-size: 1.3em;
            color: var(--cream);
            margin-bottom: 8px;
        }

        .product-desc {
            color: #a89070;
            font-size: 0.9em;
            margin-bottom: 15px;
        }

        .product-price {
            font-size: 1.5em;
            color: var(--gold);
            font-weight: bold;
            margin-bottom: 15px;
            text-shadow: 0 0 10px rgba(200,164,92,0.3);
        }

        .add-to-cart {
            width: 100%;
            padding: 12px;
            background: linear-gradient(135deg, var(--gold), #b8922e);
            color: var(--brown);
            border: none;
            border-radius: 12px;
            font-size: 1.1em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .add-to-cart:hover {
            background: linear-gradient(135deg, var(--gold-light), var(--gold));
            box-shadow: 0 5px 20px rgba(200,164,92,0.5);
            transform: translateY(-2px);
        }

        .add-to-cart:active {
            transform: scale(0.95);
        }

        .quantity-control {
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 15px;
            margin-top: 10px;
        }

        .qty-btn {
            background: var(--brown-light);
            border: 2px solid var(--gold);
            color: var(--gold);
            width: 35px;
            height: 35px;
            border-radius: 50%;
            font-size: 1.2em;
            cursor: pointer;
            transition: all 0.3s;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .qty-btn:hover {
            background: var(--gold);
            color: var(--brown);
        }

        .qty-display {
            font-size: 1.3em;
            font-weight: bold;
            color: var(--cream);
            min-width: 30px;
            text-align: center;
        }

        /* نافذة السلة */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.85);
            z-index: 2000;
            display: none;
            justify-content: center;
            align-items: center;
            backdrop-filter: blur(5px);
        }

        .modal-overlay.active {
            display: flex;
            animation: fadeIn 0.3s;
        }

        .modal-content {
            background: linear-gradient(145deg, #2c2420, #1a1512);
            border: 2px solid var(--gold);
            border-radius: 25px;
            padding: 30px;
            width: 90%;
            max-width: 650px;
            max-height: 85vh;
            overflow-y: auto;
            position: relative;
            animation: bounceIn 0.5s;
            box-shadow: 0 0 60px rgba(200,164,92,0.2);
        }

        .modal-close {
            position: absolute;
            top: 15px;
            left: 20px;
            background: none;
            border: none;
            color: var(--gold);
            font-size: 2em;
            cursor: pointer;
            transition: all 0.3s;
            z-index: 10;
        }

        .modal-close:hover {
            color: var(--red);
            transform: rotate(90deg) scale(1.2);
        }

        .cart-title {
            color: var(--gold);
            font-size: 1.8em;
            text-align: center;
            margin-bottom: 25px;
        }

        .cart-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            border-bottom: 1px solid #3a2f25;
            animation: slideInUp 0.3s;
            transition: all 0.3s;
        }

        .cart-item:hover {
            background: rgba(200,164,92,0.05);
            border-radius: 10px;
        }

        .cart-item-info {
            flex: 1;
        }

        .cart-item-name {
            color: var(--cream);
            font-weight: bold;
            font-size: 1.1em;
        }

        .cart-item-price {
            color: var(--gold);
            font-size: 0.9em;
        }

        .remove-item {
            background: var(--red);
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 8px;
            cursor: pointer;
            transition: all 0.3s;
        }

        .remove-item:hover {
            background: #c0392b;
            transform: scale(1.1);
        }

        .cart-total {
            font-size: 1.6em;
            color: var(--gold);
            text-align: center;
            margin: 25px 0;
            font-weight: bold;
            text-shadow: 0 0 20px rgba(200,164,92,0.5);
        }

        .payment-methods {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
            justify-content: center;
            margin: 20px 0;
        }

        .payment-option {
            background: #1f1a16;
            padding: 15px 20px;
            border-radius: 15px;
            cursor: pointer;
            border: 2px solid transparent;
            transition: all 0.3s;
            text-align: center;
            font-size: 1.8em;
            flex: 1;
            min-width: 100px;
        }

        .payment-option.selected {
            border-color: var(--gold);
            background: var(--brown);
            box-shadow: 0 0 20px rgba(200,164,92,0.3);
            animation: pulse 1.5s infinite;
        }

        .payment-option span {
            display: block;
            font-size: 0.35em;
            margin-top: 5px;
            color: var(--cream);
        }

        .btn-checkout {
            width: 100%;
            padding: 18px;
            background: linear-gradient(135deg, var(--green), #2ecc71);
            color: white;
            border: none;
            border-radius: 15px;
            font-size: 1.3em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 20px;
            letter-spacing: 1px;
        }

        .btn-checkout:hover {
            box-shadow: 0 10px 40px rgba(46,204,113,0.5);
            transform: translateY(-3px);
        }

        .btn-checkout:active {
            transform: scale(0.95);
        }

        /* صفحة تسجيل الدخول */
        .auth-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 3000;
            display: none;
            justify-content: center;
            align-items: center;
            backdrop-filter: blur(10px);
        }

        .auth-overlay.active {
            display: flex;
            animation: fadeIn 0.3s;
        }

        .auth-box {
            background: linear-gradient(145deg, #2c2420, #1a1512);
            border: 2px solid var(--gold);
            border-radius: 25px;
            padding: 40px;
            width: 90%;
            max-width: 450px;
            animation: bounceIn 0.6s;
            box-shadow: 0 0 80px rgba(200,164,92,0.3);
        }

        .auth-box h2 {
            color: var(--gold);
            text-align: center;
            margin-bottom: 30px;
            font-size: 2em;
        }

        .auth-tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 30px;
        }

        .auth-tab {
            flex: 1;
            padding: 12px;
            background: transparent;
            border: 2px solid var(--gold);
            color: var(--gold);
            border-radius: 12px;
            cursor: pointer;
            font-weight: bold;
            transition: all 0.3s;
        }

        .auth-tab.active {
            background: var(--gold);
            color: var(--brown);
        }

        .form-group {
            margin-bottom: 20px;
            position: relative;
        }

        .form-group label {
            display: block;
            color: var(--gold);
            margin-bottom: 8px;
            font-weight: bold;
        }

        .form-group input {
            width: 100%;
            padding: 14px 20px;
            background: #1f1a16;
            border: 2px solid #3a2f25;
            border-radius: 12px;
            color: var(--cream);
            font-size: 1em;
            transition: all 0.3s;
        }

        .form-group input:focus {
            outline: none;
            border-color: var(--gold);
            box-shadow: 0 0 20px rgba(200,164,92,0.2);
        }

        .btn-submit {
            width: 100%;
            padding: 15px;
            background: linear-gradient(135deg, var(--gold), #b8922e);
            color: var(--brown);
            border: none;
            border-radius: 12px;
            font-size: 1.2em;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
            margin-top: 10px;
        }

        .btn-submit:hover {
            box-shadow: 0 10px 30px rgba(200,164,92,0.4);
            transform: translateY(-2px);
        }

        .error-msg {
            color: var(--red);
            text-align: center;
            margin-top: 10px;
            display: none;
            animation: shake 0.5s;
        }

        .success-msg {
            color: var(--green);
            text-align: center;
            margin-top: 10px;
            display: none;
        }

        /* لوحة تحكم الموظف */
        .admin-panel {
            display: none;
            background: linear-gradient(145deg, #2c2420, #1a1512);
            border: 2px solid var(--gold);
            border-radius: 25px;
            padding: 30px;
            margin: 30px 0;
            animation: slideInUp 0.6s;
        }

        .admin-panel.active {
            display: block;
        }

        .admin-panel h2 {
            color: var(--gold);
            text-align: center;
            margin-bottom: 25px;
            font-size: 1.8em;
        }

        .admin-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .admin-card {
            background: #1f1a16;
            padding: 20px;
            border-radius: 15px;
            border: 1px solid #3a2f25;
        }

        .admin-card h3 {
            color: var(--gold-light);
            margin-bottom: 15px;
        }

        .admin-card input,
        .admin-card select,
        .admin-card textarea {
            width: 100%;
            padding: 10px;
            margin-bottom: 10px;
            background: #2c2420;
            border: 1px solid #3a2f25;
            border-radius: 8px;
            color: var(--cream);
            font-size: 0.95em;
        }

        .admin-card button {
            width: 100%;
            padding: 12px;
            background: var(--gold);
            color: var(--brown);
            border: none;
            border-radius: 8px;
            font-weight: bold;
            cursor: pointer;
            transition: all 0.3s;
        }

        .admin-card button:hover {
            background: var(--gold-light);
        }

        .admin-card button.danger {
            background: var(--red);
            color: white;
        }

        .admin-product-list {
            max-height: 400px;
            overflow-y: auto;
        }

        .admin-product-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px;
            border-bottom: 1px solid #3a2f25;
        }

        /* زر الموظف */
        .admin-toggle {
            position: fixed;
            bottom: 100px;
            left: 30px;
            background: linear-gradient(135deg, #8e44ad, #9b59b6);
            color: white;
            width: 55px;
            height: 55px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.5em;
            z-index: 99;
            cursor: pointer;
            box-shadow: 0 5px 20px rgba(142,68,173,0.4);
            transition: all 0.3s;
            border: none;
        }

        .admin-toggle:hover {
            transform: scale(1.1);
            box-shadow: 0 10px 30px rgba(142,68,173,0.6);
        }

        .admin-toggle.logged-in {
            background: linear-gradient(135deg, var(--green), #2ecc71);
            box-shadow: 0 5px 20px rgba(46,204,113,0.4);
        }

        /* زر واتساب */
        .whatsapp-float {
            position: fixed;
            bottom: 30px;
            left: 30px;
            background: #25D366;
            color: white;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2em;
            z-index: 99;
            cursor: pointer;
            text-decoration: none;
            box-shadow: 0 5px 20px rgba(37,211,102,0.4);
            transition: all 0.3s;
            animation: pulse 2s infinite;
        }

        .whatsapp-float:hover {
            transform: scale(1.15);
        }

        /* إشعارات */
        .toast {
            position: fixed;
            bottom: 30px;
            right: 30px;
            background: var(--green);
            color: white;
            padding: 18px 30px;
            border-radius: 50px;
            z-index: 4000;
            font-weight: bold;
            box-shadow: 0 10px 40px rgba(0,0,0,0.5);
            animation: slideInUp 0.5s, fadeIn 0.5s;
            transition: all 0.5s;
        }

        .toast.error {
            background: var(--red);
        }

        /* Footer */
        .footer {
            text-align: center;
            padding: 40px;
            background: var(--brown);
            color: #a89070;
            margin-top: 60px;
            border-top: 2px solid #4a2c17;
            position: relative;
            z-index: 1;
        }

        .footer .social-links {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin: 20px 0;
        }

        .footer .social-icon {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: #1f1a16;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1.3em;
            transition: all 0.3s;
            cursor: pointer;
            border: 2px solid #3a2f25;
        }

        .footer .social-icon:hover {
            border-color: var(--gold);
            background: var(--gold);
            color: var(--brown);
            transform: translateY(-5px);
            box-shadow: 0 10px 20px rgba(200,164,92,0.3);
        }

        .empty-state {
            text-align: center;
            padding: 40px;
            color: #a89070;
        }

        .empty-state .icon {
            font-size: 4em;
            margin-bottom: 20px;
        }

        /* تحميل دوار */
        .spinner {
            width: 40px;
            height: 40px;
            border: 4px solid #3a2f25;
            border-top: 4px solid var(--gold);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }

        @media (max-width: 768px) {
            .navbar { flex-wrap: wrap; gap: 10px; justify-content: center; padding: 10px; }
            .navbar .logo-text { font-size: 1.3em; }
            .products-grid { grid-template-columns: 1fr 1fr; gap: 15px; }
            .product-image, .product-image-placeholder { height: 150px; }
            .modal-content { padding: 20px; width: 95%; }
            .auth-box { padding: 25px; }
            .section-title { font-size: 1.5em; }
            .admin-grid { grid-template-columns: 1fr; }
        }
    </style>
</head>
<body>

    <!-- جسيمات الخلفية -->
    <div id="particles"></div>

    <!-- شريط التنقل -->
    <nav class="navbar">
        <div class="logo" onclick="scrollToTop()">
            <span class="logo-icon">☕</span>
            <span class="logo-text">كافيه مصطفى</span>
        </div>
        <div class="nav-links">
            <button class="nav-btn" onclick="document.getElementById('drinksSection').scrollIntoView({behavior:'smooth'})">🥤 المشروبات</button>
            <button class="nav-btn" onclick="document.getElementById('foodSection').scrollIntoView({behavior:'smooth'})">🍽️ المأكولات</button>
            <button class="nav-btn" onclick="document.getElementById('paymentInfo').scrollIntoView({behavior:'smooth'})">💳 الدفع</button>
            <button class="cart-btn" onclick="openCart()">
                🛒 السلة <span class="cart-badge" id="cartBadge" style="display:none;">0</span>
            </button>
        </div>
    </nav>

    <!-- المحتوى الرئيسي -->
    <div class="main-container">

        <!-- قسم المشروبات -->
        <div id="drinksSection">
            <h2 class="section-title">🥤 مشروباتنا المميزة</h2>
            <div class="products-grid" id="drinksGrid"></div>
        </div>

        <!-- قسم المأكولات -->
        <div id="foodSection">
            <h2 class="section-title">🍽️ المأكولات والحلويات</h2>
            <div class="products-grid" id="foodGrid"></div>
        </div>

        <!-- معلومات الدفع -->
        <div id="paymentInfo">
            <h2 class="section-title">💳 طرق الدفع المتاحة</h2>
            <div style="display: flex; flex-wrap: wrap; gap: 15px; justify-content: center; padding: 20px;">
                <div class="payment-option" style="font-size: 2.5em; padding: 25px;">💵<span>نقداً عند الاستلام</span></div>
                <div class="payment-option" style="font-size: 2.5em; padding: 25px;">📱<span>فودافون كاش</span></div>
                <div class="payment-option" style="font-size: 2.5em; padding: 25px;">🏦<span>تحويل بنكي</span></div>
                <div class="payment-option" style="font-size: 2.5em; padding: 25px;">💳<span>بطاقة ائتمان</span></div>
                <div class="payment-option" style="font-size: 2.5em; padding: 25px;">📲<span>محفظة إلكترونية</span></div>
            </div>
        </div>

        <!-- لوحة تحكم الموظف -->
        <div class="admin-panel" id="adminPanel">
            <h2>🔧 لوحة تحكم الموظف - إدارة المنتجات</h2>
            <div class="admin-grid">
                <!-- إضافة منتج جديد -->
                <div class="admin-card">
                    <h3>➕ إضافة منتج جديد</h3>
                    <select id="newProductCategory">
                        <option value="drinks">مشروبات</option>
                        <option value="food">مأكولات</option>
                    </select>
                    <input type="text" id="newProductName" placeholder="اسم المنتج">
                    <input type="text" id="newProductDesc" placeholder="وصف المنتج">
                    <input type="number" id="newProductPrice" placeholder="السعر (ج.م)">
                    <input type="text" id="newProductEmoji" placeholder="إيموجي (مثال: ☕)">
                    <input type="text" id="newProductImage" placeholder="رابط الصورة (اختياري)">
                    <button onclick="addNewProduct()">✅ إضافة المنتج</button>
                </div>

                <!-- إدارة المنتجات الحالية -->
                <div class="admin-card">
                    <h3>📋 المنتجات الحالية</h3>
                    <div class="admin-product-list" id="adminProductList"></div>
                </div>

                <!-- إحصائيات -->
                <div class="admin-card">
                    <h3>📊 إحصائيات سريعة</h3>
                    <p style="color: var(--gold);">🥤 المشروبات: <span id="statDrinks">0</span></p>
                    <p style="color: var(--gold);">🍽️ المأكولات: <span id="statFood">0</span></p>
                    <p style="color: var(--gold);">📦 إجمالي المنتجات: <span id="statTotal">0</span></p>
                    <button class="danger" onclick="resetAllData()" style="margin-top:15px;">🗑️ إعادة ضبط كل البيانات</button>
                </div>
            </div>
        </div>
    </div>

    <!-- نافذة السلة -->
    <div class="modal-overlay" id="cartModal">
        <div class="modal-content">
            <button class="modal-close" onclick="closeCart()">✕</button>
            <h2 class="cart-title">🛒 سلة مشترياتك</h2>
            <div id="cartItems"></div>
            <div class="cart-total" id="cartTotal">الإجمالي: 0 ج.م</div>
            <h4 style="color: var(--gold); text-align: center; margin: 15px 0;">اختر طريقة الدفع:</h4>
            <div class="payment-methods" id="cartPaymentMethods">
                <div class="payment-option selected" onclick="selectPayment('cash', this)" data-method="cash">💵<span>نقداً</span></div>
                <div class="payment-option" onclick="selectPayment('vodafone', this)" data-method="vodafone">📱<span>فودافون كاش</span></div>
                <div class="payment-option" onclick="selectPayment('bank', this)" data-method="bank">🏦<span>تحويل بنكي</span></div>
            </div>
            <button class="btn-checkout" onclick="checkout()">✅ تأكيد الطلب وإرساله واتساب</button>
        </div>
    </div>

    <!-- نافذة تسجيل الدخول -->
    <div class="auth-overlay" id="authOverlay">
        <div class="auth-box">
            <h2>🔐 بوابة الموظفين</h2>
            <div class="auth-tabs">
                <button class="auth-tab active" onclick="switchAuthTab('login')">تسجيل الدخول</button>
                <button class="auth-tab" onclick="switchAuthTab('register')">إنشاء حساب</button>
            </div>
            <div id="loginForm">
                <div class="form-group">
                    <label>👤 اسم المستخدم</label>
                    <input type="text" id="loginUsername" placeholder="أدخل اسم المستخدم">
                </div>
                <div class="form-group">
                    <label>🔒 كلمة المرور</label>
                    <input type="password" id="loginPassword" placeholder="أدخل كلمة المرور">
                </div>
                <div class="error-msg" id="loginError"></div>
                <button class="btn-submit" onclick="handleLogin()">🚪 دخول</button>
            </div>
            <div id="registerForm" style="display:none;">
                <div class="form-group">
                    <label>👤 اسم المستخدم</label>
                    <input type="text" id="regUsername" placeholder="اختر اسم مستخدم">
                </div>
                <div class="form-group">
                    <label>📧 البريد الإلكتروني</label>
                    <input type="email" id="regEmail" placeholder="أدخل بريدك الإلكتروني">
                </div>
                <div class="form-group">
                    <label>🔒 كلمة المرور</label>
                    <input type="password" id="regPassword" placeholder="اختر كلمة مرور قوية">
                </div>
                <div class="form-group">
                    <label>🔒 تأكيد كلمة المرور</label>
                    <input type="password" id="regConfirmPassword" placeholder="أعد كتابة كلمة المرور">
                </div>
                <div class="form-group">
                    <label>🔑 كود الموظف السري</label>
                    <input type="password" id="regSecretCode" placeholder="أدخل كود الموظف">
                </div>
                <div class="error-msg" id="registerError"></div>
                <div class="success-msg" id="registerSuccess"></div>
                <button class="btn-submit" onclick="handleRegister()">📝 إنشاء حساب</button>
            </div>
            <button style="width:100%; margin-top:15px; padding:10px; background:transparent; border:1px solid #3a2f25; color:#a89070; border-radius:10px; cursor:pointer;" onclick="closeAuth()">✕ إغلاق</button>
        </div>
    </div>

    <!-- أزرار عائمة -->
    <button class="admin-toggle" id="adminToggle" onclick="toggleAdmin()" title="لوحة تحكم الموظف">👨‍💼</button>
    <a href="https://wa.me/201000000000?text=مرحباً كافيه مصطفى" target="_blank" class="whatsapp-float" title="تواصل واتساب" style="bottom:30px; left:100px;">💬</a>

    <!-- Footer -->
    <div class="footer">
        <h3 style="color: var(--gold);">كافيه مصطفى</h3>
        <p>📍 شارع النخيل، مدينة القهوة | 📞 01000000000</p>
        <div class="social-links">
            <div class="social-icon">📘</div>
            <div class="social-icon">📷</div>
            <div class="social-icon">🐦</div>
            <div class="social-icon">📱</div>
        </div>
        <p style="margin-top:20px;">© 2026 جميع الحقوق محفوظة - <strong>كافيه مصطفى</strong></p>
    </div>

    <script>
        // ============ البيانات ============
        const SECRET_EMPLOYEE_CODE = "MOSTAFA2026"; // كود الموظف السري

        // تحميل البيانات من localStorage أو استخدام الافتراضي
        function loadData() {
            const saved = localStorage.getItem('mustafaCafeData');
            if (saved) return JSON.parse(saved);
            return {
                drinks: [
                    { id: 1, name: "قهوة تركية", desc: "قهوة تركية أصلية على الرمل", price: 25, emoji: "☕", img: "https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=400&h=300&fit=crop" },
                    { id: 2, name: "لاتيه", desc: "لاتيه كريمي بحليب طازج", price: 35, emoji: "🥛", img: "https://images.unsplash.com/photo-1570968915860-54d5c301fa9f?w=400&h=300&fit=crop" },
                    { id: 3, name: "كابتشينو", desc: "كابتشينو إيطالي برغوة كثيفة", price: 30, emoji: "☕", img: "https://images.unsplash.com/photo-1534778101976-62847782c213?w=400&h=300&fit=crop" },
                    { id: 4, name: "شاي كرك", desc: "شاي كرك هندي أصلي", price: 20, emoji: "🍵", img: "https://images.unsplash.com/photo-1564890369478-c89ca6d9cde9?w=400&h=300&fit=crop" },
                    { id: 5, name: "موكا مثلجة", desc: "موكا باردة بصوص الشوكولاتة", price: 40, emoji: "🧊", img: "https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=400&h=300&fit=crop" },
                    { id: 6, name: "عصير مانجو", desc: "عصير مانجو طبيعي 100%", price: 30, emoji: "🥭", img: "https://images.unsplash.com/photo-1546173159-315724a31696?w=400&h=300&fit=crop" },
                    { id: 7, name: "ليمون بالنعناع", desc: "عصير ليمون طازج بالنعناع", price: 22, emoji: "🍋", img: "https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=400&h=300&fit=crop" },
                    { id: 8, name: "سحلب", desc: "سحلب ساخن بالمكسرات والقرفة", price: 28, emoji: "🥜", img: "https://images.unsplash.com/photo-1572490122747-3968b75cc699?w=400&h=300&fit=crop" }
                ],
                food: [
                    { id: 101, name: "كرواسون زبدة", desc: "كرواسون فرنسي طازج", price: 30, emoji: "🥐", img: "https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=400&h=300&fit=crop" },
                    { id: 102, name: "تشيز كيك", desc: "تشيز كيك بالتوت الطازج", price: 45, emoji: "🍰", img: "https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=400&h=300&fit=crop" },
                    { id: 103, name: "وافل شوكولاتة", desc: "وافل بلجيكي بصوص الشوكولاتة", price: 40, emoji: "🧇", img: "https://images.unsplash.com/photo-1558584724-0e4d32ca55a6?w=400&h=300&fit=crop" },
                    { id: 104, name: "بان كيك", desc: "بان كيك أمريكي بالعسل", price: 35, emoji: "🥞", img: "https://images.unsplash.com/photo-1567620905732-2d1ec7ab7445?w=400&h=300&fit=crop" },
                    { id: 105, name: "ساندوتش دجاج", desc: "ساندوتش دجاج مشوي طازج", price: 50, emoji: "🥪", img: "https://images.unsplash.com/photo-1528735602780-2552fd46c7af?w=400&h=300&fit=crop" },
                    { id: 106, name: "بيتزا صغيرة", desc: "بيتزا مارجريتا إيطالية", price: 45, emoji: "🍕", img: "https://images.unsplash.com/photo-1574071318508-1cdbab80d002?w=400&h=300&fit=crop" }
                ]
            };
        }

        function saveData(data) {
            localStorage.setItem('mustafaCafeData', JSON.stringify(data));
        }

        let cafeData = loadData();
        let cart = JSON.parse(localStorage.getItem('mustafaCafeCart') || '[]');
        let selectedPayment = 'cash';
        let isEmployeeLoggedIn = localStorage.getItem('mustafaEmployeeLoggedIn') === 'true';
        let currentUser = JSON.parse(localStorage.getItem('mustafaCurrentUser') || 'null');

        // ============ دوال مساعدة ============
        function showToast(msg, isError = false) {
            const existing = document.querySelector('.toast');
            if (existing) existing.remove();
            const toast = document.createElement('div');
            toast.className = `toast ${isError ? 'error' : ''}`;
            toast.textContent = msg;
            document.body.appendChild(toast);
            setTimeout(() => { toast.style.opacity = '0'; setTimeout(() => toast.remove(), 500); }, 3000);
        }

        function getNextId(category) {
            const items = cafeData[category];
            if (items.length === 0) return category === 'drinks' ? 1 : 101;
            const maxId = Math.max(...items.map(i => i.id));
            return maxId + 1;
        }

        // ============ عرض المنتجات ============
        function renderProducts() {
            const drinksGrid = document.getElementById('drinksGrid');
            const foodGrid = document.getElementById('foodGrid');

            drinksGrid.innerHTML = cafeData.drinks.map(p => createProductCard(p, 'drinks')).join('');
            foodGrid.innerHTML = cafeData.food.map(p => createProductCard(p, 'food')).join('');

            // إحصائيات
            document.getElementById('statDrinks').textContent = cafeData.drinks.length;
            document.getElementById('statFood').textContent = cafeData.food.length;
            document.getElementById('statTotal').textContent = cafeData.drinks.length + cafeData.food.length;
        }

        function createProductCard(product, category) {
            const imgHtml = product.img 
                ? `<img class="product-image" src="${product.img}" alt="${product.name}" loading="lazy" onerror="this.style.display='none';this.nextElementSibling.style.display='flex';">`
                : '';
            const placeholderHtml = `<div class="product-image-placeholder" style="${product.img ? 'display:none;' : ''}">${product.emoji || '🍽️'}</div>`;
            
            const cartItem = cart.find(i => i.id === product.id);
            const qty = cartItem ? cartItem.quantity : 0;

            return `
                <div class="product-card slide-in">
                    ${imgHtml}${placeholderHtml}
                    <div class="product-info">
                        <h3 class="product-name">${product.emoji ? product.emoji + ' ' : ''}${product.name}</h3>
                        <p class="product-desc">${product.desc}</p>
                        <p class="product-price">${product.price} ج.م</p>
                        ${qty > 0 ? `
                            <div class="quantity-control">
                                <button class="qty-btn" onclick="updateCartItem(${product.id}, '${product.name.replace(/'/g, "\\'")}', ${product.price}, -1)">➖</button>
                                <span class="qty-display">${qty}</span>
                                <button class="qty-btn" onclick="updateCartItem(${product.id}, '${product.name.replace(/'/g, "\\'")}', ${product.price}, 1)">➕</button>
                            </div>
                        ` : `
                            <button class="add-to-cart" onclick="updateCartItem(${product.id}, '${product.name.replace(/'/g, "\\'")}', ${product.price}, 1)">🛒 أضف للسلة</button>
                        `}
                    </div>
                </div>
            `;
        }

        // ============ السلة ============
        function updateCartItem(id, name, price, delta) {
            const existing = cart.find(i => i.id === id);
            if (existing) {
                existing.quantity += delta;
                if (existing.quantity <= 0) {
                    cart = cart.filter(i => i.id !== id);
                }
            } else if (delta > 0) {
                cart.push({ id, name, price, quantity: delta });
            }
            saveCart();
            renderProducts();
            updateCartBadge();
            if (delta > 0) showToast(`✅ تمت إضافة "${name}"`);
        }

        function removeFromCart(id) {
            cart = cart.filter(i => i.id !== id);
            saveCart();
            renderProducts();
            updateCartBadge();
            renderCartItems();
        }

        function saveCart() {
            localStorage.setItem('mustafaCafeCart', JSON.stringify(cart));
        }

        function updateCartBadge() {
            const count = cart.reduce((s, i) => s + i.quantity, 0);
            const badge = document.getElementById('cartBadge');
            badge.textContent = count;
            badge.style.display = count > 0 ? 'inline-block' : 'none';
        }

        function openCart() {
            document.getElementById('cartModal').classList.add('active');
            renderCartItems();
        }

        function closeCart() {
            document.getElementById('cartModal').classList.remove('active');
        }

        function renderCartItems() {
            const container = document.getElementById('cartItems');
            const totalEl = document.getElementById('cartTotal');

            if (cart.length === 0) {
                container.innerHTML = '<div class="empty-state"><div class="icon">🛒</div><p>السلة فارغة - أضف منتجاتك المفضلة</p></div>';
                totalEl.textContent = 'الإجمالي: 0 ج.م';
                return;
            }

            let total = 0;
            container.innerHTML = cart.map(item => {
                const itemTotal = item.price * item.quantity;
                total += itemTotal;
                return `
                    <div class="cart-item">
                        <div class="cart-item-info">
                            <span class="cart-item-name">${item.name} ×${item.quantity}</span>
                            <br><span class="cart-item-price">${itemTotal} ج.م</span>
                        </div>
                        <button class="remove-item" onclick="removeFromCart(${item.id})">🗑️ حذف</button>
                    </div>
                `;
            }).join('');

            totalEl.textContent = `الإجمالي: ${total} ج.م`;
        }

        function selectPayment(method, el) {
            selectedPayment = method;
            document.querySelectorAll('#cartPaymentMethods .payment-option').forEach(o => o.classList.remove('selected'));
            el.classList.add('selected');
        }

        function checkout() {
            if (cart.length === 0) {
                showToast('⚠️ السلة فارغة!', true);
                return;
            }

            const total = cart.reduce((s, i) => s + (i.price * i.quantity), 0);
            const paymentNames = { cash: 'نقداً عند الاستلام', vodafone: 'فودافون كاش', bank: 'تحويل بنكي' };
            const orderSummary = cart.map(i => `• ${i.name} ×${i.quantity} = ${i.price * i.quantity} ج.م`).join('\n');
            const message = `🛒 *طلب جديد من كافيه مصطفى*\n━━━━━━━━━━━━━━━\n${orderSummary}\n━━━━━━━━━━━━━━━\n💰 *الإجمالي:* ${total} ج.م\n💳 *طريقة الدفع:* ${paymentNames[selectedPayment]}\n━━━━━━━━━━━━━━━\n🙏 شكراً لثقتكم! نتمنى لكم تجربة ممتعة ☕`;

            const phone = '201000000000'; // غير هذا برقم الواتساب الحقيقي
            const whatsappUrl = `https://wa.me/${phone}?text=${encodeURIComponent(message)}`;

            showToast('🎉 جاري إرسال طلبك للواتساب...');
            cart = [];
            saveCart();
            renderProducts();
            updateCartBadge();
            closeCart();

            setTimeout(() => window.open(whatsappUrl, '_blank'), 1000);
        }

        // ============ المصادقة ============
        function toggleAdmin() {
            if (isEmployeeLoggedIn) {
                const panel = document.getElementById('adminPanel');
                panel.classList.toggle('active');
                if (panel.classList.contains('active')) {
                    renderAdminProductList();
                    panel.scrollIntoView({ behavior: 'smooth' });
                }
            } else {
                openAuth();
            }
        }

        function openAuth() {
            document.getElementById('authOverlay').classList.add('active');
            document.getElementById('loginError').style.display = 'none';
            document.getElementById('registerError').style.display = 'none';
            document.getElementById('registerSuccess').style.display = 'none';
        }

        function closeAuth() {
            document.getElementById('authOverlay').classList.remove('active');
        }

        function switchAuthTab(tab) {
            document.querySelectorAll('.auth-tab').forEach(t => t.classList.remove('active'));
            if (tab === 'login') {
                document.querySelector('.auth-tab:nth-child(1)').classList.add('active');
                document.getElementById('loginForm').style.display = 'block';
                document.getElementById('registerForm').style.display = 'none';
            } else {
                document.querySelector('.auth-tab:nth-child(2)').classList.add('active');
                document.getElementById('loginForm').style.display = 'none';
                document.getElementById('registerForm').style.display = 'block';
            }
            document.getElementById('loginError').style.display = 'none';
            document.getElementById('registerError').style.display = 'none';
            document.getElementById('registerSuccess').style.display = 'none';
        }

        function handleLogin() {
            const username = document.getElementById('loginUsername').value.trim();
            const password = document.getElementById('loginPassword').value.trim();
            const errorEl = document.getElementById('loginError');

            if (!username || !password) {
                errorEl.textContent = '⚠️ الرجاء ملء جميع الحقول';
                errorEl.style.display = 'block';
                return;
            }

            const users = JSON.parse(localStorage.getItem('mustafaEmployees') || '[]');
            const user = users.find(u => u.username === username && u.password === password);

            if (user) {
                isEmployeeLoggedIn = true;
                currentUser = user;
                localStorage.setItem('mustafaEmployeeLoggedIn', 'true');
                localStorage.setItem('mustafaCurrentUser', JSON.stringify(user));
                updateAdminButton();
                closeAuth();
                showToast(`✅ مرحباً ${user.username}! تم تسجيل الدخول بنجاح`);
                document.getElementById('adminPanel').classList.add('active');
                renderAdminProductList();
                document.getElementById('adminPanel').scrollIntoView({ behavior: 'smooth' });
            } else {
                errorEl.textContent = '❌ اسم المستخدم أو كلمة المرور غير صحيحة';
                errorEl.style.display = 'block';
            }
        }

        function handleRegister() {
            const username = document.getElementById('regUsername').value.trim();
            const email = document.getElementById('regEmail').value.trim();
            const password = document.getElementById('regPassword').value.trim();
            const confirmPassword = document.getElementById('regConfirmPassword').value.trim();
            const secretCode = document.getElementById('regSecretCode').value.trim();
            const errorEl = document.getElementById('registerError');
            const successEl = document.getElementById('registerSuccess');

            errorEl.style.display = 'none';
            successEl.style.display = 'none';

            if (!username || !email || !password || !confirmPassword || !secretCode) {
                errorEl.textContent = '⚠️ الرجاء ملء جميع الحقول';
                errorEl.style.display = 'block';
                return;
            }

            if (secretCode !== SECRET_EMPLOYEE_CODE) {
                errorEl.textContent = '❌ كود الموظف السري غير صحيح!';
                errorEl.style.display = 'block';
                return;
            }

            if (password !== confirmPassword) {
                errorEl.textContent = '❌ كلمتا المرور غير متطابقتين';
                errorEl.style.display = 'block';
                return;
            }

            if (password.length < 6) {
                errorEl.textContent = '❌ كلمة المرور يجب أن تكون 6 أحرف على الأقل';
                errorEl.style.display = 'block';
                return;
            }

            const users = JSON.parse(localStorage.getItem('mustafaEmployees') || '[]');
            if (users.find(u => u.username === username)) {
                errorEl.textContent = '❌ اسم المستخدم موجود مسبقاً';
                errorEl.style.display = 'block';
                return;
            }

            const newUser = { u
