<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arlo - Enhanced Clone</title>
    <style>
        /* Global Styles */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
            color: #333;
            background-color: #f4f4f4;
            transition: background-color 0.3s, color 0.3s;
        }

        body.dark-mode {
            background-color: #333;
            color: #f4f4f4;
        }

        a {
            color: #007BFF;
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline;
        }

        /* Header */
        header {
            background: #007BFF;
            color: #fff;
            padding: 20px 0;
            text-align: center;
        }

        header h1 {
            margin: 0;
            font-size: 2.5rem;
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: center;
            background: #333;
            padding: 10px 0;
        }

        nav a {
            color: #fff;
            margin: 0 15px;
            font-size: 1.1rem;
        }

        /* Hero Section */
        .hero {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 60vh;
            background: url('https://via.placeholder.com/1920x1080') no-repeat center center/cover;
            color: #fff;
            text-align: center;
        }

        .hero h2 {
            font-size: 2.5rem;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 1.2rem;
            max-width: 600px;
        }

        /* Features Section */
        .features {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            padding: 40px 20px;
        }

        .feature-card {
            background: #fff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        .feature-card h3 {
            margin-top: 0;
            font-size: 1.5rem;
        }

        .feature-card p {
            font-size: 1rem;
        }

        /* Footer */
        footer {
            background: #333;
            color: #fff;
            text-align: center;
            padding: 20px 0;
        }

        footer p {
            margin: 0;
        }

        /* Dark Mode Toggle */
        .dark-mode-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #007BFF;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
        }

        .dark-mode-toggle:hover {
            background: #0056b3;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <h1>Arlo</h1>
    </header>

    <!-- Navigation -->
    <nav>
        <a href="#features">Features</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <h2>Welcome to Arlo</h2>
        <p>Your ultimate solution for modern web development. Built with precision, designed for performance.</p>
    </section>

    <!-- Features Section -->
    <section id="features" class="features">
        <div class="feature-card">
            <h3>Feature One</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam scelerisque leo a libero tincidunt.</p>
        </div>
        <div class="feature-card">
            <h3>Feature Two</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam scelerisque leo a libero tincidunt.</p>
        </div>
        <div class="feature-card">
            <h3>Feature Three</h3>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nullam scelerisque leo a libero tincidunt.</p>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2023 Arlo. All rights reserved.</p>
    </footer>

    <!-- Dark Mode Toggle -->
    <button class="dark-mode-toggle" onclick="toggleDarkMode()">Toggle Dark Mode</button>

    <script>
        // Dark Mode Toggle
        function toggleDarkMode() {
            document.body.classList.toggle('dark-mode');
        }

        // Smooth Scrolling
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>
