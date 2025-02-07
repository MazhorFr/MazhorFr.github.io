<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Phaze - Enhanced Clone</title>
    <style>
        /* Global Styles */
        body {
            font-family: 'Arial', sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
            background-color: rgba(58, 27, 110, 0.9); /* Space Purple with 90% opacity */
            transition: background-color 0.3s, color 0.3s;
        }

        body.dark-mode {
            background-color: rgba(51, 51, 51, 0.9); /* Dark mode with 90% opacity */
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
        }

        a {
            color: rgba(0, 191, 255, 0.9); /* Slightly transparent bright blue for links */
            text-decoration: none;
        }

        a:hover {
            text-decoration: underline;
        }

        /* Header */
        header {
            background: rgba(46, 26, 71, 0.85); /* Midnight Purple with 85% opacity */
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
            padding: 20px 0;
            text-align: center;
            backdrop-filter: blur(5px); /* Adds a futuristic blur effect */
            position: relative; /* Ensure header is above raindrops */
            z-index: 2;
        }

        header h1 {
            margin: 0;
            font-size: 2.5rem;
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: center;
            background: rgba(51, 51, 51, 0.85); /* Semi-transparent dark background */
            padding: 10px 0;
            backdrop-filter: blur(5px); /* Adds a futuristic blur effect */
            position: relative; /* Ensure nav is above raindrops */
            z-index: 2;
        }

        nav a {
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
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
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
            text-align: center;
            backdrop-filter: blur(5px); /* Adds a futuristic blur effect */
            position: relative; /* Ensure hero is above raindrops */
            z-index: 2;
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
            position: relative; /* Ensure features are above raindrops */
            z-index: 2;
        }

        .feature-card {
            background: rgba(255, 255, 255, 0.1); /* Semi-transparent white */
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
            transition: transform 0.3s, box-shadow 0.3s;
            backdrop-filter: blur(5px); /* Adds a futuristic blur effect */
        }

        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
        }

        .feature-card h3 {
            margin-top: 0;
            font-size: 1.5rem;
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
        }

        .feature-card p {
            font-size: 1rem;
            color: rgba(255, 255, 255, 0.8); /* Slightly darker transparent white for contrast */
        }

        /* Footer */
        footer {
            background: rgba(51, 51, 51, 0.85); /* Semi-transparent dark background */
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
            text-align: center;
            padding: 20px 0;
            backdrop-filter: blur(5px); /* Adds a futuristic blur effect */
            position: relative; /* Ensure footer is above raindrops */
            z-index: 2;
        }

        footer p {
            margin: 0;
        }

        /* Dark Mode Toggle */
        .dark-mode-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(0, 123, 255, 0.85); /* Semi-transparent blue */
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            backdrop-filter: blur(5px); /* Adds a futuristic blur effect */
            z-index: 3; /* Ensure toggle is above raindrops */
        }

        .dark-mode-toggle:hover {
            background: rgba(0, 86, 179, 0.85); /* Semi-transparent darker blue */
        }

        /* Audio Toggle */
        .audio-toggle {
            position: fixed;
            bottom: 80px; /* Positioned above the dark mode toggle */
            right: 20px;
            background: rgba(0, 191, 255, 0.85); /* Semi-transparent blue */
            color: rgba(255, 255, 255, 0.9); /* Slightly transparent white for blending */
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1rem;
            backdrop-filter: blur(5px); /* Adds a futuristic blur effect */
            z-index: 3; /* Ensure toggle is above raindrops */
        }

        .audio-toggle:hover {
            background: rgba(0, 150, 255, 0.85); /* Semi-transparent darker blue */
        }

        /* Raindrop Styles */
        .raindrop {
            position: fixed; /* Use fixed positioning to avoid interfering with scrolling */
            top: -50px;
            width: 2px;
            height: 50px;
            background: linear-gradient(to bottom, rgba(0, 191, 255, 0.8), rgba(0, 191, 255, 0.2));
            animation: fall linear infinite;
            z-index: 1; /* Ensure raindrops are behind content */
        }

        @keyframes fall {
            to {
                transform: translateY(100vh);
            }
        }
    </style>
</head>
<body>
    <!-- Raindrops Container -->
    <div id="rain-container"></div>

    <!-- Audio Element -->
    <audio id="background-audio" loop>
        <source src="YOUR_DIRECT_MP3_LINK_HERE" type="audio/mpeg">
        Your browser does not support the audio element.
    </audio>

    <!-- Header -->
    <header>
        <h1>Phaze</h1>
    </header>

    <!-- Navigation -->
    <nav>
        <a href="#features">Features</a>
        <a href="#about">About</a>
        <a href="https://discord.gg/JjE92cXfvk">Contact</a>
    </nav>

    <!-- Hero Section -->
    <section class="hero">
        <h2>Welcome to Project Phaze</h2>
        <p>Phaze is a Discord bot that has many features, one of them including nuking DC servers. Phaze isn’t just a bot; it has services as well. To check it out, press the Contact button at the top.</p>
    </section>

    <!-- Features Section -->
    <section id="features" class="features">
        <div class="feature-card">
            <h3>Discord Bot</h3>
            <p>Phaze is the ultimate Discord bot that can be used as a nuke bot and a community bot. Our devs worked especially hard to make you guys a trolling and community bot. If you want your server to be protected from Phaze, click Contact Us above and make a ticket.</p>
        </div>
        <div class="feature-card">
            <h3>Services</h3>
            <p>Phaze isn’t just a Discord bot; it is part of Phaze Services. We offer many free and premium services such as AI jailbreaking, how to make multi-tools, keyloggers, and an amazing community for coders/scripters to enjoy.</p>
        </div>
        <div class="feature-card">
            <h3>About the Owners</h3>
            <p>Zyrx is the main developer and owner of Phaze Services, and he also runs Arlo Bot (another DC nuke bot server). Then there’s Mazhor, the community owner and multi-tool/keylogger creator. If you want the source code or for us to host a bot, click on Contact Us and make a buyer ticket.</p>
        </div>
    </section>

    <!-- Footer -->
    <footer>
        <p>&copy; 2023 Phaze. All rights reserved.</p>
    </footer>

    <!-- Dark Mode Toggle -->
    <button class="dark-mode-toggle" onclick="toggleDarkMode()">Toggle Dark Mode</button>

    <!-- Audio Toggle -->
    <button class="audio-toggle" onclick="toggleAudio()">Play Audio</button>

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

        // Raindrop Generator
        const rainContainer = document.getElementById('rain-container');

        function createRaindrop() {
            const raindrop = document.createElement('div');
            raindrop.classList.add('raindrop');
            raindrop.style.left = `${Math.random() * 100}vw`;
            raindrop.style.animationDuration = `${Math.random() * 0.5 + 0.5}s`;
            raindrop.style.opacity = Math.random();
            rainContainer.appendChild(raindrop);

            // Remove raindrop after it falls
            setTimeout(() => {
                raindrop.remove();
            }, 5000);
        }

        // Generate raindrops every 50ms
        setInterval(createRaindrop, 50);

        // Audio Toggle
        const audio = document.getElementById('background-audio');
        audio.volume = 0.5; // Set volume to 50%

        function toggleAudio() {
            if (audio.paused) {
                audio.play();
                document.querySelector('.audio-toggle').textContent = 'Pause Audio';
            } else {
                audio.pause();
                document.querySelector('.audio-toggle').textContent = 'Play Audio';
            }
        }
    </script>
</body>
</html>
