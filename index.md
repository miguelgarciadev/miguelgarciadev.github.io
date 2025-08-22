<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tu Nombre - Portfolio</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary-color: #2c3e50;
            --secondary-color: #3498db;
            --accent-color: #e74c3c;
            --text-color: #333;
            --light-bg: #f8f9fa;
            --white: #ffffff;
            --shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
            color: var(--text-color);
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: var(--white);
            padding: 2rem 0;
            position: relative;
            overflow: hidden;
        }

        .header-bg {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grid" width="10" height="10" patternUnits="userSpaceOnUse"><path d="M 10 0 L 0 0 0 10" fill="none" stroke="rgba(255,255,255,0.1)" stroke-width="0.5"/></pattern></defs><rect width="100" height="100" fill="url(%23grid)"/></svg>');
            animation: float 6s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .header-content {
            position: relative;
            z-index: 2;
            text-align: center;
        }

        .header-content h1 {
            font-size: 3rem;
            margin-bottom: 0.5rem;
            animation: slideInDown 1s ease;
        }

        .header-content p {
            font-size: 1.2rem;
            opacity: 0.9;
            animation: slideInUp 1s ease;
        }

        @keyframes slideInDown {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes slideInUp {
            from { transform: translateY(50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* Navigation */
        nav {
            background: var(--white);
            box-shadow: var(--shadow);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            display: flex;
            justify-content: center;
            padding: 1rem 0;
        }

        .nav-links {
            display: flex;
            list-style: none;
            gap: 2rem;
        }

        .nav-links a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 500;
            padding: 0.5rem 1rem;
            border-radius: 25px;
            transition: var(--transition);
            position: relative;
        }

        .nav-links a:hover {
            color: var(--secondary-color);
            background: var(--light-bg);
            transform: translateY(-2px);
        }

        .nav-links a::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 50%;
            width: 0;
            height: 2px;
            background: var(--secondary-color);
            transition: var(--transition);
            transform: translateX(-50%);
        }

        .nav-links a:hover::after {
            width: 80%;
        }

        /* Main Content */
        main {
            padding: 4rem 0;
        }

        section {
            margin-bottom: 4rem;
            opacity: 0;
            transform: translateY(30px);
            animation: fadeInUp 1s ease forwards;
        }

        section:nth-child(2) { animation-delay: 0.2s; }
        section:nth-child(3) { animation-delay: 0.4s; }
        section:nth-child(4) { animation-delay: 0.6s; }

        @keyframes fadeInUp {
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            color: var(--primary-color);
            position: relative;
        }

        .section-title::after {
            content: '';
            position: absolute;
            bottom: -10px;
            left: 50%;
            width: 60px;
            height: 3px;
            background: var(--secondary-color);
            transform: translateX(-50%);
        }

        /* About Section */
        .about-content {
            display: grid;
            grid-template-columns: 1fr 2fr;
            gap: 3rem;
            align-items: center;
        }

        .about-image {
            text-align: center;
        }

        .profile-pic {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 4rem;
            color: var(--white);
            margin: 0 auto;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .profile-pic:hover {
            transform: scale(1.05) rotate(5deg);
        }

        .about-text p {
            font-size: 1.1rem;
            margin-bottom: 1.5rem;
            line-height: 1.8;
        }

        /* Skills */
        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
        }

        .skill-card {
            background: var(--white);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: var(--shadow);
            text-align: center;
            transition: var(--transition);
            border: 2px solid transparent;
        }

        .skill-card:hover {
            transform: translateY(-10px);
            border-color: var(--secondary-color);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
        }

        .skill-icon {
            font-size: 3rem;
            margin-bottom: 1rem;
            color: var(--secondary-color);
        }

        .skill-card h3 {
            margin-bottom: 1rem;
            color: var(--primary-color);
        }

        /* Projects */
        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2rem;
        }

        .project-card {
            background: var(--white);
            border-radius: 15px;
            overflow: hidden;
            box-shadow: var(--shadow);
            transition: var(--transition);
        }

        .project-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 30px rgba(0, 0, 0, 0.15);
        }

        .project-image {
            height: 200px;
            background: linear-gradient(135deg, var(--secondary-color), var(--primary-color));
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--white);
            font-size: 2rem;
        }

        .project-content {
            padding: 1.5rem;
        }

        .project-content h3 {
            margin-bottom: 1rem;
            color: var(--primary-color);
        }

        .project-content p {
            margin-bottom: 1.5rem;
            color: #666;
        }

        .project-links {
            display: flex;
            gap: 1rem;
        }

        .btn {
            padding: 0.5rem 1.5rem;
            border: none;
            border-radius: 25px;
            text-decoration: none;
            font-weight: 500;
            transition: var(--transition);
            cursor: pointer;
        }

        .btn-primary {
            background: var(--secondary-color);
            color: var(--white);
        }

        .btn-primary:hover {
            background: var(--primary-color);
            transform: translateY(-2px);
        }

        .btn-secondary {
            background: transparent;
            color: var(--secondary-color);
            border: 2px solid var(--secondary-color);
        }

        .btn-secondary:hover {
            background: var(--secondary-color);
            color: var(--white);
        }

        /* Contact */
        .contact-content {
            text-align: center;
            max-width: 600px;
            margin: 0 auto;
        }

        .contact-info {
            display: flex;
            justify-content: center;
            gap: 3rem;
            margin-top: 2rem;
        }

        .contact-item {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 0.5rem;
        }

        .contact-icon {
            font-size: 2rem;
            color: var(--secondary-color);
            margin-bottom: 0.5rem;
        }

        .contact-item a {
            color: var(--text-color);
            text-decoration: none;
            transition: var(--transition);
        }

        .contact-item a:hover {
            color: var(--secondary-color);
        }

        /* Footer */
        footer {
            background: var(--primary-color);
            color: var(--white);
            text-align: center;
            padding: 2rem 0;
        }

        /* Responsive */
        @media (max-width: 768px) {
            .header-content h1 {
                font-size: 2rem;
            }

            .nav-links {
                flex-direction: column;
                gap: 1rem;
            }

            .about-content {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .contact-info {
                flex-direction: column;
                gap: 2rem;
            }

            .section-title {
                font-size: 2rem;
            }
        }

        /* Scroll Animation */
        .fade-in {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.6s ease;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
    </style>
</head>
<body>
    <header>
        <div class="header-bg"></div>
        <div class="container">
            <div class="header-content">
                <h1>Tu Nombre</h1>
                <p>Desarrollador Web & Diseñador</p>
            </div>
        </div>
    </header>

    <nav>
        <div class="container">
            <div class="nav-container">
                <ul class="nav-links">
                    <li><a href="#inicio">Inicio</a></li>
                    <li><a href="#sobre-mi">Sobre Mí</a></li>
                    <li><a href="#habilidades">Habilidades</a></li>
                    <li><a href="#proyectos">Proyectos</a></li>
                    <li><a href="#contacto">Contacto</a></li>
                </ul>
            </div>
        </div>
    </nav>

    <main>
        <div class="container">
            <section id="sobre-mi">
                <h2 class="section-title">Sobre Mí</h2>
                <div class="about-content">
                    <div class="about-image">
                        <div class="profile-pic">👨‍💻</div>
                    </div>
                    <div class="about-text">
                        <p>¡Hola! Soy un desarrollador apasionado por crear experiencias web increíbles. Me especializo en tecnologías modernas y siempre estoy buscando nuevos desafíos para crecer profesionalmente.</p>
                        <p>Con experiencia en desarrollo frontend y backend, me encanta trabajar en proyectos que combinan funcionalidad y diseño elegante. Mi objetivo es crear soluciones que no solo funcionen bien, sino que también brinden una excelente experiencia de usuario.</p>
                        <p>Cuando no estoy programando, disfruto aprender nuevas tecnologías, contribuir a proyectos de código abierto y compartir conocimientos con la comunidad.</p>
                    </div>
                </div>
            </section>

            <section id="habilidades">
                <h2 class="section-title">Habilidades</h2>
                <div class="skills-grid">
                    <div class="skill-card fade-in">
                        <div class="skill-icon">🌐</div>
                        <h3>Frontend</h3>
                        <p>HTML5, CSS3, JavaScript, React, Vue.js. Creación de interfaces modernas y responsivas.</p>
                    </div>
                    <div class="skill-card fade-in">
                        <div class="skill-icon">⚙️</div>
                        <h3>Backend</h3>
                        <p>Node.js, Python, PHP. Desarrollo de APIs robustas y sistemas escalables.</p>
                    </div>
                    <div class="skill-card fade-in">
                        <div class="skill-icon">🎨</div>
                        <h3>Diseño</h3>
                        <p>UI/UX, Figma, Adobe Creative Suite. Diseño centrado en el usuario.</p>
                    </div>
                </div>
            </section>

            <section id="proyectos">
                <h2 class="section-title">Proyectos</h2>
                <div class="projects-grid">
                    <div class="project-card fade-in">
                        <div class="project-image">📱</div>
                        <div class="project-content">
                            <h3>App Móvil</h3>
                            <p>Aplicación móvil desarrollada con React Native para gestión de tareas con sincronización en tiempo real.</p>
                            <div class="project-links">
                                <a href="#" class="btn btn-primary">Ver Demo</a>
                                <a href="#" class="btn btn-secondary">Código</a>
                            </div>
                        </div>
                    </div>
                    <div class="project-card fade-in">
                        <div class="project-image">🛒</div>
                        <div class="project-content">
                            <h3>E-commerce</h3>
                            <p>Tienda online completa con carrito de compras, pagos seguros y panel de administración.</p>
                            <div class="project-links">
                                <a href="#" class="btn btn-primary">Ver Demo</a>
                                <a href="#" class="btn btn-secondary">Código</a>
                            </div>
                        </div>
                    </div>
                    <div class="project-card fade-in">
                        <div class="project-image">📊</div>
                        <div class="project-content">
                            <h3>Dashboard Analytics</h3>
                            <p>Panel de control con visualización de datos en tiempo real y generación de reportes.</p>
                            <div class="project-links">
                                <a href="#" class="btn btn-primary">Ver Demo</a>
                                <a href="#" class="btn btn-secondary">Código</a>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <section id="contacto">
                <h2 class="section-title">Contacto</h2>
                <div class="contact-content">
                    <p>¿Tienes un proyecto en mente? ¡Me encantaría escuchar de ti! No dudes en contactarme para discutir cómo podemos trabajar juntos.</p>
                    <div class="contact-info">
                        <div class="contact-item">
                            <div class="contact-icon">📧</div>
                            <a href="mailto:tu@email.com">tu@email.com</a>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">💼</div>
                            <a href="https://linkedin.com/in/tuperfil" target="_blank">LinkedIn</a>
                        </div>
                        <div class="contact-item">
                            <div class="contact-icon">🐙</div>
                            <a href="https://github.com/tuusuario" target="_blank">GitHub</a>
                        </div>
                    </div>
                </div>
            </section>
        </div>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2025 Tu Nombre. Todos los derechos reservados.</p>
        </div>
    </footer>

    <script>
        // Smooth scrolling for navigation links
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

        // Intersection Observer for fade-in animations
        const observerOptions = {
            threshold: 0.1,
            rootMargin: '0px 0px -50px 0px'
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        // Observe all fade-in elements
        document.querySelectorAll('.fade-in').forEach(el => {
            observer.observe(el);
        });

        // Add active state to navigation
        window.addEventListener('scroll', () => {
            const sections = document.querySelectorAll('section');
            const navLinks = document.querySelectorAll('.nav-links a');
            
            let current = '';
            sections.forEach(section => {
                const sectionTop = section.offsetTop;
                const sectionHeight = section.clientHeight;
                if (scrollY >= (sectionTop - 200)) {
                    current = section.getAttribute('id');
                }
            });

            navLinks.forEach(link => {
                link.classList.remove('active');
                if (link.getAttribute('href') === '#' + current) {
                    link.classList.add('active');
                }
            });
        });

        // Add parallax effect to header
        window.addEventListener('scroll', () => {
            const scrolled = window.pageYOffset;
            const parallax = document.querySelector('.header-bg');
            const speed = scrolled * 0.5;
            parallax.style.transform = `translateY(${speed}px)`;
        });
    </script>
</body>
</html>
