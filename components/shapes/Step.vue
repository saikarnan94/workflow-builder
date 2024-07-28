<template>
  <svg class="shape step" viewBox="0 0 100 100">
    <rect width="100" height="100" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'Step'
};
</script>

<style lang="scss" scoped>

$step-fill: #fcd19c;

.step {
  min-width: 100px;
  min-height: 100px;
}
rect {
  fill: $step-fill;
  stroke: black;
  stroke-width: 1;
}
</style>
