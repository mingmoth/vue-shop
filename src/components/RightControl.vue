<template>
  <div class="control" id="right-control">
    <div class="right-button-wrapper">
      <button 
        @click.prevent="prevStep(), scrollTop()"
        :class="['right-prev', {'d-none': currentStep === 0}]" 
        id="right-prev">
        ← 上一步
      </button>
      <button v-if="currentStep<2" @click.prevent="nextStep(), scrollTop()" class="right-next" id="right-next">下一步 →</button>
      <button v-else
       @click.prevent="nextStep(), scrollTop()"
        class="right-next" 
        id="right-next">
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
.right-button-wrapper {
  margin-top: 32px;
  display: flex;
  border-top: 1px solid var(--step-grey);
}
button {
  margin-top: 24px;
  border: none;
  margin-bottom: 24px;
}
.right-prev {
  width: 55%;
  text-align: start;
  background: none;
  color: var(--text-black);
}
.right-next {
  flex: 1;
  background: var(--button-pink);
  color: white;
}
</style>