<script>
  import { onMount } from 'svelte';
  import Profile from './Profile.svelte';
  import Footer from './Footer.svelte';

  let users = [];
  let loading = true;

  onMount(async () => {
    try {
      const res = await fetch('https://api.escuelajs.co/api/v1/users');
      if (!res.ok) throw new Error("API fallando");
      const apiUsers = await res.json();
      
      const coolNames = [
        "Julieta Ruiz", "Emilio Silva", "Renata Gómez", "Nicolás Paz", 
        "Victoria Rojas", "Joaquín Vega", "Camila Ortiz", "Mateo Cruz"
      ];

      users = apiUsers.map((u, i) => ({
        ...u,
        name: coolNames[i % coolNames.length]
      }));
    } catch (error) {
      console.error('Error loading users', error);
      // Fallback
      users = [
        { name: "Juan Pérez", avatar: "https://i.pravatar.cc/150?img=1" },
        { name: "María Gómez", avatar: "https://i.pravatar.cc/150?img=2" },
        { name: "Carlos López", avatar: "https://i.pravatar.cc/150?img=3" },
        { name: "Ana Martínez", avatar: "https://i.pravatar.cc/150?img=4" },
        { name: "Pedro Rodríguez", avatar: "https://i.pravatar.cc/150?img=5" },
        { name: "Sofía Fernández", avatar: "https://i.pravatar.cc/150?img=6" },
        { name: "Diego Ramírez", avatar: "https://i.pravatar.cc/150?img=7" },
        { name: "Valentina Ruiz", avatar: "https://i.pravatar.cc/150?img=8" }
      ];
    } finally {
      loading = false;
    }
  });
</script>

<div class="RightPanel">
  <div class="RightPanel-container">
    {#if loading}
      <div class="loading">Cargando sugerencias...</div>
    {:else}
      <Profile user={users[0]} />
      
      <div class="suggestions">
        <h4>Sugerencias para ti</h4>
        <a href="/" class="see-all">Ver todo</a>
      </div>
      
      <div class="suggestions-list">
        {#each users.slice(1, 6) as user}
          <div class="suggestion-item">
            <img src={user.avatar} alt={user.name} />
            <div class="suggestion-info">
              <span class="suggestion-name">{user.name}</span>
              <span class="suggestion-desc">Nuevo en Instagram</span>
            </div>
            <button class="follow-btn">Seguir</button>
          </div>
        {/each}
      </div>
      
      <Footer />
    {/if}
  </div>
</div>

<style>
  .RightPanel {
    display: none;
  }
  
  @media (min-width: 1000px) {
    .RightPanel {
      display: block;
      width: 319px;
      padding-top: 2em;
    }
  }

  .RightPanel-container {
    position: fixed;
    width: 319px;
  }

  .loading {
    color: var(--text-secondary);
    font-size: 14px;
  }

  .suggestions {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin: 1.5em 0 1em;
  }

  .suggestions h4 {
    color: var(--text-secondary);
    font-size: 14px;
    font-weight: 600;
  }

  .see-all {
    color: var(--text-color);
    font-size: 12px;
    font-weight: 600;
  }

  .suggestion-item {
    display: flex;
    align-items: center;
    margin-bottom: 1em;
  }

  .suggestion-item img {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    margin-right: 12px;
  }

  .suggestion-info {
    display: flex;
    flex-direction: column;
    flex-grow: 1;
  }

  .suggestion-name {
    font-size: 14px;
    font-weight: 600;
  }

  .suggestion-desc {
    font-size: 12px;
    color: var(--text-secondary);
  }

  .follow-btn {
    background: none;
    border: none;
    color: var(--link-color);
    font-weight: 600;
    font-size: 12px;
    cursor: pointer;
    padding: 0;
  }
</style>
