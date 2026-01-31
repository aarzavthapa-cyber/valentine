# valentine
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Will you be my Valentine? 💕</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Dancing+Script:wght@400;600;700&family=Quicksand:wght@400;500;600&display=swap" rel="stylesheet">
    <style>
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        :root {
            --pink: #ff6b9d;
            --pink-light: #ffb3c6;
            --pink-dark: #e91e63;
            --rose: #ff85a2;
            --cream: #fff5f7;
            --gold: #ffd700;
        }

        body {
            font-family: 'Quicksand', sans-serif;
            min-height: 100vh;
            background: linear-gradient(135deg, #1a0a0e 0%, #2d1b2e 30%, #1a0a0e 100%);
            color: #fff;
            overflow-x: hidden;
            cursor: default;
        }

        /* Floating hearts background */
        .hearts-bg {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
            z-index: 0;
            overflow: hidden;
        }

        .heart-float {
            position: absolute;
            font-size: 1.5rem;
            opacity: 0.15;
            animation: float-up 8s ease-in-out infinite;
        }

        .heart-float:nth-child(1) { left: 10%; animation-delay: 0s; }
        .heart-float:nth-child(2) { left: 25%; animation-delay: 1.5s; }
        .heart-float:nth-child(3) { left: 40%; animation-delay: 3s; }
        .heart-float:nth-child(4) { left: 60%; animation-delay: 2s; }
        .heart-float:nth-child(5) { left: 75%; animation-delay: 4s; }
        .heart-float:nth-child(6) { left: 90%; animation-delay: 1s; }
        .heart-float:nth-child(7) { left: 15%; animation-delay: 5s; }
        .heart-float:nth-child(8) { left: 50%; animation-delay: 2.5s; }
        .heart-float:nth-child(9) { left: 85%; animation-delay: 3.5s; }

        @keyframes float-up {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 0; }
            10% { opacity: 0.2; }
            90% { opacity: 0.15; }
            100% { transform: translateY(-100px) rotate(360deg); opacity: 0; }
        }

        .container {
            position: relative;
            z-index: 1;
            max-width: 600px;
            margin: 0 auto;
            padding: 2rem;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            text-align: center;
        }

        .screen {
            display: none;
            animation: fadeIn 0.6s ease;
        }

        .screen.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        h1 {
            font-family: 'Dancing Script', cursive;
            font-size: clamp(2rem, 6vw, 3.5rem);
            color: var(--pink-light);
            margin-bottom: 1rem;
            text-shadow: 0 0 20px rgba(255, 107, 157, 0.5);
        }

        .message-box {
            background: rgba(255, 255, 255, 0.08);
            border: 2px solid rgba(255, 107, 157, 0.4);
            border-radius: 20px;
            padding: 1.5rem 2rem;
            margin: 1rem 0;
            backdrop-filter: blur(10px);
            line-height: 1.8;
            font-size: 1.1rem;
        }

        .message-box.highlight {
            border-color: var(--pink);
            box-shadow: 0 0 30px rgba(255, 107, 157, 0.3);
        }

        .btn {
            font-family: 'Quicksand', sans-serif;
            font-weight: 600;
            font-size: 1.1rem;
            padding: 0.9rem 2rem;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
            margin: 0.5rem;
        }

        .btn:hover {
            transform: scale(1.05);
            box-shadow: 0 6px 25px rgba(255, 107, 157, 0.5);
        }

        .btn-primary {
            background: linear-gradient(135deg, var(--pink), var(--pink-dark));
            color: white;
        }

        .btn-secondary {
            background: rgba(255, 255, 255, 0.15);
            color: var(--pink-light);
            border: 2px solid var(--pink);
        }

        .btn-yes {
            font-size: 1.3rem;
            padding: 1rem 2.5rem;
            background: linear-gradient(135deg, #4ade80, #22c55e);
            color: white;
            animation: pulse 1.5s ease-in-out infinite;
        }

        .btn-no {
            position: relative;
            transition: left 0.3s, top 0.3s;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        .hearts-row {
            margin: 1.5rem 0;
            font-size: 2rem;
            letter-spacing: 0.5rem;
        }

        .final-screen .hearts-row {
            font-size: 3rem;
            animation: heartBeat 0.8s ease infinite;
        }

        @keyframes heartBeat {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.1); }
        }

        .confetti {
            position: fixed;
            width: 10px;
            height: 10px;
            pointer-events: none;
            z-index: 100;
        }

        .tap-hint {
            font-size: 0.9rem;
            color: rgba(255, 255, 255, 0.6);
            margin-top: 1.5rem;
        }

        .emoji {
            display: inline-block;
            animation: bounce 1s ease infinite;
        }

        @keyframes bounce {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-5px); }
        }
    </style>
</head>
<body>
    <div class="hearts-bg" aria-hidden="true">
        <span class="heart-float">💕</span>
        <span class="heart-float">💗</span>
        <span class="heart-float">💖</span>
        <span class="heart-float">💕</span>
        <span class="heart-float">💗</span>
        <span class="heart-float">💖</span>
        <span class="heart-float">💕</span>
        <span class="heart-float">💗</span>
        <span class="heart-float">💖</span>
    </div>

    <div class="container">
        <!-- Screen 1: Welcome -->
        <div class="screen active" id="screen1">
            <h1>Hey, you 💕</h1>
            <div class="message-box">
                I made something special for you. Ready for a little surprise?
            </div>
            <button class="btn btn-primary" onclick="showScreen(2)">I'm ready!</button>
            <p class="tap-hint">Tap the button to continue</p>
        </div>

        <!-- Screen 2 -->
        <div class="screen" id="screen2">
            <h1>You mean the world to me</h1>
            <div class="message-box">
                Every day with you feels like a gift. Your smile, your laugh, the way you care — you make everything better.
            </div>
            <button class="btn btn-primary" onclick="showScreen(3)">Next 💗</button>
        </div>

        <!-- Screen 3 -->
        <div class="screen" id="screen3">
            <h1>You're my favorite person</h1>
            <div class="message-box">
                I love our talks, our silly moments, and every second we spend together. You're not just my girlfriend — you're my best friend and my home.
            </div>
            <button class="btn btn-primary" onclick="showScreen(4)">Next 💖</button>
        </div>

        <!-- Screen 4 -->
        <div class="screen" id="screen4">
            <h1>You deserve all the love</h1>
            <div class="message-box">
                You're kind, you're strong, and you're beautiful inside and out. I'm so lucky to have you in my life.
            </div>
            <button class="btn btn-primary" onclick="showScreen(5)">Next 💕</button>
        </div>

        <!-- Screen 5 -->
        <div class="screen" id="screen5">
            <h1>One more thing...</h1>
            <div class="message-box">
                I could write a thousand messages, but there's one question I really want to ask you.
            </div>
            <button class="btn btn-primary" onclick="showScreen(6)">What is it? 💗</button>
        </div>

        <!-- Screen 6: THE QUESTION -->
        <div class="screen" id="screen6">
            <div class="hearts-row">💕 💗 💖 💕 💗</div>
            <h1>Will you be my Valentine?</h1>
            <div class="message-box highlight">
                I'd be the happiest person in the world if you said yes. 💖
            </div>
            <div style="margin-top: 1.5rem;">
                <button class="btn btn-yes" id="btnYes" onclick="sayYes()">Yes! 💕</button>
                <button class="btn btn-secondary btn-no" id="btnNo" onmouseover="runAway()">Maybe later</button>
            </div>
        </div>

        <!-- Screen 7: SHE SAID YES! -->
        <div class="screen final-screen" id="screen7">
            <div class="hearts-row">💕 💗 💖 💕 💗 💖 💕</div>
            <h1>You said yes!</h1>
            <div class="message-box highlight">
                Best. Day. Ever. I can't wait to celebrate Valentine's with you. You're the best thing that's ever happened to me. I love you so much! 💕
            </div>
            <p class="tap-hint">Thank you for being mine 💗</p>
        </div>
    </div>

    <script>
        function showScreen(num) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById('screen' + num).classList.add('active');
        }

        function runAway() {
            const btn = document.getElementById('btnNo');
            const maxX = window.innerWidth - 120;
            const maxY = window.innerHeight - 50;
            btn.style.position = 'fixed';
            btn.style.left = Math.random() * (maxX - 50) + 'px';
            btn.style.top = Math.random() * (maxY - 30) + 'px';
        }

        function sayYes() {
            showScreen(7);
            createConfetti();
        }

        function createConfetti() {
            const colors = ['#ff6b9d', '#ffb3c6', '#ffd700', '#ff85a2', '#e91e63'];
            for (let i = 0; i < 80; i++) {
                setTimeout(() => {
                    const confetti = document.createElement('div');
                    confetti.className = 'confetti';
                    confetti.style.left = Math.random() * 100 + 'vw';
                    confetti.style.top = '-10px';
                    confetti.style.backgroundColor = colors[Math.floor(Math.random() * colors.length)];
                    confetti.style.borderRadius = Math.random() > 0.5 ? '50%' : '0';
                    confetti.style.width = (6 + Math.random() * 8) + 'px';
                    confetti.style.height = confetti.style.width;
                    document.body.appendChild(confetti);

                    const duration = 3000 + Math.random() * 2000;
                    confetti.animate([
                        { transform: 'translateY(0) rotate(0deg)', opacity: 1 },
                        { transform: `translateY(100vh) rotate(${720 + Math.random() * 360}deg)`, opacity: 0 }
                    ], { duration, easing: 'cubic-bezier(0.25, 0.46, 0.45, 0.94)' })
                        .finished.then(() => confetti.remove());
                }, i * 30);
            }
        }
    </script>
</body>
</html>
