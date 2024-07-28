<template>
  <svg class="shape decision" viewBox="0 0 100 100">
    <polygon points="50,15 85,50 50,85 15,50" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'Decision'
};
</script>

<style lang="scss" scoped>

$decision-fill: #e4ccff;

.decision {
  min-width: 100px;
  min-height: 100px;
}
polygon {
  fill: $decision-fill;
  stroke: black;
  stroke-width: 1;
}
</style>
