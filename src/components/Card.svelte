<script>
  import Comments from "./Comments.svelte";

  export let user;
  export let avatar;
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

<article class="Card">
  <div class="Card__container">
    <header class="Card__header">
      <div class="Card__user">
        <div class="Card__user-avatar-ring">
          <img src={avatar} alt={user} />
        </div>
        <div class="Card__user-info">
          <h2>{user}</h2>
          <span>{location}</span>
        </div>
      </div>
      <button class="icon-button Card__settings">
        <i class="fas fa-ellipsis-h"></i>
      </button>
    </header>

    <div class="Card__photo">
      <button class="image-button" on:dblclick={likeFromImage} aria-label="Like image">
        <img src={image} alt={`Post by ${user}`} loading="lazy" />
      </button>
    </div>

    <div class="Card__actions">
      <div class="Card__actions-group">
        <button class="icon-button" on:click={toggleLike} aria-label="Like">
          <i class={`fa-heart ${liked ? 'fas active__like' : 'far'}`}></i>
        </button>
        <button class="icon-button" aria-label="Comment">
          <i class="far fa-comment"></i>
        </button>
        <button class="icon-button" aria-label="Share">
          <i class="far fa-paper-plane"></i>
        </button>
      </div>
      <div class="Card__actions-save">
        <button class="icon-button" on:click={toggleBookmark} aria-label="Save">
          <i class={`fa-bookmark ${bookmarked ? 'fas active__bookmark' : 'far'}`}></i>
        </button>
      </div>
    </div>

    <div class="Card__likes">
      <span>{liked ? '1' : '0'} Me gusta</span>
    </div>

    <div class="Card__caption">
      <h3>{user}</h3>
      <span>{description}</span>
    </div>

    <Comments petName={user} />
  </div>
</article>

<style>
  .Card {
    background-color: var(--card-bg);
    border-bottom: 1px solid var(--border-color);
    margin: 0;
    padding-bottom: 16px;
  }

  @media (min-width: 768px) {
    .Card {
      border: 1px solid var(--border-color);
      border-radius: 8px;
      margin-bottom: 24px;
    }
  }

  .Card__header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 12px 16px;
  }

  .Card__user {
    display: flex;
    align-items: center;
  }

  .Card__user-avatar-ring {
    width: 42px;
    height: 42px;
    border-radius: 50%;
    background: linear-gradient(45deg, #f09433 0%, #e6683c 25%, #dc2743 50%, #cc2366 75%, #bc1888 100%);
    display: flex;
    justify-content: center;
    align-items: center;
    margin-right: 12px;
  }

  .Card__user img {
    width: 38px;
    height: 38px;
    border-radius: 50%;
    border: 2px solid var(--card-bg);
    object-fit: cover;
  }

  .Card__user-info h2 {
    margin: 0;
    font-size: 14px;
    font-weight: 600;
    color: var(--text-color);
  }

  .Card__user-info span {
    font-size: 12px;
    color: var(--text-secondary);
  }

  .Card__settings i {
    color: var(--text-color);
    font-size: 16px;
  }

  .Card__photo img {
    width: 100%;
    height: auto;
    max-height: 585px; /* Aspect ratio control roughly */
    object-fit: cover;
    display: block;
  }

  .Card__actions {
    display: flex;
    justify-content: space-between;
    padding: 8px 16px;
  }

  .Card__actions-group {
    display: flex;
    gap: 16px;
  }

  .icon-button {
    background: none;
    border: none;
    padding: 0;
    cursor: pointer;
    color: var(--text-color);
  }
  
  .icon-button i {
    font-size: 24px;
    transition: transform 0.1s ease;
  }

  .icon-button:active i {
    transform: scale(0.9);
  }

  .active__like {
    color: #ff3040;
    animation: bounce linear 0.3s;
  }

  .active__bookmark {
    color: var(--text-color);
  }

  .Card__likes {
    padding: 0 16px;
    margin-bottom: 8px;
  }

  .Card__likes span {
    font-weight: 600;
    font-size: 14px;
    color: var(--text-color);
  }

  .Card__caption {
    padding: 0 16px;
    margin-bottom: 8px;
    font-size: 14px;
  }

  .Card__caption h3 {
    display: inline;
    font-weight: 600;
    color: var(--text-color);
    margin-right: 4px;
  }

  .image-button {
    all: unset;
    display: block;
    width: 100%;
    cursor: pointer;
  }

  @keyframes bounce {
    0% { transform: scale(1); }
    50% { transform: scale(1.2); }
    100% { transform: scale(1); }
  }
</style>
