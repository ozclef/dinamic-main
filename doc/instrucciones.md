




 usar un `<main>` y dentro un `<div>` para mostrar contenido dinámico es justo lo que se hace en sitios profesionales — es limpio, semántico y te deja jugar con animaciones o actualizaciones sin recargar la página.

Vamos a hacerlo así: te dejo una base **HTML + JS puro**, que puedes conectar con tus repositorios o enlaces (por ejemplo, `github.io/portafolio`, `github.io/asesoria`, etc.).
Esto mostrará *noticias o actualizaciones recientes* dentro de un `<main>`, con animación y actualización dinámica cada vez que agregues un nuevo proyecto o enlace.

---

### 🧱 **HTML (index.html)**

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Panel de Actualizaciones</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h1>Actualizaciones Recientes</h1>
  </header>

  <main id="main-content">
    <div id="news-container" class="news-grid">
      <!-- Aquí se insertarán las noticias dinámicamente -->
    </div>
  </main>

  <footer>
    <p>© 2025 Agencia Os — Innovación y Ética</p>
  </footer>

  <script src="script.js"></script>
</body>
</html>
```

---

### 🎨 **CSS (styles.css)**

*(puedes agregarlo al final o como tú prefieres)*

```css
body {
  background: #0d1117;
  color: #c9d1d9;
  font-family: "Poppins", sans-serif;
  margin: 0;
  padding: 0;
}

header, footer {
  text-align: center;
  padding: 1rem;
  background: #161b22;
  color: #58a6ff;
}

main {
  padding: 2rem;
}

.news-grid {
  display: grid;
  gap: 1.5rem;
}

.news-card {
  background: #161b22;
  padding: 1.5rem;
  border-radius: 12px;
  box-shadow: 0 0 10px #0003;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.news-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 0 15px #58a6ff44;
}

.news-card a {
  color: #58a6ff;
  text-decoration: none;
}

.news-card a:hover {
  text-decoration: underline;
}
```

---

### ⚙️ **JS (script.js)**

Aquí es donde entra la magia dinámica.
El script toma tus enlaces o proyectos, y los “inyecta” al HTML, con fecha, animación y enlace activo.

```js
// Datos de tus proyectos o enlaces
const proyectos = [
  {
    titulo: "Portafolio Profesional",
    descripcion: "Presentación visual de mis proyectos, servicios y CV.",
    url: "https://tuusuario.github.io/portafolio",
    fecha: "2025-11-10"
  },
  {
    titulo: "Asesoría Legal y Ética Digital",
    descripcion: "Documentación y servicios de consultoría profesional.",
    url: "https://tuusuario.github.io/asesoria",
    fecha: "2025-11-08"
  },
  {
    titulo: "Tesis: Autoconciencia y Superación",
    descripcion: "Investigación sobre desarrollo personal, ética y tecnología.",
    url: "https://tuusuario.github.io/tesis",
    fecha: "2025-11-05"
  }
];

// Función para mostrar dinámicamente las noticias
function mostrarNoticias() {
  const contenedor = document.getElementById("news-container");
  contenedor.innerHTML = ""; // Limpia contenido previo

  proyectos.forEach((p) => {
    const card = document.createElement("div");
    card.className = "news-card";
    card.innerHTML = `
      <h2>${p.titulo}</h2>
      <p>${p.descripcion}</p>
      <small>📅 ${p.fecha}</small><br>
      <a href="${p.url}" target="_blank">Ver proyecto</a>
    `;
    contenedor.appendChild(card);
  });
}

// Llamar la función al cargar
document.addEventListener("DOMContentLoaded", mostrarNoticias);
```

---

### 💡 Cómo funciona

* Tu `<main>` mantiene la estructura principal.
* El `<div id="news-container">` recibe los bloques dinámicos.
* Solo editas el array `proyectos` en `script.js` y automáticamente se actualiza todo el contenido.
* Puedes hacer que se actualice desde una base de datos (Supabase o JSON remoto) después, sin tocar el HTML.

---

¿Quieres que le agregue también un efecto tipo *“fade-in”* o desplazamiento animado cuando aparezcan las tarjetas (para hacerlo más dinámico visualmente)?
Puedo incluirlo en CSS o con un poco de JS.
