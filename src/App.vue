<template>
  <div id="app">
    <Navbar />
    <main role="main">
      <router-view/>
    </main>
    <footer>
      <Footer />
    </footer>
  </div>
</template> 

<script>
import "bootstrap"
import 'bootstrap/dist/css/bootstrap.min.css'
import Navbar from '../src/components/Navbar.vue'
import Footer from '../src/components/Footer.vue'
export default {
  name: 'App',
  components: {
    Navbar,
    Footer
  }
}
</script>

<style>
#app {
  font-family: Noto Sans TC, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin-top: 0;
}
*,
*::before,
*::after {
  box-sizing: border-box;
}
ul,
li {
  list-style-type: none; /* 拿掉前方圈圈 */
  margin: 0;
  padding: 0;
}
a {
  text-decoration: none; /* 拿掉底線 */
}

:root {
  --true-black: #000000;
  --text-black: #2a2a2a;
  --footer-grey: #e5e5e5;
  --footer-text-grey: #808080;
  --step-grey: #afb1bd;
  --step-checked:#2a2a2a;
  --border-grey: #f0f0f5;
  --input-grey: #999999;
  --cart-bg: #ffffff;
  --bg: #ffffff;
  --button-pink: #f67599;
  --logo-url: url("https://i.imgur.com/TAtCacN.png");
  --toggle-url: url("https://i.imgur.com/qmuTsQ2.png");
  --search-url: url("https://i.imgur.com/3Gwb3ON.png");
  --cart-url: url("https://i.imgur.com/P0nmeEj.png");
  --darkmode-toggle-url: url("https://i.imgur.com/CJKanuv.png");
  --minus-url: url("https://i.imgur.com/HHP48cJ.png");
  --plus-url: url("https://i.imgur.com/CY9ZtY4.png");
}
[data-theme="dark"] {
  --true-black: #000000;
  --text-black: #ffffff;
  --footer-grey: #333333;
  --step-grey: #383838;
  --step-checked: #333333;
  --border-grey: #383838;
  --input-grey: #5e5e5e;
  --cart-bg: #383838;
  --bg: #000000;
  --logo-url: url("https://i.imgur.com/ZAGlPQF.png");
  --toggle-url: url("https://i.imgur.com/2FaonVe.png");
  --search-url: url("https://i.imgur.com/m398oYJ.png");
  --cart-url: url("https://i.imgur.com/mRtsxz4.png");
  --darkmode-toggle-url: url("https://i.imgur.com/jYhM92K.png");
  --minus-url: url("https://i.imgur.com/7mdtOMh.png");
  --plus-url: url("https://i.imgur.com/eTm2P2X.png");
}
body {
  background: var(--bg);
  margin: 0;
}
footer {
  display: none;
}
label {
  display: block;
  font-size: 12px;
  margin-bottom: 8px;
  color: var(--footer-text-grey);
}
input,
select {
  border: 1px solid var(--step-grey);
  height: 40px;
  width: 100%;
  border-radius: 4px;
  font-size: 12px;
  padding: 12px;
  background: transparent;
}
input:hover, 
input:focus,
select:hover,
select:focus {
  border-color: var(--text-black);
}
@media screen and (min-width: 1110px) {
  footer {
    display: block;
  }
}
</style>
