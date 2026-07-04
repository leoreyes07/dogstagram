<script>
  import Card from "./Card.svelte";
  import Stories from "./Stories.svelte";
  import { onMount } from "svelte";

  // Locations para los posts
  const locations = [
    "Austin, Texas", "New York, USA", "Los Angeles, CA", "Chicago, IL",
    "Veracruz, MX", "Miami, FL", "Denver, CO", "Seattle, WA",
    "Portland, OR", "Phoenix, AZ", "Orlando, FL", "Boston, MA",
    "San Jose, CA", "Atlanta, GA", "Dallas, TX", "Raleigh, NC",
    "Kansas City, MO", "Santa Monica, CA", "Las Vegas, NV", "Madison, WI",
  ];

  let posts = [];
  let users = [];

  onMount(async () => {
    // Fetch simultáneo: imágenes de perros + usuarios con género de RandomUser API
    const [dogResult, personResult] = await Promise.allSettled([
      fetch("https://api.thedogapi.com/v1/images/search?limit=20").then(r => {
        if (!r.ok) throw new Error("Dog API no disponible");
        return r.json();
      }),
      fetch("https://randomuser.me/api/?results=20&nat=es,mx,ar").then(r => {
        if (!r.ok) throw new Error("RandomUser API no disponible");
        return r.json();
      }),
    ]);

    const dogImages = dogResult.status === "fulfilled"
      ? dogResult.value
      : Array(20).fill({ url: "https://images.unsplash.com/photo-1543466835-00a7907e9de1?w=500" });

    const personData = personResult.status === "fulfilled"
      ? personResult.value.results
      : null;

    posts = dogImages.map((item, index) => {
      const person = personData?.[index];
      const name = person
        ? `${person.name.first} ${person.name.last}`
        : locations[index % locations.length].split(",")[0];

      return {
        id: index,
        user: name,
        location: person
          ? `${person.location.city}, ${person.location.country}`
          : locations[index % locations.length],
        // avatar = foto de persona (genero correcto), image = foto del perro (post)
        avatar: person?.picture?.large ?? `https://i.pravatar.cc/150?u=${index}`,
        image: item.url,
        description: "¡Hola a todos! 🐶",
      };
    });

    // Stories: también usan RandomUser para tener avatares de personas reales
    try {
      const uRes = await fetch("https://randomuser.me/api/?results=15&nat=es,mx,ar,co");
      if (!uRes.ok) throw new Error("RandomUser stories no disponible");
      const { results } = await uRes.json();
      users = results.map(u => ({
        name: u.name.first,
        avatar: u.picture.medium,
      }));
    } catch (e) {
      console.error("Error fetching stories users:", e);
      users = locations.slice(0, 15).map((loc, i) => ({
        name: loc.split(",")[0],
        avatar: `https://i.pravatar.cc/150?u=story${i}`,
      }));
    }
  });
</script>

<div class="TimeLine">
  <div class="TimeLine__container">
    {#if users.length > 0}
      <Stories users={users.slice(1, 10)} />
    {/if}

    <div class="feed">
      {#each posts as post (post.id)}
        <Card {...post} />
      {/each}
    </div>
  </div>
</div>

<style>
  .TimeLine {
    width: 100%;
    max-width: 470px; /* Instagram feed max-width */
    margin: 0 auto;
  }
  
  .feed {
    display: flex;
    flex-direction: column;
    gap: 16px; /* spacing between cards */
  }
</style>
