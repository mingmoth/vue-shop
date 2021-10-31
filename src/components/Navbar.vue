<template>
  <div class="header">
    <div class="header-logo"></div>
    <label for="nav-toggle" class="nav-toggle-label"></label>
    <input type="checkbox" name="nav-toggle" id="nav-toggle" />
    <div class="nav">
      <div class="nav-select">
        <ul class="nav-list">
          <li class="nav-item">
            <a class="nav-link" href="#activity">男款</a>
          </li>
          <hr />
          <li class="nav-item">
            <a class="nav-link" href="#activity">女款</a>
          </li>
          <hr />
          <li class="nav-item">
            <a class="nav-link" href="#activity">最新消息</a>
          </li>
          <hr />
          <li class="nav-item">
            <a class="nav-link" href="#activity">客製商品</a>
          </li>
          <hr />
          <li class="nav-item">
            <a class="nav-link" href="#activity">聯絡我們</a>
          </li>
          <hr />
        </ul>
      </div>
      <div class="nav-option">
        <div class="option-img-wrapper">
          <div class="search"></div>
          <div class="cart"></div>
          <label for="darkmode" class="darkmode-toggle"></label>
          <input
            type="checkbox"
            class="darkmode"
            id="darkmode"
            @change="darkToggle"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    darkToggle(e) {
      if (e.target.checked) {
        document.documentElement.setAttribute("data-theme", "dark");
      } else {
        document.documentElement.setAttribute("data-theme", "light");
      }
    },
  },
};
</script>

<style lang="scss">
.header {
  position: fixed;
  left: 5%;
  width: 90%;
  height: 64px;
  margin: 0 auto;
  z-index: 999;
  background: var(--bg);
  &-logo {
    background: var(--logo-url);
    background-size: 100% 100%;
    width: 135.86px;
    height: 24px;
    margin: 15px auto 15px auto;
    z-index: 999;
  }
  .nav-toggle-label {
    background: var(--toggle-url);
    background-size: 100% 100%;
    width: 20px;
    height: 20px;
    position: absolute;
    top: 0%;
    margin-top: 16px;
  }
  #nav-toggle {
    display: none;
  }
  #nav-toggle:checked ~ .nav {
    transform: scale(1, 1);
    transform-origin: top;
    transition: transform 0.3s ease-out;
  }
  .nav {
    display: block;
    transform: scale(1, 0);
    background: var(--bg);
    &-item {
      margin-top: 24px;
      padding: 24px auto 24px auto;
    }
    &-link {
      color: var(--text-black);
    }
    hr {
      background-color: var(--text-black);
    }
    .option-img-wrapper {
      margin: 24px auto 24px auto;
      padding-bottom: 24px;
      width: 152px;
      display: flex;
      justify-content: space-between;
      .search {
        background: var(--search-url);
      }
      .cart {
        background: var(--cart-url);
      }
      .darkmode-toggle {
        cursor: pointer;
        background: var(--darkmode-toggle-url);
      }
      .search,
      .cart,
      .darkmode-toggle {
        background-size: 100% 100%;
        width: 24px;
        height: 24px;
      }
      #darkmode {
        display: none;
      }
    }
  }
}

@media screen and (min-width: 1100px) {
  .header {
    width: 77%;
    left: 11.5%;
    height: 60px;
    &-logo {
      width: 169.83px;
      height: 30px;
      margin-top: 15px;
    }
    .nav-toggle-label {
      display: none;
    }
    .nav {
      position: absolute;
      top: 15px;
      left: 0%;
      transform: scale(1, 1);
      height: 60px;
      width: 100%;
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      grid-gap: 30px;
      background: transparent;
      &-select {
        grid-column: 1/5;
      }
      &-list {
        height: 60px;
        display: flex;
        justify-content: space-between;
      }
      &-item {
        margin-top: 0;
      }
      &-link {
        padding: 4px 0 0 0;
        font-size: 16px;
      }
      &-option {
        grid-column: 9/13;
      }
      hr {
        display: none;
      }
      .option-img-wrapper {
        width: 180px;
        margin-top: 4px;
        margin-right: 0;
        display: flex;
        justify-content: space-between;
        .search,
        .cart,
        .darkmode-toggle {
          margin-left: 30px;
        }
      }
    }
  }
}
</style>