<!DOCTYPE html>
<html lang="tr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sana Bir Mesajım Var</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background: radial-gradient(circle, #fff5f5 0%, #fed7e2 100%);
            font-family: 'Times New Roman', Times, serif;
            color: #2d3436;
            overflow: hidden;
        }

        .container {
            text-align: center;
            padding: 50px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 30px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.1);
            max-width: 550px;
            position: relative;
            z-index: 2;
            border: 1px solid #fab1a0;
        }

        h1 {
            color: #d63031;
            font-style: italic;
            margin-bottom: 20px;
        }

        .text-content {
            font-size: 1.2rem;
            line-height: 1.8;
            margin-bottom: 40px;
            font-style: italic;
        }

        .heart-icon {
            font-size: 40px;
            color: #d63031;
            margin-bottom: 10px;
            display: block;
        }

        .buttons {
            display: flex;
            justify-content: center;
            gap: 30px;
            height: 60px;
            align-items: center;
        }

        button {
            padding: 15px 40px;
            font-size: 1.2rem;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            transition: all 0.2s ease;
            font-weight: bold;
        }

        #yesBtn {
            background-color: #d63031;
            color: white;
            box-shadow: 0 4px 15px rgba(214, 48, 49, 0.3);
        }

        #yesBtn:hover {
            transform: scale(1.1);
        }

        #noBtn {
            background-color: #636e72;
            color: white;
            position: relative;
        }

        #music-status {
            position: fixed;
            bottom: 10px;
            right: 10px;
            font-size: 0.8rem;
            color: #b2bec3;
        }

        .heart {
            position: fixed;
            bottom: -20px;
            font-size: 20px;
            animation: floatUp 6s linear infinite;
            opacity: 0.7;
        }

        @keyframes floatUp {
            0% {
                transform: translateY(0) scale(1);
                opacity: 0.7;
            }
            100% {
                transform: translateY(-110vh) scale(1.5);
                opacity: 0;
            }
        }
    </style>
</head>
<body onclick="playMusic()">

    <iframe id="youtubePlayer" width="0" height="0" src="https://www.youtube.com/embed/S6z70vH5iI8?enablejsapi=1" frameborder="0" allow="autoplay"></iframe>

    <div class="container">
        <span class="heart-icon">❦</span>
        <h1>Sana Bir Notum Var...</h1>
        
        <div class="text-content">
            "Seninle geçirdiğim her an, hayatımın en güzel hikayesine dönüşüyor. Bu hikayenin her sayfasını seninle el ele, aynı heyecanla yazmaya devam etmek istiyorum. Benim için çok özelsin. Bir süredir beraberiz ve ben senin yanındayken kendimi hiç olmadığım kadar mutlu hissediyorum. Hayatımı seninle paylaşmak, seninle bir (biz) olmak beni çok mutlu eder. "
            <br><br>
            <strong>Benimle sevgili olur musun?</strong> <br>
            Kalbimde senin için ayırdığım o en güzel yerde, sonsuza dek beraber olalım mı?
        </div>

        <div class="buttons">
            <button id="yesBtn" onclick="celebrate()">EVET!</button>
            <button id="noBtn" onmouseover="moveButton()" onclick="moveButton()">YOOOOOK</button>
        </div>
    </div>

    <div id="music-status">Sayfaya dokunarak müziği başlatabilirsin...</div>

    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.5.1/dist/confetti.browser.min.js"></script>
    <script>
        let musicStarted = false;

        function playMusic() {
            if (!musicStarted) {
                const player = document.getElementById('youtubePlayer');
                player.src = "https://www.youtube.com/embed/S6z70vH5iI8?autoplay=1&enablejsapi=1";
                musicStarted = true;
                document.getElementById('music-status').innerText = "🎵 Tanju Okan - Kadınım çalıyor...";
            }
        }

        function celebrate() {
            confetti({
                particleCount: 200,
                spread: 100,
                origin: { y: 0.6 }
            });
            
            document.querySelector('.text-content').innerHTML =
            "<h1>Seni Çok Seviyorum! ❤️</h1><p>Bu hikaye artık bizim… ve ben her sayfasını seninle yazmak istiyorum.</p>";
            document.querySelector('.buttons').style.display = 'none';
        }

        function moveButton() {
            const btn = document.getElementById('noBtn');
            const maxX = window.innerWidth - btn.offsetWidth;
            const maxY = window.innerHeight - btn.offsetHeight;
            
            const randomX = Math.random() * maxX;
            const randomY = Math.random() * maxY;
            
            btn.style.position = 'fixed';
            btn.style.left = randomX + 'px';
            btn.style.top = randomY + 'px';
        }

        function createHearts() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerText = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (4 + Math.random() * 3) + 's';
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 7000);
        }

        setInterval(createHearts, 500);
    </script>
</body>
</html>
