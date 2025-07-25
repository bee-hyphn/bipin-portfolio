# bipin-portfolio
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Bipin - Aspiring Physicist & Quantum Science Enthusiast</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <!-- MathJax for LaTeX support -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/3.2.2/es5/tex-mml-chtml.min.js"></script>
    <style>
        /* ========== CSS VARIABLES ========== */
        :root {
            /* Dark Theme Colors */
            --bg-primary: #121212;
            --bg-secondary: #1E1E2F;
            --bg-tertiary: #2C2C3C;
            --bg-card: #2A2A3A;
            --bg-card-hover: #323244;
            
            /* Accent Colors */
            --primary-color: #6C63FF;
            --primary-hover: #5B52E8;
            --secondary-color: #8F00FF;
            --accent-color: #00D4AA;
            --success-color: #10B981;
            --warning-color: #F59E0B;
            
            /* Text Colors */
            --text-primary: #F1F1F1;
            --text-secondary: #CCCCCC;
            --text-muted: #9CA3AF;
            --text-inverse: #1F2937;
            
            /* Border and Shadow */
            --border-color: #3A3A4A;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
            --shadow-lg: 0 10px 30px rgba(0, 0, 0, 0.4);
            --glow: 0 0 20px rgba(108, 99, 255, 0.3);
            
            /* Gradients */
            --gradient-primary: linear-gradient(135deg, #6C63FF 0%, #8F00FF 100%);
            --gradient-hero: linear-gradient(135deg, #1E1E2F 0%, #2C2C3C 50%, #121212 100%);
        }

        /* Light Theme Variables (for toggle) */
        [data-theme="light"] {
            --bg-primary: #FFFFFF;
            --bg-secondary: #F9FAFB;
            --bg-tertiary: #F3F4F6;
            --bg-card: #FFFFFF;
            --bg-card-hover: #F9FAFB;
            
            --text-primary: #1F2937;
            --text-secondary: #374151;
            --text-muted: #6B7280;
            --text-inverse: #F1F1F1;
            
            --border-color: #E5E7EB;
            --shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 10px 30px rgba(0, 0, 0, 0.15);
            --glow: 0 0 20px rgba(108, 99, 255, 0.2);
            
            --gradient-hero: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
        }

        /* ========== BASE STYLES ========== */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, sans-serif;
            line-height: 1.6;
            color: var(--text-primary);
            background: var(--bg-primary);
            overflow-x: hidden;
            transition: all 0.3s ease;
        }

        /* ========== NAVIGATION ========== */
        .navbar {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(18, 18, 18, 0.95);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            transition: all 0.3s ease;
            border-bottom: 1px solid var(--border-color);
        }

        [data-theme="light"] .navbar {
            background: rgba(255, 255, 255, 0.95);
        }

        .navbar.scrolled {
            background: rgba(18, 18, 18, 0.98);
            box-shadow: var(--shadow);
        }

        [data-theme="light"] .navbar.scrolled {
            background: rgba(255, 255, 255, 0.98);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 1.5rem;
            font-weight: 700;
            color: var(--primary-color);
            text-decoration: none;
            transition: all 0.3s ease;
        }

        .logo:hover {
            text-shadow: var(--glow);
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
            align-items: center;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-primary);
            font-weight: 500;
            transition: all 0.3s ease;
            position: relative;
        }

        .nav-links a:hover {
            color: var(--primary-color);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background: var(--primary-color);
            transition: width 0.3s ease;
        }

        .nav-links a:hover::after {
            width: 100%;
        }

        .nav-controls {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .theme-toggle {
            background: var(--bg-card);
            border: 2px solid var(--border-color);
            border-radius: 50px;
            padding: 0.5rem;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            font-size: 1.2rem;
        }

        .theme-toggle:hover {
            background: var(--bg-card-hover);
            box-shadow: var(--glow);
        }

        .search-container {
            position: relative;
        }

        .search-bar {
            padding: 0.5rem 1rem;
            border: 2px solid var(--border-color);
            border-radius: 25px;
            font-size: 0.9rem;
            width: 200px;
            background: var(--bg-card);
            color: var(--text-primary);
            transition: all 0.3s ease;
        }

        .search-bar:focus {
            outline: none;
            border-color: var(--primary-color);
            width: 250px;
            box-shadow: var(--glow);
        }

        .search-bar::placeholder {
            color: var(--text-muted);
        }

        /* Mobile Navigation */
        .mobile-menu-btn {
            display: none;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-primary);
        }

        .mobile-nav {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100vh;
            background: var(--bg-primary);
            z-index: 999;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            gap: 2rem;
        }

        .mobile-nav.active {
            display: flex;
        }

        .mobile-nav a {
            color: var(--text-primary);
            text-decoration: none;
            font-size: 1.5rem;
            font-weight: 500;
            transition: all 0.3s ease;
        }

        .mobile-nav a:hover {
            color: var(--primary-color);
        }

        .mobile-close {
            position: absolute;
            top: 2rem;
            right: 2rem;
            background: none;
            border: none;
            font-size: 2rem;
            cursor: pointer;
            color: var(--text-primary);
        }

        /* ========== HERO SECTION ========== */
        .hero {
            height: 100vh;
            background: var(--gradient-hero);
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            overflow: hidden;
        }

        /* Particle Animation Background */
        .particles {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
        }

        .particle {
            position: absolute;
            background: rgba(108, 99, 255, 0.2);
            border-radius: 50%;
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px) scale(1); opacity: 0.7; }
            50% { transform: translateY(-20px) scale(1.1); opacity: 1; }
        }

        .hero-content {
            text-align: center;
            color: var(--text-primary);
            z-index: 2;
            position: relative;
            max-width: 800px;
            padding: 0 2rem;
        }

        .hero h1 {
            font-size: 4rem;
            font-weight: 700;
            margin-bottom: 1rem;
            opacity: 0;
            animation: slideUp 1s ease-out 0.5s forwards;
            background: var(--gradient-primary);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }

        .hero .tagline {
            font-size: 1.5rem;
            margin-bottom: 2rem;
            opacity: 0;
            animation: slideUp 1s ease-out 0.8s forwards;
            font-weight: 400;
            color: var(--text-secondary);
        }

        .cta-buttons {
            display: flex;
            gap: 1rem;
            justify-content: center;
            flex-wrap: wrap;
            opacity: 0;
            animation: slideUp 1s ease-out 1.1s forwards;
        }

        .cta-btn {
            display: inline-block;
            padding: 12px 24px;
            background: var(--bg-card);
            border: 2px solid var(--primary-color);
            color: var(--primary-color);
            text-decoration: none;
            border-radius: 50px;
            font-weight: 600;
            transition: all 0.3s ease;
            backdrop-filter: blur(10px);
        }

        .cta-btn:hover {
            background: var(--primary-color);
            color: var(--text-inverse);
            transform: translateY(-3px);
            box-shadow: var(--glow);
        }

        .cta-btn.primary {
            background: var(--gradient-primary);
            border-color: transparent;
            color: white;
        }

        .cta-btn.primary:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-lg);
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }



        /* ========== SECTION STYLES ========== */
        .section {
            padding: 5rem 2rem;
            max-width: 1200px;
            margin: 0 auto;
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            color: var(--text-primary);
            position: relative;
            font-weight: 600;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            transform: translateX(-50%);
            width: 60px;
            height: 4px;
            background: var(--gradient-primary);
            border-radius: 2px;
        }

        /* ========== ABOUT SECTION ========== */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 4rem;
            align-items: center;
        }

        .profile-section {
            text-align: center;
        }

        .profile-image {
            width: 280px;
            height: 280px;
            border-radius: 50%;
            background: var(--gradient-primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 4rem;
            margin: 0 auto 1rem;
            box-shadow: var(--shadow-lg);
            transition: transform 0.3s ease;
        }

        .profile-image:hover {
            transform: scale(1.05);
            box-shadow: var(--glow);
        }

        .about-text {
            font-size: 1.1rem;
            color: var(--text-secondary);
            line-height: 1.8;
        }

        .about-text p {
            margin-bottom: 1.5rem;
        }

        .highlight {
            color: var(--primary-color);
            font-weight: 600;
        }

        /* ========== SKILLS SECTION ========== */
        .skills {
            background: var(--bg-secondary);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 2rem;
        }

        .skill-category {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
        }

        .skill-category:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary-color);
        }

        .skill-icon {
            width: 60px;
            height: 60px;
            background: var(--gradient-primary);
            border-radius: 50%;
            margin: 0 auto 1rem;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 1.5rem;
        }

        .skill-category h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            text-align: center;
            color: var(--text-primary);
        }

        .skill-list {
            list-style: none;
            text-align: center;
        }

        .skill-list li {
            padding: 0.3rem 0;
            color: var(--text-secondary);
        }

        /* ========== PROJECTS SECTION ========== */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .project-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary-color);
        }

        .project-image {
            width: 100%;
            height: 200px;
            background: var(--gradient-primary);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-size: 3rem;
        }

        .project-content {
            padding: 1.5rem;
        }

        .project-title {
            font-size: 1.3rem;
            font-weight: 600;
            margin-bottom: 0.5rem;
            color: var(--text-primary);
        }

        .project-description {
            color: var(--text-secondary);
            margin-bottom: 1rem;
            line-height: 1.6;
        }

        .tech-stack {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
            margin-bottom: 1rem;
        }

        .tech-tag {
            background: var(--bg-tertiary);
            border: 1px solid var(--border-color);
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.9rem;
            color: var(--text-secondary);
        }

        .project-links {
            display: flex;
            gap: 1rem;
        }

        .project-link {
            padding: 0.5rem 1rem;
            background: var(--primary-color);
            color: white;
            text-decoration: none;
            border-radius: 8px;
            font-size: 0.9rem;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .project-link:hover {
            background: var(--primary-hover);
            transform: translateY(-2px);
        }

        .project-link.secondary {
            background: transparent;
            color: var(--primary-color);
            border: 2px solid var(--primary-color);
        }

        .project-link.secondary:hover {
            background: var(--primary-color);
            color: white;
        }

        /* ========== PROJECT MODAL ========== */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.8);
            z-index: 1100;
            backdrop-filter: blur(5px);
        }

        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            border-radius: 20px;
            padding: 2rem;
            max-width: 600px;
            width: 90%;
            max-height: 80vh;
            overflow-y: auto;
            position: relative;
            box-shadow: var(--shadow-lg);
        }

        .modal-close {
            position: absolute;
            top: 1rem;
            right: 1rem;
            background: none;
            border: none;
            font-size: 1.5rem;
            cursor: pointer;
            color: var(--text-muted);
            transition: color 0.3s ease;
        }

        .modal-close:hover {
            color: var(--text-primary);
        }

        .modal-title {
            font-size: 1.8rem;
            color: var(--text-primary);
            margin-bottom: 1rem;
        }

        .modal-description {
            color: var(--text-secondary);
            line-height: 1.8;
            margin-bottom: 1.5rem;
        }

        /* ========== BLOG SECTION ========== */
        .blog {
            background: var(--bg-secondary);
        }

        .blog-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 2rem;
        }

        .blog-search {
            padding: 0.8rem 1.2rem;
            border: 2px solid var(--border-color);
            border-radius: 10px;
            background: var(--bg-card);
            color: var(--text-primary);
            font-size: 1rem;
            width: 300px;
        }

        .blog-search:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: var(--glow);
        }

        .blog-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 2rem;
        }

        .blog-post {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            cursor: pointer;
        }

        .blog-post:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary-color);
        }

        .blog-post.coming-soon {
            opacity: 0.7;
            cursor: default;
            border-style: dashed;
        }

        .blog-post.coming-soon:hover {
            transform: none;
            border-color: var(--border-color);
        }

        .blog-date {
            color: var(--text-muted);
            font-size: 0.9rem;
            margin-bottom: 0.5rem;
        }

        .blog-title {
            font-size: 1.4rem;
            color: var(--text-primary);
            margin-bottom: 1rem;
            font-weight: 600;
        }

        .blog-summary {
            color: var(--text-secondary);
            line-height: 1.6;
            margin-bottom: 1rem;
        }

        .blog-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 0.5rem;
        }

        .blog-tag {
            background: var(--bg-tertiary);
            border: 1px solid var(--border-color);
            padding: 0.2rem 0.8rem;
            border-radius: 15px;
            font-size: 0.8rem;
            color: var(--text-muted);
        }

        .blog-tag.physics { border-color: var(--primary-color); color: var(--primary-color); }
        .blog-tag.ielts { border-color: var(--accent-color); color: var(--accent-color); }
        .blog-tag.sat { border-color: var(--warning-color); color: var(--warning-color); }

        /* ========== RESOURCES SECTION ========== */
        .resources-filters {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-bottom: 3rem;
            flex-wrap: wrap;
        }

        .filter-btn {
            padding: 0.8rem 1.5rem;
            background: var(--bg-card);
            border: 2px solid var(--border-color);
            color: var(--text-secondary);
            border-radius: 25px;
            cursor: pointer;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .filter-btn.active,
        .filter-btn:hover {
            background: var(--primary-color);
            border-color: var(--primary-color);
            color: white;
        }

        .resources-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .resource-card {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
        }

        .resource-card:hover {
            transform: translateY(-5px);
            box-shadow: var(--shadow-lg);
            border-color: var(--primary-color);
        }

        .resource-card.hidden {
            display: none;
        }

        .resource-card h3 {
            color: var(--primary-color);
            margin-bottom: 1rem;
            font-size: 1.2rem;
        }

        .resource-list {
            list-style: none;
        }

        .resource-list li {
            padding: 0.5rem 0;
            border-bottom: 1px solid var(--border-color);
        }

        .resource-list a {
            color: var(--text-secondary);
            text-decoration: none;
            transition: color 0.3s ease;
        }

        .resource-list a:hover {
            color: var(--primary-color);
        }

        /* ========== CONTACT SECTION ========== */
        .contact {
            background: var(--bg-secondary);
        }

        .contact-content {
            max-width: 800px;
            margin: 0 auto;
        }

        .contact-intro {
            text-align: center;
            margin-bottom: 3rem;
            color: var(--text-secondary);
            font-size: 1.1rem;
        }

        .contact-form {
            background: var(--bg-card);
            border: 1px solid var(--border-color);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
            margin-bottom: 3rem;
        }

        .form-group {
            margin-bottom: 1.5rem;
        }

        .form-group label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 600;
            color: var(--text-primary);
        }

        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 1rem;
            border: 2px solid var(--border-color);
            border-radius: 10px;
            font-size: 1rem;
            background: var(--bg-tertiary);
            color: var(--text-primary);
            transition: border-color 0.3s ease;
            font-family: inherit;
        }

        .form-group input:focus,
        .form-group textarea:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: var(--glow);
        }

        .form-group input::placeholder,
        .form-group textarea::placeholder {
            color: var(--text-muted);
        }

        .submit-btn {
            width: 100%;
            padding: 1rem 2rem;
            background: var(--gradient-primary);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 1rem;
            font-weight: 600;
            cursor: pointer;
            transition: all 0.3s ease;
        }

        .submit-btn:hover {
            transform: translateY(-2px);
            box-shadow: var(--shadow-lg);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
        }

        .social-link {
            width: 50px;
            height: 50px;
            background: var(--bg-card);
            border: 2px solid var(--border-color);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--text-secondary);
            text-decoration: none;
            font-size: 1.2rem;
            transition: all 0.3s ease;
        }

        .social-link:hover {
            background: var(--primary-color);
            color: white;
            border-color: var(--primary-color);
            transform: translateY(-3px);
        }

        /* ========== FOOTER ========== */
        .footer {
            background: var(--bg-primary);
            border-top: 1px solid var(--border-color);
            color: var(--text-secondary);
            text-align: center;
            padding: 2rem;
        }

        .footer p {
            margin-bottom: 0.5rem;
        }

        .footer .built-by {
            color: var(--accent-color);
            font-weight: 500;
        }

        /* ========== RESPONSIVE DESIGN ========== */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }

            .mobile-menu-btn {
                display: block;
            }

            .hero h1 {
                font-size: 2.5rem;
            }

            .hero .tagline {
                font-size: 1.2rem;
            }

            .cta-buttons {
                flex-direction: column;
                align-items: center;
            }

            .about-content {
                grid-template-columns: 1fr;
                text-align: center;
                gap: 2rem;
            }

            .blog-header {
                flex-direction: column;
                gap: 1rem;
            }

            .blog-search {
                width: 100%;
            }

            .resources-filters {
                flex-direction: column;
                align-items: center;
            }

            .section {
                padding: 3rem 1rem;
            }

            .section-title {
                font-size: 2rem;
            }

            .search-bar {
                width: 150px;
            }

            .search-bar:focus {
                width: 180px;
            }

            .progress-widget {
                bottom: 1rem;
                right: 1rem;
                width: 250px;
            }

            .nav-controls {
                gap: 0.5rem;
            }
        }

        /* ========== UTILITY CLASSES ========== */
        .text-center { text-align: center; }
        .mb-1 { margin-bottom: 1rem; }
        .mb-2 { margin-bottom: 2rem; }
        .hidden { display: none; }
        
        /* Smooth scrolling */
        html {
            scroll-behavior: smooth;
        }

        /* Loading animation */
        .pulse {
            animation: pulse 2s ease-in-out infinite;
        }

        @keyframes pulse {
            0%, 100% { opacity: 1; }
            50% { opacity: 0.7; }
        }

        /* GitHub integration styles */
        .github-projects {
            margin-top: 3rem;
        }

        .github-header {
            text-align: center;
            margin-bottom: 2rem;
            color: var(--text-muted);
        }
    </style>
</head>
<body>
    <!-- Navigation -->
    <nav class="navbar" id="navbar">
        <div class="nav-container">
            <a href="#" class="logo">Bipin</a>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#blog">Blog</a></li>
                <li><a href="#resources">Resources</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
            <div class="nav-controls">
                <div class="search-container">
                    <input type="text" class="search-bar" placeholder="Search..." id="globalSearch">
                </div>
                <button class="theme-toggle" id="themeToggle">🌙</button>
                <button class="mobile-menu-btn" id="mobileMenuBtn">☰</button>
            </div>
        </div>
    </nav>

    <!-- Mobile Navigation -->
    <div class="mobile-nav" id="mobileNav">
        <button class="mobile-close" id="mobileClose">×</button>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#projects">Projects</a>
        <a href="#blog">Blog</a>
        <a href="#resources">Resources</a>
        <a href="#contact">Contact</a>
    </div>



    <!-- Hero Section -->
    <section id="home" class="hero">
        <div class="particles" id="particles"></div>
        <div class="hero-content">
            <h1>Bipin</h1>
            <p class="tagline">Aspiring Physicist | Quantum Science Enthusiast | Scholarship Seeker</p>
            <div class="cta-buttons">
                <a href="#projects" class="cta-btn primary">View Projects</a>
                <a href="#" class="cta-btn" onclick="downloadCV()">Download CV</a>
                <a href="#blog" class="cta-btn">Explore Blog</a>
            </div>
        </div>
    </section>

    <!-- About Me Section -->
    <section id="about" class="section">
        <h2 class="section-title">About Me</h2>
        <div class="about-content">
            <div class="profile-section">
                <div class="profile-image">🧑‍🔬</div>
                <p><strong>Physics Enthusiast</strong></p>
            </div>
            <div class="about-text">
                <p>Hello! I'm <span class="highlight">Bipin</span>, a passionate student with an insatiable curiosity for understanding the fundamental laws that govern our universe. My journey in physics began with simple questions about everyday phenomena, and has evolved into a deep fascination with <span class="highlight">quantum mechanics</span> and its applications.</p>
                
                <p>Currently, I'm preparing for my <span class="highlight">IELTS and SAT exams</span> as I pursue my dream of studying abroad, particularly in the United States. My goal is to complete a <span class="highlight">Bachelor's degree in Physics</span> followed by a <span class="highlight">Master's in Quantum Science</span>, where I can contribute to cutting-edge research in quantum computing and quantum information theory.</p>
                
                <p>Beyond academics, I'm actively building this portfolio to showcase my projects, document my learning journey, and connect with like-minded individuals. I believe in the power of sharing knowledge and am committed to making physics accessible to fellow students through my blog and resource recommendations.</p>
                
                <p>When I'm not studying or coding physics simulations, you can find me exploring new programming languages, reading about the latest discoveries in quantum physics, or working on projects that bridge the gap between theoretical concepts and practical applications.</p>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills" class="section skills">
        <h2 class="section-title">Skills & Expertise</h2>
        <div class="skills-grid">
            <div class="skill-category">
                <div class="skill-icon">💻</div>
                <h3>Programming</h3>
                <ul class="skill-list">
                    <li>Python (NumPy, Matplotlib, SciPy)</li>
                    <li>HTML5 & CSS3</li>
                    <li>JavaScript (Basic)</li>
                    <li>MATLAB (Learning)</li>
                </ul>
            </div>
            <div class="skill-category">
                <div class="skill-icon">⚛️</div>
                <h3>Physics Knowledge</h3>
                <ul class="skill-list">
                    <li>Classical Mechanics</li>
                    <li>Quantum Mechanics (Basics)</li>
                    <li>Thermodynamics</li>
                    <li>Electromagnetism</li>
                    <li>Mathematical Physics</li>
                </ul>
            </div>
            <div class="skill-category">
                <div class="skill-icon">🛠️</div>
                <h3>Tools & Software</h3>
                <ul class="skill-list">
                    <li>LaTeX (Document Preparation)</li>
                    <li>Git & GitHub</li>
                    <li>GeoGebra (Visualizations)</li>
                    <li>Jupyter Notebooks</li>
                    <li>Microsoft Office Suite</li>
                </ul>
            </div>
            <div class="skill-category">
                <div class="skill-icon">🎯</div>
                <h3>Soft Skills</h3>
                <ul class="skill-list">
                    <li>Public Speaking</li>
                    <li>Research Writing</li>
                    <li>Problem Solving</li>
                    <li>Team Collaboration</li>
                    <li>Self-directed Learning</li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Projects Gallery -->
    <section id="projects" class="section">
        <h2 class="section-title">Featured Projects</h2>
        <div class="projects-grid" id="projectsGrid">
            <div class="project-card" data-project="handglove">
                <div class="project-image">🧤</div>
                <div class="project-content">
                    <h3 class="project-title">Smart Hand Glove Project</h3>
                    <p class="project-description">An innovative wearable device that translates hand gestures into digital commands, bridging the gap between physical movement and digital interaction.</p>
                    <div class="tech-stack">
                        <span class="tech-tag">Arduino</span>
                        <span class="tech-tag">Sensors</span>
                        <span class="tech-tag">C++</span>
                        <span class="tech-tag">Electronics</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View on GitHub</a>
                        <a href="#" class="project-link secondary">Learn More</a>
                    </div>
                </div>
            </div>

            <div class="project-card" data-project="wave-sim">
                <div class="project-image">🌊</div>
                <div class="project-content">
                    <h3 class="project-title">Wave Interference Simulation</h3>
                    <p class="project-description">Interactive Python simulation demonstrating wave interference patterns, helping visualize constructive and destructive interference in physics.</p>
                    <div class="tech-stack">
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">Matplotlib</span>
                        <span class="tech-tag">NumPy</span>
                        <span class="tech-tag">Physics</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View on GitHub</a>
                        <a href="#" class="project-link secondary">Live Demo</a>
                    </div>
                </div>
            </div>

            <div class="project-card" data-project="data-analysis">
                <div class="project-image">📊</div>
                <div class="project-content">
                    <h3 class="project-title">Physics Data Analysis Tool</h3>
                    <p class="project-description">A comprehensive tool for analyzing experimental physics data, including error analysis, curve fitting, and statistical interpretation.</p>
                    <div class="tech-stack">
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">Pandas</span>
                        <span class="tech-tag">SciPy</span>
                        <span class="tech-tag">Statistics</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View on GitHub</a>
                        <a href="#" class="project-link secondary">Documentation</a>
                    </div>
                </div>
            </div>

            <div class="project-card" data-project="monte-carlo">
                <div class="project-image">🎲</div>
                <div class="project-content">
                    <h3 class="project-title">Monte Carlo Simulation Suite</h3>
                    <p class="project-description">Collection of Monte Carlo simulations for physics problems, including random walks, particle interactions, and statistical mechanics.</p>
                    <div class="tech-stack">
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">Random</span>
                        <span class="tech-tag">Visualization</span>
                        <span class="tech-tag">Statistics</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View on GitHub</a>
                        <a href="#" class="project-link secondary">Examples</a>
                    </div>
                </div>
            </div>

            <div class="project-card" data-project="quantum-viz">
                <div class="project-image">⚛️</div>
                <div class="project-content">
                    <h3 class="project-title">Quantum State Visualizer</h3>
                    <p class="project-description">Interactive visualization tool for quantum mechanical states, helping students understand wave functions and probability distributions.</p>
                    <div class="tech-stack">
                        <span class="tech-tag">Python</span>
                        <span class="tech-tag">Quantum</span>
                        <span class="tech-tag">3D Graphics</span>
                        <span class="tech-tag">Education</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View on GitHub</a>
                        <a href="#" class="project-link secondary">Try Online</a>
                    </div>
                </div>
            </div>

            <div class="project-card" data-project="lab-notebook">
                <div class="project-image">📝</div>
                <div class="project-content">
                    <h3 class="project-title">Digital Lab Notebook</h3>
                    <p class="project-description">Web-based laboratory notebook for physics experiments with LaTeX support, data visualization, and collaborative features.</p>
                    <div class="tech-stack">
                        <span class="tech-tag">HTML/CSS</span>
                        <span class="tech-tag">JavaScript</span>
                        <span class="tech-tag">LaTeX</span>
                        <span class="tech-tag">Charts</span>
                    </div>
                    <div class="project-links">
                        <a href="#" class="project-link">View on GitHub</a>
                        <a href="#" class="project-link secondary">Demo</a>
                    </div>
                </div>
            </div>
        </div>

        <!-- GitHub Projects Integration -->
        <div class="github-projects" id="githubProjects">
            <div class="github-header">
                <h3>Latest GitHub Repositories</h3>
                <p>Automatically fetched from my GitHub profile</p>
            </div>
            <div class="projects-grid" id="githubGrid">
                <!-- GitHub projects will be populated here -->
            </div>
        </div>
    </section>

    <!-- Project Modal -->
    <div class="modal" id="projectModal">
        <div class="modal-content">
            <button class="modal-close" id="modalClose">×</button>
            <h2 class="modal-title" id="modalTitle">Project Title</h2>
            <div class="modal-description" id="modalDescription">
                Project description will be loaded here...
            </div>
            <div class="project-links" id="modalLinks">
                <!-- Links will be populated dynamically -->
            </div>
        </div>
    </div>

    <!-- Blog Section -->
    <section id="blog" class="section blog">
        <h2 class="section-title">Learning Journey Blog</h2>
        <div class="blog-header">
            <div></div>
            <input type="text" class="blog-search" id="blogSearch" placeholder="Search blog posts...">
        </div>
        <div class="blog-grid" id="blogGrid">
            <article class="blog-post" data-tags="physics quantum">
                <div class="blog-date">December 15, 2024</div>
                <h3 class="blog-title">Understanding Quantum Superposition</h3>
                <p class="blog-summary">Exploring the fascinating concept of quantum superposition and its implications for quantum computing. In this post, I dive deep into the mathematical formalism and practical applications...</p>
                <div class="blog-tags">
                    <span class="blog-tag physics">Physics</span>
                    <span class="blog-tag quantum">Quantum</span>
                </div>
            </article>

            <article class="blog-post" data-tags="ielts preparation">
                <div class="blog-date">December 8, 2024</div>
                <h3 class="blog-title">IELTS Speaking Practice: My Journey</h3>
                <p class="blog-summary">Sharing my experience and strategies for improving IELTS speaking scores. From overcoming nervousness to mastering complex topics, here's what worked for me...</p>
                <div class="blog-tags">
                    <span class="blog-tag ielts">IELTS</span>
                    <span class="blog-tag preparation">Preparation</span>
                </div>
            </article>

            <article class="blog-post" data-tags="sat math physics">
                <div class="blog-date">November 28, 2024</div>
                <h3 class="blog-title">SAT Math: Physics Problem-Solving Techniques</h3>
                <p class="blog-summary">How my physics background helps me approach SAT math problems differently. Discover techniques that can boost your problem-solving speed and accuracy...</p>
                <div class="blog-tags">
                    <span class="blog-tag sat">SAT</span>
                    <span class="blog-tag math">Math</span>
                    <span class="blog-tag physics">Physics</span>
                </div>
            </article>

            <article class="blog-post" data-tags="programming python">
                <div class="blog-date">November 20, 2024</div>
                <h3 class="blog-title">Python for Physics: Essential Libraries</h3>
                <p class="blog-summary">A comprehensive guide to Python libraries every physics student should know. From NumPy for numerical computations to Matplotlib for visualizations...</p>
                <div class="blog-tags">
                    <span class="blog-tag programming">Programming</span>
                    <span class="blog-tag python">Python</span>
                </div>
            </article>

            <article class="blog-post" data-tags="university applications">
                <div class="blog-date">November 10, 2024</div>
                <h3 class="blog-title">Crafting the Perfect Physics Personal Statement</h3>
                <p class="blog-summary">Tips and insights for writing compelling personal statements for physics programs. What admissions committees look for and how to stand out...</p>
                <div class="blog-tags">
                    <span class="blog-tag university">University</span>
                    <span class="blog-tag applications">Applications</span>
                </div>
            </article>

            <article class="blog-post coming-soon" data-tags="quantum research">
                <div class="blog-date">Coming Soon</div>
                <h3 class="blog-title">My First Quantum Computing Research Paper</h3>
                <p class="blog-summary">Currently working on my first research paper in quantum computing. I'll share the entire process, from literature review to final submission...</p>
                <div class="blog-tags">
                    <span class="blog-tag quantum">Quantum</span>
                    <span class="blog-tag research">Research</span>
                </div>
            </article>
        </div>
    </section>

    <!-- Resources Section -->
    <section id="resources" class="section">
        <h2 class="section-title">Student Resources</h2>
        <div class="resources-filters">
            <button class="filter-btn active" data-filter="all">All Resources</button>
            <button class="filter-btn" data-filter="ielts">IELTS Prep</button>
            <button class="filter-btn" data-filter="sat">SAT Prep</button>
            <button class="filter-btn" data-filter="physics">Physics Books</button>
            <button class="filter-btn" data-filter="programming">Free Courses</button>
        </div>
        <div class="resources-grid" id="resourcesGrid">
            <div class="resource-card" data-category="ielts">
                <h3>🎯 IELTS Preparation</h3>
                <ul class="resource-list">
                    <li><a href="#">IELTS Official Practice Tests</a></li>
                    <li><a href="#">British Council Free Resources</a></li>
                    <li><a href="#">Cambridge IELTS Books (1-17)</a></li>
                    <li><a href="#">IELTS Liz Website</a></li>
                    <li><a href="#">Speaking Practice Apps</a></li>
                </ul>
            </div>

            <div class="resource-card" data-category="sat">
                <h3>📚 SAT Preparation</h3>
                <ul class="resource-list">
                    <li><a href="#">Khan Academy SAT Practice</a></li>
                    <li><a href="#">College Board Official Tests</a></li>
                    <li><a href="#">Princeton Review SAT Prep</a></li>
                    <li><a href="#">Barron's SAT Study Guide</a></li>
                    <li><a href="#">SAT Math Level 2 Resources</a></li>
                </ul>
            </div>

            <div class="resource-card" data-category="physics">
                <h3>⚛️ Physics Learning</h3>
                <ul class="resource-list">
                    <li><a href="#">Griffiths Introduction to Quantum Mechanics</a></li>
                    <li><a href="#">Halliday, Resnick & Walker Physics</a></li>
                    <li><a href="#">MIT OpenCourseWare Physics</a></li>
                    <li><a href="#">Feynman Lectures on Physics</a></li>
                    <li><a href="#">Physics Classroom Online</a></li>
                </ul>
            </div>

            <div class="resource-card" data-category="programming">
                <h3>💻 Programming Courses</h3>
                <ul class="resource-list">
                    <li><a href="#">Python for Everybody (Coursera)</a></li>
                    <li><a href="#">CS50 Introduction to Computer Science</a></li>
                    <li><a href="#">FreeCodeCamp Python Course</a></li>
                    <li><a href="#">Codecademy Learn Python</a></li>
                    <li><a href="#">Automate the Boring Stuff with Python</a></li>
                </ul>
            </div>

            <div class="resource-card" data-category="physics programming">
                <h3>🔬 For Curious Students</h3>
                <ul class="resource-list">
                    <li><a href="#">Computational Physics with Python</a></li>
                    <li><a href="#">LaTeX Tutorial for Scientists</a></li>
                    <li><a href="#">Jupyter Notebooks for Physics</a></li>
                    <li><a href="#">Git Version Control Guide</a></li>
                    <li><a href="#">Academic Writing Resources</a></li>
                </ul>
            </div>

            <div class="resource-card" data-category="university">
                <h3>🎓 University Applications</h3>
                <ul class="resource-list">
                    <li><a href="#">Common Application Guide</a></li>
                    <li><a href="#">Physics Program Rankings</a></li>
                    <li><a href="#">Scholarship Search Engines</a></li>
                    <li><a href="#">Personal Statement Examples</a></li>
                    <li><a href="#">Recommendation Letter Tips</a></li>
                </ul>
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="section contact">
        <h2 class="section-title">Get In Touch</h2>
        <div class="contact-content">
            <p class="contact-intro">I'm always interested in connecting with fellow physics enthusiasts, mentors, and potential collaborators. Whether you have questions about my projects, want to discuss physics, or share study tips, feel free to reach out!</p>
            <form class="contact-form" id="contactForm">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" id="name" name="name" placeholder="Your name" required>
                </div>
                <div class="form-group">
                    <label for="email">Email</label>
                    <input type="email" id="email" name="email" placeholder="your.email@example.com" required>
                </div>
                <div class="form-group">
                    <label for="subject">Subject</label>
                    <input type="text" id="subject" name="subject" placeholder="What's this about?">
                </div>
                <div class="form-group">
                    <label for="message">Message</label>
                    <textarea id="message" name="message" rows="5" placeholder="Your message here..." required></textarea>
                </div>
                <button type="submit" class="submit-btn">Send Message</button>
            </form>
            <div class="social-links">
                <a href="#" class="social-link" title="GitHub">🐱</a>
                <a href="#" class="social-link" title="LinkedIn">💼</a>
                <a href="#" class="social-link" title="Facebook">📘</a>
                <a href="#" class="social-link" title="YouTube">📺</a>
                <a href="mailto:bipin@example.com" class="social-link" title="Gmail">📧</a>
            </div>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <p>&copy; 2025 Bipin. All rights reserved.</p>
        <p class="built-by">Built by Bipin with 💡 curiosity and HTML</p>
    </footer>

    <script>
        // ========== THEME TOGGLE ========== 
        const themeToggle = document.getElementById('themeToggle');
        const body = document.body;

        // Check for saved theme preference or default to dark
        const currentTheme = JSON.parse(localStorage.getItem('theme')) || 'dark';
        body.setAttribute('data-theme', currentTheme);
        themeToggle.textContent = currentTheme === 'dark' ? '🌙' : '☀️';

        themeToggle.addEventListener('click', () => {
            const currentTheme = body.getAttribute('data-theme');
            const newTheme = currentTheme === 'dark' ? 'light' : 'dark';
            
            body.setAttribute('data-theme', newTheme);
            localStorage.setItem('theme', JSON.stringify(newTheme));
            themeToggle.textContent = newTheme === 'dark' ? '🌙' : '☀️';
        });

        // ========== MOBILE NAVIGATION ========== 
        const mobileMenuBtn = document.getElementById('mobileMenuBtn');
        const mobileNav = document.getElementById('mobileNav');
        const mobileClose = document.getElementById('mobileClose');

        mobileMenuBtn.addEventListener('click', () => {
            mobileNav.classList.add('active');
        });

        mobileClose.addEventListener('click', () => {
            mobileNav.classList.remove('active');
        });

        // Close mobile nav when clicking on links
        document.querySelectorAll('.mobile-nav a').forEach(link => {
            link.addEventListener('click', () => {
                mobileNav.classList.remove('active');
            });
        });

        // ========== NAVBAR SCROLL EFFECT ========== 
        window.addEventListener('scroll', () => {
            const navbar = document.getElementById('navbar');
            if (window.scrollY > 50) {
                navbar.classList.add('scrolled');
            } else {
                navbar.classList.remove('scrolled');
            }
        });

        // ========== PARTICLE ANIMATION ========== 
        function createParticles() {
            const particlesContainer = document.getElementById('particles');
            const particleCount = 50;

            for (let i = 0; i < particleCount; i++) {
                const particle = document.createElement('div');
                particle.className = 'particle';
                particle.style.left = Math.random() * 100 + '%';
                particle.style.top = Math.random() * 100 + '%';
                particle.style.width = Math.random() * 4 + 2 + 'px';
                particle.style.height = particle.style.width;
                particle.style.animationDelay = Math.random() * 6 + 's';
                particle.style.animationDuration = (Math.random() * 4 + 4) + 's';
                particlesContainer.appendChild(particle);
            }
        }



        // ========== PROJECT MODAL ========== 
        const projectCards = document.querySelectorAll('.project-card');
        const projectModal = document.getElementById('projectModal');
        const modalClose = document.getElementById('modalClose');
        const modalTitle = document.getElementById('modalTitle');
        const modalDescription = document.getElementById('modalDescription');
        const modalLinks = document.getElementById('modalLinks');

        // Project data for modal
        const projectData = {
            'handglove': {
                title: 'Smart Hand Glove Project',
                description: `
                    <p>This innovative wearable device represents my first major hardware project, combining electronics, programming, and human-computer interaction principles.</p>
                    
                    <h4>🔧 Technical Details:</h4>
                    <ul>
                        <li>Arduino Uno microcontroller as the main processing unit</li>
                        <li>Flex sensors attached to each finger for gesture detection</li>
                        <li>Accelerometer and gyroscope for hand orientation</li>
                        <li>Bluetooth module for wireless communication</li>
                        <li>Custom PCB design for compact integration</li>
                    </ul>
                    
                    <h4>💡 Key Features:</h4>
                    <ul>
                        <li>Real-time gesture recognition with 95% accuracy</li>
                        <li>Customizable gesture commands through companion app</li>
                        <li>Low-power design with 8+ hours battery life</li>
                        <li>Machine learning calibration for user adaptation</li>
                    </ul>
                    
                    <h4>🎯 Applications:</h4>
                    <p>This project has potential applications in assistive technology, virtual reality interfaces, and remote device control. I'm currently exploring partnerships with local disability organizations to test real-world applications.</p>
                `,
                links: [
                    { text: 'View on GitHub', url: '#', class: 'project-link' },
                    { text: 'Demo Video', url: '#', class: 'project-link secondary' },
                    { text: 'Technical Report', url: '#', class: 'project-link secondary' }
                ]
            },
            'wave-sim': {
                title: 'Wave Interference Simulation',
                description: `
                    <p>An interactive educational tool that visualizes wave interference phenomena, making abstract physics concepts tangible for students.</p>
                    
                    <h4>🌊 Physics Concepts Covered:</h4>
                    <ul>
                        <li>Constructive and destructive interference</li>
                        <li>Standing waves and resonance</li>
                        <li>Doppler effect visualization</li>
                        <li>Wave reflection and refraction</li>
                    </ul>
                    
                    <h4>💻 Technical Implementation:</h4>
                    <ul>
                        <li>Real-time wave equation solving using NumPy</li>
                        <li>Interactive parameter controls (frequency, amplitude, phase)</li>
                        <li>3D visualization using Matplotlib's animation features</li>
                        <li>Export functionality for lab reports</li>
                    </ul>
                    
                    <h4>🎓 Educational Impact:</h4>
                    <p>This simulation has been used by over 200 students in my local physics club. Teachers report that visual learners particularly benefit from seeing wave interactions in real-time.</p>
                `,
                links: [
                    { text: 'GitHub Repository', url: '#', class: 'project-link' },
                    { text: 'Live Demo', url: '#', class: 'project-link secondary' },
                    { text: 'Educational Guide', url: '#', class: 'project-link secondary' }
                ]
            },
            'data-analysis': {
                title: 'Physics Data Analysis Tool',
                description: `
                    <p>A comprehensive Python toolkit designed to streamline the analysis of experimental physics data, with built-in error analysis and statistical methods.</p>
                    
                    <h4>📊 Core Features:</h4>
                    <ul>
                        <li>Automated error propagation calculations</li>
                        <li>Non-linear curve fitting with confidence intervals</li>
                        <li>Statistical hypothesis testing</li>
                        <li>Professional graph generation with publication-ready formatting</li>
                        <li>LaTeX equation rendering in plots</li>
                    </ul>
                    
                    <h4>🔬 Experimental Support:</h4>
                    <ul>
                        <li>Mechanics experiments (pendulum, projectile motion)</li>
                        <li>Thermodynamics data analysis</li>
                        <li>Optics interference pattern analysis</li>
                        <li>Radioactive decay curve fitting</li>
                    </ul>
                    
                    <h4>📈 Impact:</h4>
                    <p>This tool has reduced my lab report preparation time by 60% while improving the quality of my data analysis. I'm sharing it with fellow physics students to help streamline their experimental work.</p>
                `,
                links: [
                    { text: 'Source Code', url: '#', class: 'project-link' },
                    { text: 'Documentation', url: '#', class: 'project-link secondary' },
                    { text: 'Example Analyses', url: '#', class: 'project-link secondary' }
                ]
            },
            'monte-carlo': {
                title: 'Monte Carlo Simulation Suite',
                description: `
                    <p>A collection of Monte Carlo simulations addressing various physics problems, from simple random walks to complex particle interactions.</p>
                    
                    <h4>🎲 Included Simulations:</h4>
                    <ul>
                        <li><strong>Random Walks:</strong> 1D, 2D, and 3D Brownian motion</li>
                        <li><strong>Ising Model:</strong> Magnetic phase transitions</li>
                        <li><strong>Particle Scattering:</strong> Cross-section calculations</li>
                        <li><strong>Quantum Tunneling:</strong> Transmission probability estimation</li>
                        <li><strong>Statistical Mechanics:</strong> Ideal gas properties</li>
                    </ul>
                    
                    <h4>⚡ Performance Features:</h4>
                    <ul>
                        <li>Optimized algorithms for large-scale simulations</li>
                        <li>Parallel processing support using multiprocessing</li>
                        <li>Memory-efficient data structures</li>
                        <li>Progress tracking for long-running simulations</li>
                    </ul>
                    
                    <h4>📚 Learning Outcomes:</h4>
                    <p>These simulations deepened my understanding of statistical mechanics and computational physics methods. They've been particularly valuable for visualizing concepts that are difficult to grasp analytically.</p>
                `,
                links: [
                    { text: 'GitHub Repository', url: '#', class: 'project-link' },
                    { text: 'Run Examples', url: '#', class: 'project-link secondary' },
                    { text: 'Theory Guide', url: '#', class: 'project-link secondary' }
                ]
            },
            'quantum-viz': {
                title: 'Quantum State Visualizer',
                description: `
                    <p>An interactive tool for visualizing quantum mechanical states and operations, designed to make quantum mechanics more intuitive for students.</p>
                    
                    <h4>⚛️ Visualization Features:</h4>
                    <ul>
                        <li>3D wave function plotting with customizable parameters</li>
                        <li>Probability density animations</li>
                        <li>Bloch sphere representation for qubit states</li>
                        <li>Time evolution of quantum states</li>
                        <li>Interactive measurement simulation</li>
                    </ul>
                    
                    <h4>🎯 Educational Applications:</h4>
                    <ul>
                        <li>Hydrogen atom orbital visualization</li>
                        <li>Quantum harmonic oscillator states</li>
                        <li>Particle in a box solutions</li>
                        <li>Quantum tunneling demonstrations</li>
                    </ul>
                    
                    <h4>🔬 Technical Implementation:</h4>
                    <p>Built using Python with matplotlib for 2D/3D plotting and scipy for numerical solutions to the Schrödinger equation. The interactive interface uses ipywidgets for Jupyter notebook integration.</p>
                `,
                links: [
                    { text: 'Source Code', url: '#', class: 'project-link' },
                    { text: 'Online Demo', url: '#', class: 'project-link secondary' },
                    { text: 'Tutorial Videos', url: '#', class: 'project-link secondary' }
                ]
            },
            'lab-notebook': {
                title: 'Digital Lab Notebook',
                description: `
                    <p>A modern, web-based laboratory notebook designed specifically for physics experiments, featuring LaTeX support and collaborative capabilities.</p>
                    
                    <h4>📝 Core Features:</h4>
                    <ul>
                        <li>Rich text editor with LaTeX equation support</li>
                        <li>Integrated data plotting and analysis tools</li>
                        <li>Photo and video attachment capabilities</li>
                        <li>Version control for experiment iterations</li>
                        <li>Collaborative sharing with supervisors</li>
                    </ul>
                    
                    <h4>📊 Data Management:</h4>
                    <ul>
                        <li>CSV data import with automatic plotting</li>
                        <li>Real-time calculation fields</li>
                        <li>Error propagation tracking</li>
                        <li>Export to PDF for submission</li>
                    </ul>
                    
                    <h4>🎓 Benefits:</h4>
                    <p>This digital approach has improved my lab organization and made it easier to reference previous experiments. The LaTeX integration ensures professional presentation of equations and results.</p>
                `,
                links: [
                    { text: 'GitHub Code', url: '#', class: 'project-link' },
                    { text: 'Live Demo', url: '#', class: 'project-link secondary' },
                    { text: 'User Guide', url: '#', class: 'project-link secondary' }
                ]
            }
        };

        projectCards.forEach(card => {
            card.addEventListener('click', (e) => {
                // Don't open modal if clicking on links
                if (e.target.tagName === 'A') return;
                
                const projectId = card.getAttribute('data-project');
                const project = projectData[projectId];
                
                if (project) {
                    modalTitle.textContent = project.title;
                    modalDescription.innerHTML = project.description;
                    
                    // Clear and populate links
                    modalLinks.innerHTML = '';
                    project.links.forEach(link => {
                        const linkElement = document.createElement('a');
                        linkElement.href = link.url;
                        linkElement.textContent = link.text;
                        linkElement.className = link.class;
                        modalLinks.appendChild(linkElement);
                    });
                    
                    projectModal.classList.add('active');
                    document.body.style.overflow = 'hidden';
                }
            });
        });

        modalClose.addEventListener('click', () => {
            projectModal.classList.remove('active');
            document.body.style.overflow = 'auto';
        });

        projectModal.addEventListener('click', (e) => {
            if (e.target === projectModal) {
                projectModal.classList.remove('active');
                document.body.style.overflow = 'auto';
            }
        });

        // ========== BLOG SEARCH ========== 
        const blogSearch = document.getElementById('blogSearch');
        const blogPosts = document.querySelectorAll('.blog-post');

        blogSearch.addEventListener('input', (e) => {
            const searchTerm = e.target.value.toLowerCase();
            
            blogPosts.forEach(post => {
                const title = post.querySelector('.blog-title').textContent.toLowerCase();
                const summary = post.querySelector('.blog-summary').textContent.toLowerCase();
                const tags = post.getAttribute('data-tags').toLowerCase();
                
                if (title.includes(searchTerm) || summary.includes(searchTerm) || tags.includes(searchTerm)) {
                    post.style.display = 'block';
                } else {
                    post.style.display = 'none';
                }
            });
        });

        // ========== GLOBAL SEARCH ========== 
        const globalSearch = document.getElementById('globalSearch');

        globalSearch.addEventListener('input', (e) => {
            const searchTerm = e.target.value.toLowerCase();
            
            // Search blog posts
            blogPosts.forEach(post => {
                const title = post.querySelector('.blog-title').textContent.toLowerCase();
                const summary = post.querySelector('.blog-summary').textContent.toLowerCase();
                
                if (title.includes(searchTerm) || summary.includes(searchTerm)) {
                    post.style.display = 'block';
                } else {
                    post.style.display = 'none';
                }
            });
            
            // Search resources
            const resourceCards = document.querySelectorAll('.resource-card');
            resourceCards.forEach(card => {
                const text = card.textContent.toLowerCase();
                if (text.includes(searchTerm)) {
                    card.style.display = 'block';
                } else {
                    card.style.display = 'none';
                }
            });
        });

        // ========== RESOURCE FILTERS ========== 
        const filterBtns = document.querySelectorAll('.filter-btn');
        const resourceCards = document.querySelectorAll('.resource-card');

        filterBtns.forEach(btn => {
            btn.addEventListener('click', () => {
                // Update active button
                filterBtns.forEach(b => b.classList.remove('active'));
                btn.classList.add('active');
                
                const filter = btn.getAttribute('data-filter');
                
                resourceCards.forEach(card => {
                    if (filter === 'all') {
                        card.classList.remove('hidden');
                    } else {
                        const categories = card.getAttribute('data-category').split(' ');
                        if (categories.includes(filter)) {
                            card.classList.remove('hidden');
                        } else {
                            card.classList.add('hidden');
                        }
                    }
                });
            });
        });

        // ========== GITHUB INTEGRATION ========== 
        async function fetchGitHubRepos() {
            try {
                // Replace 'your-username' with actual GitHub username
                const response = await fetch('https://api.github.com/users/your-username/repos?sort=updated&per_page=6');
                const repos = await response.json();
                
                const githubGrid = document.getElementById('githubGrid');
                githubGrid.innerHTML = '';
                
                repos.forEach(repo => {
                    const repoCard = document.createElement('div');
                    repoCard.className = 'project-card';
                    repoCard.innerHTML = `
                        <div class="project-image">📁</div>
                        <div class="project-content">
                            <h3 class="project-title">${repo.name}</h3>
                            <p class="project-description">${repo.description || 'No description available'}</p>
                            <div class="tech-stack">
                                <span class="tech-tag">${repo.language || 'Unknown'}</span>
                                <span class="tech-tag">⭐ ${repo.stargazers_count}</span>
                            </div>
                            <div class="project-links">
                                <a href="${repo.html_url}" class="project-link" target="_blank">View Repository</a>
                                ${repo.homepage ? `<a href="${repo.homepage}" class="project-link secondary" target="_blank">Live Demo</a>` : ''}
                            </div>
                        </div>
                    `;
                    githubGrid.appendChild(repoCard);
                });
            } catch (error) {
                console.log('GitHub API not available, using placeholder data');
                // Fallback to placeholder data if API fails
            }
        }

        // ========== CONTACT FORM ========== 
        const contactForm = document.getElementById('contactForm');

        contactForm.addEventListener('submit', (e) => {
            e.preventDefault();
            
            // Get form data
            const formData = new FormData(contactForm);
            const name = formData.get('name');
            const email = formData.get('email');
            const subject = formData.get('subject');
            const message = formData.get('message');
            
            // Simulate form submission
            alert(`Thank you, ${name}! Your message has been received. I'll get back to you at ${email} soon.`);
            
            // Reset form
            contactForm.reset();
        });

        // ========== CV DOWNLOAD ========== 
        function downloadCV() {
            // In a real implementation, this would download an actual CV file
            alert('CV download feature coming soon! For now, please contact me directly for my resume.');
        }

        // ========== SMOOTH SCROLLING ========== 
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                if (target) {
                    target.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });

        // ========== SCROLL ANIMATIONS ========== 
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver(function(entries) {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, observerOptions);

        // Observe elements for scroll animations
        document.querySelectorAll('.skill-category, .project-card, .blog-post, .resource-card').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(30px)';
            el.style.transition = 'opacity 0.6s ease, transform 0.6s ease';
            observer.observe(el);
        });

        // ========== MATHJS CONFIGURATION ========== 
        window.MathJax = {
            tex: {
                inlineMath: [[', '], ['\\(', '\\)']],
                displayMath: [['$', '$'], ['\\[', '\\]']]
            },
            svg: {
                fontCache: 'global'
            }
        };

        // ========== INITIALIZATION ========== 
        document.addEventListener('DOMContentLoaded', () => {
            createParticles();
            // fetchGitHubRepos(); // Uncomment when you have a GitHub username
            
            // Initialize theme from localStorage
            const savedTheme = localStorage.getItem('theme');
            if (savedTheme) {
                document.body.setAttribute('data-theme', JSON.parse(savedTheme));
                themeToggle.textContent = JSON.parse(savedTheme) === 'dark' ? '🌙' : '☀️';
            }
        });

        // ========== KEYBOARD SHORTCUTS ========== 
        document.addEventListener('keydown', (e) => {
            // Press 'T' to toggle theme
            if (e.key === 't' || e.key === 'T') {
                if (!e.target.matches('input, textarea')) {
                    themeToggle.click();
                }
            }
            
            // Press 'Escape' to close modal
            if (e.key === 'Escape') {
                if (projectModal.classList.contains('active')) {
                    modalClose.click();
                }
                if (mobileNav.classList.contains('active')) {
                    mobileClose.click();
                }
            }
        });
    </script>
</body>
</html>
