<template>
  <svg class="shape process" viewBox="0 0 100 100">
    <rect width="100" height="50" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'Process'
};
</script>

<style lang="scss" scoped>
$process-fill: #aff4c6;

.process {
  min-width: auto;
  min-height: auto;
}
rect {
  fill: $process-fill;
  stroke: black;
  stroke-width: 1;
}
</style>
