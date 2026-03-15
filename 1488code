<!DOCTYPE html>
<html>
<head>
    <title>Mini Evade Clone</title>
    <style>
        body { margin: 0; overflow: hidden; background: #000; font-family: sans-serif; }
        #ui { position: absolute; top: 10px; left: 10px; color: white; }
    </style>
</head>
<body>
    <div id="ui">Беги! (Стрелки или WASD) <br> Скины: ВСЕ ОТКРЫТЫ</div>
    <canvas id="game"></canvas>

    <script>
        const canvas = document.getElementById('game');
        const ctx = canvas.getContext('2d');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let player = { x: 100, y: 100, size: 20, speed: 5 };
        let bot = { x: 500, y: 500, size: 40, speed: 3.5 };
        let keys = {};

        window.addEventListener('keydown', e => keys[e.key.toLowerCase()] = true);
        window.addEventListener('keyup', e => keys[e.key.toLowerCase()] = false);

        function update() {
            // Движение игрока
            if (keys['w'] || keys['arrowup']) player.y -= player.speed;
            if (keys['s'] || keys['arrowdown']) player.y += player.speed;
            if (keys['a'] || keys['arrowleft']) player.x -= player.speed;
            if (keys['d'] || keys['arrowright']) player.x += player.speed;

            // Бот бежит за игроком
            let dx = player.x - bot.x;
            let dy = player.y - bot.y;
            let dist = Math.sqrt(dx*dx + dy*dy);
            bot.x += (dx / dist) * bot.speed;
            bot.y += (dy / dist) * bot.speed;

            if (dist < player.size + bot.size/2) {
                alert("Поймали! Обнови страницу.");
                player.x = 100; player.y = 100;
            }
        }

        function draw() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            // Игрок
            ctx.fillStyle = '#0f0';
            ctx.fillRect(player.x, player.y, player.size, player.size);
            // Бот (Некстбот)
            ctx.fillStyle = '#f00';
            ctx.fillRect(bot.x, bot.y, bot.size, bot.size);
            requestAnimationFrame(() => { update(); draw(); });
        }
        draw();
    </script>
</body>
</html>
