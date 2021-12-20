<script>
import Vue from "vue";
import VueMzcSteps from "@/vue-mzc-steps.vue";
import "../src/vue-mzc-steps.css";
import "./serve.css";

export default Vue.extend({
  name: "ServeDev",
  components: {
    VueMzcSteps,
  },
  data() {
    return {
      step: 2,
      steps: [
        {
          id: 1,
          title: "Account",
        },
        {
          id: 2,
          title: "Delivery",
        },
        {
          id: 3,
          title: "Payment",
        },
        {
          id: 4,
          title: "Confirm",
        },
      ],
    };
  },
  methods: {
    prev() {
      if (this.step > 1) {
        this.step = this.step - 1;
      }
    },
    next() {
      if (this.step < this.steps.length) {
        this.step = this.step + 1;
      }
    },
  },
});
</script>

<template>
  <div id="app">
    <div class="row">
      <vue-mzc-steps :items="steps" :step="step" />
    </div>
    <div class="row">
      <button @click="prev" :disable="step === 1">prev</button>
      <button @click="next" :disable="step === steps.length">next</button>
    </div>
  </div>
</template>