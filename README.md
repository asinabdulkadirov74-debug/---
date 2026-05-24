<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Для Сабилы ❤️</title>
    <!-- Подключаем красивый романтичный шрифт -->
    <link href="https://googleapis.com" rel="stylesheet">
    <style>
        body {
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #ff758c 0%, #ff7eb3 100%);
            height: 100vh;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            overflow: hidden;
            font-family: 'Pacifico', cursive; /* Применяем новый шрифт */
        }

        /* Контейнер для текста */
        .text-container {
            text-align: center;
            z-index: 10;
            margin-bottom: 30px;
            animation: pulse 2s infinite ease-in-out;
            user-select: none;
        }

        h1 {
            color: white;
            font-size: 5.5rem;
            text-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
            margin: 0;
        }

        /* Стиль для первой фразы */
        .love-text {
            color: #fff0f2;
            font-size: 2.2rem;
            text-shadow: 0 5px 10px rgba(0, 0, 0, 0.15);
            margin-top: 10px;
        }

        /* Стиль для секретного ответа, который появится позже */
        .secret-answer {
            color: #ffffd0; /* Нежно-желтый оттенок, чтобы выделить ответ */
            font-size: 2.5rem;
            text-shadow: 0 5px 15px rgba(255, 75, 92, 0.4);
            margin-top: 15px;
            opacity: 0;
            transform: scale(0.8);
            transition: all 1s ease; /* Плавное появление */
            display: none; /* Изначально скрыт */
        }

        /* Класс, который включит анимацию появления */
        .secret-answer.show {
            display: block;
            opacity: 1;
            transform: scale(1);
        }

        /* Стильная кнопка для удивления */
        .magic-btn {
            background-color: white;
            color: #ff4b5c;
            border: none;
            padding: 15px 35px;
            font-size: 1.5rem;
            font-family: 'Pacifico', cursive;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 25px rgba(0,0,0,0.15);
            transition: all 0.3s ease;
            z-index: 10;
        }

        .magic-btn:hover {
            transform: scale(1.1);
            box-shadow: 0 15px 30px rgba(0,0,0,0.25);
            background-color: #fff0f2;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.03); }
            100% { transform: scale(1); }
        }

        /* Стили для летающих сердечек */
        .heart {
            position: absolute;
            opacity: 0.8;
            animation: fall linear forwards;
            user-select: none;
            pointer-events: none;
        }

        @keyframes fall {
            0% {
                transform: translateY(-10vh) translateX(0) rotate(0deg);
                opacity: 1;
            }
            100% {
                transform: translateY(110vh) translateX(var(--spread)) rotate(360deg);
                opacity: 0;
            }
        }

        /* Анимация взрыва сердечек */
        .burst-heart {
            position: absolute;
            user-select: none;
            pointer-events: none;
            animation: burst 1.5s cubic-bezier(0.1, 0.8, 0.3, 1) forwards;
        }

        @keyframes burst {
            0% {
                transform: translate(0, 0) scale(1);
                opacity: 1;
            }
            100% {
                transform: translate(var(--mx), var(--my)) scale(0.5);
                opacity: 0;
            }
        }
    </style>
</head>
<body>

    <div class="text-container">
        <h1>Сабила</h1>
        <div class="love-text">вайш ар мац дол ?</div>
        <!-- Секретный текст ответа -->
        <div id="answer" class="secret-answer">тахан дол</div>
    </div>

    <button id="main-btn" class="magic-btn" onclick="supriseEffect()">Нажми меня ✨</button>

    <!-- Фоновая музыка -->
    <audio id="bg-music" src="https://soundhelix.com" loop></audio>

    <script>
        const heartTypes = ['❤️', '💖', '💝', '💕', '💗', '⭐'];

        // 1. Постоянный дождь из сердечек
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerText = heartTypes[Math.floor(Math.random() * heartTypes.length)];
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.fontSize = Math.random() * 20 + 20 + 'px';
            heart.style.animationDuration = Math.random() * 3 + 4 + 's';
            heart.style.setProperty('--spread', (Math.random() * 200 - 100) + 'px');
            
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 7000);
        }
        setInterval(createHeart, 200);

        // 2. Функция Сюрприза при нажатии на кнопку
        function supriseEffect() {
            // Включаем музыку
            const music = document.getElementById('bg-music');
            music.play().catch(e => console.log("Музыка ждет разрешения"));

            // Показываем секретный текст ответа
            const answerText = document.getElementById('answer');
            answerText.classList.add('show');

            // Скрываем кнопку после нажатия, чтобы она не мешала тексту
            document.getElementById('main-btn').style.display = 'none';

            // Создаем мощный взрыв из 70 сердечек
            for (let i = 0; i < 70; i++) {
                const bHeart = document.createElement('div');
                bHeart.classList.add('burst-heart');
                bHeart.innerText = heartTypes[Math.floor(Math.random() * heartTypes.length)];
                bHeart.style.fontSize = Math.random() * 25 + 20 + 'px';
                
                bHeart.style.left = '50vw';
                bHeart.style.top = '55vh';

                const angle = Math.random() * Math.PI * 2;
                const distance = Math.random() * 350 + 100;
                const mx = Math.cos(angle) * distance + 'px';
                const my = Math.sin(angle) * distance + 'px';
                
                bHeart.style.setProperty('--mx', mx);
                bHeart.style.setProperty('--my', my);

                document.body.appendChild(bHeart);
                setTimeout(() => bHeart.remove(), 1500);
            }
        }

        // 3. Сердечки за курсором мыши / пальцем
        window.addEventListener('mousemove', (e) => {
            if(Math.random() > 0.85) {
                const trailHeart = document.createElement('div');
                trailHeart.classList.add('burst-heart');
                trailHeart.innerText = '💖';
                trailHeart.style.left = e.clientX + 'px';
                trailHeart.style.top = e.clientY + 'px';
                trailHeart.style.setProperty('--mx', (Math.random() * 40 - 20) + 'px');
                trailHeart.style.setProperty('--my', (Math.random() * 40 - 20) + 'px');
                document.body.appendChild(trailHeart);
                setTimeout(() => trailHeart.remove(), 1000);
            }
        });
    </script>
</body>
</html>
