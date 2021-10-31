<template>
  <div class="control" id="left-control">
    <div class="left-button-wrapper">
      <!-- <input :style="{visibility: showMore ? 'visible' : 'hidden'}" ... > -->
      <button @click.prevent="prevStep(), scrollTop()" class="left-prev" id="left-prev" :style="{visibility: (currentStep === 0) ? 'hidden' : 'visible'}">
        ← 上一步
      </button>
      <button v-if="currentStep<2"
       @click.prevent="nextStep(), scrollTop()"
        class="left-next" 
        id="left-next">
        下一步 →</button>
      <button v-else
       @click.prevent="nextStep(), scrollTop()"
        class="left-next" 
        id="left-next"
        :disabled="currentStep>2">
        送出訂單</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    currentStep: {
      type: Number,
      required: true
    }
  },
  methods: {
    nextStep() {
      this.$emit('nextStep')
    },
    prevStep() {
      this.$emit('prevStep')
    },
    scrollTop() {
      window.scrollTo(0, 0)
    }
  }
}
</script>

<style>
.left-button-wrapper {
  margin-top: 50px;
  border-top: 1px solid var(--step-grey);
  display: flex;
  justify-content: space-between;
}
button {
  margin-top: 24px;
  height: 46px;
  border-radius: 8px;
  border: none;
  cursor: pointer;
}
.left-prev {
  background: none;
  color: var(--text-black);
}
.left-next {
  width: 184px;
  background: var(--button-pink);
  color: white;
}
</style>