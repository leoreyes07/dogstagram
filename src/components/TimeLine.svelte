<script>
  import Card from "./Card.svelte";
  import Stories from "./Stories.svelte";
  import { onMount } from "svelte";

  const userNames = [
    { name: "Elmo", location: "Austin, Texas" },
    { name: "Brady", location: "New York, USA" },
    { name: "Rocky", location: "Los Angeles, CA" },
    { name: "Max", location: "Chicago, IL" },
    { name: "Luna", location: "Veracruz, NI" },
    { name: "Bela", location: "Tipitapa, NI" },
    { name: "Charlie", location: "Denver, CO" },
    { name: "Milo", location: "Seattle, WA" },
    { name: "Daisy", location: "Portland, OR" },
    { name: "Toby", location: "Phoenix, AZ" },
    { name: "Nala", location: "Orlando, FL" },
    { name: "Oscar", location: "Boston, MA" },
    { name: "Coco", location: "San Jose, CA" },
    { name: "Simba", location: "Atlanta, GA" },
    { name: "Leo", location: "Dallas, TX" },
    { name: "Lucy", location: "Raleigh, NC" },
    { name: "Buddy", location: "Kansas City, MO" },
    { name: "Chloe", location: "Santa Monica, CA" },
    { name: "Zeus", location: "Las Vegas, NV" },
    { name: "Penny", location: "Madison, WI" },
  ];

  let posts = [];
  let users = [];

  onMount(async () => {
    // Fetch posts images
    try {
      const res = await fetch("https://dog.ceo/api/breeds/image/random/8");
      if (!res.ok) throw new Error("API Dog CEO no disponible");
      const data = await res.json();

      posts = data.message.map((img, index) => ({
        id: index,
        user: userNames[index].name,
        location: userNames[index].location,
        image: img,
        description: "¡Hola a todos! 🐶",
      }));
    } catch (e) {
      console.error('Error fetching dog images:', e);
      // Fallback data
      posts = userNames.map((u, index) => ({
        id: index,
        user: u.name,
        location: u.location,
        image: "https://images.unsplash.com/photo-1543466835-00a7907e9de1?ixlib=rb-1.2.1&auto=format&fit=crop&w=500&q=60", 
        description: "¡Falló la API pero acá sigo! 🐶",
      }));
    }

    // Fetch users for stories
    try {
      const uRes = await fetch('https://api.escuelajs.co/api/v1/users');
      if (!uRes.ok) throw new Error("API Escuela JS no disponible");
      const apiUsers = await uRes.json();
      
      const coolNames = [
        "Valentina", "Mateo", "Camila", "Sebastián", "Martín", 
        "Valeria", "Lucas", "Emma", "Andrés", "Isabella", 
        "Joaquín", "Mía", "Santiago", "Lucía", "Tomás"
      ];
      
      // Override API names with our cool names to avoid "Admin", "John", etc.
      users = apiUsers.map((u, i) => ({
        ...u,
        name: coolNames[i % coolNames.length]
      }));
      
    } catch (e) {
      console.error('Error fetching users for stories:', e);
      // Fallback data for stories
      users = userNames.map((u, i) => ({
        name: u.name,
        avatar: `https://i.pravatar.cc/150?u=${i}`
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
