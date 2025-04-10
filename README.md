# Cómo construir la tarjeta

- Acceder a [https://codepen.io](https://codepen.io)
- Crear una cuenta y un primer proyecto.
- Trabajaremos sobre el HTML, CSS y JavaScript

# Nuestro código

**HTML**

```html
<div class="card" id="profile-card">
  <div class="card-header">
    <div class="profile-img">
      <img src="https://images.unsplash.com/photo-1494790108377-be9c29b29330?w=250" alt="Foto de perfil">
    </div>
    <div class="theme-toggle">
      <button id="theme-button">🌙</button>
    </div>
  </div>
  
  <div class="card-body">
    <h2 class="name">Ana García</h2>
    <p class="title">Desarrolladora Web</p>
    <p class="bio">Apasionada por crear experiencias web increíbles. Me encanta el diseño y la programación.</p>
  </div>
  
  <div class="card-footer">
    <div class="social-links">
      <a href="#" class="social-link">📱</a>
      <a href="#" class="social-link">📧</a>
      <a href="#" class="social-link">🔗</a>
    </div>
    <button class="contact-btn" id="contact-button">Contactar</button>
  </div>
</div>

<div id="message" class="message hidden">¡Gracias por tu interés! Te contactaré pronto.</div>
```

**CSS**

```css
:root {
  --primary-color: #3498db;
  --secondary-color: #2980b9;
  --text-color: #333;
  --bg-color: #f9f9f9;
  --card-bg: white;
  --shadow-color: rgba(0, 0, 0, 0.1);
}

.dark-theme {
  --primary-color: #3498db;
  --secondary-color: #2980b9;
  --text-color: #f9f9f9;
  --bg-color: #333;
  --card-bg: #444;
  --shadow-color: rgba(0, 0, 0, 0.3);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background-color: var(--bg-color);
  transition: background-color 0.3s ease;
}

.card {
  width: 300px;
  border-radius: 15px;
  overflow: hidden;
  box-shadow: 0 10px 20px var(--shadow-color);
  background-color: var(--card-bg);
  transition: all 0.3s ease;
}

.card:hover {
  transform: translateY(-10px);
  box-shadow: 0 15px 30px var(--shadow-color);
}

.card-header {
  position: relative;
  padding: 25px;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  display: flex;
  justify-content: center;
}

.profile-img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  overflow: hidden;
  border: 3px solid white;
}

.profile-img img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.theme-toggle {
  position: absolute;
  top: 15px;
  right: 15px;
}

#theme-button {
  background: none;
  border: none;
  font-size: 20px;
  cursor: pointer;
  color: white;
}

.card-body {
  padding: 20px;
  text-align: center;
  color: var(--text-color);
}

.name {
  font-size: 22px;
  margin-bottom: 5px;
}

.title {
  color: var(--primary-color);
  font-weight: bold;
  margin-bottom: 15px;
}

.bio {
  font-size: 14px;
  line-height: 1.5;
}

.card-footer {
  padding: 15px 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border-top: 1px solid rgba(0, 0, 0, 0.1);
}

.social-links {
  display: flex;
  gap: 15px;
  margin-bottom: 15px;
}

.social-link {
  text-decoration: none;
  font-size: 20px;
  transition: transform 0.2s ease;
}

.social-link:hover {
  transform: scale(1.2);
}

.contact-btn {
  width: 100%;
  padding: 10px;
  border: none;
  border-radius: 5px;
  background-color: var(--primary-color);
  color: white;
  font-weight: bold;
  cursor: pointer;
  transition: background-color 0.2s ease;
}

.contact-btn:hover {
  background-color: var(--secondary-color);
}

.message {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
  background-color: var(--primary-color);
  color: white;
  padding: 10px 20px;
  border-radius: 5px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
  transition: all 0.3s ease;
}

.hidden {
  opacity: 0;
  transform: translate(-50%, 20px);
  pointer-events: none;
}

```

**JavaScript**

```javascript
// Seleccionar elementos
const themeButton = document.getElementById('theme-button');
const profileCard = document.getElementById('profile-card');
const contactButton = document.getElementById('contact-button');
const message = document.getElementById('message');

// Cambiar entre modo claro y oscuro
themeButton.addEventListener('click', function() {
  document.body.classList.toggle('dark-theme');
  
  // Cambiar el ícono del botón
  if (document.body.classList.contains('dark-theme')) {
    themeButton.textContent = '☀️';
  } else {
    themeButton.textContent = '🌙';
  }
});

// Mostrar mensaje al hacer clic en el botón de contacto
contactButton.addEventListener('click', function() {
  message.classList.remove('hidden');
  
  // Ocultar el mensaje después de 3 segundos
  setTimeout(function() {
    message.classList.add('hidden');
  }, 3000);
});
```

