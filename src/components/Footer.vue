<template>
  <footer>
    <div class="footer">
      <div class="footer-logo"></div>
      <div class="footer-service">
        <div class="footer-title">客戶服務</div>
        <div class="footer-content">
          <p id="p" class="footer-des">運送說明</p>
          <p id="p" class="footer-back">退換貨相關</p>
          <p id="p" class="footer-pay">付款資訊</p>
          <p id="p" class="footer-faq">FAQ</p>
        </div>
      </div>
      <div class="footer-about">
        <div class="footer-title">關於我們</div>
        <div class="footer-content">
          <p id="p" class="footer-story">品牌故事</p>
          <p id="p" class="footer-media">媒體連繫</p>
          <p id="p" class="footer-kit">Press Kit</p>
        </div>
      </div>
      <div class="footer-info">
        <div class="footer-title">資訊</div>
        <div class="footer-content">
          <p id="p" class="footer-private">隱私權政策</p>
          <p id="p" class="footer-cookie">Cookie</p>
          <p id="p" class="footer-gdpr">GDPR</p>
        </div>
      </div>
      <div class="footer-follow">
        <div class="footer-title">ALPHA Shop</div>
        <div class="footer-content">
          <p id="p" class="footer-des">+886 02123-45678</p>
          <div class="footer-image-container">
            <img
              src="https://i.imgur.com/DBVdQnm.png"
              alt="facebook icon"
              class="fb"
            />
            <img
              src="https://i.imgur.com/Dl0kI5T.png"
              alt="instagram icon"
              class="ig"
            />
            <img
              src="https://i.imgur.com/MABBtn8.png"
              alt="telephone icon"
              class="phone"
            />
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<style lang="scss">
footer {
  margin-top: 120px;
  background: var(--footer-grey);
}
.footer {
  margin: 0 auto 0 auto;
  width: 77%;
  display: flex;
  justify-content: space-between;
  padding-top: 64px;
  text-align: start;
  &-logo {
    background: var(--logo-url);
    background-size: 100% 100%;
    margin-top: 62px;
    width: 175.49px;
    height: 31px;
  }
  &-title {
    font-size: 24px;
    font-weight: 700;
    margin-bottom: 24px;
    color: var(--text-black);
  }
  p {
    font-size: 16px;
    color: var(--footer-text-grey);
    margin: 0 0 8px 0;
  }
  &-image-container {
    display: flex;
    flex-flow: row nowrap;
    justify-content: space-between;
    width: 104px;
    margin-top: 8px;
    .fb {
      width: 9.33px;
      height: 20px;
    }
    .ig,
    .phone {
      width: 20px;
      height: 20px;
    }
  }
}
</style>