<template>
  <form action="" id="pay-form">
    <div :class="['part', { 'd-none': currentStep !== 0 }]">
      <p class="part-title">寄送地址</p>
      <div id="pay" class="part-one">
        <div class="call">
          <label for="pay-call">稱謂</label>
          <input
            type="input"
            class="pay-call"
            id="pay-call"
            placeholder="請選擇稱謂"
            required
          />
        </div>
        <div class="name">
          <label for="pay-name">姓名</label>
          <input
            type="input"
            class="pay-name"
            id="pay-name"
            placeholder="請輸入姓名"
            required
          />
        </div>
      </div>
      <div id="pay" class="part-two">
        <div class="tel">
          <label for="pay-tel">行動電話</label>
          <input
            type="input"
            class="pay-tel"
            id="pay-tel"
            placeholder="請輸入行動電話"
            required
          />
        </div>
        <div class="email">
          <label for="pay-email">Email</label>
          <input
            type="input"
            class="pay-email"
            id="pay-email"
            placeholder="請輸電子郵件"
            required
          />
        </div>
      </div>
      <div id="pay" class="part-three">
        <div class="county">
          <label for="pay-county">縣市</label>
          <select name="pay-county" id="pay-county" required>
            <option value="" selected disabled>請選擇縣市</option>
          </select>
        </div>
        <div class="address">
          <label for="pay-address">地址</label>
          <input
            type="input"
            class="pay-address"
            id="pay-address"
            placeholder="請輸入地址"
            required
          />
        </div>
      </div>
    </div>
    <div :class="['part', { 'd-none': currentStep !== 1 }]">
      <p class="part-title">運送方式</p>
      <div class="radio-wrapper">
        <div class="ship-wrapper">
          <input
            type="radio"
            name="delivery"
            id="standard"
            @click="setDelivery('standard')"
          />
          <div class="ship">
            <div class="ship-left">
              <p class="ship-title">標準運送</p>
              <p class="ship-duration">約3~7個工作天</p>
            </div>
            <div class="ship-right">
              <p class="ship-price">免費</p>
            </div>
          </div>
        </div>
        <div class="ship-wrapper">
          <input
            type="radio"
            name="delivery"
            id="dhl"
            @click="setDelivery('dhl')"
          />
          <div class="ship">
            <div class="ship-left">
              <p class="ship-title">DHL貨運</p>
              <p class="ship-duration">48小時內送達</p>
            </div>
            <div class="ship-right">
              <p class="ship-price">$500</p>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div :class="['part', { 'd-none': currentStep < 2 }]">
      <p class="part-title">付款資訊</p>
      <div id="pay" class="part-five">
        <div class="card-name">
          <label for="cardName">持卡人姓名</label>
          <input
            type="input"
            name="cardName"
            id="cardName"
            placeholder="請輸入持卡人姓名"
            required
          />
        </div>
      </div>
      <div id="pay" class="part-six">
        <div class="number">
          <label for="cardNumber">卡號</label>
          <input
            type="input"
            name="cardNumber"
            id="cardNumber"
            placeholder="1111 2222 3333 4444"
            required
          />
        </div>
      </div>
      <div id="pay" class="part-seven">
        <div class="date">
          <label for="cardDate">有效期限</label>
          <input
            type="input"
            name="cardDate"
            id="cardDate"
            placeholder="MM/YY"
            required
          />
        </div>
        <div class="confirm">
          <label for="cardConfirm">CVC / CCV</label>
          <input
            type="input"
            name="cardConfirm"
            id="cardConfirm"
            placeholder="123"
            required
          />
        </div>
      </div>
    </div>
  </form>
</template>

<script>
export default {
  props: {
    currentStep: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {};
  },
  methods: {
    setDelivery(ship) {
      this.$emit("setDelivery", ship);
    },
  },
};
</script>

<style lang="scss">
.part {
  text-align: start;
  margin-top: 24px;
  &-title {
    font-size: 24px;
    font-weight: 700;
    margin: 0 auto 0 0;
    color: var(--text-black);
  }
  #pay {
    margin-top: 24px;
  }
  &-one,
  &-seven {
    display: grid;
    grid-template-columns: repeat(13, 1fr);
    .call {
      grid-column: 1/6;
    }
    .name {
      grid-column: 7/14;
    }
    .date {
      grid-column: 1/7;
    }
    .confirm {
      grid-column: 8/14;
    }
  }
  .email,
  .address {
    margin-top: 16px;
  }
  .ship-wrapper {
    display: flex;
    align-items: center;
    margin-top: 24px;
    height: 60px;
    position: relative;
    .ship {
      flex: 1;
      padding: 11px 20px 11px 20px;
      display: flex;
      flex-flow: row nowrap;
      justify-content: space-between;
      color: var(--text-black);
      height: 60px;
      &-title {
        margin-bottom: 0;
        font-size: 14px;
        font-weight: 700;
      }
      &-duration,
      &-price {
        font-size: 12px;
      }
    }
  }
}

input[type="radio"] {
  -webkit-appearance: none;
  width: 20px;
  height: 20px;
  border-radius: 50%;
  cursor: pointer;
  margin-left: 20px;
  &:checked {
    box-shadow: inset 0 0 0 7px var(--text-black);
  }
  &::after {
    content: "";
    position: absolute;
    top: 0%;
    left: 0%;
    width: 100%;
    height: 100%;
    border: 1px solid var(--step-grey);
    border-radius: 4px;
  }
  &:hover::after {
    border: 1px solid var(--text-black);
  }
  &:checked::after {
    border: 1px solid var(--text-black);
  }
}

@media screen and (min-width: 1110px) {
  .part {
    margin-top: 34px;
    height: 288px;
    #pay {
      display: grid;
      grid-template-columns: repeat(13, 1fr);
    }
    .tel {
      grid-column: 1/7;
    }
    .email {
      margin-top: 2px;
      grid-column: 8/14;
    }
    .county {
      grid-column: 1/6;
    }
    .address {
      margin-top: 0;
      grid-column: 7/14;
    }
    .card-name,
    .number {
      grid-column: 1/9;
    }
  }
}
</style>