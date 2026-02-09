<div class="Header">
    <div class="Header__container">
        <div class="Header__content">
            <div class="Header__logo">
                <h1>Dogstagram</h1>
            </div>
            <div class="Header__nav">
                <ul>
                    <li>
                        <i class="fa-thin fa-heart"></i>
                    </li>
                    <li>
                        <i class="fa-thin fa-user-alt"></i>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</div>


<style>
  .Header {
    background-color: white;
    position: fixed;
    width: 100%;
  }
  .Header__container {
    grid-template-columns: minmax(auto, 936px);
    display: grid;
    justify-content: center;
    background-color: white;
    border-bottom: 1px solid rgba(38, 38, 38, 0.4);
  }
  .Header__content {
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 0.5em;
  }
  .Header ul {
    list-style: none;
  }
  .Header li {
    display: inline-block;
    margin: 0 0 0 1em;
  }
  .Header i {
    font-size: 16px;
    color: rgba(38, 38, 38, 0.7);
    cursor: pointer;
  }

  h1 {
    padding: 0;
    margin: 0;
    font-size: 28px;
    color: black;
    font-family: "Pacifico", cursive;
    cursor: pointer;
    position: relative;
    background: #fff;
    mix-blend-mode: multiply;
    display: inline-block;
  }

  h1:before {
    content: "";
    display: block;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at top left, #f09433, #bc1888);
    mix-blend-mode: screen;
    position: absolute;
    top: 0;
    left: 0;
  }
</style>
