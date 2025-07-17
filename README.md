<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Мой профиль - Матрица</title>
    <link href="https://fonts.googleapis.com/css2?family=Ubuntu+Mono:wght@400;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background-color: #000;
            color: #0f0;
            font-family: 'Ubuntu Mono', monospace;
            line-height: 1.6;
            overflow-x: hidden;
            position: relative;
        }

        #matrix-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.15;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
            position: relative;
            z-index: 10;
        }

        header {
            text-align: center;
            padding: 30px 0;
            border-bottom: 1px solid #0f0;
            margin-bottom: 30px;
            position: relative;
            overflow: hidden;
        }

        .header-content {
            position: relative;
            z-index: 2;
        }

        .glitch {
            font-size: 2.5rem;
            font-weight: 700;
            text-transform: uppercase;
            position: relative;
            text-shadow: 0 0 10px #0f0, 0 0 20px #0f0;
            animation: glitch-anim 5s infinite;
        }

        @keyframes glitch-anim {
            0% { transform: translate(0); }
            20% { transform: translate(-3px, 3px); }
            40% { transform: translate(-3px, -3px); }
            60% { transform: translate(3px, 3px); }
            80% { transform: translate(3px, -3px); }
            100% { transform: translate(0); }
        }

        .social-icons {
            margin: 20px 0;
            display: flex;
            justify-content: center;
            gap: 15px;
        }

        .social-icons a {
            display: inline-block;
            transition: all 0.3s ease;
            filter: drop-shadow(0 0 3px #0f0);
        }

        .social-icons a:hover {
            transform: translateY(-5px);
            filter: drop-shadow(0 0 10px #0f0);
        }

        .content {
            display: flex;
            flex-wrap: wrap;
            gap: 30px;
            margin-bottom: 40px;
        }

        .text-content {
            flex: 1;
            min-width: 300px;
        }

        .typing-effect {
            overflow: hidden;
            border-right: 0.15em solid #0f0;
            white-space: nowrap;
            margin: 0 0 20px 0;
            letter-spacing: 0.15em;
            animation: typing 3.5s steps(40, end), blink-caret 0.75s step-end infinite;
        }

        @keyframes typing {
            from { width: 0; }
            to { width: 100%; }
        }

        @keyframes blink-caret {
            from, to { border-color: transparent; }
            50% { border-color: #0f0; }
        }

        .image-content {
            flex: 1;
            min-width: 300px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        .matrix-image {
            max-width: 100%;
            height: auto;
            border: 2px solid #0f0;
            box-shadow: 0 0 15px #0f0;
            filter: grayscale(100%) brightness(120%) contrast(150%);
            transition: transform 0.3s ease;
        }

        .matrix-image:hover {
            transform: scale(1.03);
        }

        .languages {
            margin: 30px 0;
        }

        .languages-title {
            font-size: 1.5rem;
            margin-bottom: 15px;
            text-shadow: 0 0 5px #0f0;
        }

        .tech-icons {
            display: flex;
            flex-wrap: wrap;
            gap: 15px;
            margin-top: 10px;
        }

        .tech-icon {
            background: rgba(0, 255, 0, 0.1);
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #0f0;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .tech-icon:hover {
            background: rgba(0, 255, 0, 0.3);
            transform: translateY(-5px);
            box-shadow: 0 0 10px #0f0;
        }

        .tasks {
            margin: 30px 0;
            padding: 20px;
            border: 1px solid #0f0;
            box-shadow: 0 0 15px rgba(0, 255, 0, 0.2);
        }

        .tasks-title {
            font-size: 1.5rem;
            margin-bottom: 15px;
            text-shadow: 0 0 5px #0f0;
        }

        .task-list {
            list-style-type: none;
            padding-left: 20px;
        }

        .task-list li {
            margin-bottom: 10px;
            position: relative;
            padding-left: 30px;
        }

        .task-list li:before {
            content: ">";
            position: absolute;
            left: 0;
            color: #0f0;
            font-weight: bold;
        }

        .task-list li.completed:before {
            content: "✓";
            color: #0f0;
        }

        footer {
            text-align: center;
            padding: 20px;
            border-top: 1px solid #0f0;
            margin-top: 30px;
            font-size: 0.9rem;
            text-shadow: 0 0 3px #0f0;
        }

        .matrix-rain {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.2;
        }

        @media (max-width: 768px) {
            .content {
                flex-direction: column;
            }
            
            .typing-effect {
                white-space: normal;
                animation: none;
                border-right: none;
            }
        }
    </style>
</head>
<body>
    <canvas id="matrix-bg"></canvas>
    
    <div class="container">
        <header>
            <div class="header-content">
                <h1 class="glitch">Мой профиль в Матрице</h1>
                
                <div class="social-icons">
                    <a href="https://vk.com/your_profile" target="_blank">
                        <img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/vk.svg" alt="VKontakte" width="30">
                    </a>
                    <a href="https://twitter.com/your_profile" target="_blank">
                        <img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/twitter.svg" alt="Twitter" width="30">
                    </a>
                    <a href="https://www.linkedin.com/in/your_profile" target="_blank">
                        <img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/linkedin.svg" alt="LinkedIn" width="30">
                    </a>
                    <a href="https://t.me/your_profile" target="_blank">
                        <img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/telegram.svg" alt="Telegram" width="30">
                    </a>
                    <a href="https://www.instagram.com/your_profile" target="_blank">
                        <img src="https://cdn.jsdelivr.net/npm/simple-icons@v3/icons/instagram.svg" alt="Instagram" width="30">
                    </a>
                </div>
            </div>
        </header>
        
        <div class="content">
            <div class="text-content">
                <div class="typing-effect">
                    Привет-привет! <img src="https://media.giphy.com/media/hvRJCLFzcasrR4ia7z/giphy.gif" width="25px">
                </div>
                
                <p>Привет, меня зовут <span style="color:#ff0; text-shadow: 0 0 5px #ff0;">ВАШЕ ИМЯ</span>, я студент. Сейчас учусь на ИТ-специалиста. Изучаю Git и ещё несколько интересных технологий.</p>
                
                <div class="languages">
                    <h2 class="languages-title">Languages and Tools:</h2>
                    <div class="tech-icons">
                        <div class="tech-icon">
                            <img height="20" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/git/git.png">
                            <span>Git</span>
                        </div>
                        <div class="tech-icon">
                            <img height="20" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/python/python.png">
                            <span>Python</span>
                        </div>
                        <div class="tech-icon">
                            <img height="20" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/ruby/ruby.png">
                            <span>Ruby</span>
                        </div>
                        <div class="tech-icon">
                            <img height="20" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/javascript/javascript.png">
                            <span>JavaScript</span>
                        </div>
                        <div class="tech-icon">
                            <img height="20" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/vue/vue.png">
                            <span>Vue</span>
                        </div>
                        <div class="tech-icon">
                            <img height="20" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/react/react.png">
                            <span>React</span>
                        </div>
                        <div class="tech-icon">
                            <img height="20" src="https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/nodejs/nodejs.png">
                            <span>Node.js</span>
                        </div>
                    </div>
                </div>
                
                <div class="tasks">
                    <h2 class="tasks-title">🚧 Мои задачи на ближайшее время:</h2>
                    <ul class="task-list">
                        <li class="completed">Прокачать свой профиль на Github</li>
                        <li>Пройти курс по Git на Slurm</li>
                        <li>Создать свой первый проект на Github</li>
                    </ul>
                </div>
            </div>
            
            <div class="image-content">
                <img src="https://raw.githubusercontent.com/kalashnikov-ulmic/kalashnikov-ulmic/main/%D0%A3%D1%87%D1%83%D1%81%D1%8C%20%D0%BD%D0%B0%20Slurm.png?raw=true" 
                     alt="Учусь на Slurm" class="matrix-image">
            </div>
        </div>
        
        <footer>
            <p>01000111 01101001 01110100 00100000 01101001 01110011 00100000 01100001 01110111 01100101 01110011 01101111 01101101 01100101</p>
            <p>(Git is awesome)</p>
        </footer>
    </div>
    
    <script>
        // Matrix background effect
        const canvas = document.getElementById('matrix-bg');
        const ctx = canvas.getContext('2d');
        
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        
        const matrixChars = "アァカサタナハマヤャラワガザダバパイィキシチニヒミリヰギジヂビピウゥクスツヌフムユュルグズブヅプエェケセテネヘメレヱゲゼデベペオォコソトノホモヨョロヲゴゾドボポヴッン0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
        const chars = matrixChars.split('');
        
        const fontSize = 14;
        const columns = canvas.width / fontSize;
        
        const drops = [];
        for (let i = 0; i < columns; i++) {
            drops[i] = Math.floor(Math.random() * canvas.height / fontSize);
        }
        
        function drawMatrix() {
            ctx.fillStyle = 'rgba(0, 0, 0, 0.05)';
            ctx.fillRect(0, 0, canvas.width, canvas.height);
            
            ctx.fillStyle = '#0f0';
            ctx.font = `${fontSize}px monospace`;
            
            for (let i = 0; i < drops.length; i++) {
                const text = chars[Math.floor(Math.random() * chars.length)];
                const x = i * fontSize;
                const y = drops[i] * fontSize;
                
                ctx.fillText(text, x, y);
                
                if (y > canvas.height && Math.random() > 0.975) {
                    drops[i] = 0;
                }
                
                drops[i]++;
            }
        }
        
        setInterval(drawMatrix, 35);
        
        // Handle window resize
        window.addEventListener('resize', () => {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
        });
        
        // Glitch effect for completed tasks
        const completedTask = document.querySelector('.completed');
        setInterval(() => {
            if (Math.random() > 0.8) {
                completedTask.style.textShadow = '0 0 10px #ff0';
                setTimeout(() => {
                    completedTask.style.textShadow = 'none';
                }, 100);
            }
        }, 2000);
    </script>
</body>
</html>
