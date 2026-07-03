<script>
  export let users = [];
</script>

<div class="Stories">
  <div class="Stories__container">
    {#each users as user}
      <div class="Stories__item">
        <div class="Stories__item-box">
          <img src={user.avatar} alt={user.name} />
        </div>
        <h2>{user.name.split(' ')[0]}</h2>
      </div>
    {/each}
  </div>
</div>

<style>
  .Stories {
    border: none;
    margin-bottom: 24px;
    background-color: var(--bg-color); /* Instagram en mobile y nuevo desktop no suele tener card blanca para stories */
  }

  .Stories__container {
    display: flex;
    overflow-x: auto;
    gap: 16px;
    padding: 16px 0;
    scrollbar-width: none; /* Firefox */
  }

  .Stories__container::-webkit-scrollbar {
    display: none; /* Safari and Chrome */
  }

  .Stories__item {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 66px;
    flex-shrink: 0;
  }

  .Stories__item-box {
    width: 66px;
    height: 66px;
    border-radius: 50%;
    background: linear-gradient(45deg, #f09433 0%, #e6683c 25%, #dc2743 50%, #cc2366 75%, #bc1888 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 2px; /* Espacio para el borde de gradiente */
    cursor: pointer;
    transition: transform 0.2s ease;
  }

  .Stories__item-box:active {
    transform: scale(0.95);
  }

  .Stories__item img {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    border: 2px solid var(--bg-color);
    background-color: var(--bg-color);
    object-fit: cover;
  }

  .Stories__item h2 {
    font-size: 12px;
    color: var(--text-color);
    margin: 8px 0 0 0;
    font-weight: 400;
    white-space: nowrap;
    overflow: hidden;
    text-overflow: ellipsis;
    max-width: 100%;
  }
</style>
