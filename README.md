<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Evil Bar - إيفل بار | Luxury Cafe & Bar</title>
    
    <!-- Bootstrap 5 RTL -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.rtl.min.css" rel="stylesheet">
    <!-- Font Awesome 6 -->
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <!-- AOS Animations -->
    <link href="https://unpkg.com/aos@2.3.1/dist/aos.css" rel="stylesheet">
    <!-- Google Fonts -->
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&family=Playfair+Display:wght@700;900&display=swap" rel="stylesheet">

    <style>
        :root {
            --bg: #050505;
            --bg2: #0d0d0d;
            --bg3: #1a1a1a;
            --gold: #D4AF37;
            --gold-light: #FFD700;
            --gold-dark: #B8960C;
            --brown: #4E342E;
            --white: #ffffff;
            --gray: #999999;
            --red: #e74c3c;
            --green: #2ecc71;
            --blue: #4285f4;
            --glass: rgba(20,20,20,0.8);
            --glass-border: rgba(212,175,55,0.2);
            --shadow-gold: 0 0 30px rgba(212,175,55,0.3);
            --shadow-gold-big: 0 0 60px rgba(212,175,55,0.5);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }
        html { scroll-behavior: smooth; }
        
        body {
            background: var(--bg);
            color: var(--white);
            font-family: 'Cairo', 'Segoe UI', Tahoma, sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
        }

        /* ========== PARTICLES BACKGROUND ========== */
        #particlesCanvas {
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            z-index: 0;
            pointer-events: none;
        }

        /* ========== CUSTOM SCROLLBAR ========== */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: var(--bg); }
        ::-webkit-scrollbar-thumb { background: var(--gold); border-radius: 10px; }
        ::-webkit-scrollbar-thumb:hover { background: var(--gold-light); }

        /* ========== PRELOADER ========== */
        #preloader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: var(--bg); z-index: 99999;
            display: flex; align-items: center; justify-content: center;
            transition: opacity 0.5s, visibility 0.5s;
        }
        #preloader.hide { opacity: 0; visibility: hidden; }
        
        .preloader-content { text-align: center; }
        .preloader-logo {
            font-family: 'Playfair Display', serif;
            font-size: 50px; font-weight: 900; color: var(--gold);
            letter-spacing: 8px; animation: preloaderPulse 1.5s infinite;
            text-shadow: 0 0 30px rgba(212,175,55,0.6);
        }
        .preloader-bar {
            width: 200px; height: 3px; background: rgba(255,255,255,0.1);
            margin: 20px auto; border-radius: 10px; overflow: hidden;
        }
        .preloader-bar-fill {
            height: 100%; background: var(--gold);
            animation: preloaderBar 1.5s ease-in-out infinite;
            border-radius: 10px;
        }
        @keyframes preloaderPulse {
            0%,100% { opacity: 1; transform: scale(1); }
            50% { opacity: 0.7; transform: scale(1.05); }
        }
        @keyframes preloaderBar {
            0% { width: 0%; margin-left: 0; }
            50% { width: 100%; margin-left: 0; }
            100% { width: 0%; margin-left: 100%; }
        }

        /* ========== GLASS EFFECT ========== */
        .glass {
            background: var(--glass);
            backdrop-filter: blur(20px);
            -webkit-backdrop-filter: blur(20px);
            border: 1px solid var(--glass-border);
            border-radius: 20px;
            box-shadow: 0 8px 32px rgba(0,0,0,0.3);
        }
        .glass:hover { border-color: rgba(212,175,55,0.5); }

        /* ========== AUTH PAGE ========== */
        .auth-wrapper {
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            z-index: 1;
            padding: 20px;
        }
        .auth-card {
            width: 100%; max-width: 480px;
            padding: 40px 35px;
            animation: slideUp 0.6s ease;
        }
        @keyframes slideUp {
            from { opacity: 0; transform: translateY(30px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes slideDown {
            from { opacity: 0; transform: translateY(-30px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .auth-logo {
            text-align: center; margin-bottom: 30px;
        }
        .auth-logo h1 {
            font-family: 'Playfair Display', serif;
            font-size: 42px; font-weight: 900;
            background: linear-gradient(135deg, var(--gold-dark), var(--gold), var(--gold-light));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            background-clip: text;
            letter-spacing: 6px;
        }
        .auth-logo .subtitle {
            color: var(--gray); font-size: 14px; margin-top: 5px;
        }

        /* Auth Tabs */
        .auth-tabs {
            display: flex; gap: 8px; margin-bottom: 25px;
            background: rgba(255,255,255,0.03); border-radius: 15px;
            padding: 5px;
        }
        .auth-tab {
            flex: 1; padding: 12px; text-align: center;
            border: none; background: transparent; color: var(--gray);
            border-radius: 12px; cursor: pointer; font-size: 14px;
            transition: all 0.3s; font-weight: 600;
        }
        .auth-tab.active {
            background: linear-gradient(135deg, var(--gold-dark), var(--gold));
            color: #000; font-weight: 700;
            box-shadow: var(--shadow-gold);
        }
        .auth-tab:hover:not(.active) { color: var(--white); }

        /* Form */
        .form-group { margin-bottom: 18px; }
        .form-group label {
            display: block; margin-bottom: 6px;
            color: var(--gray); font-size: 13px; font-weight: 600;
        }
        .form-input {
            width: 100%; padding: 14px 18px;
            background: rgba(255,255,255,0.04);
            border: 1px solid rgba(255,255,255,0.12);
            border-radius: 14px; color: var(--white);
            font-size: 15px; transition: all 0.3s;
            font-family: 'Cairo', sans-serif;
        }
        .form-input:focus {
            outline: none; border-color: var(--gold);
            box-shadow: 0 0 20px rgba(212,175,55,0.15);
            background: rgba(255,255,255,0.07);
        }
        .form-input::placeholder { color: rgba(255,255,255,0.25); }

        /* Buttons */
        .btn {
            width: 100%; padding: 15px; border: none;
            border-radius: 14px; font-size: 16px; font-weight: 700;
            cursor: pointer; transition: all 0.3s;
            display: flex; align-items: center; justify-content: center;
            gap: 10px; font-family: 'Cairo', sans-serif;
            letter-spacing: 0.5px;
        }
        .btn-gold {
            background: linear-gradient(135deg, #8B7500, var(--gold), #FFE44D);
            color: #000; position: relative; overflow: hidden;
        }
        .btn-gold::before {
            content: ''; position: absolute; top: -50%; left: -50%;
            width: 200%; height: 200%;
            background: linear-gradient(45deg, transparent, rgba(255,255,255,0.3), transparent);
            transform: rotate(45deg); animation: btnShine 3s infinite;
        }
        @keyframes btnShine {
            0% { left: -100%; }
            100% { left: 100%; }
        }
        .btn-gold:hover {
            transform: translateY(-3px);
            box-shadow: 0 10px 30px rgba(212,175,55,0.4);
        }
        
        .btn-google {
            background: #fff; color: #333; font-weight: 600;
        }
        .btn-google:hover { background: #f1f1f1; transform: translateY(-2px); }
        
        .btn-outline {
            background: transparent; border: 2px solid rgba(255,255,255,0.2); color: var(--white);
        }
        .btn-outline:hover { border-color: var(--gold); color: var(--gold); }

        .btn-danger {
            background: var(--red); color: #fff; width: auto; display: inline-flex;
        }

        /* OTP */
        .otp-section { display: none; animation: slideDown 0.4s ease; }
        .otp-section.show { display: block; }
        .otp-inputs {
            display: flex; gap: 10px; justify-content: center; margin: 20px 0;
        }
        .otp-inputs input {
            width: 50px; height: 55px; text-align: center;
            font-size: 22px; font-weight: 700;
            background: rgba(255,255,255,0.05);
            border: 2px solid rgba(255,255,255,0.15);
            border-radius: 12px; color: var(--gold);
            transition: all 0.3s;
        }
        .otp-inputs input:focus {
            outline: none; border-color: var(--gold);
            box-shadow: 0 0 15px rgba(212,175,55,0.3);
        }
        .timer-text {
            text-align: center; color: var(--gold); font-weight: 700;
            font-size: 16px; margin: 10px 0;
        }
        .timer-text.expired { color: var(--red); }

        .divider-text {
            text-align: center; margin: 20px 0; position: relative;
            color: var(--gray); font-size: 13px;
        }
        .divider-text::before, .divider-text::after {
            content: ''; position: absolute; top: 50%;
            width: 35%; height: 1px; background: rgba(255,255,255,0.15);
        }
        .divider-text::before { left: 0; }
        .divider-text::after { right: 0; }

        /* ========== MAIN APP ========== */
        #mainApp { display: none; position: relative; z-index: 1; }
        #mainApp.show { display: block; }

        /* Navbar */
        .navbar-evil {
            position: sticky; top: 0; z-index: 1000;
            background: rgba(5,5,5,0.9); backdrop-filter: blur(25px);
            border-bottom: 1px solid rgba(212,175,55,0.15);
            padding: 12px 0; transition: all 0.3s;
        }
        .navbar-evil.scrolled {
            box-shadow: 0 5px 30px rgba(0,0,0,0.5);
        }
        .brand-logo {
            font-family: 'Playfair Display', serif;
            font-size: 26px; font-weight: 900; color: var(--gold);
            text-decoration: none; letter-spacing: 4px;
            transition: all 0.3s;
        }
        .brand-logo:hover { color: var(--gold-light); text-shadow: var(--shadow-gold-big); }
        
        .nav-link-evil {
            color: var(--white) !important; margin: 0 5px; padding: 8px 15px !important;
            border-radius: 10px; transition: all 0.3s; cursor: pointer; font-weight: 600;
            font-size: 14px;
        }
        .nav-link-evil:hover, .nav-link-evil.active {
            color: var(--gold) !important; background: rgba(212,175,55,0.1);
        }

        .user-btn {
            background: rgba(212,175,55,0.1); border: 1px solid rgba(212,175,55,0.3);
            color: var(--gold); padding: 8px 16px; border-radius: 50px;
            cursor: pointer; font-weight: 600; transition: all 0.3s; font-size: 14px;
        }
        .user-btn:hover { background: var(--gold); color: #000; }

        .cart-btn {
            position: relative; background: transparent; border: 1px solid rgba(255,255,255,0.2);
            color: var(--white); padding: 8px 16px; border-radius: 50px;
            cursor: pointer; transition: all 0.3s; font-size: 14px;
        }
        .cart-btn:hover { border-color: var(--gold); color: var(--gold); }
        .cart-badge {
            position: absolute; top: -8px; right: -8px;
            background: var(--gold); color: #000; border-radius: 50%;
            width: 22px; height: 22px; font-size: 11px;
            display: flex; align-items: center; justify-content: center;
            font-weight: 900;
        }

        /* Hero */
        .hero-section {
            min-height: 100vh; display: flex; align-items: center; justify-content: center;
            text-align: center; position: relative; padding: 100px 20px;
        }
        .hero-title {
            font-family: 'Playfair Display', serif;
            font-size: clamp(50px, 10vw, 100px); font-weight: 900;
            background: linear-gradient(135deg, #8B7500, var(--gold), #FFE44D, var(--gold));
            background-size: 300% 300%;
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
            background-clip: text; animation: gradientShift 4s ease infinite;
            letter-spacing: 10px;
        }
        @keyframes gradientShift {
            0%,100% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
        }
        .hero-subtitle {
            font-size: clamp(16px, 3vw, 22px); color: var(--gray);
            margin: 20px 0 30px; letter-spacing: 2px;
        }
        .hero-buttons { display: flex; gap: 15px; justify-content: center; flex-wrap: wrap; }
        .hero-btn {
            padding: 16px 35px; border-radius: 50px; font-size: 16px;
            font-weight: 700; cursor: pointer; transition: all 0.4s;
            text-decoration: none; display: inline-flex; align-items: center; gap: 10px;
            letter-spacing: 1px;
        }
        .hero-btn-primary {
            background: linear-gradient(135deg, #8B7500, var(--gold));
            color: #000; border: none;
        }
        .hero-btn-primary:hover {
            transform: translateY(-5px); box-shadow: 0 15px 40px rgba(212,175,55,0.5);
        }
        .hero-btn-outline {
            background: transparent; border: 2px solid var(--gold); color: var(--gold);
        }
        .hero-btn-outline:hover {
            background: var(--gold); color: #000; transform: translateY(-5px);
        }

        /* Scroll Down */
        .scroll-down {
            position: absolute; bottom: 30px; left: 50%; transform: translateX(-50%);
            animation: bounceDown 2s infinite;
        }
        .scroll-down span {
            display: block; width: 10px; height: 10px;
            border-right: 2px solid var(--gold); border-bottom: 2px solid var(--gold);
            transform: rotate(45deg); margin: -5px;
            animation: scrollArrow 2s infinite;
        }
        .scroll-down span:nth-child(2) { animation-delay: 0.2s; }
        .scroll-down span:nth-child(3) { animation-delay: 0.4s; }
        @keyframes scrollArrow {
            0% { opacity: 0; transform: rotate(45deg) translate(-10px, -10px); }
            50% { opacity: 1; }
            100% { opacity: 0; transform: rotate(45deg) translate(10px, 10px); }
        }
        @keyframes bounceDown {
            0%,100% { transform: translateX(-50%) translateY(0); }
            50% { transform: translateX(-50%) translateY(15px); }
        }

        /* Sections */
        .section { padding: 100px 0; position: relative; }
        .section-dark { background: var(--bg2); }
        .section-title {
            text-align: center; font-size: clamp(28px, 5vw, 42px);
            font-weight: 900; margin-bottom: 50px; letter-spacing: 2px;
        }
        .section-title .gold { color: var(--gold); }

        /* Product Cards */
        .product-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(280px, 1fr)); gap: 25px; }
        
        .product-card {
            background: rgba(20,20,20,0.8); border: 1px solid rgba(255,255,255,0.08);
            border-radius: 20px; overflow: hidden; transition: all 0.4s;
            position: relative;
        }
        .product-card:hover {
            transform: translateY(-10px);
            border-color: rgba(212,175,55,0.4);
            box-shadow: 0 20px 50px rgba(0,0,0,0.5), 0 0 30px rgba(212,175,55,0.15);
        }
        .product-card-img {
            height: 240px; overflow: hidden; position: relative;
        }
        .product-card-img img {
            width: 100%; height: 100%; object-fit: cover;
            transition: transform 0.6s;
        }
        .product-card:hover .product-card-img img { transform: scale(1.12); }
        
        .product-badge-discount {
            position: absolute; top: 15px; left: 15px;
            background: var(--red); color: #fff; padding: 5px 12px;
            border-radius: 20px; font-size: 12px; font-weight: 700;
            animation: pulseBadge 2s infinite;
        }
        @keyframes pulseBadge {
            0%,100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }
        
        .product-card-actions {
            position: absolute; top: 15px; right: 15px;
            display: flex; flex-direction: column; gap: 8px;
            opacity: 0; transform: translateX(15px); transition: all 0.3s;
        }
        .product-card:hover .product-card-actions {
            opacity: 1; transform: translateX(0);
        }
        .product-action-btn {
            width: 38px; height: 38px; border-radius: 50%;
            border: none; background: rgba(0,0,0,0.7); color: var(--gold);
            cursor: pointer; transition: all 0.3s; display: flex;
            align-items: center; justify-content: center; font-size: 14px;
        }
        .product-action-btn:hover { background: var(--gold); color: #000; }
        
        .product-card-body { padding: 20px; }
        .product-card-body h5 { font-size: 18px; margin-bottom: 5px; font-weight: 700; }
        .product-card-body .desc { color: var(--gray); font-size: 13px; margin-bottom: 12px; }
        .product-price-row { display: flex; align-items: center; gap: 12px; margin-bottom: 10px; }
        .price-old { text-decoration: line-through; color: var(--gray); font-size: 14px; }
        .price-current { color: var(--gold); font-size: 24px; font-weight: 900; }
        .product-rating { color: var(--gold); margin-bottom: 15px; font-size: 13px; }
        
        .btn-add-cart {
            width: 100%; padding: 12px; background: linear-gradient(135deg, #8B7500, var(--gold));
            color: #000; border: none; border-radius: 12px; font-weight: 700;
            cursor: pointer; transition: all 0.3s; font-size: 14px;
        }
        .btn-add-cart:hover { box-shadow: 0 8px 20px rgba(212,175,55,0.4); }

        /* Category Pills */
        .cat-pills {
            display: flex; gap: 10px; flex-wrap: wrap; justify-content: center; margin-bottom: 40px;
        }
        .cat-pill {
            padding: 12px 25px; border-radius: 50px; cursor: pointer;
            border: 1px solid rgba(255,255,255,0.15); background: transparent;
            color: var(--white); transition: all 0.3s; font-weight: 600; font-size: 14px;
        }
        .cat-pill:hover, .cat-pill.active {
            background: var(--gold); color: #000; border-color: var(--gold);
            box-shadow: 0 5px 20px rgba(212,175,55,0.3);
        }

        /* Cart Sidebar */
        .cart-overlay {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.8); z-index: 2000; display: none;
            backdrop-filter: blur(5px);
        }
        .cart-overlay.open { display: block; }
        .cart-sidebar {
            position: fixed; top: 0; right: -450px; width: 420px; height: 100%;
            background: #111; z-index: 2001; transition: right 0.4s cubic-bezier(0.4,0,0.2,1);
            border-left: 1px solid rgba(212,175,55,0.2); padding: 25px; overflow-y: auto;
        }
        .cart-sidebar.open { right: 0; }

        /* Dashboard */
        .dashboard-grid {
            display: grid; grid-template-columns: repeat(auto-fill, minmax(250px, 1fr)); gap: 20px;
        }
        .dashboard-stat {
            background: rgba(20,20,20,0.8); border: 1px solid rgba(255,255,255,0.1);
            border-radius: 20px; padding: 30px; text-align: center; transition: all 0.3s;
        }
        .dashboard-stat:hover {
            border-color: var(--gold); transform: translateY(-5px);
            box-shadow: 0 10px 30px rgba(0,0,0,0.3);
        }
        .dashboard-stat h2 { font-size: 40px; font-weight: 900; color: var(--gold); }
        .dashboard-stat p { color: var(--gray); margin: 5px 0 0; }

        /* Table */
        .table-evil {
            width: 100%; border-collapse: collapse;
        }
        .table-evil th {
            background: rgba(212,175,55,0.1); color: var(--gold);
            padding: 15px; text-align: right; font-weight: 700;
        }
        .table-evil td {
            padding: 15px; border-bottom: 1px solid rgba(255,255,255,0.05);
        }
        .table-evil tr:hover td { background: rgba(255,255,255,0.02); }

        /* Toast */
        .toast-container {
            position: fixed; bottom: 30px; right: 30px; z-index: 9999;
            display: flex; flex-direction: column; gap: 10px;
        }
        .toast-item {
            background: #1a1a1a; border: 1px solid rgba(212,175,55,0.3);
            padding: 16px 24px; border-radius: 14px; color: #fff;
            font-weight: 600; animation: toastIn 0.4s ease;
            box-shadow: 0 10px 30px rgba(0,0,0,0.5);
            display: flex; align-items: center; gap: 10px;
            min-width: 300px;
        }
        .toast-item.success { border-left: 4px solid var(--green); }
        .toast-item.error { border-left: 4px solid var(--red); }
        @keyframes toastIn {
            from { opacity: 0; transform: translateX(100px); }
            to { opacity: 1; transform: translateX(0); }
        }

        /* Footer */
        .footer-evil {
            background: #050505; border-top: 1px solid rgba(212,175,55,0.15);
            padding: 60px 0 30px; text-align: center;
        }
        .footer-evil a { color: var(--gray); text-decoration: none; transition: 0.3s; }
        .footer-evil a:hover { color: var(--gold); }

        /* Responsive */
        @media (max-width: 768px) {
            .hero-title { font-size: 40px; letter-spacing: 4px; }
            .auth-card { padding: 25px 20px; }
            .cart-sidebar { width: 100%; right: -100%; }
            .section { padding: 60px 0; }
            .product-grid { grid-template-columns: repeat(auto-fill, minmax(160px, 1fr)); gap: 15px; }
            .product-card-img { height: 180px; }
        }
    </style>
</head>
<body>

    <!-- Particles Canvas -->
    <canvas id="particlesCanvas"></canvas>

    <!-- Preloader -->
    <div id="preloader">
        <div class="preloader-content">
            <div class="preloader-logo">EVIL BAR</div>
            <div class="preloader-bar"><div class="preloader-bar-fill"></div></div>
        </div>
    </div>

    <!-- Toast Container -->
    <div class="toast-container" id="toastContainer"></div>

    <!-- ==================== AUTH PAGE ==================== -->
    <div id="authPage" class="auth-wrapper">
        <div class="auth-card glass">
            <div class="auth-logo">
                <h1>EVIL BAR</h1>
                <p class="subtitle">✦ أفخم كافيه وبار في المدينة ✦</p>
            </div>

            <!-- Tabs -->
            <div class="auth-tabs" id="authTabs">
                <button class="auth-tab active" onclick="switchAuthTab('email')">
                    <i class="fas fa-envelope"></i> البريد
                </button>
                <button class="auth-tab" onclick="switchAuthTab('phone')">
                    <i class="fas fa-mobile-alt"></i> الهاتف
                </button>
                <button class="auth-tab" onclick="switchAuthTab('google')">
                    <i class="fab fa-google"></i> Google
                </button>
            </div>

            <!-- Email Tab -->
            <div id="tabEmail">
                <div class="form-group">
                    <label>البريد الإلكتروني</label>
                    <input type="email" class="form-input" id="loginEmail" placeholder="example@email.com" dir="ltr">
                </div>
                <div class="form-group">
                    <label>كلمة المرور</label>
                    <input type="password" class="form-input" id="loginPassword" placeholder="••••••••">
                </div>
                <button class="btn btn-gold" onclick="loginEmail()">
                    <i class="fas fa-sign-in-alt"></i> تسجيل الدخول
                </button>
            </div>

            <!-- Phone Tab -->
            <div id="tabPhone" style="display:none;">
                <div class="form-group">
                    <label>رقم الهاتف</label>
                    <input type="tel" class="form-input" id="phoneNumber" placeholder="+20 1xx xxxx xxx" dir="ltr">
                    <small style="color:var(--gray);font-size:11px;">سيتم إرسال رمز تحقق إلى هاتفك</small>
                </div>
                <button class="btn btn-gold" id="btnSendOTP" onclick="sendOTP()">
                    <i class="fas fa-paper-plane"></i> إرسال رمز التحقق
                </button>
                <div class="otp-section" id="otpSection">
                    <label style="text-align:center;display:block;margin:15px 0;color:var(--gray);">أدخل رمز التحقق المكون من 6 أرقام</label>
                    <div class="otp-inputs" id="otpInputs">
                        <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp1">
                        <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp2">
                        <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp3">
                        <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp4">
                        <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp5">
                        <input type="text" maxlength="1" oninput="otpNext(this)" onkeydown="otpPrev(event,this)" id="otp6">
                    </div>
                    <div class="timer-text" id="timerText">02:00</div>
                    <button class="btn btn-gold" id="btnVerifyOTP" onclick="verifyOTP()">
                        <i class="fas fa-check-circle"></i> تأكيد الرمز
                    </button>
                    <button class="btn btn-outline mt-2" id="btnResendOTP" onclick="sendOTP()" disabled>
                        <i class="fas fa-redo"></i> إعادة الإرسال
                    </button>
                </div>
            </div>

            <!-- Google Tab -->
            <div id="tabGoogle" style="display:none;">
                <p style="text-align:center;color:var(--gray);margin-bottom:20px;">تسجيل الدخول باستخدام حساب Google الخاص بك</p>
                <button class="btn btn-google" onclick="loginGoogle()">
                    <i class="fab fa-google" style="color:#4285f4;"></i> تسجيل الدخول بـ Google
                </button>
                <p style="text-align:center;margin-top:15px;font-size:12px;color:var(--gray);">
                    سيتم فتح نافذة اختيار الحساب
                </p>
            </div>

            <div class="divider-text">أو</div>

            <p style="text-align:center;font-size:14px;">
                ليس لديك حساب؟ 
                <a href="#" onclick="showRegister()" style="color:var(--gold);font-weight:700;">إنشاء حساب جديد</a>
            </p>

            <!-- Register -->
            <div id="registerSection" style="display:none;animation:slideDown 0.4s ease;">
                <div class="form-group">
                    <label>الاسم الكامل</label>
                    <input type="text" class="form-input" id="regName" placeholder="الاسم الكامل">
                </div>
                <div class="form-group">
                    <label>البريد الإلكتروني</label>
                    <input type="email" class="form-input" id="regEmail" placeholder="example@email.com" dir="ltr">
                </div>
                <div class="form-group">
                    <label>رقم الهاتف</label>
                    <input type="tel" class="form-input" id="regPhone" placeholder="+20 1xx xxxx xxx" dir="ltr">
                </div>
                <div class="form-group">
                    <label>كلمة المرور</label>
                    <input type="password" class="form-input" id="regPassword" placeholder="••••••••">
                </div>
                <button class="btn btn-gold" onclick="registerUser()">
                    <i class="fas fa-user-plus"></i> إنشاء حساب
                </button>
                <button class="btn btn-outline mt-2" onclick="hideRegister()">
                    العودة لتسجيل الدخول
                </button>
            </div>
        </div>
    </div>

    <!-- ==================== MAIN APP ==================== -->
    <div id="mainApp">
        <!-- Navbar -->
        <nav class="navbar-evil" id="navbarEvil">
            <div class="container">
                <div class="d-flex justify-content-between align-items-center">
                    <a class="brand-logo" href="#" onclick="navigateTo('home')">EVIL BAR</a>
                    <button class="navbar-toggler d-lg-none" type="button" data-bs-toggle="collapse" data-bs-target="#navMenu" style="border-color:var(--gold);">
                        <span class="navbar-toggler-icon" style="filter:invert(1);"></span>
                    </button>
                    <div class="collapse navbar-collapse d-lg-flex" id="navMenu">
                        <ul class="navbar-nav me-auto mb-2 mb-lg-0">
                            <li class="nav-item"><a class="nav-link-evil active" href="#" onclick="navigateTo('home')">🏠 الرئيسية</a></li>
                            <li class="nav-item"><a class="nav-link-evil" href="#" onclick="navigateTo('menu')">📋 المنيو</a></li>
                            <li class="nav-item"><a class="nav-link-evil" href="#" onclick="navigateTo('drinks')">🥤 المشروبات</a></li>
                            <li class="nav-item"><a class="nav-link-evil" href="#" onclick="navigateTo('food')">🍰 المأكولات</a></li>
                            <li class="nav-item"><a class="nav-link-evil" href="#" onclick="navigateTo('reservation')">🍽 حجز طاولة</a></li>
                            <li class="nav-item" id="dashboardNav" style="display:none;"><a class="nav-link-evil" href="#" onclick="navigateTo('dashboard')">📊 لوحة التحكم</a></li>
                        </ul>
                        <div class="d-flex align-items-center gap-2">
                            <button class="cart-btn" onclick="toggleCart()">
                                <i class="fas fa-shopping-cart"></i> <span id="cartBadgeCount">0</span>
                                <span class="cart-badge" id="cartBadge">0</span>
                            </button>
                            <div class="dropdown">
                                <button class="user-btn dropdown-toggle" data-bs-toggle="dropdown" id="userBtn">
                                    <i class="fas fa-user"></i> <span id="userNameNav">حسابي</span>
                                </button>
                                <ul class="dropdown-menu dropdown-menu-end glass" style="background:rgba(10,10,10,0.95);">
                                    <li><a class="dropdown-item" href="#" onclick="navigateTo('profile')" style="color:#fff;">👤 الملف الشخصي</a></li>
                                    <li><a class="dropdown-item" href="#" onclick="navigateTo('orders')" style="color:#fff;">📦 طلباتي</a></li>
                                    <li><hr class="dropdown-divider" style="border-color:rgba(255,255,255,0.1);"></li>
                                    <li><a class="dropdown-item" href="#" onclick="logout()" style="color:var(--red);">🚪 تسجيل الخروج</a></li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </nav>

        <!-- Page Content -->
        <div id="pageContent"></div>

        <!-- Footer -->
        <footer class="footer-evil">
            <div class="container">
                <h3 style="font-family:'Playfair Display',serif;color:var(--gold);font-size:28px;">EVIL BAR</h3>
                <p style="color:var(--gray);">أفخم كافيه وبار في المدينة | منذ 2020</p>
                <div class="mt-3">
                    <a href="#" onclick="navigateTo('home')">الرئيسية</a> |
                    <a href="#" onclick="navigateTo('menu')">المنيو</a> |
                    <a href="#">اتصل بنا</a> |
                    <a href="#">الخصوصية</a>
                </div>
                <p style="color:var(--gray);margin-top:20px;font-size:13px;">&copy; 2024 Evil Bar. Developed by <span style="color:var(--gold);">The Developer</span>. All rights reserved.</p>
            </div>
        </footer>
    </div>

    <!-- Cart Sidebar -->
    <div class="cart-overlay" id="cartOverlay" onclick="toggleCart()"></div>
    <div class="cart-sidebar" id="cartSidebar">
        <div class="d-flex justify-content-between align-items-center mb-3">
            <h5 class="gold-text" style="color:var(--gold);"><i class="fas fa-shopping-cart"></i> سلة المشتريات</h5>
            <button class="btn-close btn-close-white" onclick="toggleCart()"></button>
        </div>
        <div id="cartItemsList"></div>
        <hr style="border-color:rgba(255,255,255,0.1);">
        <div class="d-flex justify-content-between mb-2">
            <span>المجموع:</span>
            <span style="color:var(--gold);font-weight:900;font-size:22px;" id="cartTotal">0 ج.م</span>
        </div>
        <button class="btn btn-gold mt-3" onclick="checkout()"><i class="fas fa-credit-card"></i> إتمام الشراء</button>
        <button class="btn btn-outline mt-2" onclick="clearCart()"><i class="fas fa-trash"></i> تفريغ السلة</button>
    </div>

    <!-- Scripts -->
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js"></script>
    <script src="https://unpkg.com/aos@2.3.1/dist/aos.js"></script>
    <script src="https://accounts.google.com/gsi/client" async defer></script>

    <script>
        // ==================== DEVELOPER ACCOUNT ====================
        // This is the ONLY super admin account
        const DEVELOPER = {
            name: 'المطور',
            email: 'admin@evilbar.com',
            password: 'Admin@2024Secure#',
            phone: '+201000000000',
            role: 'super_admin',
            canAccessDashboard: true
        };

        // ==================== PRODUCTS DATA ====================
        const PRODUCTS = [
            // Hot Drinks
            { id:1, name:'إسبرسو', cat:'hot', catName:'مشروبات ساخنة', price:35, disc:null, rating:4.8, orders:1250, stock:100, img:'https://images.unsplash.com/photo-1510707577719-ae7c14805e3a?w=500&q=80', desc:'إسبرسو إيطالي أصيل، غني وقوي بنكهة عميقة' },
            { id:2, name:'كابتشينو', cat:'hot', catName:'مشروبات ساخنة', price:45, disc:null, rating:4.9, orders:1580, stock:100, img:'https://images.unsplash.com/photo-1534778101976-62847782c213?w=500&q=80', desc:'كابتشينو إيطالي برغوة حليب كثيفة وناعمة' },
            { id:3, name:'لاتيه', cat:'hot', catName:'مشروبات ساخنة', price:45, disc:38, rating:4.7, orders:1320, stock:100, img:'https://images.unsplash.com/photo-1461023058943-07fcbe16d735?w=500&q=80', desc:'لاتيه كريمي ناعم مع حليب مبخر' },
            { id:4, name:'موكا', cat:'hot', catName:'مشروبات ساخنة', price:50, disc:null, rating:4.8, orders:1100, stock:100, img:'https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=500&q=80', desc:'موكا غنية بالشوكولاتة البلجيكية الفاخرة' },
            { id:5, name:'أمريكانو', cat:'hot', catName:'مشروبات ساخنة', price:40, disc:35, rating:4.6, orders:980, stock:100, img:'https://images.unsplash.com/photo-1551030173-122aabc4489c?w=500&q=80', desc:'أمريكانو كلاسيكي منعش بطعم القهوة الصافي' },
            { id:6, name:'قهوة تركي', cat:'hot', catName:'مشروبات ساخنة', price:30, disc:null, rating:4.9, orders:2100, stock:100, img:'https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=500&q=80', desc:'قهوة تركية تقليدية محضرة على الرمل' },

            // Cold Drinks
            { id:7, name:'آيس لاتيه', cat:'cold', catName:'مشروبات باردة', price:50, disc:null, rating:4.6, orders:900, stock:100, img:'https://images.unsplash.com/photo-1517701604599-bb29b565090c?w=500&q=80', desc:'آيس لاتيه منعش مع ثلج وحليب بارد' },
            { id:8, name:'ليمون نعناع', cat:'cold', catName:'مشروبات باردة', price:35, disc:30, rating:4.8, orders:1500, stock:100, img:'https://images.unsplash.com/photo-1621263764928-df1444c5e859?w=500&q=80', desc:'ليمونادة طازجة مع نعناع أخضر منعش' },
            { id:9, name:'عصير برتقال', cat:'cold', catName:'مشروبات باردة', price:30, disc:null, rating:4.5, orders:1100, stock:100, img:'https://images.unsplash.com/photo-1621506289937-a8e4df240d0b?w=500&q=80', desc:'عصير برتقال طبيعي 100% بدون سكر مضاف' },
            { id:10, name:'مانجو', cat:'cold', catName:'مشروبات باردة', price:40, disc:null, rating:4.9, orders:1800, stock:100, img:'https://images.unsplash.com/photo-1546173159-315724a31696?w=500&q=80', desc:'عصير مانجو طازج من أفضل الأنواع' },

            // Food
            { id:11, name:'تشيز كيك', cat:'food', catName:'حلويات', price:60, disc:50, rating:4.9, orders:1600, stock:50, img:'https://images.unsplash.com/photo-1533134242443-d4fd215305ad?w=500&q=80', desc:'تشيز كيك نيويورك الأصلية مع صوص التوت' },
            { id:12, name:'براوني', cat:'food', catName:'حلويات', price:45, disc:null, rating:4.8, orders:1400, stock:60, img:'https://images.unsplash.com/photo-1606313564200-e75d5e30476c?w=500&q=80', desc:'براوني شوكولاتة بلجيكية مع آيس كريم' },
            { id:13, name:'كرواسون', cat:'food', catName:'مخبوزات', price:35, disc:null, rating:4.7, orders:1700, stock:80, img:'https://images.unsplash.com/photo-1555507036-ab1f4038024a?w=500&q=80', desc:'كرواسون فرنسي طازج بالزبدة' },
            { id:14, name:'كيك شوكولاتة', cat:'food', catName:'حلويات', price:70, disc:60, rating:4.9, orders:1900, stock:30, img:'https://images.unsplash.com/photo-1578985545062-69928b1d9587?w=500&q=80', desc:'كيك شوكولاتة ثلاثي الطبقات فاخر' },

            // Alcoholic
            { id:15, name:'هاينكن', cat:'alcohol', catName:'مشروبات كحولية', price:70, disc:null, rating:4.6, orders:950, stock:150, img:'https://images.unsplash.com/photo-1618885472179-5e474019f2a9?w=500&q=80', desc:'بيرة هاينكن الهولندية الأصلية' },
            { id:16, name:'ويسكي', cat:'alcohol', catName:'مشروبات كحولية', price:120, disc:100, rating:4.8, orders:550, stock:80, img:'https://images.unsplash.com/photo-1527281400683-1aae777175f0?w=500&q=80', desc:'ويسكي سكوتش معتق 12 سنة' },
            { id:17, name:'موهيتو', cat:'alcohol', catName:'مشروبات كحولية', price:75, disc:null, rating:4.9, orders:1300, stock:100, img:'https://images.unsplash.com/photo-1551538827-9c037cb4f32a?w=500&q=80', desc:'موهيتو كوبي منعش بالنعناع والليمون' },
            { id:18, name:'مارتيني', cat:'alcohol', catName:'مشروبات كحولية', price:85, disc:null, rating:4.8, orders:750, stock:90, img:'https://images.unsplash.com/photo-1575023782549-62ca0d244b39?w=500&q=80', desc:'مارتيني جاف كلاسيكي مع زيتون' },
        ];

        // ==================== STATE ====================
        let cart = JSON.parse(localStorage.getItem('evilCart') || '[]');
        let currentUser = JSON.parse(localStorage.getItem('evilCurrentUser') || 'null');
        let otpCode = '';
        let otpTimerInterval = null;
        let otpSeconds = 120;
        let isMainAppVisible = false;

        // ==================== INIT ====================
        window.addEventListener('DOMContentLoaded', () => {
            // Preloader
            setTimeout(() => {
                document.getElementById('preloader').classList.add('hide');
            }, 1500);

            // Check if developer account exists
            if (!localStorage.getItem('evilDeveloperCreated')) {
                localStorage.setItem('evilDeveloperCreated', 'true');
                const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
                if (!users.find(u => u.email === DEVELOPER.email)) {
                    users.push(DEVELOPER);
                    localStorage.setItem('evilUsers', JSON.stringify(users));
                }
            }

            // Init particles
            initParticles();
            
            // AOS
            AOS.init({ duration: 800, once: false, offset: 50 });
            
            // GSAP
            gsap.registerPlugin(ScrollTrigger);
            
            // Check if user is logged in
            if (currentUser) {
                showMainApp();
            }
            
            // Scroll navbar effect
            window.addEventListener('scroll', () => {
                const nav = document.getElementById('navbarEvil');
                if (window.scrollY > 50) nav.classList.add('scrolled');
                else nav.classList.remove('scrolled');
            });
        });

        // ==================== PARTICLES ====================
        function initParticles() {
            const canvas = document.getElementById('particlesCanvas');
            const ctx = canvas.getContext('2d');
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            
            const particles = [];
            for (let i = 0; i < 50; i++) {
                particles.push({
                    x: Math.random() * canvas.width,
                    y: Math.random() * canvas.height,
                    size: Math.random() * 2 + 0.5,
                    speedX: (Math.random() - 0.5) * 0.5,
                    speedY: (Math.random() - 0.5) * 0.5,
                    opacity: Math.random() * 0.5 + 0.1,
                    color: Math.random() > 0.7 ? '212,175,55' : '255,255,255'
                });
            }
            
            function animate() {
                ctx.clearRect(0, 0, canvas.width, canvas.height);
                particles.forEach(p => {
                    p.x += p.speedX;
                    p.y += p.speedY;
                    if (p.x < 0) p.x = canvas.width;
                    if (p.x > canvas.width) p.x = 0;
                    if (p.y < 0) p.y = canvas.height;
                    if (p.y > canvas.height) p.y = 0;
                    
                    ctx.beginPath();
                    ctx.arc(p.x, p.y, p.size, 0, Math.PI * 2);
                    ctx.fillStyle = `rgba(${p.color},${p.opacity})`;
                    ctx.fill();
                });
                
                // Draw connections
                particles.forEach((p1, i) => {
                    particles.slice(i+1).forEach(p2 => {
                        const dist = Math.hypot(p1.x-p2.x, p1.y-p2.y);
                        if (dist < 150) {
                            ctx.beginPath();
                            ctx.moveTo(p1.x, p1.y);
                            ctx.lineTo(p2.x, p2.y);
                            ctx.strokeStyle = `rgba(212,175,55,${0.05 * (1 - dist/150)})`;
                            ctx.lineWidth = 0.5;
                            ctx.stroke();
                        }
                    });
                });
                
                requestAnimationFrame(animate);
            }
            animate();
            
            window.addEventListener('resize', () => {
                canvas.width = window.innerWidth;
                canvas.height = window.innerHeight;
            });
        }

        // ==================== AUTH ====================
        function switchAuthTab(tab) {
            document.querySelectorAll('#authTabs .auth-tab').forEach(t => t.classList.remove('active'));
            event.target.classList.add('active');
            document.getElementById('tabEmail').style.display = tab === 'email' ? 'block' : 'none';
            document.getElementById('tabPhone').style.display = tab === 'phone' ? 'block' : 'none';
            document.getElementById('tabGoogle').style.display = tab === 'google' ? 'block' : 'none';
        }

        function loginEmail() {
            const email = document.getElementById('loginEmail').value.trim();
            const password = document.getElementById('loginPassword').value.trim();
            if (!email || !password) return showToast('يرجى ملء جميع الحقول', 'error');
            
            const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
            const user = users.find(u => u.email === email && u.password === password);
            
            if (user) {
                loginSuccess(user);
            } else {
                showToast('بيانات الدخول غير صحيحة', 'error');
            }
        }

        function sendOTP() {
            const phone = document.getElementById('phoneNumber').value.trim();
            if (!phone) return showToast('يرجى إدخال رقم الهاتف', 'error');
            
            // Generate OTP
            otpCode = String(Math.floor(100000 + Math.random() * 900000));
            localStorage.setItem('evilOTP', otpCode);
            localStorage.setItem('evilOTPPhone', phone);
            
            // Show OTP section
            document.getElementById('otpSection').classList.add('show');
            document.getElementById('btnSendOTP').style.display = 'none';
            document.getElementById('otpInputs').querySelector('input').focus();
            
            // Start timer
            otpSeconds = 120;
            updateTimer();
            if (otpTimerInterval) clearInterval(otpTimerInterval);
            otpTimerInterval = setInterval(() => {
                otpSeconds--;
                updateTimer();
                if (otpSeconds <= 0) {
                    clearInterval(otpTimerInterval);
                    document.getElementById('btnResendOTP').disabled = false;
                    document.getElementById('timerText').classList.add('expired');
                    document.getElementById('timerText').textContent = 'انتهت الصلاحية';
                }
            }, 1000);
            
            document.getElementById('btnResendOTP').disabled = true;
            
            // Show OTP in console (simulating SMS)
            console.log(`🔐 رمز التحقق لـ ${phone}: ${otpCode}`);
            showToast(`تم إرسال رمز التحقق إلى ${phone} (تحقق من الـ Console)`);
        }

        function updateTimer() {
            const mins = Math.floor(otpSeconds / 60);
            const secs = otpSeconds % 60;
            document.getElementById('timerText').textContent = 
                `${String(mins).padStart(2,'0')}:${String(secs).padStart(2,'0')}`;
        }

        function otpNext(input) {
            if (input.value.length === 1) {
                const next = input.nextElementSibling;
                if (next) next.focus();
            }
        }

        function otpPrev(e, input) {
            if (e.key === 'Backspace' && input.value.length === 0) {
                const prev = input.previousElementSibling;
                if (prev) prev.focus();
            }
        }

        function verifyOTP() {
            const inputs = document.querySelectorAll('#otpInputs input');
            const code = Array.from(inputs).map(i => i.value).join('');
            const correctOTP = localStorage.getItem('evilOTP');
            
            if (code === correctOTP) {
                clearInterval(otpTimerInterval);
                const phone = localStorage.getItem('evilOTPPhone');
                const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
                let user = users.find(u => u.phone === phone);
                
                if (!user) {
                    user = { name: 'مستخدم', email: '', phone, password: '', role: 'user' };
                    users.push(user);
                    localStorage.setItem('evilUsers', JSON.stringify(users));
                }
                
                loginSuccess(user);
            } else {
                showToast('رمز التحقق غير صحيح', 'error');
            }
        }

        function loginGoogle() {
            // Simulated Google login with account selection
            const googleAccounts = [
                'user1@gmail.com',
                'user2@gmail.com',
                'work@company.com',
                'personal@email.com'
            ];
            
            const selected = prompt(
                '🔐 اختر حساب Google:\n\n' +
                googleAccounts.map((a, i) => `${i+1}. ${a}`).join('\n') +
                '\n\nأدخل رقم الحساب:'
            );
            
            if (selected && googleAccounts[parseInt(selected)-1]) {
                const email = googleAccounts[parseInt(selected)-1];
                const users = JSON.parse(localStorage.getItem('evilUsers') || '[]');
                let user = users.find(u => u.email === email);
                
                if (!user) {
                    user = { name: email.split('@')[0], email, phone: '', password: '', role: 'user', googleAuth: true };
                    users.push(user);
                    localStorage.setItem('evilUsers', JSON.stringify(users));
                }
                
                loginSuccess(user);
            } else if (selected) {
                showToast('حساب غير صالح', 'error');
            }
        }

        function showRegister() {
       
