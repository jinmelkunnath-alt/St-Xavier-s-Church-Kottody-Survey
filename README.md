<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>St Xavier's Church Kottody | Survey Portal</title>
    <style>
        /* Reset & Base Styles */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-color: #2c5530;
            --primary-dark: #1e3a23;
            --secondary-color: #8b4513;
            --accent-color: #d4af37;
            --light-color: #f8f9fa;
            --dark-color: #212529;
            --gray-color: #6c757d;
            --gray-light: #e9ecef;
            --shadow: 0 10px 20px rgba(0, 0, 0, 0.08);
            --shadow-hover: 0 15px 30px rgba(0, 0, 0, 0.12);
            --radius: 12px;
            --transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.1);
            --transition-smooth: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
        }

        body {
            font-family: 'Inter', sans-serif;
            line-height: 1.6;
            color: var(--dark-color);
            background: linear-gradient(135deg, #f5f7fa 0%, #e9f5eb 100%);
            min-height: 100vh;
            overflow-x: hidden;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        .header {
            padding: 2.5rem 0;
            text-align: center;
            background: linear-gradient(135deg, var(--primary-color), var(--primary-dark));
            color: white;
            position: relative;
            overflow: hidden;
        }

        .header::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100" preserveAspectRatio="none" opacity="0.05"><path d="M0,0 L100,0 L100,100 Z" fill="white"/></svg>');
            background-size: cover;
        }

        .logo {
            font-size: 2.8rem;
            font-weight: 700;
            margin-bottom: 0.8rem;
            position: relative;
            display: inline-block;
            letter-spacing: 1px;
        }

        .logo i {
            margin-right: 15px;
            color: var(--accent-color);
        }

        .church-name {
            font-size: 1.8rem;
            font-weight: 400;
            margin-bottom: 0.8rem;
            color: var(--accent-color);
            letter-spacing: 2px;
        }

        .subtitle {
            font-size: 1.2rem;
            font-weight: 300;
            opacity: 0.9;
            max-width: 700px;
            margin: 0 auto;
            line-height: 1.8;
        }

        /* Main Content */
        .main-content {
            padding: 3.5rem 0;
            position: relative;
        }

        .section-title {
            font-size: 2.4rem;
            font-weight: 700;
            text-align: center;
            margin-bottom: 1.2rem;
            color: var(--primary-dark);
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -12px;
            left: 0;
            width: 100%;
            height: 4px;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
            border-radius: 2px;
        }

        .section-description {
            text-align: center;
            color: var(--gray-color);
            max-width: 800px;
            margin: 0 auto 3.5rem;
            font-size: 1.2rem;
            line-height: 1.8;
            padding: 0 20px;
        }

        /* Grid */
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            gap: 2rem;
            margin-bottom: 5rem;
        }

        /* Card Styles - NO ICONS */
        .survey-card {
            background: white;
            border-radius: var(--radius);
            padding: 2.5rem 1.8rem;
            box-shadow: var(--shadow);
            transition: var(--transition);
            cursor: pointer;
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(255, 255, 255, 0.2);
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
            min-height: 220px;
            opacity: 0;
            transform: translateY(30px);
        }

        .survey-card.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .survey-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 6px;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
        }

        .survey-card:hover {
            transform: translateY(-12px);
            box-shadow: var(--shadow-hover);
            background: linear-gradient(145deg, #ffffff, #f8f9fa);
        }

        .survey-card:active {
            transform: translateY(-6px) scale(0.98);
            transition: all 0.1s ease;
        }

        .card-title {
            font-size: 1.8rem;
            font-weight: 700;
            margin-bottom: 1.2rem;
            color: var(--primary-dark);
            line-height: 1.4;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .card-number {
            position: absolute;
            top: 15px;
            right: 15px;
            background: var(--gray-light);
            color: var(--gray-color);
            width: 36px;
            height: 36px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 1rem;
            font-weight: 700;
            border: 2px solid var(--primary-color);
        }

        .card-description {
            font-size: 1rem;
            color: var(--gray-color);
            line-height: 1.6;
            margin-top: 0.5rem;
            font-weight: 400;
        }

        /* Info Section */
        .info-section {
            background: white;
            border-radius: var(--radius);
            padding: 3rem;
            box-shadow: var(--shadow);
            margin-top: 3rem;
            border-left: 6px solid var(--primary-color);
            background: linear-gradient(135deg, #ffffff, #f9f9f9);
        }

        .info-section h3 {
            font-size: 1.8rem;
            margin-bottom: 1.5rem;
            color: var(--primary-dark);
            display: flex;
            align-items: center;
        }

        .info-section h3 i {
            color: var(--primary-color);
            margin-right: 12px;
        }

        .info-section p {
            color: var(--gray-color);
            margin-bottom: 1.5rem;
            line-height: 1.8;
            font-size: 1.1rem;
        }

        .info-section p:last-child {
            margin-bottom: 0;
        }

        /* Footer */
        .footer {
            padding: 2.5rem 0;
            text-align: center;
            background: var(--primary-dark);
            color: white;
            margin-top: 4rem;
        }

        .footer p {
            margin-bottom: 0.8rem;
            font-size: 1.1rem;
        }

        .footer-note {
            font-size: 1rem;
            opacity: 0.8;
        }

        .church-address {
            font-size: 0.95rem;
            opacity: 0.7;
            margin-top: 1rem;
            font-style: italic;
        }

        /* Responsive Design */
        @media (max-width: 1024px) {
            .grid-container {
                grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
                gap: 1.8rem;
            }
            
            .section-title {
                font-size: 2.2rem;
            }
            
            .logo {
                font-size: 2.4rem;
            }
            
            .church-name {
                font-size: 1.6rem;
            }
        }

        @media (max-width: 768px) {
            .grid-container {
                grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
                gap: 1.5rem;
            }
            
            .logo {
                font-size: 2rem;
            }
            
            .church-name {
                font-size: 1.4rem;
            }
            
            .section-title {
                font-size: 2rem;
            }
            
            .survey-card {
                padding: 2.2rem 1.5rem;
                min-height: 200px;
            }
            
            .card-title {
                font-size: 1.6rem;
            }
            
            .info-section {
                padding: 2.5rem;
            }
        }

        @media (max-width: 576px) {
            .grid-container {
                grid-template-columns: repeat(2, 1fr);
                gap: 1.2rem;
            }
            
            .header {
                padding: 2rem 0;
            }
            
            .logo {
                font-size: 1.8rem;
            }
            
            .church-name {
                font-size: 1.2rem;
                letter-spacing: 1px;
            }
            
            .subtitle {
                font-size: 1rem;
                padding: 0 15px;
            }
            
            .main-content {
                padding: 2.5rem 0;
            }
            
            .section-title {
                font-size: 1.8rem;
            }
            
            .survey-card {
                padding: 2rem 1.2rem;
                min-height: 180px;
            }
            
            .card-title {
                font-size: 1.4rem;
            }
            
            .card-description {
                font-size: 0.9rem;
            }
            
            .info-section {
                padding: 2rem;
            }
        }

        @media (max-width: 400px) {
            .grid-container {
                grid-template-columns: 1fr;
                gap: 1.2rem;
            }
            
            .logo {
                font-size: 1.6rem;
            }
            
            .survey-card {
                min-height: 160px;
                padding: 1.8rem 1rem;
            }
        }

        /* Animation for scroll */
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

        /* Loading animation for cards */
        @keyframes pulse {
            0% {
                box-shadow: 0 0 0 0 rgba(44, 85, 48, 0.4);
            }
            70% {
                box-shadow: 0 0 0 12px rgba(44, 85, 48, 0);
            }
            100% {
                box-shadow: 0 0 0 0 rgba(44, 85, 48, 0);
            }
        }

        /* Touch device optimizations */
        @media (hover: none) and (pointer: coarse) {
            .survey-card:hover {
                transform: none;
            }
            
            .survey-card:active {
                transform: scale(0.96);
                box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            }
        }

        /* Decorative cross pattern */
        .cross-pattern {
            position: absolute;
            width: 100px;
            height: 100px;
            opacity: 0.03;
            pointer-events: none;
            z-index: 0;
        }

        .cross-pattern::before,
        .cross-pattern::after {
            content: '';
            position: absolute;
            background-color: var(--primary-color);
        }

        .cross-pattern::before {
            width: 100%;
            height: 20%;
            top: 40%;
            left: 0;
        }

        .cross-pattern::after {
            width: 20%;
            height: 100%;
            top: 0;
            left: 40%;
        }
    </style>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>⛪</text></svg>">
</head>
<body>
    <!-- Header Section -->
    <header class="header">
        <div class="container">
            <h1 class="logo">
                <i class="fas fa-church"></i> St Xavier's Church
            </h1>
            <div class="church-name">KOTTODY</div>
            <p class="subtitle">Parish Survey Portal - Share your feedback, suggestions, and participate in our community surveys</p>
        </div>
    </header>

    <!-- Main Content -->
    <main class="main-content">
        <div class="container">
            <!-- Grid Section -->
            <section class="grid-section">
                <h2 class="section-title">Parish Surveys</h2>
                <p class="section-description">Click on any survey card below to participate. Your feedback helps us improve our parish community and services.</p>
                
                <div class="grid-container" id="surveyGrid">
                    <!-- Grid items will be generated by JavaScript -->
                </div>
            </section>

            <!-- Info Section -->
            <section class="info-section">
                <h3><i class="fas fa-info-circle"></i> Important Information</h3>
                <p>Each card represents your ward and is used to enter your data. Your participation is valuable for the growth and improvement of St Xavier's Church Kottody.</p>
                <p>All surveys are anonymous and confidential. Please provide honest feedback to help us serve our community better.</p>
                <p>For any technical issues with the surveys, please contact the parish office.</p>
            </section>
        </div>
    </main>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <p>© <span id="currentYear"></span> St Xavier's Church Kottody. All rights reserved.</p>
            <p class="church-address">St Xavier's Church, Kottody, Kerala, India</p>
            <p class="footer-note">Parish Survey Portal | <span id="totalSurveys">16</span> Active Surveys</p>
        </div>
    </footer>

    <!-- JavaScript -->
    <script>
        // Survey data for St Xavier's Church Kottody - Updated with church-related surveys (NO ICONS)
        const surveyData = [
            { 
                id: 1, 
                title: "പെരുമ്പള്ളി", 
                description: "Fill Out For പെരുമ്പള്ളി",
                link: "https://form.svhrt.com/69882e793da1fbe0ac0d1d27" 
            },
            { 
                id: 2, 
                title: "മാവുങ്കാൽ", 
                description: "Fill Out For മാവുങ്കാൽ",
                link: "https://form.svhrt.com/69882dd57536b447853f05f1" 
            },
            { 
                id: 3, 
                title: "ഒരള", 
                description: "Fill Out For ഒരള",
                link: "https://form.svhrt.com/69882f7b5469c0f212b232b3" 
            },
            { 
                id: 4, 
                title: "പേരടുക്കം A", 
                description: "Fill Out For പേരടുക്കം A",
                link: "https://form.svhrt.com/69882fb9cced77ecf7171557" 
            },
            { 
                id: 5, 
                title: "പേരടുക്കം B", 
                description: "Fill Out For പേരടുക്കം B",
                link: "https://form.svhrt.com/69882ff53da1fbe0ac0d3b05" 
            },
            { 
                id: 6, 
                title: "പയ്യച്ചേരി", 
                description: "Fill Out For പയ്യച്ചേരി",
                link: "https://form.svhrt.com/6988320c7536b447853f56f7" 
            },
            { 
                id: 7, 
                title: "ചുള്ളിക്കര", 
                description: "Fill Out For ചുള്ളിക്കര",
                link: "https://form.svhrt.com/6988326f5469c0f212b268fe" 
            },
            { 
                id: 8, 
                title: "കുരിശുമല", 
                description: "Fill Out For കുരിശുമല",
                link: "https://form.svhrt.com/698832e95469c0f212b27365" 
            },
            { 
                id: 9, 
                title: "എരുമപ്പള്ള", 
                description: "Fill Out For എരുമപ്പള്ള",
                link: "https://form.svhrt.com/698832a5cced77ecf7174b12" 
            },
            { 
                id: 10, 
                title: "അയറോട്", 
                description: "Fill Out For അയറോട്",
                link: "https://form.svhrt.com/69883354cced77ecf7175b4c" 
            },
            { 
                id: 11, 
                title: "ഉമിക്കുപ്പ", 
                description: "Fill Out For ഉമിക്കുപ്പ",
                link: "https://form.svhrt.com/698833927536b447853f78c9" 
            },
            { 
                id: 12, 
                title: "കൊട്ടോടി", 
                description: "Fill Out For കൊട്ടോടി",
                link: "https://form.svhrt.com/698833b15469c0f212b2848d" 
            },
            { 
                id: 13, 
                title: "പാലപ്പുഴ", 
                description: "Fill Out For പാലപ്പുഴ",
                link: "https://form.svhrt.com/69883408cced77ecf7176a8d" 
            },
            { 
                id: 14, 
                title: "ഗ്രാഡിപ്പള്ള", 
                description: "Fill Out For ഗ്രാഡിപ്പള്ള",
                link: "https://form.svhrt.com/6988342a3da1fbe0ac0d8f77" 
            },
            { 
                id: 15, 
                title: "ചീച്ചക്കയ", 
                description: "Fill Out For ചീച്ചക്കയ",
                link: "https://form.svhrt.com/698834475469c0f212b29180" 
            },
            { 
                id: 16, 
                title: "ചീമുള്ള്", 
                description: "Fill Out For ചീമുള്ള്",
                link: "https://form.svhrt.com/698834823da1fbe0ac0d966e" 
            }
        ];

        // DOM elements
        const surveyGrid = document.getElementById('surveyGrid');
        const totalSurveysElement = document.getElementById('totalSurveys');
        const currentYearElement = document.getElementById('currentYear');

        // Initialize the application
        function initApp() {
            // Set current year in footer
            currentYearElement.textContent = new Date().getFullYear();
            
            // Set total surveys count
            totalSurveysElement.textContent = surveyData.length;
            
            // Generate survey cards
            generateSurveyCards();
            
            // Initialize scroll animations
            initScrollAnimations();
            
            // Add smooth scrolling to the page
            document.documentElement.style.scrollBehavior = 'smooth';
            
            // Add decorative cross patterns
            addDecorativePatterns();
        }

        // Generate survey cards dynamically
        function generateSurveyCards() {
            // Clear any existing content
            surveyGrid.innerHTML = '';
            
            // Create and append each survey card
            surveyData.forEach(survey => {
                const card = createSurveyCard(survey);
                surveyGrid.appendChild(card);
            });
            
            // Add click handlers to all cards
            attachCardClickHandlers();
        }

        // Create a single survey card element - NO ICONS
        function createSurveyCard(survey) {
            const card = document.createElement('div');
            card.className = 'survey-card';
            card.dataset.id = survey.id;
            
            // Card content WITHOUT icons
            card.innerHTML = `
                <div class="card-number">${survey.id}</div>
                <h3 class="card-title">${survey.title}</h3>
                <p class="card-description">${survey.description}</p>
                <div class="card-hint" style="margin-top: 1rem; font-size: 0.9rem; color: var(--accent-color); font-weight: 600;">Click to Participate</div>
            `;
            
            return card;
        }

        // Attach click handlers to all survey cards
        function attachCardClickHandlers() {
            const cards = document.querySelectorAll('.survey-card');
            
            cards.forEach(card => {
                card.addEventListener('click', function() {
                    const cardId = parseInt(this.dataset.id);
                    const survey = surveyData.find(s => s.id === cardId);
                    
                    if (survey) {
                        // Add click animation
                        this.style.animation = 'pulse 0.5s';
                        
                        // Reset animation after it completes
                        setTimeout(() => {
                            this.style.animation = '';
                        }, 500);
                        
                        // Open survey link in new tab after a brief delay for animation
                        setTimeout(() => {
                            window.open(survey.link, '_blank');
                        }, 300);
                    }
                });
            });
        }

        // Initialize scroll-based animations
        function initScrollAnimations() {
            // Create an intersection observer to animate cards when they enter the viewport
            const observerOptions = {
                root: null,
                rootMargin: '0px',
                threshold: 0.1
            };
            
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                        
                        // Add staggered animation delay based on element index
                        const cards = document.querySelectorAll('.survey-card');
                        const index = Array.from(cards).indexOf(entry.target);
                        entry.target.style.transitionDelay = `${index * 0.05}s`;
                    }
                });
            }, observerOptions);
            
            // Observe each survey card
            const cards = document.querySelectorAll('.survey-card');
            cards.forEach(card => {
                observer.observe(card);
            });
            
            // Add scroll effect to header
            window.addEventListener('scroll', () => {
                const header = document.querySelector('.header');
                const scrollPosition = window.scrollY;
                
                if (scrollPosition > 50) {
                    header.style.padding = '1.5rem 0';
                    header.style.boxShadow = '0 5px 20px rgba(0, 0, 0, 0.1)';
                } else {
                    header.style.padding = '2.5rem 0';
                    header.style.boxShadow = 'none';
                }
            });
        }

        // Add decorative cross patterns to the background
        function addDecorativePatterns() {
            const mainContent = document.querySelector('.main-content');
            const numberOfCrosses = 8;
            
            for (let i = 0; i < numberOfCrosses; i++) {
                const cross = document.createElement('div');
                cross.className = 'cross-pattern';
                
                // Random positioning
                const top = Math.random() * 80 + 10;
                const left = Math.random() * 80 + 10;
                const size = Math.random() * 40 + 30;
                
                cross.style.top = `${top}%`;
                cross.style.left = `${left}%`;
                cross.style.width = `${size}px`;
                cross.style.height = `${size}px`;
                
                mainContent.appendChild(cross);
            }
        }

        // Initialize the app when DOM is loaded
        document.addEventListener('DOMContentLoaded', initApp);

        // Add a simple loader effect for initial page load
        window.addEventListener('load', () => {
            document.body.style.opacity = '0';
            document.body.style.transition = 'opacity 0.5s ease';
            
            setTimeout(() => {
                document.body.style.opacity = '1';
            }, 100);
        });

        // Utility function to update survey links if needed
        function updateSurveyLink(surveyId, newLink) {
            const survey = surveyData.find(s => s.id === surveyId);
            if (survey) {
                survey.link = newLink;
                console.log(`Survey ${surveyId} link updated to: ${newLink}`);
            }
        }

        // Utility function to update survey title if needed
        function updateSurveyTitle(surveyId, newTitle) {
            const survey = surveyData.find(s => s.id === surveyId);
            if (survey) {
                survey.title = newTitle;
                
                // Update the card title in the DOM
                const card = document.querySelector(`.survey-card[data-id="${surveyId}"] .card-title`);
                if (card) {
                    card.textContent = newTitle;
                }
                
                console.log(`Survey ${surveyId} title updated to: ${newTitle}`);
            }
        }

        // Utility function to update survey description if needed
        function updateSurveyDescription(surveyId, newDescription) {
            const survey = surveyData.find(s => s.id === surveyId);
            if (survey) {
                survey.description = newDescription;
                
                // Update the card description in the DOM
                const cardDesc = document.querySelector(`.survey-card[data-id="${surveyId}"] .card-description`);
                if (cardDesc) {
                    cardDesc.textContent = newDescription;
                }
                
                console.log(`Survey ${surveyId} description updated to: ${newDescription}`);
            }
        }
    </script>
</body>
</html>
