<template>
  <div class="main">
    <p class="page-title">結帳</p>
    <div class="content">
      <div class="left">
        <StepPanel :currentStep="currentStep" />
        <Form :currentStep="currentStep" @setDelivery="deliverySet" />
        <div class="left-control">
          <LeftControl
            :currentStep="currentStep"
            @prevStep="stepMinus"
            @nextStep="stepPlus"
          />
        </div>
      </div>
      <div class="right">
        <CartPanel :shipType="shipType" :shipPrice="shipPrice" />
        <div class="right-control">
          <RightControl
            :currentStep="currentStep"
            @prevStep="stepMinus"
            @nextStep="stepPlus"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import StepPanel from "../components/StepPanel.vue";
import Form from "../components/Form.vue";
import CartPanel from "../components/CartPanel.vue";
import LeftControl from "../components/LeftControl.vue";
import RightControl from "../components/RightControl.vue";
export default {
  components: {
    StepPanel,
    Form,
    CartPanel,
    LeftControl,
    RightControl,
  },
  data() {
    return {
      currentStep: 0,
      shipType: "",
      shipArray: { standard: 0, dhl: 500 },
      shipPrice: 0,
    };
  },
  methods: {
    stepPlus() {
      this.currentStep += 1;
    },
    stepMinus() {
      this.currentStep -= 1;
    },
    deliverySet(ship) {
      this.shipType = ship;
      this.shipPrice = this.shipArray[ship];
    },
  },
};
</script>

<style lang="scss">
.main {
  width: 90%;
  margin: 0 auto;
  padding-top: 60px;
  .page-title {
    margin: 16px auto 0px 0px;
    text-align: start;
    font-size: 24px;
    font-weight: 700;
    color: var(--text-black);
  }
  .left-control {
    display: none;
  }
}

@media screen and (min-width: 1110px) {
  .main {
    width: 77%;
    .page-title {
      margin: 70px auto 0px 0px;
      text-align: start;
      font-size: 32px;
    }
    .content {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      grid-gap: 30px;
    }
    .left {
      grid-column: 1/7;
    }
    .left-control {
      display: block;
    }
    .right {
      grid-column: 8/13;
    }
    .right-control {
      display: none;
    }
  }
}
</style>