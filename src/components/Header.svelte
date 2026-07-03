<div class="Header">
    <div class="Header__container">
        <div class="Header__content">
            <div class="Header__logo">
                <h1>Dogstagram</h1>
            </div>
            <div class="Header__nav">
                <ul>
                    <li>
                        <i class="far fa-heart"></i>
                    </li>
                    <li>
                        <i class="far fa-paper-plane"></i>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</div>

<style>
  .Header {
    background-color: var(--nav-bg);
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 100;
    display: none; /* Oculto por defecto en desktop */
  }

  @media (max-width: 768px) {
    .Header {
      display: block;
    }
  }

  .Header__container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px solid var(--border-color);
  }
  .Header__content {
    display: flex;
    width: 100%;
    align-items: center;
    justify-content: space-between;
    padding: 0 1em;
    height: 60px;
  }
  .Header ul {
    list-style: none;
    display: flex;
    align-items: center;
    margin: 0;
    padding: 0;
  }
  .Header li {
    margin-left: 1.5em;
  }
  .Header i {
    font-size: 24px;
    color: var(--text-color);
    cursor: pointer;
  }

  h1 {
    padding: 0;
    margin: 0;
    font-size: 28px;
    color: var(--text-color);
    font-family: "Pacifico", cursive;
    cursor: pointer;
  }
</style>
