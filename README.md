# vue-mzc-steps
Simple Vue2 steps component

![](demo.gif)

[Online demo](https://codesandbox.io/s/angry-morse-byc4p?file=/src/App.vue)

## Installation
```sh
npm install vue-mzc-steps --save
```

## Usage
```js
import VueMzcSteps from "vue-mzc-steps";

export default {
  components: {
    VueMzcSteps,
  },
  data() {
    return {
      step: 1, // current step
      steps: [
        { id: 1, title: "Account" },
        { id: 2, title: "Delivery" },
        { id: 3, title: "Payment" },
        { id: 4, title: "Confirm" },
      ],
    };
  },
};
```
```html
<vue-mzc-steps :items="steps" :step="step" />
```
## Customize
```css
.vue-mzc-steps {
  --vue-mzc-steps-gap: 24px;
  --vue-mzc-steps-line-width: 1px;
  --vue-mzc-steps-circle-border-width: 1px;
  --vue-mzc-steps-circle-size: 40px;
  --vue-mzc-steps-primary-color: #306EC4;
  --vue-mzc-steps-background-color: #ffffff;
  --vue-mzc-steps-border-disable-color: #bdbdbd;
  --vue-mzc-steps-circle-active-color: #ffffff;
  --vue-mzc-steps-text-disable-color: #acacac;
  --vue-mzc-steps-text-active-color: #030303;
}
```