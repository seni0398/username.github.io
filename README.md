<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HOMME - 남성 의류 전문몰</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #333;
        }

        /* 띠배너 */
        .top-banner {
            background-color: black;
            color: white;
            text-align: center;
            padding: 2px 0;
            font-size: 14px;
            position: relative;
            overflow: hidden;
            height:23.04px;
        }

        .banner-text {
            display: none;
            animation: fadeInOut 6s infinite;
        }

        .banner-text.active {
            display: block;
        }

        @keyframes fadeInOut {
            0%, 20%, 80%, 100% { opacity: 1; }
            40%, 60% { opacity: 0; }
        }

        /* 헤더 */
        .header {
            background: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        /* 로고 영역 */
        .logo-section {
            text-align: center;
            padding: 15px 0;
            border-bottom: 1px solid #f0f0f0;
        }

        .logo {
            max-height: 60px;
            height: auto;
            width: auto;
        }

        /* 네비게이션 헤더 */
        .nav-header {
            max-width: 1200px;
            margin: 0 auto;
            padding: 15px 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .hamburger {
            display: none;
            flex-direction: column;
            cursor: pointer;
        }

        .hamburger span {
            width: 25px;
            height: 3px;
            background: #333;
            margin: 2px 0;
            transition: 0.3s;
        }

        .nav-menu {
            display: flex;
            list-style: none;
            gap: 40px;
            flex: 1;
            justify-content: center;
            margin: 0;
        }

        .nav-menu a {
            text-decoration: none;
            color: #333;
            font-weight: 600;
            font-size: 16px;
            transition: color 0.3s;
            position: relative;
        }

        .nav-menu a:hover {
            color: #3498db;
        }

        .nav-menu .new-item {
            color: #333;
            font-weight: 600;
        }

        .nav-menu .new-item:hover {
            color: #c0392b;
        }

        .header-icons {
            display: flex;
            gap: 15px;
        }

        .icon {
            width: 24px;
            height: 24px;
            cursor: pointer;
            fill: #333;
            transition: fill 0.3s;
        }

        .icon:hover {
            fill: #3498db;
        }

        /* 스마트팝업 */
        .popup {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 2000;
        }

        .popup-content {
            background: white;
            padding: 40px;
            border-radius: 15px;
            text-align: center;
            max-width: 400px;
            width: 90%;
            position: relative;
        }

        .popup-close {
            position: absolute;
            top: 15px;
            right: 20px;
            font-size: 24px;
            cursor: pointer;
            color: #999;
        }

        .coupon-text {
            font-size: 18px;
            margin: 20px 0;
            color: #2c3e50;
        }

        .coupon-amount {
            font-size: 36px;
            font-weight: bold;
            color: #e74c3c;
            margin: 10px 0;
        }

        .signup-btn {
            background: linear-gradient(45deg, #3498db, #2c3e50);
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 25px;
            font-size: 16px;
            cursor: pointer;
            transition: transform 0.3s;
        }

        .signup-btn:hover {
            transform: translateY(-2px);
        }

        /* 메인 배너 슬라이드 */
        .main-banner {
            height: 400px;
            position: relative;
            overflow: hidden;
        }

        .banner-slider {
            position: relative;
            width: 300%; /* 3개 슬라이드 (원본 2개 + 복사본 1개) */
            height: 100%;
            display: flex;
            animation: infiniteSlide 12s ease-in-out infinite;
        }

        .banner-slide {
            width: 33.333%; /* 전체 너비의 1/3 */
            height: 100%;
            background-size: cover;
            background-position: center;
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
        }

        @keyframes infiniteSlide {
            0% {
                transform: translateX(0);
            }
            40% {
                transform: translateX(0);
            }
            50% {
                transform: translateX(-33.333%);
            }
            90% {
                transform: translateX(-33.333%);
            }
            100% {
                transform: translateX(-66.666%);
            }
        }

        /* 호버 시 애니메이션 일시정지 */
        .banner-slider:hover {
            animation-play-state: paused;
        }

        .banner-slide:nth-child(1) {
            background-image: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), url('https://ifh.cc/g/CbvPAZ.jpg');
        }

        .banner-slide:nth-child(2) {
            background-image: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), url('https://ifh.cc/g/SxR5m8.png');
        }

        .banner-content {
            text-align: center;
            color: white;
            z-index: 10;
            position: relative;
        }

        .banner-content h1 {
            font-size: 48px;
            margin-bottom: 20px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .banner-content p {
            font-size: 18px;
            margin-bottom: 30px;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.5);
        }

        /* 슬라이드 네비게이션 */
        .banner-nav {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            display: flex;
            gap: 10px;
            z-index: 20;
        }

        .banner-dot {
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: rgba(255,255,255,0.5);
            cursor: pointer;
            transition: background 0.3s;
        }

        .banner-dot.active {
            background: white;
        }

        .cta-button {
            background: #3498db;
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 25px;
            font-size: 16px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .cta-button:hover {
            background: #2980b9;
        }

        /* 상품 섹션 */
        .products-section {
            max-width: 1200px;
            margin: 50px auto;
            padding: 0 20px;
        }

        .section-title {
            text-align: center;
            font-size: 32px;
            margin-bottom: 40px;
            color: #2c3e50;
        }

        .products-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-bottom: 50px;
        }

        .product-card {
            background: white;
            border-radius: 15px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            cursor: pointer;
        }

        .product-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
        }

        .product-image {
            width: 100%;
            height: 250px;
            position: relative;
            overflow: hidden;
            border-radius: 10px 10px 0 0;
        }

        .product-image .main-image,
        .product-image .hover-image {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-size: cover;
            background-position: center;
            transition: opacity 0.8s ease;
        }

        .product-image .hover-image {
            opacity: 0;
        }

        .product-card:hover .product-image .hover-image {
            opacity: 1;
        }

        .product-card:hover .product-image .main-image {
            opacity: 0;
        }

        /* 자동 이미지 변경 애니메이션 */
        .product-image.auto-change .hover-image {
            animation: autoImageChange 4s ease-in-out infinite;
        }

        @keyframes autoImageChange {
            0%, 50% {
                opacity: 0;
            }
            25% {
                opacity: 1;
            }
            75%, 100% {
                opacity: 0;
            }
        }

        .product-info {
            padding: 20px;
        }

        .product-name {
            font-size: 16px;
            font-weight: 600;
            margin-bottom: 8px;
            color: #2c3e50;
        }

        .product-color {
            font-size: 14px;
            color: #7f8c8d;
            margin-bottom: 10px;
        }

        .delivery-info {
            font-size: 12px;
            color: #e74c3c;
            margin-bottom: 10px;
        }

        .product-price {
            font-size: 18px;
            font-weight: bold;
            color: #2c3e50;
        }

        .product-original-price {
            text-decoration: line-through;
            color: #999;
            font-size: 14px;
            margin-right: 10px;
        }

        /* 상품 상세 모달 */
        .product-modal {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 2000;
            overflow-y: auto;
        }

        .modal-content {
            background: white;
            width: 90%;
            max-width: 800px;
            max-height: 90vh;
            overflow-y: auto;
            border-radius: 15px;
        }

        .modal-header {
            padding: 20px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .modal-close {
            font-size: 24px;
            cursor: pointer;
            color: #999;
        }

        .modal-body {
            padding: 30px;
        }

        .product-detail-image {
            width: 100%;
            height: 300px;
            background: #f8f9fa;
            border-radius: 10px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #666;
        }

        .product-options {
            margin: 20px 0;
        }

        .option-group {
            margin-bottom: 15px;
        }

        .option-label {
            display: block;
            margin-bottom: 5px;
            font-weight: 600;
        }

        .option-select {
            width: 100%;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 14px;
        }

        .quantity-control {
            display: flex;
            align-items: center;
            gap: 10px;
            margin: 20px 0;
        }

        .qty-btn {
            width: 30px;
            height: 30px;
            border: 1px solid #ddd;
            background: white;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .qty-input {
            width: 60px;
            text-align: center;
            border: 1px solid #ddd;
            padding: 5px;
        }

        /* 고정 구매 버튼 */
        .fixed-purchase {
            position: fixed;
            bottom: 0;
            left: 0;
            right: 0;
            background: white;
            padding: 15px 20px;
            box-shadow: 0 -2px 10px rgba(0,0,0,0.1);
            display: none;
            z-index: 1500;
        }

        .purchase-buttons {
            display: flex;
            gap: 10px;
            max-width: 800px;
            margin: 0 auto;
        }

        .cart-btn, .buy-btn, .kakao-btn {
            flex: 1;
            padding: 15px;
            border: none;
            border-radius: 5px;
            font-size: 14px;
            cursor: pointer;
            transition: background 0.3s;
        }

        .cart-btn {
            background: #95a5a6;
            color: white;
        }

        .buy-btn {
            background: #2c3e50;
            color: white;
        }

        .kakao-btn {
            background: #fee500;
            color: #3c1e1e;
        }

        /* 우측 하단 고정 버튼 */
        .floating-buttons {
            position: fixed;
            bottom: 80px;
            right: 20px;
            display: flex;
            flex-direction: column;
            gap: 10px;
            z-index: 1000;
        }

        .floating-btn {
            width: 60px;
            height: 60px;
            border-radius: 50%;
            border: none;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            font-size: 12px;
            font-weight: 600;
            transition: transform 0.3s;
        }

        .floating-btn:hover {
            transform: scale(1.1);
        }

        .channel-talk {
            background: #6c5ce7;
            color: white;
        }

        /* 추천 상품 섹션 */
        .upsell-section {
            background: #f8f9fa;
            padding: 50px 0;
            margin-top: 50px;
        }

        .shipping-notice {
            text-align: center;
            background: #e8f4fd;
            padding: 20px;
            margin: 30px 0;
            border-radius: 10px;
            color: #2c3e50;
            font-weight: 600;
        }

        /* 반응형 */
        @media (max-width: 768px) {
            .hamburger {
                display: flex;
            }

            .nav-menu {
                display: none;
            }

            .nav-header {
                padding: 10px 15px;
                justify-content: space-between;
            }

            .logo-section {
                padding: 10px 0;
            }

            .logo {
                max-height: 40px;
            }

            .main-banner {
                height: 250px;
            }

            .banner-content h1 {
                font-size: 32px;
            }

            .banner-content p {
                font-size: 16px;
            }

            .products-grid {
                grid-template-columns: repeat(2, 1fr);
                gap: 15px;
            }

            .floating-buttons {
                bottom: 60px;
                right: 15px;
            }

            .floating-btn {
                width: 50px;
                height: 50px;
                font-size: 10px;
            }
        }
    </style>
</head>
<body>
      <!-- 띠배너 -->
    <div class="top-banner">
        <div class="banner-text active"> 15시 이전 주문 시 당일배송</div>
        <div class="banner-text">70,000원 이상 구매 시 무료배송</div>
        <div class="banner-text"> 신규 회원가입 3,000원 쿠폰</div>
    </div>

    <!-- 헤더 -->
    <header class="header">
        <!-- 로고 섹션 -->
        <div class="logo-section">
            <img src="https://ifh.cc/g/2MqCk4.png" alt="HOMME 로고" class="logo">
        </div>
        
        <!-- 네비게이션 섹션 -->
        <div class="nav-header">
    <div class="hamburger" onclick="toggleMenu()">
        <span></span>
        <span></span>
        <span></span>
    </div>
    
    <nav class="nav-menu">
        <a href="#best">BEST</a>
        <a href="#same-day">당일발송</a>
        <a href="#new" class="new-item">NEW 7%</a>
        <a href="#top">TOP</a>
        <a href="#shirts">SHIRTS</a>
        <a href="#bottom">BOTTOM</a>
        <a href="#acc">ACC</a>
        <a href="#shoes">SHOES</a>
        <a href="#community">COMMUNITY</a>
    </nav>
    
    <div class="header-icons">
        <svg class="icon" viewBox="0 0 24 24">
            <path d="M15.5 14h-.79l-.28-.27A6.471 6.471 0 0 0 16 9.5 6.5 6.5 0 1 0 9.5 16c1.61 0 3.09-.59 4.23-1.57l.27.28v.79l5 4.99L20.49 19l-4.99-5zm-6 0C7.01 14 5 11.99 5 9.5S7.01 5 9.5 5 14 7.01 14 9.5 11.99 14 9.5 14z"/>
        </svg>
        <svg class="icon" viewBox="0 0 24 24">
            <path d="M7 18c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2zM1 2v2h2l3.6 7.59-1.35 2.45c-.16.28-.25.61-.25.96 0 1.1.9 2 2 2h12v-2H7.42c-.14 0-.25-.11-.25-.25l.03-.12L8.1 13h7.45c.75 0 1.41-.41 1.75-1.03L21.7 4H5.21l-.94-2H1zm16 16c-1.1 0-2 .9-2 2s.9 2 2 2 2-.9 2-2-.9-2-2-2z"/>
        </svg>
        <svg class="icon" viewBox="0 0 24 24">
            <path d="M12 12c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm0 2c-2.67 0-8 1.34-8 4v2h16v-2c0-2.66-5.33-4-8-4z"/>
        </svg>
    </div>
</div>

<style>
/* 반응형 메뉴 스타일 추가 */
.nav-menu {
    display: flex;
    list-style: none;
    gap: 40px;
    flex: 1;
    justify-content: center;
    margin: 0;
}

.nav-menu a {
    text-decoration: none;
    color: #333;
    font-weight: 600;
    font-size: 12px;
    transition: color 0.3s;
    position: relative;
    white-space: nowrap;
}

/* 태블릿 크기 */
@media (max-width: 1024px) {
    .nav-menu {
        gap: 25px;
    }
    .nav-menu a {
        font-size: 10px;
    }
}

/* 작은 태블릿 크기 */
@media (max-width: 900px) {
    .nav-menu {
        gap: 15px;
    }
    .nav-menu a {
        font-size: 10px;
    }
}

/* 큰 모바일 크기 */
@media (max-width: 768px) {
    .nav-menu {
        gap: 10px;
    }
    .nav-menu a {
        font-size: 12px;
    }
}

/* 작은 모바일에서는 햄버거 메뉴 */
@media (max-width: 640px) {
    .hamburger {
        display: flex !important;
    }
    .nav-menu {
        display: none !important;
    }
}
</style>
    </header>

    <!-- 메인 배너 슬라이드 -->
    <section class="main-banner">
        <div class="banner-slider" id="bannerSlider">
            <!-- 첫 번째 이미지 -->
            <div class="banner-slide" style="background-image: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), url('https://ifh.cc/g/CbvPAZ.jpg');">
                <div class="banner-content">
                    <h1>2025 NEW COLLECTION</h1>
                    <p>스타일리시한 남성 의류를 만나보세요</p>
                    <button class="cta-button">컬렉션 보기</button>
                </div>
            </div>
            <!-- 두 번째 이미지 -->
            <div class="banner-slide" style="background-image: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), url('https://ifh.cc/g/SxR5m8.png');">
                <div class="banner-content">
                    <h1>PREMIUM FASHION</h1>
                    <p>고품질 원단으로 만든 프리미엄 의류</p>
                    <button class="cta-button">상품 보기</button>
                </div>
            </div>
            <!-- 무한 루프를 위한 첫 번째 이미지 복사본 -->
            <div class="banner-slide" style="background-image: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.3)), url('https://ifh.cc/g/CbvPAZ.jpg');">
                <div class="banner-content">
                    <h1>2025 NEW COLLECTION</h1>
                    <p>스타일리시한 남성 의류를 만나보세요</p>
                    <button class="cta-button">컬렉션 보기</button>
                </div>
            </div>
        </div>
        
        <!-- 슬라이드 네비게이션 -->
        <div class="banner-nav">
            <div class="banner-dot active"></div>
            <div class="banner-dot"></div>
        </div>
    </section>

    <!-- 베스트 상품 -->
    <section class="products-section">
        <h2 class="section-title">BEST PRODUCTS</h2>
        <div class="products-grid">
            <div class="product-card" onclick="openProductModal('오버핏 코튼 셔츠')">
                <div class="product-image auto-change">
                    <div class="main-image" style="background-image: url('https://ifh.cc/g/j6q7Qh.jpg');"></div>
                    <div class="hover-image" style="background-image: url('https://ifh.cc/g/5wqkW6.jpg');"></div>
                </div>
                <div class="product-info">
                    <div class="product-name">오버핏 코튼 셔츠</div>
                    <div class="product-color">색깔: 화이트, 블랙, 네이비</div>
                    <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                    <div class="product-price">
                        <span class="product-original-price">59,000원</span>
                        45,000원
                    </div>
                </div>
            </div>
            
            <div class="product-card" onclick="openProductModal('슬림핏 면바지')">
                <div class="product-image auto-change">
                    <div class="main-image" style="background-image: url('https://ifh.cc/g/LAwATh.jpg');"></div>
                    <div class="hover-image" style="background-image: url('https://ifh.cc/g/4aCROl.jpg');"></div>
                </div>
                <div class="product-info">
                    <div class="product-name">슬림핏 면바지</div>
                    <div class="product-color">색깔: 베이지, 블랙, 카키</div>
                    <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                    <div class="product-price">38,000원</div>
                </div>
            </div>
            
            <div class="product-card" onclick="openProductModal('캐주얼 니트')">
                <div class="product-image auto-change">
                    <div class="main-image" style="background-image: url('https://ifh.cc/g/pWNKlR.jpg');"></div>
                    <div class="hover-image" style="background-image: url('https://ifh.cc/g/cyg5fl.jpg');"></div>
                </div>
                <div class="product-info">
                    <div class="product-name">캐주얼 니트</div>
                    <div class="product-color">색깔: 그레이, 네이비, 브라운</div>
                    <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                    <div class="product-price">52,000원</div>
                </div>
            </div>
            
            <div class="product-card" onclick="openProductModal('레더 재킷')">
                <div class="product-image auto-change">
                    <div class="main-image" style="background-image: url('https://ifh.cc/g/j6q7Qh.jpg');"></div>
                    <div class="hover-image" style="background-image: url('https://ifh.cc/g/LAwATh.jpg');"></div>
                </div>
                <div class="product-info">
                    <div class="product-name">레더 재킷</div>
                    <div class="product-color">색깔: 블랙, 브라운</div>
                    <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                    <div class="product-price">
                        <span class="product-original-price">180,000원</span>
                        150,000원
                    </div>
                </div>
            </div>
            
            <div class="product-card" onclick="openProductModal('데님 재킷')">
                <div class="product-image auto-change">
                    <div class="main-image" style="background-image: url('https://ifh.cc/g/5wqkW6.jpg');"></div>
                    <div class="hover-image" style="background-image: url('https://ifh.cc/g/pWNKlR.jpg');"></div>
                </div>
                <div class="product-info">
                    <div class="product-name">데님 재킷</div>
                    <div class="product-color">색깔: 인디고, 라이트블루</div>
                    <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                    <div class="product-price">68,000원</div>
                </div>
            </div>
            
            <div class="product-card" onclick="openProductModal('스웨터')">
                <div class="product-image auto-change">
                    <div class="main-image" style="background-image: url('https://ifh.cc/g/4aCROl.jpg');"></div>
                    <div class="hover-image" style="background-image: url('https://ifh.cc/g/cyg5fl.jpg');"></div>
                </div>
                <div class="product-info">
                    <div class="product-name">스웨터</div>
                    <div class="product-color">색깔: 화이트, 그레이, 블랙</div>
                    <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                    <div class="product-price">46,000원</div>
                </div>
            </div>
        </div>
        
       
    </section>

    <!-- 추천 상품 섹션 -->
    <section class="upsell-section">
        <div class="products-section">
            <h2 class="section-title">다른 고객이 함께 본 상품</h2>
            <div class="products-grid">
                <div class="product-card">
                    <div class="product-image auto-change">
                        <div class="main-image" style="background-image: url('https://ifh.cc/g/cyg5fl.jpg');"></div>
                        <div class="hover-image" style="background-image: url('https://ifh.cc/g/j6q7Qh.jpg');"></div>
                    </div>
                    <div class="product-info">
                        <div class="product-name">베이직 후드티</div>
                        <div class="product-color">색깔: 블랙, 그레이, 네이비</div>
                        <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                        <div class="product-price">42,000원</div>
                    </div>
                </div>
                
                <div class="product-card">
                    <div class="product-image auto-change">
                        <div class="main-image" style="background-image: url('https://ifh.cc/g/pWNKlR.jpg');"></div>
                        <div class="hover-image" style="background-image: url('https://ifh.cc/g/4aCROl.jpg');"></div>
                    </div>
                    <div class="product-info">
                        <div class="product-name">스키니 진</div>
                        <div class="product-color">색깔: 인디고, 블랙</div>
                        <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                        <div class="product-price">48,000원</div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- 상품 상세 모달 -->
    <div id="productModal" class="product-modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3 id="modalProductName">상품명</h3>
                <span class="modal-close" onclick="closeProductModal()">&times;</span>
            </div>
            <div class="modal-body">
                <div class="product-detail-image">상품 이미지 (자동 스크롤)</div>
                
                <div class="product-info">
                    <div class="product-name" id="modalProductTitle">오버핏 코튼 셔츠</div>
                    <div class="product-color">색깔: 화이트, 블랙, 네이비</div>
                    <div class="delivery-info">15시 이전 주문 시 당일배송</div>
                    <div class="product-price">45,000원</div>
                </div>
                
                <div class="product-options">
                    <div class="option-group">
                        <label class="option-label">색상</label>
                        <select class="option-select">
                            <option>화이트</option>
                            <option>블랙</option>
                            <option>네이비</option>
                        </select>
                    </div>
                    
                    <div class="option-group">
                        <label class="option-label">사이즈</label>
                        <select class="option-select">
                            <option>S</option>
                            <option>M</option>
                            <option>L</option>
                            <option>XL</option>
                        </select>
                    </div>
                    
                    <div class="quantity-control">
                        <span>수량:</span>
                        <button class="qty-btn" onclick="changeQuantity(-1)">-</button>
                        <input type="number" class="qty-input" value="1" min="1" id="quantity">
                        <button class="qty-btn" onclick="changeQuantity(1)">+</button>
                    </div>
                </div>
                
                <div style="margin-top: 30px;">
                    <h4>📸 사진 리뷰</h4>
                    <p style="color: #666; margin: 10px 0;">고객들의 실제 착용 사진을 확인해보세요.</p>
                    
                    <h4 style="margin-top: 20px;">📋 상품 정보</h4>
                    <p style="color: #666; margin: 10px 0;">소재: 면 100%<br>원산지: 한국<br>세탁방법: 드라이클리닝</p>
                    
                    <h4 style="margin-top: 20px;">🎁 추가 구성상품</h4>
                    <p style="color: #666; margin: 10px 0;">코디 추천 아이템을 함께 구매해보세요.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- 고정 구매 버튼 -->
    <div id="fixedPurchase" class="fixed-purchase">
        <div class="purchase-buttons">
            <button class="cart-btn">장바구니</button>
            <button class="buy-btn">구매하기</button>
            <button class="kakao-btn">카카오페이</button>
        </div>
    </div>

    <!-- 우측 하단 고정 버튼 -->
    <div class="floating-buttons">
        <a href="#" class="floating-btn channel-talk" style="background-image: url('https://ifh.cc/g/Rmgjon.png'); background-size: 60px 60px; background-repeat: no-repeat; background-position: center; width: 60px; height: 60px; border-radius: 100px; text-decoration: none; display: flex; align-items: center; justify-content: center; background-size: 61px;"></a>
        <a href="#" class="floating-btn kakao-talk" style="background-image: url('https://ifh.cc/g/vndkgc.png'); background-size: 60px 60px; background-repeat: no-repeat; background-position: center; width: 60px; height: 60px; border-radius: 100px; text-decoration: none; display: flex; align-items: center; justify-content: center;"></a>
    </div>

    <script>
        // 띠배너 자동 순환
        let currentBanner = 0;
        const banners = document.querySelectorAll('.banner-text');
        
        function rotateBanner() {
            banners[currentBanner].classList.remove('active');
            currentBanner = (currentBanner + 1) % banners.length;
            banners[currentBanner].classList.add('active');
        }
        
        setInterval(rotateBanner, 3000);

        // 메인 배너 자동 슬라이드 (CSS 애니메이션으로 처리)
        // 닷 네비게이션 애니메이션
        const dots = document.querySelectorAll('.banner-dot');
        let currentDotIndex = 0;
        
        function updateDots() {
            dots.forEach(dot => dot.classList.remove('active'));
            dots[currentDotIndex].classList.add('active');
            currentDotIndex = (currentDotIndex + 1) % dots.length;
        }
        
        // 6초마다 닷 네비게이션 업데이트 (각 슬라이드가 6초씩 표시)
        setInterval(updateDots, 6000);

        // 팝업 관련
        function closePopup() {
            document.getElementById('popup').style.display = 'none';
        }

        function signUp() {
            alert('카카오 1초 로그인/회원가입으로 이동합니다.');
            closePopup();
        }

        // 상품 모달 관련
        function openProductModal(productName) {
            document.getElementById('modalProductName').textContent = productName;
            document.getElementById('modalProductTitle').textContent = productName;
            document.getElementById('productModal').style.display = 'flex';
            document.getElementById('fixedPurchase').style.display = 'block';
        }

        function closeProductModal() {
            document.getElementById('productModal').style.display = 'none';
            document.getElementById('fixedPurchase').style.display = 'none';
        }

        // 수량 조절
        function changeQuantity(change) {
            const quantityInput = document.getElementById('quantity');
            const currentValue = parseInt(quantityInput.value);
            const newValue = currentValue + change;
            if (newValue >= 1) {
                quantityInput.value = newValue;
            }
        }

        // 햄버거 메뉴
        function toggleMenu() {
            alert('카테고리 메뉴가 열립니다 (바이도)');
        }

        // 모달 외부 클릭 시 닫기
        window.onclick = function(event) {
            const popup = document.getElementById('popup');
            const modal = document.getElementById('productModal');
            
            if (event.target == popup) {
                closePopup();
            }
            if (event.target == modal) {
                closeProductModal();
            }
        }

        // 페이지 로드 시 팝업 표시 (3초 후)
        setTimeout(() => {
            document.getElementById('popup').style.display = 'flex';
        }, 3000);

        // 플로팅 버튼 이벤트
        document.querySelector('.channel-talk').onclick = function() {
            alert('채널톡 상담이 시작됩니다.');
        };

        document.querySelector('.kakao-talk').onclick = function() {
            alert('카카오톡 채널로 이동합니다.');
        };

        // 구매 버튼 이벤트
        document.querySelector('.cart-btn').onclick = function() {
            alert('장바구니에 추가되었습니다.');
        };

        document.querySelector('.buy-btn').onclick = function() {
            alert('카카오 1초 로그인으로 구매하기');
        };

        document.querySelector('.kakao-btn').onclick = function() {
            alert('카카오페이로 간편 결제');
        };
    </script>
</body>
</html>
