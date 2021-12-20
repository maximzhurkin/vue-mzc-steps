<script>
export default /*#__PURE__*/ {
  name: "VueMzcSteps", // vue component name
  props: {
    items: {
      type: Array,
      default() {
        return [];
      },
    },
    step: {
      type: Number,
      default: 1,
    },
  },
  methods: {
    getStatus(stepId) {
      if (stepId === this.step) {
        return "active";
      }
      if (stepId < this.step) {
        return "complete";
      }
      return null;
    },
  },
};
</script>

<template>
  <div class="vue-mzc-steps">
    <div v-for="item in items" :key="item.id" class="vue-mzc-steps__item">
      <div
        class="vue-mzc-steps-line vue-mzc-steps-line--left"
        :class="step > item.id - 1 ? 'vue-mzc-steps-line--filled' : ''"
      ></div>
      <div
        class="vue-mzc-steps-line vue-mzc-steps-line--right"
        :class="step > item.id ? 'vue-mzc-steps-line--filled' : ''"
      ></div>
      <div
        class="vue-mzc-steps-item"
        :class="
          getStatus(item.id) ? `vue-mzc-steps-item--${getStatus(item.id)}` : ''
        "
      >
        <div class="vue-mzc-steps-item__circle">
          <span v-if="getStatus(item.id) == 'complete'">✔</span>
          <span v-else>{{ item.id }}</span>
        </div>
        <div class="vue-mzc-steps-item__title">{{ item.title }}</div>
      </div>
    </div>
  </div>
</template>
