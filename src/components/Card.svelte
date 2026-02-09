<script>
  import Comments from "./Comments.svelte";

  export let user;
  export let location;
  export let image;
  export let description;
  
</script>

<div class="Card">
  <div class="Card__container">
    <div class="Card__header">
      <div class="Card__user">
        <img src={image} alt={user} />
        <h2>{user}<span>{location}</span></h2>
      </div>
      <div class="Card__settings">
        <i class="fas fa-ellipsis-h"></i>
      </div>
    </div>
    <div class="Card__photo">
      <figure>
        <img src={image} alt={user} />
      </figure>
    </div>
    <div class="Card__icons">
      <div class="Card__icons-first">
        <i class="fas fa-heart"></i>
        <i class="fas fa-paper-plane"></i>
      </div>
      <div class="Card__icons-second">
        <i class="fas fa-bookmark"></i>
      </div>
    </div>
    <div class="Card__description">
      <h3>{user}</h3>
      <span>{description}</span>
    </div>
    <Comments />
  </div>
</div>

<style>
  .Card {
    border: 1px solid rgba(219, 219, 219, 1);
    border-radius: 4px;
    background-color: white;
    margin: 0 0 2em 0;
  }
  .Card__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1em;
  }
  .Card__user {
    display: flex;
    align-items: center;
    justify-content: flex-end;
  }
  .Card__user img {
    width: 32px;
    height: 32px;
    border-radius: 50%;
  }
  .Card__user h2 {
    margin: 0;
    padding: 0;
    font-size: 14px;
    font-weight: 600;
    margin: 0 0 0 1em;
    color: black;
  }
  .Card__user h2 span {
    display: block;
    font-size: 12px;
    font-weight: normal;
    color: rgba(38, 38, 38, 0.7);
  }
  .Card__photo {
    padding: 0;
    margin: 0;
  }
  .Card__photo img {
    width: 100%;
    height: auto;
  }
  .Card__photo figure {
    margin: 0;
    padding: 0;
    cursor: pointer;
  }
  .Card__settings i {
    cursor: pointer;
  }
  .Card__icons {
    padding: 1em;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .Card__icons i {
    margin: 0 1em 0 0;
    cursor: pointer;
    font-size: 20px;
  }
  .Card__icons i:last-child {
    margin: 0;
  }
  .Card__description {
    padding: 0 1em 1em 1em;
  }
  .Card__description h3 {
    font-size: 14px;
    font-weight: bold;
    color: black;
  }
  .Card__description span {
    font-size: 14px;
  }
  /*   .active__like {
    color: #bc1888;
    animation: bounce linear 0.8s;
    animation-iteration-count: 1;
    transform-origin: 20% 20%;
  }
  .active__bookmark {
    color: #f09433;
  } */

  @keyframes bounce {
    0% {
      transform: translate(0px, 0px);
    }
    15% {
      transform: translate(0px, -25px);
    }
    30% {
      transform: translate(0px, 0px);
    }
    45% {
      transform: translate(0px, -15px);
    }
    60% {
      transform: translate(0px, 0px);
    }
    75% {
      transform: translate(0px, -5px);
    }
    100% {
      transform: translate(0px, 0px);
    }
  }
</style>
