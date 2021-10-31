<template>
  <div class="summary">
    <p class="summary-title">購物籃</p>
    <div class="jean">
      <img
        src="https://i.imgur.com/MRdy9z2.png"
        alt="damaged slim jean"
        class="jean-photo"
      />
      <div class="jean-wrapper">
        <div class="jean-wrapper-left">
          <div class="jean-wrapper-title">破壞補丁修身牛仔褲</div>
          <div class="count">
            <button
              class="minus"
              :disabled="this.jeanOneAmount < 1"
              @click.prevent="jeanOneMinus"
            ></button>
            <div class="count-number">{{ jeanOneAmount }}</div>
            <button class="plus" @click.prevent="jeanOnePlus"></button>
          </div>
        </div>
        <div class="jean-wrapper-right">
          <p class="cost">${{ jeanOneSum }}</p>
        </div>
      </div>
    </div>
    <div class="jean">
      <img
        src="https://i.imgur.com/a0BP98T.png"
        alt="plain stright jean"
        class="jean-photo"
      />
      <div class="jean-wrapper">
        <div class="jean-wrapper-left">
          <div class="jean-wrapper-title">刷色直筒牛仔褲</div>
          <div class="count">
            <button
              class="minus"
              :disabled="this.jeanTwoAmount < 1"
              @click.prevent="jeanTwoMinus"
            ></button>
            <div class="count-number">{{ jeanTwoAmount }}</div>
            <button class="plus" @click.prevent="jeanTwoPlus"></button>
          </div>
        </div>
        <div class="jean-wrapper-right">
          <p class="cost">${{ jeanTwoSum }}</p>
        </div>
      </div>
    </div>
    <div class="ship-card">
      <p class="ship-card-title">運費</p>
      <p class="ship-card-price">{{ delivery }}</p>
    </div>
    <div class="ship-card">
      <p class="ship-card-title">小計</p>
      <p class="ship-card-price">${{ orderSum }}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    shipType: {
      type: String,
      required: true,
    },
    shipPrice: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      delivery: "免費",
      jeanOne: 3999,
      jeanTwo: 1299,
      jeanOneAmount: 1,
      jeanTwoAmount: 1,
      jeanOneSum: 3999,
      jeanTwoSum: 1299,
    };
  },
  computed: {
    orderSum() {
      return this.jeanOneSum + this.jeanTwoSum + this.shipPrice;
    },
  },
  methods: {
    jeanOnePlus() {
      this.jeanOneAmount += 1;
    },
    jeanTwoPlus() {
      this.jeanTwoAmount += 1;
    },
    jeanOneMinus() {
      this.jeanOneAmount -= 1;
    },
    jeanTwoMinus() {
      this.jeanTwoAmount -= 1;
    },
  },
  watch: {
    shipType() {
      console.log(this.shipType);
      if (this.shipType === "standard") {
        return (this.delivery = "免費");
      } else if (this.shipType === "dhl") {
        return (this.delivery = `$ ${this.shipPrice}`);
      }
    },
    jeanOneAmount() {
      return (this.jeanOneSum = this.jeanOne * this.jeanOneAmount);
    },
    jeanTwoAmount() {
      return (this.jeanTwoSum = this.jeanTwo * this.jeanTwoAmount);
    },
  },
};
</script>

<style lang="scss">
.summary {
  text-align: start;
  margin-top: 32px;
  border: 1px solid var(--step-grey);
  border-radius: 8px;
  padding: 18px 16px 0px 16px;
  background-color: var(--cart-bg);
  color: var(--text-black);
  &-title {
    display: none;
  }
  .jean {
    display: flex;
    justify-content: space-between;
    margin-bottom: 18px;
    height: 100px;
    &-photo {
      width: 100px;
      height: 100px;
    }
    &-wrapper {
      text-align: end;
      &-right {
        margin-top: 12px;
        font-weight: 700;
      }
    }
    .count {
      display: flex;
      justify-content: end;
      align-items: center;
      margin-top: 18px;
      height: 26px;
      .minus,
      .plus {
        background-size: 100% 100%;
        width: 26px;
        height: 26px;
      }
      .minus {
        position: relative;
        width: 26px;
        height: 26px;
        background-color: #f0f0f5;
        margin-right: 18px;
        border-radius: 50%;
        cursor: pointer;
        &::after {
          position: absolute;
          content: "-";
          font-size: 28px;
          top: -36%;
          left: 30%;
        }
      }
      .plus {
        position: relative;
        width: 26px;
        height: 26px;
        background-color: #f0f0f5;
        margin-left: 18px;
        border-radius: 50%;
        cursor: pointer;
        &::after {
          position: absolute;
          content: "+";
          font-size: 22px;
          top: -12%;
          left: 25%;
        }
      }
    }
  }
  .ship-card {
    display: flex;
    justify-content: space-between;
    border-top: 1px solid var(--footer-text-grey);
    font-size: 14px;
    padding-top: 16px;
    padding-bottom: 8px;
    &-price {
      font-weight: 700;
    }
  }
}

@media screen and (min-width: 1110px) {
  .summary {
    margin-top: 34px;
    padding: 18px 24px 0px 24px;
    &-title {
      display: block;
      font-size: 18px;
      font-weight: 700px;
      color: var(--text-black);
      margin-top: 14px;
    }
    .jean {
      margin-bottom: 32px;
      &-wrapper {
        flex: 1;
        margin-left: 21px;
        display: flex;
        justify-content: space-between;
        &-title {
          margin-top: 0;
        }
        &-left {
          text-align: start;
        }
        &-right {
          margin-top: 0;
          .cost {
            margin-top: 0;
          }
        }
      }
      .count {
        justify-content: start;
      }
    }
  }
}
</style>