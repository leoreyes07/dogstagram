<script>
    import Comments from './Comments.svelte';
</script>

<div class="Card">
    <div class="Card__container">
        <div class="Card__header">
            <div class="Card__header-user">
                <img src="" alt="" />
                <h2>Brady
                    <span>Austin, Texas</span>
                </h2>
            </div>
            <div class="Card__settings">
                <i class="fas fa-ellipsis-h"></i>
            </div>
        </div>
        <div class="Card__photo">
            <figure>
                <img src="" alt="" />
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
            <h3>Brady</h3>
            <span>Hi everyone!</span>
        </div>
        <Comments />
    </div>
</div>
