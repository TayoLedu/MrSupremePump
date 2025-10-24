<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mr Surpeme Pump 💪</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: #2a2a2a; /* dark neutral text */
            background-color: #f5f2ed; /* warm beige background */
        }

        /* =========================
        Gateway Form Styles
        ========================= */
        .gateway-overlay {
            position: fixed;
            top: 0; 
            left: 0;
            width: 100%; 
            height: 100%;
            background: linear-gradient(135deg, #b3541e 0%, #d2691e 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            z-index: 10000;
            transition: opacity 0.5s, visibility 0.5s;
        }

        .gateway-overlay.hidden {
            opacity: 0;
            visibility: hidden;
        }

        .gateway-form-container {
            background: white;
            padding: 3rem;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            max-width: 500px;
            width: 90%;
            animation: slideIn 0.6s ease;
        }

        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to   { transform: translateY(0); opacity: 1; }
        }

        .gateway-form-container h2 {
            color: #b3541e;
            margin-bottom: 0.5rem;
            text-align: center;
            font-size: 2rem;
        }

        .gateway-form-container p {
            text-align: center;
            color: #666;
            margin-bottom: 2rem;
        }

        .gateway-form .form-group {
            margin-bottom: 1.5rem;
        }

        .gateway-form label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: bold;
            color: #b3541e;
        }

        .gateway-form input {
            width: 100%;
            padding: 0.9rem;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 1rem;
            transition: border-color 0.3s;
        }

        .gateway-form input:focus {
            outline: none;
            border-color: #d2691e;
        }

        .gateway-submit {
            width: 100%;
            background: #b3541e;
            color: white;
            padding: 1rem;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .gateway-submit:hover {
            background: #d2691e;
            transform: translateY(-2px);
            box-shadow: 0 10px 25px rgba(210, 105, 30, 0.4);
        }

        .main-content {
            opacity: 0;
            transition: opacity 0.5s;
        }
        .main-content.visible {
            opacity: 1;
        }

        /* =========================
        Header & Navigation
        ========================= */
        header {
            background: linear-gradient(135deg, #b3541e 0%, #d2691e 100%);
            color: white;
            padding: 1rem 0;
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        nav {
            max-width: 1200px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0 2rem;
        }

        nav h1 {
            font-size: 1.5rem;
        }

        nav ul {
            list-style: none;
            display: flex;
            gap: 2rem;
        }

        nav a {
            color: white;
            text-decoration: none;
            transition: opacity 0.3s;
        }
        nav a:hover { opacity: 0.8; }

        /* =========================
        Hero / Banner Section
        ========================= */
        .banner {
            background: url("images/Banner.png") center/cover no-repeat;
            color: white;
            padding: 150px 2rem 100px;
            text-align: center;
            margin-top: 60px;
            position: relative;
        }

        .banner::before {
            content: "";
            position: absolute;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0, 0, 0, 0.4);
            z-index: -1;
        }

        .banner h2 {
            font-size: 3rem;
            margin-bottom: 1rem;
            animation: fadeInUp 1s ease;
        }

        .banner p {
            font-size: 1.3rem;
            margin-bottom: 2rem;
            animation: fadeInUp 1s ease 0.2s backwards;
        }

        .cta-button {
            background: #b3541e;
            color: white;
            padding: 1rem 2rem;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            font-weight: bold;
            cursor: pointer;
            transition: transform 0.3s, box-shadow 0.3s;
            animation: fadeInUp 1s ease 0.4s backwards;
        }
        .cta-button:hover {
            background: #d2691e;
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(0,0,0,0.2);
        }

        /* =========================
        Sections & Headings
        ========================= */
        section {
            max-width: 1200px;
            margin: 0 auto;
            padding: 4rem 2rem;
        }

        h2 {
            font-size: 2.5rem;
            margin-bottom: 2rem;
            text-align: center;
            color: #b3541e;
        }

        /* =========================
        Services
        ========================= */
        .services-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .service-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }
        .service-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 40px rgba(0,0,0,0.15);
        }
        .service-card h3 {
            color: #d2691e;
            margin-bottom: 1rem;
            font-size: 1.5rem;
        }

        /* =========================
        About Section
        ========================= */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 3rem;
            align-items: center;
        }

        .about-image {
            width: 100%;
            height: 400px;
            background: linear-gradient(135deg, #b3541e 0%, #d2691e 100%);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
        }

        /* =========================
        Testimonials
        ========================= */
        .testimonial-image {
            width: 100%;
            height: 400px;
            background: linear-gradient(135deg, #b3541e 0%, #d2691e 100%);
            border-radius: 15px;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.2rem;
        }

        .testimonials {
            background: #f5f2ed;
        }

        .testimonial-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
            margin-top: 3rem;
        }

        .testimonial-card {
            background: white;
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 5px 20px rgba(0,0,0,0.08);
            border-left: 4px solid #b3541e;
        }
        .testimonial-card p {
            font-style: italic;
            margin-bottom: 1rem;
        }
        .testimonial-card .client-name {
            font-weight: bold;
            color: #d2691e;
        }
    /* =========================
    Contact Form
    ========================= */
    .contact-form {
        max-width: 600px;
        margin: 3rem auto;
    }

    .form-group {
        margin-bottom: 1.5rem;
    }

    .form-group label {
        display: block;
        margin-bottom: 0.5rem;
        font-weight: bold;
        color: #b3541e; /* burnt orange */
    }

    .form-group input,
    .form-group textarea {
        width: 100%;
        padding: 0.8rem;
        border: 2px solid #e0e0e0;
        border-radius: 8px;
        font-size: 1rem;
        transition: border-color 0.3s;
    }

    .form-group input:focus,
    .form-group textarea:focus {
        outline: none;
        border-color: #d2691e; /* terracotta focus */
    }

    .form-group textarea {
        resize: vertical;
        min-height: 120px;
    }

    .profile-pic {
        width: 350px;
        height: auto;
    }

    .testimonal-pic {
        width: 250px;
        height: auto;
    }

    /* =========================
    Download Button
    ========================= */
    .download-btn {
        display: inline-block;
        padding: 12px 24px;
        background-color: #b3541e; /* burnt orange */
        color: white;
        text-decoration: none;
        font-weight: bold;
        border-radius: 5px;
        transition: background-color 0.3s ease;
    }
    .download-btn:hover {
        background-color: #d2691e; /* terracotta hover */
    }

    /* =========================
    Stretch Guide
    ========================= */
    .stretch-guide {
        background-color: #f5f2ed; /* warm beige */
        padding: 30px;
        text-align: center;
        border-radius: 10px;
        max-width: 600px;
        margin: 40px auto;
        box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
    }

    .stretch-guide h2 {
        text-align: center;
        font-size: 24px;
        margin-bottom: 10px;
        color: #b3541e; /* burnt orange */
    }

    .stretch-guide p {
        text-align: center;
        font-size: 16px;
        margin-bottom: 20px;
        color: #555;
    }

    /* =========================
    Banner Section
    ========================= */
    .banner {
        background: url("images/Banner.png") center/cover no-repeat;
        color: white;
        padding: 150px 2rem 100px;
        text-align: center;
        margin-top: 60px;
        position: relative;
    }

    .banner::before {
        content: "";
        position: absolute;
        top: 0; left: 0;
        width: 100%; height: 100%;
        background: rgba(0, 0, 0, 0.4);
        z-index: -1;
    }

    .banner h2 {
        font-size: 3rem;
        margin-bottom: 1rem;
        animation: fadeInUp 1s ease;
    }

    .banner p {
        font-size: 1.3rem;
        margin-bottom: 2rem;
        animation: fadeInUp 1s ease 0.2s backwards;
    }

    /* =========================
    Footer
    ========================= */
    footer {
        background: #3b2f2f; /* deep coffee brown */
        color: white;
        text-align: center;
        padding: 2rem;
    }

    /* =========================
    Animations
    ========================= */
    @keyframes fadeInUp {
        from {
            opacity: 0;
            transform: translateY(30px);
        }
        to {
            opacity: 1;
            transform: translateY(0);
        }
    }

    /* =========================
    Responsive
    ========================= */
    @media (max-width: 768px) {
        .hero h2 {
            font-size: 2rem;
        }

        nav ul {
            gap: 1rem;
        }

        .about-content {
            grid-template-columns: 1fr;
        }

        h2 {
            font-size: 2rem;
        }

        .gateway-form-container {
            padding: 2rem;
        }
    }
    </style>
</head>
<body>
    <!-- Gateway Form Overlay -->
    <div class="gateway-overlay" id="gatewayOverlay">
        <div class="gateway-form-container">
            <h2>Welcome!</h2>
            <p>Please enter your details to access the website</p>
            <form class="gateway-form" id="gatewayForm" onsubmit="handleGatewaySubmit(event)">
                <div class="form-group">
                    <label>First Name *</label>
                    <input type="text" id="firstName" required placeholder="Enter your first name">
                </div>
                <div class="form-group">
                    <label>Last Name *</label>
                    <input type="text" id="lastName" required placeholder="Enter your last name">
                </div>
                <div class="form-group">
                    <label>Phone Number *</label>
                    <input type="tel" id="phoneNumber" required placeholder="Enter your phone number">
                </div>
                <button type="submit" class="gateway-submit">Access Website</button>
            </form>
        </div>
    </div>

    <!-- Main Website Content -->
    <div class="main-content" id="mainContent">
        <header>
            <nav>
                <h1>The SurpemePump Team💪</h1>
                <ul style="display: flex; flex-wrap: wrap; padding: 10px 15px;">
                    <li><a href="#home">Home</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#testimonials">Testimonials</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </header>

        <section class="banner" id="home">
            <h2 style="color: white;">Transform Your Body, Transform Your Life</h2>
            <p>Professional Online Coaching & In-Person Training</p>
            <button class="cta-button" onclick="document.getElementById('contact').scrollIntoView({behavior: 'smooth'})">Start Your Journey And Contact Us Today!</button>
        </section>

        <section id="services">
            <h2>My Services</h2>
            <div class="services-grid">
                <div class="service-card">
                    <h3>🖥️ Online Coaching</h3>
                    <p>Personalized workout plans and nutrition guidance delivered directly to you. Perfect for busy schedules with flexible training times.</p>
                    <ul style="margin-top: 1rem; padding-left: 1.5rem;">
                        <li>Custom training programs</li>
                        <li>Weekly check-ins</li>
                        <li>Nutrition planning</li>
                        <li>24/7 support via app and mobile</li>
                    </ul>
                </div>
                <div class="service-card">
                    <h3>💪 In-Person Training</h3>
                    <p>One-on-one personal training sessions focused on your goals with hands-on guidance and real-time form correction.</p>
                    <ul style="margin-top: 1rem; padding-left: 1.5rem;">
                        <li>1-on-1 attention</li>
                        <li>Form correction</li>
                        <li>Motivation & accountability</li>
                        <li>Flexible scheduling</li>
                    </ul>
                </div>
                <div class="service-card">
                    <h3>🎯 Body Speciliest Transformation Program's</h3>
                    <p>Complete 12-week transformation programs for maximum results. Specfic to get you to your goals</p>
                    <ul style="margin-top: 1rem; padding-left: 1.5rem;">
                        <li>12-week programs</li>
                        <li>Progress tracking</li>
                        <li>Granted Change</li>
                        <li>Continous Improvement Options</li>
                    </ul>
                </div>
            </div>
        </section>

        <section id="about">
            <h2>About Me</h2>
            <div class="about-content">
                <div class="about-image">
                    <img src="images/WhatsApp Image 2025-08-15 at 11.18.13_71f3971a.jpg" class="profile-pic">
                </div>
                <div>
                    <h3 style="color: #764ba2; margin-bottom: 1rem;">Olutayo - Certified Fitness Coach</h3>
                    <p style="margin-bottom: 1rem;">With over 10 years of experience in fitness industry, I've helped clients around the world achieve their health and fitness goals.</p>
                    <p style="margin-bottom: 1rem;">My approach combines science-based and experience training methods catered to each person with nutrition strategies to create sustainable, long-term results.</p>
                    <!--<p style="margin-bottom: 1rem;"><strong>Certifications:</strong></p>
                    <ul style="padding-left: 1.5rem; margin-bottom: 1rem;">
                        <li>Certified Personal Trainer (CPT)</li>
                        <li>Nutrition Specialist</li>
                        <li>Strength & Conditioning Coach</li>
                    </ul>-->
                    <p><em>If you desire confidence, 
                        to lose weight, build muscle, I'm here to guide you every step of the way.</em></p>
                </div>
            </div>
        </section>

        <section class="testimonials" id="testimonials">
            <h2>Client Success Stories</h2>
            <div class="testimonial-grid">
                <div class="testimonial-card">
                    <p>"The personalized approach made all the difference! Tayo is so engaing and not only cares about the physical but also motivates you in other areas of your life to succed"</p>
                    <div class="testimonial-image"> <img src="images/atestNatTransformation.png" class="testimonal-pic"> </div>
                    <p class="client-name">- Natalie. B/p>
                </div>
                <div class="testimonial-card">
                    <p>"Best investment I've made in myself. I had a wedding in 6Months from joining and only 3 days a week of training avalible, yet I still managed to get to the size I wanted in 5 months!"</p>
                    <div class="testimonial-image"> <img src="images/DayoTransformation.jpg" class="testimonal-pic"> </div>
                    <p class="client-name">- Dayo. L</p>
                </div>
                <div class="testimonial-card">
                    <p>"Finally found a coach who understands my busy schedule. The flexibility of online coaching and the in person sessions has been game changing for my physique and couldnt be happier."</p>
                    <div class="testimonial-image"> <img src="images/GlensTransformation3.png" class="testimonal-pic"> </div> 
                    <p class="client-name">- Glen. O</p>
                </div>
            </div>
        </section>

        <section id="contact">
            <h2>Desire More? Register For A Free Consultaion Today</h2>
            <div class="contact-form">
                <form onsubmit="handleSubmit(event)">
                    <div class="form-group">
                        <label>Name</label>
                        <input type="text" required placeholder="Your name">
                    </div>
                    <div class="form-group">
                        <label>Email</label>
                        <input type="email" required placeholder="your.email@example.com">
                    </div>
                    <div class="form-group">
                        <label>Service Interested In</label>
                        <select style="width: 100%; padding: 0.8rem; border: 2px solid #e0e0e0; border-radius: 8px; font-size: 1rem;">
                            <option>Online Coaching</option>
                            <option>In-Person Training</option>
                            <option>Body Transformation Program</option>
                        </select>
                    </div>
                    <div class="form-group">
                        <label>Message</label>
                        <textarea required placeholder="Tell me about your fitness goals..."></textarea>
                    </div>
                    <button type="submit" class="cta-button" style="width: 100%;">Send Message</button>
                </form>
            </div>
            <div class="stretch-guide">
                <h2>Here's a PDF to our Free Stretch Guide!</h2>
                <p>Download our expert-designed stretch routine to help improve flexibility, reduce soreness, and support recovery.</p>
                <a href="images/Full Body Stretch PDF.pdf" download class="download-btn">Download Stretch Guide</a>
            </div>
        </section>

        <footer>
            <p>&copy; 2025 Olutayo - Fitness Coach. All rights reserved.</p>
            <!-- <p style="margin-top: 0.5rem;"></p> -->
        </footer>
    </div>

    <script>
        let userInfo = {};

        function handleGatewaySubmit(e) {
            e.preventDefault();
            
            // Get user information
            const firstName = document.getElementById('firstName').value;
            const lastName = document.getElementById('lastName').value;
            const phoneNumber = document.getElementById('phoneNumber').value;
            
            userInfo = {
                firstName: firstName,
                lastName: lastName,
                phoneNumber: phoneNumber,
                timestamp: new Date().toLocaleString()
            };

            // Send email using FormSubmit.co
            const form = e.target;
            const formData = new FormData();
            
            // Replace 'YOUR_EMAIL@example.com' with your actual email address
            formData.append('_to', 'olutayo@leduweglobal.com');
            formData.append('_subject', 'New Website Lead - ' + firstName + ' ' + lastName);
            formData.append('_captcha', 'false');
            formData.append('First Name', firstName);
            formData.append('Last Name', lastName);
            formData.append('Phone Number', phoneNumber);
            formData.append('Timestamp', userInfo.timestamp);

            // Send the form data
            fetch('https://formsubmit.co/ajax/olutayo@leduweglobal.com', {
                method: 'POST',
                body: formData
            })
            .then(response => response.json())
            .then(data => {
                console.log('Email sent successfully:', data);
            })
            .catch(error => {
                console.error('Error sending email:', error);
            });

            // Hide the gateway overlay
            const overlay = document.getElementById('gatewayOverlay');
            overlay.classList.add('hidden');

            // Show main content
            setTimeout(() => {
                document.getElementById('mainContent').classList.add('visible');
            }, 300);
        }

        function handleSubmit(e) {
            e.preventDefault();
            alert('Thank you for your message! I will get back to you within 24 hours.');
            e.target.reset();
        }

        // Smooth scrolling for navigation
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                target.scrollIntoView({ behavior: 'smooth' });
            });
        });
    </script>
</body>
</html>
