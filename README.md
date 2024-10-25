<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TrotamundoTv</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f0f0f0;
            margin: 0;
        }

        /* Contenedor de Login con imagen de fondo */
        .login-container {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            min-height: 100vh;
            background-image: url('https://img.global.news.samsung.com/mx/wp-content/uploads/2022/08/MX_TV_Mockup_03-1.jpg');
            background-size: cover;
            background-position: center;
            background-repeat: no-repeat;
        }

        .login-container.hidden {
            display: none;
        }

        .login-box {
            text-align: center;
            background-color: rgba(0, 0, 0, 0.8); /* Fondo negro */
            padding: 20px 30px;
            border: 1px solid #ddd;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            max-width: 400px;
            width: 100%;
            color: white; /* Letras en blanco */
        }

        .login-box h2 {
            margin-bottom: 20px;
        }

        .login-box input {
            padding: 10px;
            margin: 10px 0;
            font-size: 16px;
            width: 100%;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .login-box button {
            padding: 10px 20px;
            background-color: #000; /* Fondo negro */
            color: white; /* Letras en blanco */
            border: none;
            cursor: pointer;
            font-size: 16px;
            width: 100%;
            border-radius: 4px;
        }

        .login-box button:hover {
            background-color: #333; /* Fondo gris oscuro al pasar el mouse */
        }

        /* Contenedor Principal */
        .main-container {
            display: none;
            padding: 20px;
            max-width: 1200px;
            margin: 0 auto;
            color: white; /* Letras en blanco */
        }

        .main-container.active {
            display: block;
        }

        /* Encabezado */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 20px;
            background-color: #000; /* Fondo negro */
            color: white; /* Letras en blanco */
        }

        .header h1 {
            margin: 0;
        }

        .header button {
            background-color: #000; /* Fondo negro */
            color: white; /* Letras en blanco */
            border: none;
            padding: 10px;
            cursor: pointer;
            font-size: 16px;
        }

        .header button:hover {
            background-color: rgba(255, 255, 255, 0.2); /* Fondo gris claro al pasar el mouse */
        }

        /* Carrusel de Imágenes */
        .carousel {
            position: relative;
            overflow: hidden;
            width: 100%;
            height: 50vh; /* Ocupa la mitad de la altura de la pantalla */
            margin: 0 auto;
        }

        .carousel img {
            width: 100%;
            height: 100%;
            object-fit: cover; /* Mantiene la proporción y cubre todo el contenedor */
            display: none; /* Oculto inicialmente */
        }

        .carousel img.active {
            display: block; /* Mostrar solo la imagen activa */
        }

        /* Sección de Información */
        .info-section {
            margin-top: 20px;
            background-color: rgba(0, 0, 0, 0.8); /* Fondo negro */
            padding: 15px;
            border-radius: 8px;
            position: relative; /* Para posicionar el ícono */
        }

        .info-section h3 {
            margin: 10px 0;
            font-weight: bold;
        }

        /* Ícono de WhatsApp */
        .whatsapp-icon {
            position: absolute;
            bottom: 10px; /* Ajustar para que esté en la parte inferior */
            right: 10px; /* Ajustar para que esté en la esquina derecha */
            width: 40px;
            height: 40px;
            background-color: #25D366; /* Color de fondo de WhatsApp */
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
        }

        .whatsapp-icon img {
            width: 60%; /* Ajustar el tamaño del ícono */
        }

        /* Grid de Canales y Películas */
        .grid-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
            gap: 20px;
        }

        .grid-item {
            background-color: #000; /* Fondo negro */
            padding: 10px;
            border: 1px solid #ddd;
            text-align: center;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            border-radius: 8px;
            color: white; /* Letras en blanco */
        }

        .grid-item img {
            width: 100%;
            height: auto;
            max-height: 100px;
            object-fit: cover;
            border-radius: 4px;
        }

        .grid-item h4 {
            margin: 10px 0 0 0;
            font-size: 14px;
        }

        .grid-item button {
            margin-top: 10px;
            padding: 8px 16px;
            background-color: #000; /* Fondo negro */
            color: white; /* Letras en blanco */
            border: none;
            cursor: pointer;
            font-size: 14px;
            border-radius: 4px;
            width: 100%;
        }

        .grid-item button:hover {
            background-color: #333; /* Fondo gris oscuro al pasar el mouse */
        }

        /* Contenedor del Reproductor de Video */
        #video-player-container {
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            width: 90vw;
            height: 50vh;
            background-color: #000; /* Fondo negro */
            border: 2px solid #007BFF;
            border-radius: 8px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.3);
            display: none;
            z-index: 1000;
        }

        #video-player-container.active {
            display: block;
        }

        #video-player {
            width: 100%;
            height: 100%;
            border: 0;
            border-radius: 8px;
        }

        .close-button, .show-channels-button {
            position: absolute;
            top: 10px;
            background-color: rgba(255, 0, 0, 0.7);
            border: none;
            color: white; /* Letras en blanco */
            padding: 8px 12px;
            cursor: pointer;
            border-radius: 50%;
            font-size: 16px;
            z-index: 1001;
        }

        .close-button {
            right: 10px;
        }

        .show-channels-button {
            right: 50px;
            background-color: rgba(0, 123, 255, 0.7);
        }

        .close-button:hover, .show-channels-button:hover {
            background-color: rgba(255, 0, 0, 0.9);
        }

        .show-channels-button:hover {
            background-color: rgba(0, 123, 255, 0.9);
        }

        /* Lista de Canales flotante dentro del reproductor */
        .channel-list {
            position: absolute;
            top: 10%;
            left: 10px;
            background-color: rgba(255, 255, 255, 0.9);
            border-radius: 8px;
            padding: 10px;
            z-index: 1002;
            display: none;
            width: 200px;
            max-height: 80%;
            overflow-y: auto;
        }

        .channel-list.active {
            display: block;
        }

        .channel-list button {
            display: block;
            margin-bottom: 10px;
            background-color: #000; /* Fondo negro */
            color: white; /* Letras en blanco */
            border: none;
            padding: 10px;
            cursor: pointer;
            width: 100%;
            border-radius: 4px;
        }

        .channel-list button:hover {
            background-color: #333; /* Fondo gris oscuro al pasar el mouse */
        }

        /* Media Queries para Responsividad */
        @media (min-width: 768px) {
            .grid-item img {
                max-height: 150px;
            }

            #video-player-container {
                width: 70vw;
                height: 60vh;
            }
        }

        @media (min-width: 1024px) {
            .grid-item img {
                max-height: 200px;
            }

            #video-player-container {
                width: 60vw;
                height: 70vh;
            }
        }
    </style>
    <script>
        let currentImageIndex = 0;
        let images = [];

        // Función de Login
        function login() {
            const id = document.getElementById("id").value;
            const password = document.getElementById("password").value;

            if (id === "jhon" && password === "frio123") {
                document.querySelector('.login-container').classList.add('hidden');
                document.querySelector('.main-container').classList.add('active');
                startCarousel(); // Iniciar el carrusel en el inicio
            } else {
                alert("ID o contraseña incorrectos. Intenta de nuevo.");
            }
        }

        // Función para iniciar el carrusel de imágenes
        function startCarousel() {
            images = document.querySelectorAll('.carousel img');
            images[currentImageIndex].classList.add('active');

            setInterval(() => {
                images[currentImageIndex].classList.remove('active');
                currentImageIndex = (currentImageIndex + 1) % images.length;
                images[currentImageIndex].classList.add('active');
            }, 7000); // Cambiar cada 7 segundos
        }

        // Funciones para mostrar secciones
        function showSection(section) {
            document.querySelector('.home-section').style.display = 'none';
            document.querySelector('.channels-section').style.display = 'none';
            document.querySelector('.movies-section').style.display = 'none';

            if (section === 'home') {
                document.querySelector('.home-section').style.display = 'block';
            } else if (section === 'channels') {
                document.querySelector('.channels-section').style.display = 'block';
            } else if (section === 'movies') {
                document.querySelector('.movies-section').style.display = 'block';
            }
        }

        // Función para Cargar Video
        function loadVideo(url) {
            var videoPlayerContainer = document.getElementById('video-player-container');
            var iframe = document.getElementById('video-player');

            // Establecer la URL del video
            iframe.src = url;

            // Mostrar el reproductor
            videoPlayerContainer.classList.add('active');

            // Entrar en fullscreen
            enterFullScreen(videoPlayerContainer);
        }

        // Función para Cerrar el Video
        function closeVideo() {
            var videoPlayerContainer = document.getElementById('video-player-container');
            var iframe = document.getElementById('video-player');

            // Ocultar el reproductor
            videoPlayerContainer.classList.remove('active');

            // Detener el video
            iframe.src = "";
        }

        // Función para Entrar en Fullscreen
        function enterFullScreen(element) {
            if (element.requestFullscreen) {
                element.requestFullscreen();
            } else if (element.mozRequestFullScreen) { // Firefox
                element.mozRequestFullScreen();
            } else if (element.webkitRequestFullscreen) { // Chrome, Safari, Opera
                element.webkitRequestFullscreen();
            } else if (element.msRequestFullscreen) { // IE/Edge
                element.msRequestFullscreen();
            }
        }

        // Función para mostrar la lista de canales en el reproductor
        function toggleChannelList() {
            var channelList = document.querySelector('.channel-list');
            channelList.classList.toggle('active');
        }
    </script>
</head>
<body>
    <!-- Formulario de Login -->
    <div class="login-container">
        <div class="login-box">
            <h2>Iniciar Sesión</h2>
            <input type="text" id="id" placeholder="ID de usuario">
            <input type="password" id="password" placeholder="Contraseña">
            <button onclick="login()">Ingresar</button>
        </div>
    </div>

    <!-- Contenedor Principal Después del Login -->
    <div class="main-container">
        <div class="header">
            <h1>TrotamundoTv</h1>
            <div>
                <button onclick="showSection('home')">Inicio</button>
                <button onclick="showSection('channels')">TV Online</button>
                <button onclick="showSection('movies')">Películas</button>
            </div>
        </div>

        <div class="content-container">
            <!-- Sección de Inicio con Carrusel -->
            <div class="home-section" style="display: block;">
                <div class="carousel">
                    <img src="hs.jpg" alt="Imagen 1" class="active">
                    <img src="lia.jfif" alt="Imagen 2">
                    <img src="canaa.jpg" alt="Imagen 3">
                </div>

                <!-- Sección de Información -->
                <div class="info-section">
                    <h3>También contamos con :</h3>
                    <p>
                        
                    
                        🌟 Cuentas de Streaming a Precios Bajos:
                        
                        📺 Disney+, Netflix, HBO, Crunchyroll, Star+, Paramount+, Prime Video, Vix .
                        Perfiles o cuentas desde 5 soles.

                        🛡️ Antivirus Originales - 12 Meses de Protección:
                        
                        🖥️ NOD32, McAfee, Total Security, Norton, AVG.
                        💻 Software Original:
                        
                        🖱️ Windows 10 Pro y Windows 11 Pro.
                        💡 Parches Alternativos para cualquier programa 
                        a precios especiales (estilo COVID) para cualquier programa.
                        
                        🔧 Repuestos para Computadoras y Laptops.
                    </p>
                    <div class="whatsapp-icon" onclick="window.open('https://wa.me/925519546', '_blank')">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/6/6b/WhatsApp.svg" alt="WhatsApp">
                    </div>
                </div>
            </div>

            <!-- Sección de Canales -->
            <div class="channels-section" style="display: none;">
                <h2>Canales</h2>
                <div class="grid-container">
                    <div class="grid-item">
                        <img src="aa.jfif" alt="America">
                        <h4>America</h4>
                        <button onclick="loadVideo('https://nebunexa.co/red/?get=https://embed.sdfgnksbounce.com/embed2/americatv.html')">Ver canal</button>
                    </div>
                    <div class="grid-item">
                        <img src="gol.jpg" alt="Gol Peru">
                        <h4>Gol Peru</h4>
                        <button onclick="loadVideo('https://gol12.com/vivo/canales.php?stream=golperu')">Ver canal</button>
                    </div>
                </div>
            </div>

            <!-- Sección de Películas -->
            <div class="movies-section" style="display: none;">
                <h3>Películas</h3>
                <div class="grid-container">
                    <div class="grid-item">
                        <img src="garf.jpg" alt="Garfield">
                        <h4>Garfield</h4>
                        <button onclick="loadVideo('https://nuuuppp.pro/watch/7kz7jIHYMkPnCGUQ5OVCQ3jz3s7kz70Y8cv7kz7kU4p45xzpNojXZmI?h=')">Ver película</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <!-- Reproductor de Video (Ventana Grande) -->
    <div id="video-player-container">
        <button class="close-button" onclick="closeVideo()">✖</button>
        <button class="show-channels-button" onclick="toggleChannelList()">📺</button>
        <iframe id="video-player" frameborder="0" allowfullscreen></iframe>

        <!-- Lista de Canales dentro del reproductor -->
        <div class="channel-list">
            <button onclick="loadVideo('https://gol12.com/vivo/canales.php?stream=golperu')">Gol Peru</button>
            <button onclick="loadVideo('https://nebunexa.co/red/?get=https://embed.sdfgnksbounce.com/embed2/americatv.html')">America</button>
        </div>
    </div>

    <!-- Agregar FontAwesome para los íconos -->
    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
</body>
</html>