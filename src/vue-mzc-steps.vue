<script>
export default /*#__PURE__*/ {
  name: "VueMzcSteps",
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

<style>
:root {
  --vue-mzc-steps-gap: 24px;
  --vue-mzc-steps-line-width: 1px;
  --vue-mzc-steps-circle-border-width: 1px;
  --vue-mzc-steps-circle-size: 40px;
  --vue-mzc-steps-primary-color: #306ec4;
  --vue-mzc-steps-background-color: #ffffff;
  --vue-mzc-steps-border-disable-color: #bdbdbd;
  --vue-mzc-steps-circle-active-color: #ffffff;
  --vue-mzc-steps-text-disable-color: #acacac;
  --vue-mzc-steps-text-active-color: #030303;
}
.vue-mzc-steps {
  display: flex;
}
.vue-mzc-steps__item {
  padding-left: 24px;
  padding-right: 24px;
  padding-left: var(--vue-mzc-steps-gap);
  padding-right: var(--vue-mzc-steps-gap);
  position: relative;
}
.vue-mzc-steps__item:first-child {
  padding-left: 0;
}
.vue-mzc-steps__item:last-child {
  padding-right: 0;
}
.vue-mzc-steps-line {
  position: absolute;
  top: 20px;
  top: calc(
    (var(--vue-mzc-steps-circle-size) / 2) -
      (var(--vue-mzc-steps-line-width) / 2)
  );
  width: 50%;
  height: 1px;
  height: var(--vue-mzc-steps-line-width);
  background-color: #bdbdbd;
  background-color: var(--vue-mzc-steps-border-disable-color);
  transition: background-color 0.25s ease-in-out;
}
.vue-mzc-steps-line--filled {
  background-color: #306ec4;
  background-color: var(--vue-mzc-steps-primary-color);
}
.vue-mzc-steps-line--left {
  left: 0;
}
.vue-mzc-steps-line--right {
  right: 0;
}
.vue-mzc-steps__item:first-child .vue-mzc-steps-line--left,
.vue-mzc-steps__item:last-child .vue-mzc-steps-line--right {
  display: none;
}
.vue-mzc-steps-item__circle {
  margin-left: auto;
  margin-right: auto;
  margin-bottom: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  width: 40px;
  height: 40px;
  width: var(--vue-mzc-steps-circle-size);
  height: var(--vue-mzc-steps-circle-size);
  background-color: #ffffff;
  background-color: var(--vue-mzc-steps-background-color);
  border-width: 1px;
  border-width: var(--vue-mzc-steps-circle-border-width);
  border-style: solid;
  border-color: #bdbdbd;
  border-color: var(--vue-mzc-steps-border-disable-color);
  border-radius: 50%;
  box-shadow: 0 0 0 4px #ffffff;
  box-shadow: 0 0 0 4px var(--vue-mzc-steps-background-color);
  transition: background-color 0.25s ease-in-out, border-color 0.25s ease-in-out;
}
.vue-mzc-steps-item {
  font-weight: 500;
  color: #acacac;
  color: var(--vue-mzc-steps-text-disable-color);
  transition: color 0.25s ease-in-out;
}
.steps-item__title {
  text-align: center;
}
.vue-mzc-steps-item--active .vue-mzc-steps-item__circle {
  font-weight: 700;
}
.vue-mzc-steps-item--active .vue-mzc-steps-item__circle,
.vue-mzc-steps-item--complete .vue-mzc-steps-item__circle {
  color: #ffffff;
  color: var(--vue-mzc-steps-circle-active-color);
}
.vue-mzc-steps-item--active .vue-mzc-steps-item__title,
.vue-mzc-steps-item--complete .vue-mzc-steps-item__title {
  color: #030303;
  color: var(--vue-mzc-steps-text-active-color);
}
.vue-mzc-steps-item--active .vue-mzc-steps-item__circle,
.vue-mzc-steps-item--complete .vue-mzc-steps-item__circle {
  background-color: #306ec4;
  background-color: var(--vue-mzc-steps-primary-color);
  border-color: #306ec4;
  border-color: var(--vue-mzc-steps-primary-color);
}
</style>