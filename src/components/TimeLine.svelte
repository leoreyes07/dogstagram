<script>
  import Card from "./Card.svelte";
  import { onMount } from "svelte";

  const users = [
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

  onMount(async () => {
    const res = await fetch("https://dog.ceo/api/breeds/image/random/20");
    const data = await res.json();

    posts = data.message.map((img, index) => ({
      id: index,
      user: users[index].name,
      location: users[index].location,
      image: img,
      description: "Hi everyone!",
    }));
  });
</script>

<div class="TimeLine">
  <div class="TimeLine__container">
    {#each posts as post (post.id)}
      <Card {...post} />
    {/each}
  </div>
</div>

<style>
  .TimeLine {
    padding: 4em 0 0 0;
  }
</style>
