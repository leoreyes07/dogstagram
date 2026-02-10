<script>
  import { onMount } from 'svelte';
  import Profile from './Profile.svelte';
  import Stories from './Stories.svelte';
  import Footer from './Footer.svelte';

  let users = [];
  let loading = true;

  onMount(async () => {
    try {
      const res = await fetch('https://api.escuelajs.co/api/v1/users');
      users = await res.json();
    } catch (error) {
      console.error('Error loading users', error);
    } finally {
      loading = false;
    }
  });
</script>


<div class="Sidebar">
  <div class="Sidebar-container">

    {#if loading}
      <p>Cargando usuarios...</p>
    {:else}
      <Profile user={users[0]} />
      <Stories users={users.slice(1, 6)} />
      <Footer />
    {/if}
    </div>
</div>

<style>
  .Sidebar {
    position: relative;
    padding: 4.5em 0 0 0;
  }
  .Sidebar-container {
    position: fixed;
  }
</style>