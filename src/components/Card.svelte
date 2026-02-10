<script>
  import Comments from "./Comments.svelte";

  export let user;
  export let location;
  export let image;
  export let description;

  let liked = false;
  let bookmarked = false;

  function toggleLike() {
    liked = !liked;
  }

  function likeFromImage() {
    if (!liked) {
      liked = true;
    }
  }

  function toggleBookmark() {
    bookmarked = !bookmarked;
  }
</script>

<div class="Card">
  <div class="Card__container">

    <div class="Card__header">
      <div class="Card__user">
        <img src={image} alt={user} />
        <h2>
          {user}
          <span>{location}</span>
        </h2>
      </div>

      <div class="Card__settings">
        <i class="fas fa-ellipsis-h"></i>
      </div>
    </div>

    <div class="Card__photo">
      <button
        class="image-button"
        on:dblclick={likeFromImage}
        aria-label="Like image"
      >
        <img src={image} alt={user} />
      </button>
    </div>

    <div class="Card__icons">
      <div class="Card__icons-first">
        <button
          class="icon-button"
          on:click={toggleLike}
          aria-label="Like"
        >
          <i class={`fa-heart ${liked ? 'fas active__like' : 'far'}`}></i>
        </button>

        <i class="fas fa-paper-plane"></i>
      </div>

      <div class="Card__icons-second">
        <button
          class="icon-button"
          on:click={toggleBookmark}
          aria-label="Bookmark"
        >
          <i class={`fa-bookmark ${bookmarked ? 'fas active__bookmark' : 'far'}`}></i>
        </button>
      </div>
    </div>

    <div class="Card__description">
      <h3>{user}</h3>
      <span>{description}</span>
    </div>

    <Comments petName={user}/>

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
  }

  .Card__user img {
    width: 32px;
    height: 32px;
    border-radius: 50%;
  }

  .Card__user h2 {
    margin: 0 0 0 1em;
    font-size: 14px;
    font-weight: 600;
    color: black;
  }

  .Card__user h2 span {
    display: block;
    font-size: 12px;
    font-weight: normal;
    color: rgba(38, 38, 38, 0.7);
  }

  .Card__photo img {
    width: 100%;
    height: auto;
    display: block;
  }

  .Card__icons {
    padding: 1em;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .Card__icons i {
    font-size: 20px;
    cursor: pointer;
  }

  .Card__description {
    padding: 0 1em 1em;
  }

  .Card__description h3 {
    font-size: 14px;
    font-weight: bold;
    color: black;
  }

  .Card__description span {
    font-size: 14px;
  }

  .active__like {
    color: #bc1888;
    animation: bounce linear 0.8s;
  }

  .active__bookmark {
    color: #f09433;
  }

  .icon-button {
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;
  }

  .image-button {
    all: unset;
    display: block;
    width: 100%;
    cursor: pointer;
  }

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
