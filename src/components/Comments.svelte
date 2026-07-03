<script>
  export let petName = "Brady";

  const randomUsers = [
    "Chris",
    "Alex",
    "Sam",
    "Jordan",
    "Taylor",
    "Jamie",
    "Morgan",
  ];

  let commentUser = randomUsers[Math.floor(Math.random() * randomUsers.length)];
</script>

<div class="Comments">
  <div class="Comments__content">
    <div class="Comments__users">
      <h3>{commentUser}</h3>
      <span>¡Hola {petName}! 👋</span>
    </div>
  </div>

  <div class="Comments__add">
    <form on:submit|preventDefault>
      <input
        type="text"
        class="Comments__input"
        placeholder="Añade un comentario..."
        id="text"
      />
      <button type="submit">Publicar</button>
    </form>
  </div>
</div>

<style>
  .Comments h3 {
    font-size: 14px;
    color: var(--text-color);
    font-weight: 600;
    margin: 0;
    padding: 0;
  }

  .Comments span {
    font-size: 14px;
    margin: 0 0 0 4px;
    font-weight: normal;
    color: var(--text-color);
  }

  .Comments__content {
    padding: 0 16px 8px 16px;
  }

  .Comments__users {
    display: flex;
    margin-bottom: 4px;
  }

  .Comments__add {
    padding: 12px 16px;
    border-top: 1px solid var(--border-color);
  }
  
  .Comments__add form {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  input {
    background: transparent;
    color: var(--text-color);
    border: none;
    font-size: 14px;
    outline: none;
    width: 100%;
    display: flex;
  }

  input::placeholder {
    color: var(--text-secondary);
  }

  button {
    background: transparent;
    border: none;
    color: var(--link-color);
    font-size: 14px;
    font-weight: 600;
    outline: none;
    cursor: pointer;
    padding: 0;
    margin-left: 8px;
    transition: opacity 0.2s;
  }

  button:hover {
    opacity: 0.7;
  }
</style>
