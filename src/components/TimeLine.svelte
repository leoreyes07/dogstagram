<script>
  import Card from "./Card.svelte";
  import { onMount } from "svelte";

  let posts = [];
  let loading = true;

  async function loadDogs() {
    try {
      const res = await fetch("https://dog.ceo/api/breeds/image/random/20");
      const data = await res.json();

      posts = data.message.map((img, index) => ({
        id: index,
        user: "Elmo",
        location: "Austin, Texas",
        image: img,
        description: "Hi everyone!",
      }));
    } catch (error) {
      console.error("Error loading dogs", error);
    } finally {
      loading = false;
    }
  }

  onMount(loadDogs);
</script>

<div class="TimeLine">
  <div class="TimeLine__container">

    {#if loading}
      <p>Loading 🐶...</p>
    {:else}
      {#each posts as post (post.id)}
        <Card {...post} />
      {/each}
    {/if}

  </div>
</div>

<style>
  .TimeLine {
    padding: 4em 0 0 0;
  }
</style>
