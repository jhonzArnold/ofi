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

        /* Encabezado Principal */
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 20px;
            background-color: #000; /* Fondo negro */
            color: white; /* Letras en blanco */
        }

        /* Estilos para el título y la imagen */
        .title-container {
            display: flex;
            align-items: center;
        }

        .title-container h1 {
            margin: 0;
        }

        .title-container img {
            width: 40px;
            height: auto;
            margin-left: 10px;
        }
    </style>
    <script>
        // Función de Login
        function login() {
            const id = document.getElementById("id").value;
            const password = document.getElementById("password").value;

            if (id === "jhon" && password === "frio123") {
                document.querySelector('.login-container').classList.add('hidden');
                document.querySelector('.main-container').classList.add('active');
            } else {
                alert("ID o contraseña incorrectos. Intenta de nuevo.");
            }
        }
    </script>
</head>
<body>
    <!-- Contenedor Principal de Título -->
    <div class="header">
        <div class="title-container">
            <h1>TrotamundoTv</h1>
            <img src="ruta/a/tu_imagen.jpg" alt="Logo"> <!-- Reemplaza la ruta con tu imagen -->
        </div>
        <div>
            <button onclick="showSection('home')">Inicio</button>
            <button onclick="showSection('channels')">TV Online</button>
            <button onclick="showSection('movies')">Películas</button>
        </div>
    </div>

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
        <!-- Aquí continúa el contenido de tu aplicación -->
    </div>
</body>
</html>