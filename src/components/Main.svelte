<div class="Main">
    <div class="Main-container">
        <slot />
    </div>
</div>


<style>
  .Main {
    display: flex;
    justify-content: center;
    padding-top: 2em;
    width: 100%;
  }
  
  .Main-container {
    display: flex;
    max-width: 820px;
    width: 100%;
    justify-content: center;
    gap: 32px;
  }

  @media (max-width: 1000px) {
    .Main-container {
      max-width: 630px;
    }
  }

  @media (max-width: 768px) {
    .Main {
      padding-top: 60px; /* Space for mobile header */
    }
    .Main-container {
      max-width: 100%;
      padding: 0;
    }
  }
</style>