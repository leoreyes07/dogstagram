<script>
  import { createEventDispatcher } from 'svelte';
  export let isDarkMode;

  const dispatch = createEventDispatcher();

  function toggleDark() {
    dispatch('toggle');
  }
</script>

<nav class="Navigation">
  <div class="logo-container">
    <h1 class="logo">Dogstagram</h1>
  </div>
  
  <div class="nav-links">
    <a href="/" class="nav-item active">
      <i class="fas fa-home"></i>
      <span>Inicio</span>
    </a>
    <a href="/" class="nav-item">
      <i class="fas fa-search"></i>
      <span>Búsqueda</span>
    </a>
    <a href="/" class="nav-item">
      <i class="far fa-compass"></i>
      <span>Explorar</span>
    </a>
    <a href="/" class="nav-item">
      <i class="far fa-play-circle"></i>
      <span>Reels</span>
    </a>
    <a href="/" class="nav-item">
      <i class="far fa-paper-plane"></i>
      <span>Mensajes</span>
    </a>
    <a href="/" class="nav-item">
      <i class="far fa-heart"></i>
      <span>Notificaciones</span>
    </a>
    <a href="/" class="nav-item">
      <i class="far fa-plus-square"></i>
      <span>Crear</span>
    </a>
    <a href="/" class="nav-item">
      <div class="avatar-ph"></div>
      <span>Perfil</span>
    </a>
  </div>

  <div class="nav-bottom">
    <button class="nav-item theme-toggle" on:click={toggleDark}>
      <i class={isDarkMode ? "fas fa-sun" : "fas fa-moon"}></i>
      <span>{isDarkMode ? 'Modo Claro' : 'Modo Oscuro'}</span>
    </button>
    <a href="/" class="nav-item">
      <i class="fas fa-bars"></i>
      <span>Más</span>
    </a>
  </div>
</nav>

<style>
  .Navigation {
    position: fixed;
    top: 0;
    left: 0;
    height: 100vh;
    width: 244px;
    background-color: var(--nav-bg);
    border-right: 1px solid var(--border-color);
    display: flex;
    flex-direction: column;
    padding: 20px 12px;
    box-sizing: border-box;
    z-index: 100;
  }

  .logo-container {
    padding: 25px 12px;
    margin-bottom: 20px;
  }

  .logo {
    font-family: 'Pacifico', cursive;
    font-size: 24px;
    color: var(--text-color);
    font-weight: 400;
  }

  .nav-links {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .nav-item {
    display: flex;
    align-items: center;
    padding: 12px;
    border-radius: 8px;
    color: var(--text-color);
    transition: background-color 0.2s;
    background: none;
    border: none;
    width: 100%;
    cursor: pointer;
    text-align: left;
    font-size: 16px;
  }

  .nav-item:hover {
    background-color: var(--highlight);
  }

  .nav-item i {
    font-size: 24px;
    margin-right: 16px;
    width: 24px;
    text-align: center;
  }

  .nav-item span {
    font-weight: 400;
  }

  .nav-item.active span {
    font-weight: 700;
  }

  .avatar-ph {
    width: 24px;
    height: 24px;
    border-radius: 50%;
    background-color: var(--text-secondary);
    margin-right: 16px;
  }

  .nav-bottom {
    margin-top: auto;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  @media (max-width: 1200px) {
    .Navigation {
      width: 72px;
      align-items: center;
    }
    .logo-container {
      display: none;
    }
    .nav-item span {
      display: none;
    }
    .nav-item i {
      margin-right: 0;
    }
    .avatar-ph {
      margin-right: 0;
    }
  }

  @media (max-width: 768px) {
    .Navigation {
      top: auto;
      bottom: 0;
      height: 50px;
      width: 100%;
      flex-direction: row;
      justify-content: space-around;
      border-right: none;
      border-top: 1px solid var(--border-color);
      padding: 0;
    }
    .nav-bottom, .logo-container {
      display: none;
    }
    .nav-links {
      flex-direction: row;
      justify-content: space-around;
      width: 100%;
      gap: 0;
    }
    .nav-item {
      padding: 0;
      justify-content: center;
      border-radius: 0;
    }
    .nav-item:hover {
      background-color: transparent;
    }
    .nav-links a:nth-child(2),
    .nav-links a:nth-child(3),
    .nav-links a:nth-child(6) {
      display: none;
    }
  }
</style>
