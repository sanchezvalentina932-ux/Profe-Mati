# Profe-Mati
connect_error) { die("
Conexión fallida: " . $conn->connect_error . "
"); } // Login if (isset($_POST['login'])) { $email = $_POST['email']; $password = $_POST['password']; if ($email === "admin@escuela.com" && $password === "123456") { $_SESSION['loggedin'] = true; header("Location: index.php?page=home"); exit; } else { $login_error = "Credenciales incorrectas. Por favor, inténtalo de nuevo."; } } // Logout if (isset($_POST['logout'])) { session_destroy(); header("Location: index.php"); exit; } // CRUD if (isset($_POST['agregar'])) { $documento = $conn->real_escape_string($_POST['documento']); $nombre = $conn->real_escape_string($_POST['nombre']); $edad = $conn->real_escape_string($_POST['edad']); $sql_insert = "INSERT INTO persona (documento, nombre, edad) VALUES ('$documento', '$nombre', '$edad')"; $conn->query($sql_insert); } if (isset($_POST['eliminar'])) { $id = $conn->real_escape_string($_POST['id']); $sql_delete = "DELETE FROM persona WHERE id = '$id'"; $conn->query($sql_delete); } if (isset($_POST['modificar'])) { $id = $conn->real_escape_string($_POST['id']); $documento = $conn->real_escape_string($_POST['documento']); $nombre = $conn->real_escape_string($_POST['nombre']); $edad = $conn->real_escape_string($_POST['edad']); $sql_update = "UPDATE persona SET documento='$documento', nombre='$nombre', edad='$edad' WHERE id='$id'"; $conn->query($sql_update); } // Cargar datos para modificar $estudiante_a_modificar = null; if (isset($_GET['edit'])) { $id = $conn->real_escape_string($_GET['edit']); $sql = "SELECT * FROM persona WHERE id = '$id'"; $resultado = $conn->query($sql); if ($resultado->num_rows > 0) { $estudiante_a_modificar = $resultado->fetch_assoc(); } } // Página actual $page = isset($_GET['page']) ? $_GET['page'] : 'login'; if (!isset($_SESSION['loggedin']) && $page !== 'login') { header("Location: index.php?page=login"); exit; } ?> <title>Sistema Educativo - Login</title> <style> /* Estilos login */ body { background: linear-gradient(135deg,rgb(255, 1, 1),rgb(0, 0, 0)); height: 100vh; display: flex; justify-content: center; align-items: center; } .login-container { background: white; padding: 2rem; border-radius: 10px; box-shadow: 0 15px 30px rgba(0, 0, 0, 0.1); max-width: 400px; width: 100%; text-align: center; } .login-container img { width: 80px; margin-bottom: 1rem; } h1 { margin-bottom: 1rem; } .input-group { margin-bottom: 1rem; text-align: left; } label { display: block; margin-bottom: 0.5rem; } input { width: 100%; padding: 0.75rem; border-radius: 5px; border: 1px solid #ccc; } button { width: 100%; padding: 0.75rem; border: none; border-radius: 5px; background: linear-gradient(to right,rgb(255, 21, 21),rgb(2, 5, 4)); color: white; font-weight: bold; } .error-message { color: red; margin-top: 1rem; } </style>
width: 300px;
    }
    .card a {
        display: inline-block;
        margin-top: 1rem;
        padding: 0.5rem 1rem;
        background: linear-gradient(to right,rgb(245, 3, 3),rgb(224, 62, 12));
        color: white;
        text-decoration: none;
        border-radius: 5px;
    }
    .logout-form {
        text-align: center;
        margin-top: 1rem;
    }
    .logout-form button {
        background:rgb(219, 0, 0);
        color: white;
        padding: 0.5rem 1rem;
        border: none;
        border-radius: 5px;
    }
</style>
width: 300px;
    }
    .card a {
        display: inline-block;
        margin-top: 1rem;
        padding: 0.5rem 1rem;
        background: linear-gradient(to right,rgb(245, 3, 3),rgb(224, 62, 12));
        color: white;
        text-decoration: none;
        border-radius: 5px;
    }
    .logout-form {
        text-align: center;
        margin-top: 1rem;
    }
    .logout-form button {
        background:rgb(219, 0, 0);
        color: white;
        padding: 0.5rem 1rem;
        border: none;
        border-radius: 5px;
    }
</style>
