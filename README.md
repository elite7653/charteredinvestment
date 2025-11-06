
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chartered Investments</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* CSS Reset and Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --primary: #001F3F; /* Navy Blue */
            --accent: #0056D2; /* Royal Blue */
            --luxury: #FFD700; /* Gold */
            --glow: #00FFFF; /* Cyan Blue */
            --bg-dark: #1E0039; /* Dark Purple */
            --bg-black: #000000; /* Black */
            --text-light: #F1F1F1; /* White */
            --shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
            --transition: all 0.3s ease;
        }

        body {
            background-color: var(--bg-black);
            color: var(--text-light);
            overflow-x: hidden;
            position: relative;
            min-height: 100vh;
        }

        /* Background Elements */
        .background-gradient {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(-45deg, var(--primary), var(--bg-dark), var(--bg-black), var(--accent), var(--luxury));
            background-size: 400% 400%;
            animation: gradientShift 15s ease infinite;
            z-index: -2;
            opacity: 0.9;
        }

        @keyframes gradientShift {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }

        .dollar-background {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><text x="50%" y="50%" font-family="Arial" font-size="20" fill="rgba(255,255,255,0.05)" text-anchor="middle" dominant-baseline="middle">$</text></svg>');
            z-index: -1;
            opacity: 0.2;
        }

        .floating-dollars {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: -1;
        }

        .dollar {
            position: absolute;
            color: var(--glow);
            font-size: 24px;
            font-weight: bold;
            text-shadow: 0 0 10px var(--glow);
            animation: float 15s linear infinite;
            opacity: 0.7;
        }

        .dollar.gold {
            color: var(--luxury);
            text-shadow: 0 0 10px var(--luxury);
        }

        @keyframes float {
            0% {
                transform: translateY(100vh) rotate(0deg);
                opacity: 0;
            }
            10% {
                opacity: 0.7;
            }
            90% {
                opacity: 0.7;
            }
            100% {
                transform: translateY(-100px) rotate(360deg);
                opacity: 0;
            }
        }

        /* Header Styles */
        header {
            background-color: rgba(0, 31, 63, 0.9);
            padding: 20px 0;
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
            border-bottom: 1px solid rgba(255, 215, 0, 0.3);
        }

        .header-content {
            display: flex;
            align-items: center;
            justify-content: center;
            flex-direction: column;
        }

        .logo-container {
            margin-bottom: 15px;
        }

        .logo {
            width: 80px;
            height: 80px;
            border-radius: 50%;
            background: linear-gradient(145deg, var(--luxury), var(--accent));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 2rem;
            font-weight: bold;
            color: var(--primary);
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.5);
            border: 2px solid var(--luxury);
        }

        .company-name {
            text-align: center;
            font-size: 2.5rem;
            font-weight: 700;
            background: linear-gradient(to right, var(--luxury), var(--text-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
            text-shadow: 0 0 15px rgba(255, 215, 0, 0.3);
            margin-bottom: 15px;
            letter-spacing: 2px;
        }

        .marquee-container {
            background-color: rgba(0, 0, 0, 0.4);
            padding: 10px 0;
            overflow: hidden;
            position: relative;
            border-top: 1px solid rgba(0, 255, 255, 0.2);
            border-bottom: 1px solid rgba(0, 255, 255, 0.2);
        }

        .marquee {
            white-space: nowrap;
            display: inline-block;
            animation: marquee 30s linear infinite;
        }

        @keyframes marquee {
            0% { transform: translateX(100%); }
            100% { transform: translateX(-100%); }
        }

        .marquee-item {
            display: inline-block;
            margin: 0 30px;
            font-size: 1.1rem;
        }

        .deposit {
            color: #4CAF50;
        }

        .withdrawal {
            color: #f44336;
        }

        /* Navigation Menu */
        .nav-container {
            position: absolute;
            top: 20px;
            right: 20px;
        }

        .menu-icon {
            font-size: 1.8rem;
            cursor: pointer;
            color: var(--text-light);
            background-color: var(--accent);
            padding: 10px 15px;
            border-radius: 5px;
            transition: var(--transition);
            box-shadow: 0 0 10px rgba(0, 86, 210, 0.5);
        }

        .menu-icon:hover {
            background-color: var(--luxury);
            transform: scale(1.05);
            box-shadow: 0 0 15px rgba(255, 215, 0, 0.7);
        }

        .nav-menu {
            position: absolute;
            top: 100%;
            right: 0;
            background-color: rgba(0, 31, 63, 0.95);
            width: 200px;
            border-radius: 5px;
            box-shadow: var(--shadow);
            display: none;
            z-index: 101;
            border: 1px solid rgba(255, 215, 0, 0.3);
        }

        .nav-menu.active {
            display: block;
        }

        .nav-menu a {
            display: block;
            padding: 15px 20px;
            color: var(--text-light);
            text-decoration: none;
            border-bottom: 1px solid rgba(255, 255, 255, 0.1);
            transition: var(--transition);
        }

        .nav-menu a:hover {
            background-color: var(--accent);
            padding-left: 25px;
            color: var(--luxury);
        }

        /* Main Content */
        main {
            padding: 40px 20px;
            max-width: 1200px;
            margin: 0 auto;
        }

        .cta-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .cta-box {
            background: linear-gradient(145deg, var(--primary), var(--bg-dark));
            border-radius: 15px;
            padding: 30px 20px;
            text-align: center;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            min-height: 200px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            border: 1px solid rgba(0, 255, 255, 0.2);
        }

        .cta-box::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(45deg, transparent, rgba(255, 215, 0, 0.1), transparent);
            transform: translateX(-100%);
            transition: transform 0.6s;
        }

        .cta-box:hover::before {
            transform: translateX(100%);
        }

        .cta-box:hover {
            transform: translateY(-10px) rotateX(5deg) rotateY(5deg);
            box-shadow: 0 15px 30px rgba(0, 0, 0, 0.4), 0 0 20px rgba(0, 255, 255, 0.3);
            border-color: var(--glow);
        }

        .cta-title {
            font-size: 1.8rem;
            margin-bottom: 15px;
            font-weight: 600;
            background: linear-gradient(to right, var(--luxury), var(--text-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .cta-subtitle {
            font-size: 1.1rem;
            opacity: 0.8;
            color: var(--text-light);
        }

        /* Content Sections */
        .content-section {
            padding: 80px 20px;
            background-color: rgba(0, 31, 63, 0.7);
            margin: 40px 0;
            border-radius: 15px;
            border: 1px solid rgba(255, 215, 0, 0.2);
        }

        .content-section .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        .content-section h2 {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 40px;
            background: linear-gradient(to right, var(--luxury), var(--text-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        /* About Section */
        .about-features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 40px;
        }

        .feature {
            background: rgba(255, 255, 255, 0.1);
            padding: 30px;
            border-radius: 10px;
            border: 1px solid rgba(255, 215, 0, 0.2);
            transition: var(--transition);
        }

        .feature:hover {
            transform: translateY(-5px);
            border-color: var(--glow);
        }

        .feature h3 {
            color: var(--luxury);
            margin-bottom: 15px;
            font-size: 1.5rem;
        }

        /* Contact Section */
        .contact-info {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            max-width: 800px;
            margin: 0 auto;
        }

        .contact-item {
            display: flex;
            align-items: center;
            gap: 15px;
            padding: 20px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            border: 1px solid rgba(255, 215, 0, 0.2);
            transition: var(--transition);
        }

        .contact-item:hover {
            transform: translateX(10px);
            border-color: var(--glow);
        }

        .contact-item i {
            font-size: 1.5rem;
            color: var(--luxury);
            width: 30px;
        }

        /* Reviews Section */
        .reviews-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            max-width: 1000px;
            margin: 0 auto;
        }

        .review {
            background: rgba(255, 255, 255, 0.1);
            padding: 30px;
            border-radius: 10px;
            border: 1px solid rgba(255, 215, 0, 0.2);
            transition: var(--transition);
            position: relative;
        }

        .review:hover {
            transform: translateY(-5px);
            border-color: var(--glow);
        }

        .review-text {
            font-style: italic;
            margin-bottom: 20px;
            line-height: 1.6;
        }

        .review-author {
            color: var(--luxury);
            font-weight: 600;
            text-align: right;
        }

        .review::before {
            content: '"';
            font-size: 4rem;
            color: var(--luxury);
            position: absolute;
            top: 10px;
            left: 20px;
            opacity: 0.3;
        }

        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 0, 0, 0.8);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }

        .modal.active {
            display: flex;
        }

        .modal-content {
            background: linear-gradient(145deg, var(--primary), var(--bg-dark));
            width: 90%;
            max-width: 500px;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.5);
            position: relative;
            max-height: 90vh;
            overflow-y: auto;
            border: 1px solid rgba(255, 215, 0, 0.3);
        }

        .close-modal {
            position: absolute;
            top: 15px;
            right: 15px;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-light);
            transition: var(--transition);
        }

        .close-modal:hover {
            color: var(--luxury);
            transform: scale(1.2);
        }

        .modal-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
            text-align: center;
            background: linear-gradient(to right, var(--luxury), var(--text-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .plan-list {
            list-style-type: none;
            margin: 20px 0;
        }

        .plan-item {
            padding: 15px;
            background-color: rgba(255, 255, 255, 0.1);
            margin-bottom: 10px;
            border-radius: 8px;
            transition: var(--transition);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }

        .plan-item:hover {
            background-color: rgba(255, 255, 255, 0.2);
            transform: translateX(5px);
            border-color: rgba(255, 215, 0, 0.3);
        }

        .invest-btn, .submit-btn {
            display: block;
            width: 100%;
            padding: 15px;
            background-color: var(--accent);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1.1rem;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
            margin-top: 20px;
            box-shadow: 0 0 10px rgba(0, 86, 210, 0.5);
            position: relative;
            overflow: hidden;
        }

        .invest-btn::before, .submit-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
            transition: left 0.5s;
        }

        .invest-btn:hover::before, .submit-btn:hover::before {
            left: 100%;
        }

        .invest-btn:hover, .submit-btn:hover {
            background-color: var(--luxury);
            transform: translateY(-3px);
            box-shadow: 0 5px 15px rgba(255, 215, 0, 0.4), 0 0 15px rgba(0, 255, 255, 0.5);
        }

        /* Form Styles */
        .form-group {
            margin-bottom: 20px;
        }

        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--text-light);
        }

        .form-input {
            width: 100%;
            padding: 12px 15px;
            border-radius: 8px;
            border: 1px solid rgba(255, 255, 255, 0.3);
            background-color: rgba(255, 255, 255, 0.1);
            color: var(--text-light);
            font-size: 1rem;
            transition: var(--transition);
        }

        .form-input:focus {
            outline: none;
            border-color: var(--luxury);
            background-color: rgba(255, 255, 255, 0.15);
            box-shadow: 0 0 10px rgba(255, 215, 0, 0.3);
        }

        textarea.form-input {
            min-height: 100px;
            resize: vertical;
        }

        /* Footer Styles */
        footer {
            background-color: rgba(0, 31, 63, 0.9);
            padding: 40px 20px;
            margin-top: 60px;
            border-top: 1px solid rgba(255, 215, 0, 0.3);
        }

        .social-section {
            text-align: center;
            margin-bottom: 40px;
        }

        .social-title {
            font-size: 1.5rem;
            margin-bottom: 20px;
            background: linear-gradient(to right, var(--luxury), var(--text-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .social-icons {
            display: flex;
            justify-content: center;
            gap: 30px;
        }

        .social-icon {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 60px;
            height: 60px;
            border-radius: 50%;
            color: white;
            font-size: 1.5rem;
            transition: var(--transition);
            text-decoration: none;
            opacity: 0.9;
        }

        .social-icon.whatsapp {
            background-color: #25D366;
        }

        .social-icon.facebook {
            background-color: #3b5998;
        }

        .social-icon.gmail {
            background-color: #D44638;
        }

        .social-icon:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 255, 255, 0.5);
            opacity: 1;
        }

        .partners-section {
            text-align: center;
        }

        .partners-title {
            font-size: 1.5rem;
            margin-bottom: 30px;
            background: linear-gradient(to right, var(--luxury), var(--text-light));
            -webkit-background-clip: text;
            background-clip: text;
            color: transparent;
        }

        .partners-container {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 30px;
        }

        .partner-logo {
            width: 100px;
            height: 100px;
            border-radius: 50%;
            background-color: rgba(255, 255, 255, 0.1);
            display: flex;
            justify-content: center;
            align-items: center;
            font-weight: 600;
            color: rgba(255, 255, 255, 0.7);
            transition: var(--transition);
            border: 2px solid transparent;
        }

        .partner-logo:hover {
            border-color: var(--glow);
            box-shadow: 0 0 15px rgba(0, 255, 255, 0.5);
            transform: scale(1.05);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .company-name {
                font-size: 2rem;
            }
            
            .cta-container {
                grid-template-columns: 1fr;
            }
            
            .social-icons {
                gap: 20px;
            }
            
            .social-icon {
                width: 50px;
                height: 50px;
                font-size: 1.2rem;
            }
            
            .logo {
                width: 60px;
                height: 60px;
                font-size: 1.5rem;
            }
            
            .content-section {
                padding: 60px 20px;
            }
            
            .content-section h2 {
                font-size: 2rem;
            }
        }

        @media (max-width: 480px) {
            .company-name {
                font-size: 1.8rem;
            }
            
            .marquee-item {
                font-size: 0.9rem;
                margin: 0 15px;
            }
            
            .cta-title {
                font-size: 1.5rem;
            }
            
            .modal-content {
                padding: 20px;
            }
        }
    </style>
</head>
<body>
    <!-- Background Elements -->
    <div class="background-gradient"></div>
    <div class="dollar-background"></div>
    <div class="floating-dollars" id="floatingDollars"></div>

    <!-- Header Section -->
    <header>
        <div class="container">
            <div class="header-content">
                <!-- Logo Placeholder - Replace with your actual logo -->
                <div class="logo-container">
                    <div class="logo">CI</div>
                </div>
                <h1 class="company-name">Chartered Investments</h1>
            </div>
            <div class="marquee-container">
                <div class="marquee">
                    <span class="marquee-item deposit">254712*** deposited 50k</span>
                    <span class="marquee-item withdrawal">254734*** withdrew 23k</span>
                    <span class="marquee-item deposit">254701*** deposited 17k</span>
                    <span class="marquee-item withdrawal">254789*** withdrew 42k</span>
                    <span class="marquee-item deposit">254756*** deposited 65k</span>
                    <span class="marquee-item withdrawal">254723*** withdrew 28k</span>
                    <span class="marquee-item deposit">254798*** deposited 33k</span>
                    <span class="marquee-item withdrawal">254745*** withdrew 19k</span>
                    <span class="marquee-item deposit">254732*** deposited 71k</span>
                    <span class="marquee-item withdrawal">254777*** withdrew 54k</span>
                    <span class="marquee-item deposit">254764*** deposited 38k</span>
                    <span class="marquee-item withdrawal">254799*** withdrew 22k</span>
                    <span class="marquee-item deposit">254781*** deposited 47k</span>
                    <span class="marquee-item withdrawal">254758*** withdrew 31k</span>
                    <span class="marquee-item deposit">254793*** deposited 59k</span>
                </div>
            </div>
        </div>

        <!-- Navigation Menu -->
        <div class="nav-container">
            <div class="menu-icon" id="menuToggle">☰</div>
            <div class="nav-menu" id="navMenu">
                <a href="#about">About Us</a>
                <a href="#contact">Contact Us</a>
                <a href="#reviews">Reviews</a>
            </div>
        </div>
    </header>

    <!-- Main Content -->
    <main>
        <div class="cta-container">
            <!-- Chartered Loans Box -->
            <div class="cta-box" id="loansBox">
                <h2 class="cta-title">Chartered Loans</h2>
                <p class="cta-subtitle">Flexible financing solutions</p>
            </div>

            <!-- Premium Box -->
            <div class="cta-box" id="premiumBox">
                <h2 class="cta-title">Premium</h2>
                <p class="cta-subtitle">Daily Yield</p>
            </div>

            <!-- Standard Box -->
            <div class="cta-box" id="standardBox">
                <h2 class="cta-title">Standard</h2>
                <p class="cta-subtitle">Weekly Yield</p>
            </div>

            <!-- Corporate Box -->
            <div class="cta-box" id="corporateBox">
                <h2 class="cta-title">Corporate</h2>
                <p class="cta-subtitle">Monthly Yield</p>
            </div>
        </div>
    </main>

    <!-- Content Sections -->
    <section id="about" class="content-section">
        <div class="container">
            <h2>About Chartered Investments</h2>
            <p>We are a premier investment firm with over 15 years of experience in wealth management and financial solutions. Our mission is to provide secure and profitable investment opportunities while maintaining the highest standards of integrity and transparency.</p>
            <div class="about-features">
                <div class="feature">
                    <h3>Our Vision</h3>
                    <p>To be the leading investment platform in East Africa, empowering individuals and businesses to achieve financial freedom.</p>
                </div>
                <div class="feature">
                    <h3>Our Mission</h3>
                    <p>To provide innovative financial solutions that generate sustainable returns while prioritizing client security and satisfaction.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="contact" class="content-section">
        <div class="container">
            <h2>Contact Us</h2>
            <div class="contact-info">
                <div class="contact-item">
                    <i class="fas fa-envelope"></i>
                    <span>info@charteredinvestments.com</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-phone"></i>
                    <span>+254 712 345 678</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-map-marker-alt"></i>
                    <span>Nairobi, Kenya</span>
                </div>
                <div class="contact-item">
                    <i class="fas fa-clock"></i>
                    <span>Mon - Fri: 8:00 AM - 6:00 PM</span>
                </div>
            </div>
        </div>
    </section>

    <section id="reviews" class="content-section">
        <div class="container">
            <h2>Client Reviews</h2>
            <div class="reviews-container">
                <div class="review">
                    <div class="review-text">
                        "Chartered Investments transformed my financial situation. The daily yield from Premium package is amazing!"
                    </div>
                    <div class="review-author">- Sarah M.</div>
                </div>
                <div class="review">
                    <div class="review-text">
                        "The loan process was smooth and professional. Got the funds I needed within 24 hours."
                    </div>
                    <div class="review-author">- John K.</div>
                </div>
                <div class="review">
                    <div class="review-text">
                        "Corporate investment plans helped our business expand. Highly recommended for serious investors."
                    </div>
                    <div class="review-author">- Tech Solutions Ltd</div>
                </div>
            </div>
        </div>
    </section>

    <!-- Modals -->
    <!-- Loans Modal -->
    <div class="modal" id="loansModal">
        <div class="modal-content">
            <span class="close-modal" id="closeLoansModal">&times;</span>
            <h2 class="modal-title">Loan Application</h2>
            <form id="loanForm" action="https://formspree.io/f/xjkpneqr" method="POST">
                <div class="form-group">
                    <label class="form-label" for="fullName">Full Name (as in ID)</label>
                    <input type="text" id="fullName" name="fullName" class="form-input" required>
                </div>
                <div class="form-group">
                    <label class="form-label" for="phone">Phone Number</label>
                    <input type="tel" id="phone" name="phone" class="form-input" required>
                </div>
                <div class="form-group">
                    <label class="form-label" for="location">Location</label>
                    <input type="text" id="location" name="location" class="form-input" required>
                </div>
                <div class="form-group">
                    <label class="form-label" for="nextOfKin">Next of Kin Name</label>
                    <input type="text" id="nextOfKin" name="nextOfKin" class="form-input" required>
                </div>
                <div class="form-group">
                    <label class="form-label" for="nextOfKinPhone">Next of Kin Phone Number</label>
                    <input type="tel" id="nextOfKinPhone" name="nextOfKinPhone" class="form-input" required>
                </div>
                <div class="form-group">
                    <label class="form-label" for="loanAmount">Loan Amount Needed</label>
                    <input type="number" id="loanAmount" name="loanAmount" class="form-input" required>
                </div>
                <div class="form-group">
                    <label class="form-label" for="returnPeriod">Period of Return (months)</label>
                    <input type="number" id="returnPeriod" name="returnPeriod" class="form-input" required>
                </div>
                <div class="form-group">
                    <label class="form-label" for="additionalDetails">Additional Details</label>
                    <textarea id="additionalDetails" name="additionalDetails" class="form-input"></textarea>
                </div>
                <button type="submit" class="submit-btn">SEND APPLICATION</button>
            </form>
        </div>
    </div>

    <!-- Premium Modal -->
    <div class="modal" id="premiumModal">
        <div class="modal-content">
            <span class="close-modal" id="closePremiumModal">&times;</span>
            <h2 class="modal-title">Premium Investment Plans</h2>
            <ul class="plan-list">
                <li class="plan-item">Invest 500, earn 750</li>
                <li class="plan-item">Invest 750, earn 1000</li>
                <li class="plan-item">Invest 1000, earn 1400</li>
                <li class="plan-item">Invest 1500, earn 2100</li>
                <li class="plan-item">Invest 2000, earn 2900</li>
            </ul>
            <button class="invest-btn">INVEST NOW</button>
        </div>
    </div>

    <!-- Standard Modal -->
    <div class="modal" id="standardModal">
        <div class="modal-content">
            <span class="close-modal" id="closeStandardModal">&times;</span>
            <h2 class="modal-title">Standard Investment Plans</h2>
            <ul class="plan-list">
                <li class="plan-item">Invest 1000, earn 1300</li>
                <li class="plan-item">Invest 2000, earn 2700</li>
                <li class="plan-item">Invest 3000, earn 4000</li>
                <li class="plan-item">Invest 5000, earn 6800</li>
                <li class="plan-item">Invest 10000, earn 14000</li>
            </ul>
            <button class="invest-btn">INVEST NOW</button>
        </div>
    </div>

    <!-- Corporate Modal -->
    <div class="modal" id="corporateModal">
        <div class="modal-content">
            <span class="close-modal" id="closeCorporateModal">&times;</span>
            <h2 class="modal-title">Corporate Investment Plans</h2>
            <ul class="plan-list">
                <li class="plan-item">Invest 5000, earn 7500</li>
                <li class="plan-item">Invest 10000, earn 15500</li>
                <li class="plan-item">Invest 25000, earn 40000</li>
                <li class="plan-item">Invest 50000, earn 85000</li>
                <li class="plan-item">Invest 100000, earn 175000</li>
            </ul>
            <button class="invest-btn">INVEST NOW</button>
        </div>
    </div>

    <!-- Footer -->
    <footer>
        <div class="social-section">
            <h3 class="social-title">Connect With Us</h3>
            <div class="social-icons">
                <a href="https://wa.me/qr/R7FJCNVDFMTCP1" class="social-icon whatsapp" target="_blank">
                    <i class="fab fa-whatsapp"></i>
                </a>
                <a href="https://facebook.com/CharteredInvestments" class="social-icon facebook" target="_blank">
                    <i class="fab fa-facebook-f"></i>
                </a>
                <a href="mailto:info@charteredinvestments.com" class="social-icon gmail">
                    <i class="fas fa-envelope"></i>
                </a>
            </div>
        </div>

        <div class="partners-section">
            <h3 class="partners-title">Our Partners</h3>
            <div class="partners-container">
                <div class="partner-logo">Partner 1</div>
                <div class="partner-logo">Partner 2</div>
                <div class="partner-logo">Partner 3</div>
                <div class="partner-logo">Partner 4</div>
                <div class="partner-logo">Partner 5</div>
            </div>
        </div>
    </footer>

    <script>
        // Create floating dollar signs
        function createFloatingDollars() {
            const container = document.getElementById('floatingDollars');
            const dollarCount = 20;
            
            for (let i = 0; i < dollarCount; i++) {
                const dollar = document.createElement('div');
                dollar.classList.add('dollar');
                
                // Alternate between cyan and gold dollars
                if (i % 2 === 0) {
                    dollar.classList.add('gold');
                }
                
                dollar.textContent = '$';
                
                // Random position and animation delay
                const left = Math.random() * 100;
                const delay = Math.random() * 15;
                const duration = 10 + Math.random() * 10;
                
                dollar.style.left = `${left}%`;
                dollar.style.animationDelay = `${delay}s`;
                dollar.style.animationDuration = `${duration}s`;
                
                container.appendChild(dollar);
            }
        }

        // Enhanced Navigation Menu
        document.getElementById('menuToggle').addEventListener('click', function(e) {
            e.stopPropagation();
            document.getElementById('navMenu').classList.toggle('active');
        });

        // Close menu when clicking outside
        document.addEventListener('click', function(event) {
            const menu = document.getElementById('navMenu');
            const toggle = document.getElementById('menuToggle');
            
            if (!menu.contains(event.target) && !toggle.contains(event.target)) {
                menu.classList.remove('active');
            }
        });

        // Smooth scrolling for navigation links
        document.querySelectorAll('.nav-menu a').forEach(link => {
            link.addEventListener('click', function(e) {
                e.preventDefault();
                
                // Close mobile menu
                document.getElementById('navMenu').classList.remove('active');
                
                const targetId = this.getAttribute('href');
                const targetSection = document.querySelector(targetId);
                
                if (targetSection) {
                    // Smooth scroll to section
                    window.scrollTo({
                        top: targetSection.offsetTop - 80,
                        behavior: 'smooth'
                    });
                }
            });
        });

        // Modal Controls
        // Loans Modal
        document.getElementById('loansBox').addEventListener('click', function() {
            document.getElementById('loansModal').classList.add('active');
        });

        document.getElementById('closeLoansModal').addEventListener('click', function() {
            document.getElementById('loansModal').classList.remove('active');
        });

        // Premium Modal
        document.getElementById('premiumBox').addEventListener('click', function() {
            document.getElementById('premiumModal').classList.add('active');
        });

        document.getElementById('closePremiumModal').addEventListener('click', function() {
            document.getElementById('premiumModal').classList.remove('active');
        });

        // Standard Modal
        document.getElementById('standardBox').addEventListener('click', function() {
            document.getElementById('standardModal').classList.add('active');
        });

        document.getElementById('closeStandardModal').addEventListener('click', function() {
            document.getElementById('standardModal').classList.remove('active');
        });

        // Corporate Modal
        document.getElementById('corporateBox').addEventListener('click', function() {
            document.getElementById('corporateModal').classList.add('active');
        });

        document.getElementById('closeCorporateModal').addEventListener('click', function() {
            document.getElementById('corporateModal').classList.remove('active');
        });

        // Close modals when clicking outside
        window.addEventListener('click', function(event) {
            const modals = document.querySelectorAll('.modal');
            modals.forEach(modal => {
                if (event.target === modal) {
                    modal.classList.remove('active');
                }
            });
        });

        // Form submission
        document.getElementById('loanForm').addEventListener('submit', function(e) {
            e.preventDefault();
            // In a real implementation, this would submit to Formspree
            alert('Loan application submitted successfully!');
            document.getElementById('loansModal').classList.remove('active');
            this.reset();
        });

        // INVEST NOW buttons - Redirect to payment page
        document.querySelectorAll('.invest-btn').forEach(button => {
            button.addEventListener('click', function() {
                // Redirect to your M-Pesa payment page
                const paymentUrl = 'https://amodeepotfolio.github.io/MpesageneratorAMD/';
                
                // Redirect to payment page in new tab
                window.open(paymentUrl, '_blank');
                
                // Close the modal
                this.closest('.modal').classList.remove('active');
            });
        });

        // Initialize floating dollars on page load
        window.addEventListener('DOMContentLoaded', createFloatingDollars);
    </script>
</body>
</html>
