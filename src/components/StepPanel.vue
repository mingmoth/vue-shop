<template>
  <div class="step-container" id="step-container">
    <div
      :class="[
        'step',
        { checked: currentStep > 0 },
        { active: currentStep === 0 },
      ]"
    >
      <div class="circle" id="step-one"></div>
      <div class="label" id="step-one-label">寄送地址</div>
    </div>
    <div
      v-if="currentStep > 0"
      id="connect-one-completed"
      class="connect"
    ></div>
    <div v-else id="connect" class="connect"></div>
    <div
      :class="[
        'step',
        { checked: currentStep > 1 },
        { active: currentStep === 1 },
      ]"
    >
      <div class="circle" id="step-two"></div>
      <div class="label" id="step-two-label">運送方式</div>
    </div>
    <div
      v-if="currentStep > 1"
      id="connect-two-completed"
      class="connect"
    ></div>
    <div v-else id="connect" class="connect"></div>
    <div
      :class="[
        'step',
        { checked: currentStep > 2 },
        { active: currentStep === 2 },
      ]"
    >
      <div class="circle" id="step-three"></div>
      <div class="label" id="step-three-label">付款資訊</div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    currentStep: {
      type: Number,
      required: true,
    },
  },
};
</script>

<style lang="scss">
.step-container {
  margin-top: 24px;
  display: flex;
  justify-content: space-between;
  height: 24px;
  .step {
    display: flex;
    color: var(--step-grey);
    .circle {
      border: 1.5px solid var(--step-grey);
      border-radius: 50%;
      width: 24px;
      height: 24px;
      font-size: 16px;
      color: var(--step-grey);
      position: relative;
      &::after {
        position: absolute;
        top: -4%;
        left: 30%;
      }
    }
    &.active .circle {
      border: 1px solid var(--text-black);
      color: var(--text-black);
    }
    &.checked .circle {
      background-color: var(--text-black);
      color: var(--bg);
    }
    #step-one::after {
      content: "1";
    }
    #step-two::after {
      content: "2";
    }
    #step-three::after {
      content: "3";
    }
    &.checked #step-one::after,
    &.checked #step-two::after,
    &.checked #step-three::after {
      content: "\2714";
      left: 22%;
    }
    .label {
      display: none;
    }
    &.active,
    &.checked .label {
      color: var(--text-black);
    }
  }
  .connect {
    flex: 1;
    height: 1px;
    background-color: var(--step-grey);
    margin: auto 12px auto 12px;
  }
  #connect-one-completed,
  #connect-two-completed {
    background-color: var(--text-black);
  }
}

@media screen and (min-width: 1110px) {
  .step-container {
    margin-top: 32px;
    .step {
      .label {
        display: block;
        margin-left: 8px;
      }
    }
  }
}
</style>