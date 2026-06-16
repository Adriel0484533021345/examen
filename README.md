<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>RickFlix - Streaming Premium</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Netflix+Sans:wght@400;700&display=swap');

        :root {
            --netflix-red: #e50914;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Netflix Sans', Arial, sans-serif;
            background-color: #141414;
            color: #ffffff;
            overflow-x: hidden;
        }

        /* Header con animación en bucle */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 20px 40px;
            background: linear-gradient(to bottom, rgba(0,0,0,0.8), transparent);
            transition: background 0.4s;
        }

        .logo {
            font-size: 2.5rem;
            font-weight: 700;
            color: var(--netflix-red);
            text-shadow: 0 0 10px var(--netflix-red);
            animation: pulse 2s infinite;
            cursor: pointer;
        }

        @keyframes pulse {
            0%, 100% { transform: scale(1); }
            50% { transform: scale(1.05); }
        }

        nav ul {
            display: flex;
            list-style: none;
            gap: 25px;
        }

        nav a {
            color: #fff;
            text-decoration: none;
            font-size: 1.1rem;
            transition: color 0.3s;
        }

        nav a:hover {
            color: var(--netflix-red);
        }

        .profile {
            display: flex;
            align-items: center;
            gap: 15px;
            cursor: pointer;
        }

        /* Hero Section con video promocional */
        .hero {
            height: 100vh;
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .hero-video {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            z-index: -1;
        }

        .hero-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to right, rgba(20,20,20,0.8) 20%, transparent 60%, rgba(20,20,20,0.8));
            z-index: 1;
        }

        .hero-content {
            position: relative;
            z-index: 2;
            max-width: 600px;
            margin-left: 60px;
        }

        .hero-title {
            font-size: 4rem;
            margin-bottom: 20px;
            text-shadow: 0 4px 10px rgba(0,0,0,0.8);
        }

        .hero-description {
            font-size: 1.4rem;
            margin-bottom: 30px;
            line-height: 1.4;
        }

        .btn {
            padding: 12px 32px;
            font-size: 1.2rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            transition: all 0.3s;
            display: inline-flex;
            align-items: center;
            gap: 10px;
        }

        .btn-play {
            background: #fff;
            color: #000;
        }

        .btn-play:hover {
            background: #ccc;
        }

        .btn-info {
            background: rgba(255,255,255,0.3);
            color: #fff;
        }

        /* Sección de contenido */
        .content-section {
            padding: 60px 40px;
            position: relative;
            z-index: 2;
        }

        .section-title {
            font-size: 1.8rem;
            margin-bottom: 20px;
        }

        .row {
            display: flex;
            gap: 15px;
            overflow-x: auto;
            padding: 10px 0;
            scrollbar-width: none;
        }

        .row::-webkit-scrollbar {
            display: none;
        }

        .card {
            min-width: 220px;
            height: 130px;
            border-radius: 8px;
            overflow: hidden;
            position: relative;
            transition: transform 0.4s;
            cursor: pointer;
        }

        .card:hover {
            transform: scale(1.08);
        }

        .card img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }

        /* Modal de Login oculto */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.95);
            z-index: 2000;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: #141414;
            padding: 40px;
            border-radius: 8px;
            width: 400px;
            text-align: center;
            border: 2px solid var(--netflix-red);
        }

        .modal-content input {
            width: 100%;
            padding: 15px;
            margin: 15px 0;
            background: #333;
            border: none;
            color: #fff;
            border-radius: 4px;
        }

        /* Video Exclusivo */
        .exclusive-container {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: #000;
            z-index: 3000;
            flex-direction: column;
        }

        .exclusive-header {
            padding: 20px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        /* Footer */
        footer {
            padding: 40px;
            text-align: center;
            color: #777;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>
    <!-- Header con animación -->
    <header>
        <div class="logo" onclick="rickSecret()">RICKFLIX</div>
        <nav>
            <ul>
                <li><a href="#">Inicio</a></li>
                <li><a href="#" onclick="showLogin()">Series</a></li>
                <li><a href="#">Películas</a></li>
                <li><a href="#">Mi Lista</a></li>
            </ul>
        </nav>
        <div class="profile" onclick="showLogin()">
            <span>👤</span>
            <span>Usuario</span>
        </div>
    </header>

    <!-- Hero con video promocional (Rick Roll) -->
    <section class="hero">
        <iframe 
            class="hero-video"
            src="https://www.youtube.com/embed/dQw4w9WgXcQ?autoplay=1&mute=1&loop=1&playlist=dQw4w9WgXcQ&controls=0&modestbranding=1&rel=0"
            frameborder="0"
            allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
            allowfullscreen>
        </iframe>
        <div class="hero-overlay"></div>
        
        <div class="hero-content">
            <h1 class="hero-title">Never Gonna Give You Up</h1>
            <p class="hero-description">El clásico definitivo. Reproducción automática en bucle. ¿Te atreves a quedarte?</p>
            <button class="btn btn-play" onclick="alert('¡Ya estás viendo el mejor video promocional de todos los tiempos!')">▶ Reproducir</button>
            <button class="btn btn-info" onclick="showLogin()">Más Info</button>
        </div>
    </section>

    <!-- Contenido principal -->
    <section class="content-section">
        <h2 class="section-title">Tendencias en RickFlix</h2>
        <div class="row">
            <div class="card" onclick="showLogin()">
                <img src="https://picsum.photos/id/1015/300/170" alt="Rick 1">
            </div>
            <div class="card" onclick="showLogin()">
                <img src="https://picsum.photos/id/102/300/170" alt="Rick 2">
            </div>
            <div class="card" onclick="showLogin()">
                <img src="https://picsum.photos/id/106/300/170" alt="Rick 3">
            </div>
            <div class="card" onclick="showLogin()">
                <img src="https://picsum.photos/id/133/300/170" alt="Rick 4">
            </div>
        </div>
    </section>

    <section class="content-section">
        <h2 class="section-title">Exclusivos</h2>
        <div class="row">
            <div class="card" onclick="showLogin()">
                <img src="https://picsum.photos/id/201/300/170" alt="Exclusive">
                <div style="position:absolute; bottom:10px; left:10px; background:rgba(229,9,20,0.9); padding:2px 8px; border-radius:3px; font-size:0.8rem;">EXCLUSIVO</div>
            </div>
        </div>
    </section>

    <!-- Modal de Login oculto -->
    <div id="loginModal" class="modal">
        <div class="modal-content">
            <h2>Inicia Sesión para desbloquear Video Exclusivo</h2>
            <p>Usuario: <strong>rick</strong><br>Contraseña: <strong>astley</strong></p>
            <input type="text" id="username" placeholder="Usuario" value="">
            <input type="password" id="password" placeholder="Contraseña" value="">
            <button class="btn btn-play" onclick="login()" style="width:100%; margin-top:15px;">Ingresar</button>
            <button onclick="hideLogin()" style="margin-top:10px; background:none; border:none; color:#aaa;">Cerrar</button>
        </div>
    </div>

    <!-- Video Exclusivo -->
    <div id="exclusiveVideo" class="exclusive-container">
        <div class="exclusive-header">
            <div class="logo">RICKFLIX EXCLUSIVO</div>
            <button onclick="closeExclusive()" style="background:var(--netflix-red); color:white; border:none; padding:10px 20px; border-radius:4px; cursor:pointer;">Cerrar</button>
        </div>
        <div style="flex:1; display:flex; align-items:center; justify-content:center; background:#000;">
            <iframe 
                id="exclusiveIframe"
                width="1280" 
                height="720"
                src="https://www.youtube.com/embed/yPYZpwSpKmA?autoplay=1"
                frameborder="0"
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture"
                allowfullscreen>
            </iframe>
        </div>
    </div>

    <footer>
        <p>© 2026 RickFlix - Nunca te vamos a dar plantón</p>
        <p>Plataforma de streaming 100% real (no es broma... o sí)</p>
    </footer>

    <script>
        // Mostrar modal de login
        function showLogin() {
            document.getElementById('loginModal').style.display = 'flex';
        }

        function hideLogin() {
            document.getElementById('loginModal').style.display = 'none';
        }

        // Login secreto
        function login() {
            const user = document.getElementById('username').value.toLowerCase().trim();
            const pass = document.getElementById('password').value.toLowerCase().trim();
            
            if (user === 'rick' && pass === 'astley') {
                hideLogin();
                // Desbloquear video exclusivo
                document.getElementById('exclusiveVideo').style.display = 'flex';
                // Autoplay ya está configurado en el iframe
            } else {
                alert("Credenciales incorrectas. Pista: Piensa en el cantante de la promo 😉");
            }
        }

        // Easter egg en el logo
        function rickSecret() {
            alert("¡Bienvenido a RickFlix! Nunca te vamos a dar up... o sí.");
        }

        function closeExclusive() {
            const container = document.getElementById('exclusiveVideo');
            container.style.display = 'none';
            // Reset iframe para detener reproducción
            const iframe = document.getElementById('exclusiveIframe');
            const src = iframe.src;
            iframe.src = src;
        }

        // Cerrar modal con Escape
        document.addEventListener('keydown', function(e) {
            if (e.key === "Escape") {
                const modal = document.getElementById('loginModal');
                if (modal.style.display === 'flex') hideLogin();
                
                const exclusive = document.getElementById('exclusiveVideo');
                if (exclusive.style.display === 'flex') closeExclusive();
            }
        });

        // Auto-pausa del video hero cuando se hace scroll (opcional)
        window.addEventListener('scroll', () => {
            if (window.scrollY > 300) {
                // El iframe hero se mantiene reproduciéndose
            }
        });

        console.log("%cRickFlix cargado correctamente. ¡Disfruta del clásico!", "color:#e50914; font-size:16px;");
    </script>
</body>
</html>
