<template>
  <svg class="shape terminal no-border" viewBox="0 0 100 100">
    <circle cx="50" cy="50" r="50" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'Terminal'
};
</script>

<style lang="scss" scoped>

$circle-fill: #bce3ff;

.terminal {
  min-width: 100px;
  min-height: 100px;
  fill: $circle-fill;
  stroke: black;
  stroke-width: 1;
}
.no-border {
  border: none !important;
  outline: none !important;
}
</style>
