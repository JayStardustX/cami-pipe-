# cami-pipe-
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Cami & Pipe ❤️</title>
    <style>
        * { box-sizing: border-box; font-family: 'Segoe UI', sans-serif; }

        body {
            margin: 0;
            height: 100vh;
            overflow: hidden;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #ffffff;
            animation: bgChange 60s linear infinite;
        }

        @keyframes bgChange {
            0%   { background: radial-gradient(circle at top, #ffb6c1, #c2182b, #5c0a14); }
            25%  { background: radial-gradient(circle at top, #ffccd5, #d32f2f, #641220); }
            50%  { background: radial-gradient(circle at top, #ffd6e0, #c62828, #4a0f18); }
            75%  { background: radial-gradient(circle at top, #ffb3c6, #b71c1c, #3a0f1a); }
            100% { background: radial-gradient(circle at top, #ffb6c1, #c2182b, #5c0a14); }
        }

        .card {
            position: relative;
            background: rgba(255, 255, 255, 0.18);
            backdrop-filter: blur(14px);
            border-radius: 28px;
            padding: 42px 52px;
            text-align: center;
            box-shadow: 0 0 50px rgba(0,0,0,0.5);
            max-width: 480px;
            z-index: 10;
        }

        h1 {
            margin: 0;
            font-size: 2.3rem;
            color: #ffd1dc;
            text-shadow: 0 0 12px rgba(255, 90, 120, 0.9);
        }

        p { margin-top: 10px; font-size: 1.05rem; }

        .time {
            margin-top: 30px;
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 18px;
        }

        .box {
            background: rgba(0,0,0,0.28);
            padding: 18px;
            border-radius: 18px;
            box-shadow: inset 0 0 12px rgba(255, 100, 120, 0.45);
        }

        .number { font-size: 2.3rem; font-weight: bold; }
        .label { font-size: 0.95rem; color: #ffd1dc; }

        .footer {
            margin-top: 30px;
            font-size: 1.05rem;
            color: #ffe6eb;
        }

        /* Elementos flotantes */
        .heart, .flower, .trail {
            position: fixed;
            pointer-events: none;
            user-select: none;
            z-index: 1;
        }

        .heart {
            color: rgba(255, 90, 130, 0.9);
            font-size: 1.6rem;
            animation: floatUp 12s linear infinite;
        }

        @keyframes floatUp {
            from { transform: translateY(110vh) scale(0.8); }
            to { transform: translateY(-120vh) scale(1.3); }
        }

        .flower {
            font-size: 2.2rem;
            opacity: 0.18;
            animation: floatUpFlowers 26s linear infinite;
        }

        @keyframes floatUpFlowers {
            from { transform: translateY(120vh) rotate(0deg); }
            to { transform: translateY(-130vh) rotate(360deg); }
        }

        .trail {
            font-size: 1.2rem;
            color: rgba(255, 120, 150, 0.9);
            animation: fadeTrail 1.5s linear forwards;
        }

        @keyframes fadeTrail {
            from { opacity: 1; transform: scale(1); }
            to { opacity: 0; transform: scale(1.8); }
        }
    </style>
</head>
<body>

<div class="card">
    <h1>❤️ Cami & Pipe ❤️</h1>
    <p style="color:#ffd1dc">Nuestro tiempo juntos</p>
    <p>Desde el 22 de junio de 2025</p>

    <div class="time">
        <div class="box"><div class="number" id="days">0</div><div class="label">Días</div></div>
        <div class="box"><div class="number" id="hours">0</div><div class="label">Horas</div></div>
        <div class="box"><div class="number" id="minutes">0</div><div class="label">Minutos</div></div>
        <div class="box"><div class="number" id="seconds">0</div><div class="label">Segundos</div></div>
    </div>

    <div class="footer">Nuestro amor crece con cada latido 💖</div>
</div>

<script>
    const startDate = new Date(2025, 5, 22, 0, 0, 0);

    const daysEl = document.getElementById('days');
    const hoursEl = document.getElementById('hours');
    const minutesEl = document.getElementById('minutes');
    const secondsEl = document.getElementById('seconds');

    function updateCounter() {
        const now = new Date();
        let diff = Math.floor((now - startDate) / 1000);
        daysEl.textContent = Math.floor(diff / 86400);
        diff %= 86400;
        hoursEl.textContent = Math.floor(diff / 3600);
        diff %= 3600;
        minutesEl.textContent = Math.floor(diff / 60);
        secondsEl.textContent = diff % 60;
    }

    updateCounter();
    setInterval(updateCounter, 1000);

    function createHeart() {
        const h = document.createElement('div');
        h.className = 'heart';
        h.textContent = '❤';
        h.style.left = Math.random() * 100 + 'vw';
        h.style.animationDuration = (8 + Math.random() * 6) + 's';
        document.body.appendChild(h);
    }

    function createFlower() {
        const f = document.createElement('div');
        const flowers = ['🌹','🌸','🌺','💐','🌷'];
        f.className = 'flower';
        f.textContent = flowers[Math.floor(Math.random() * flowers.length)];
        f.style.left = Math.random() * 100 + 'vw';
        f.style.animationDuration = (18 + Math.random() * 10) + 's';
        document.body.appendChild(f);
    }

    setInterval(createHeart, 350);
    setInterval(createFlower, 900);

    document.addEventListener('mousemove', e => {
        const t = document.createElement('div');
        t.className = 'trail';
        t.textContent = '❤';
        t.style.left = e.clientX + 'px';
        t.style.top = e.clientY + 'px';
        document.body.appendChild(t);
        setTimeout(() => t.remove(), 1500);
    });
</script>

</body>
</html>
