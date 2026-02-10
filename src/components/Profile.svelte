<script>
    export let user;
</script>

<div class="Profile">
  <div class="Profile__content">
    <div class="Profile__avatar">
      <img src={user.avatar} alt={user.name} />
    </div>
    <div class="Profile__info">
      <h2>{user.name}</h2>
      <span>{user.email}</span>
    </div>
  </div>
</div>

<style>
  .Profile__content {
    display: flex;
    align-items: center;
  }
  .Profile__avatar img {
    width: 42px;
    height: 42px;
    border-radius: 50%;
  }
  .Profile__info {
    margin: 0 0 0 0.5em;
  }
  .Profile__info h2 {
    font-size: 14px;
    color: black;
    margin: 0;
    padding: 0;
  }
  .Profile__info span {
    font-size: 12px;
    font-weight: normal;
  }
</style>