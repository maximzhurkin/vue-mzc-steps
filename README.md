# vue-mzc-steps
Simple Vue2 steps component

![](demo.gif)

[Online demo](https://codesandbox.io/s/angry-morse-byc4p)

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