<div class="Stories">
    <div class="Stories__container">
        <div class="Stories__head">
            <h2>Stories</h2>
            <span>See all</span>
        </div>
        <div class="Stories__items">
            <div class="Stories__item">
                <div class="Stories__item-box">
                    <img src="/static/images/user_01.1.2.png" alt="" />
                </div>
                <h2>User</h2>
                <span>10 hours ago</span>
            </div>
        </div>
    </div>
</div>


<style>
  .Stories {
    border: 1px solid rgba(219, 219, 219, 1);
    border-radius: 4px;
    margin: 1em 0;
    padding: 0.5em 1em;
    background-color: white;
  }
  .Stories__item img {
    width: 32px;
    height: 32px;
    border-radius: 50%;
  }
  .Stories__item {
    display: flex;
    align-items: center;
    margin: 0 0 0.5em 0;
  }
  .Stories__item h2 {
    font-size: 14px;
    color: black;
    margin: 0 0 0 0.5em;
  }
  .Stories__item h2 span {
    display: block;
    font-size: 9px;
    text-transform: uppercase;
    color: gray;
  }
  .Stories__head {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0.5em 0 0 0;
  }
  .Stories__head h2 {
    font-size: 12px;
    font-weight: 600;
  }
  .Stories__head span {
    font-size: 12px;
    font-weight: normal;
    color: black;
  }
  .Stories__items {
    margin: 0.5em 0 0.5em 0;
  }
  .Stories__item-box {
    width: 32px;
    height: 32px;
    border: double 2px transparent;
    border-radius: 100%;
    background-image: linear-gradient(#fff, #fff),
      radial-gradient(circle at top left, #f09433, #bc1888);
    background-origin: border-box;
    background-clip: content-box, border-box;
  }
</style>
