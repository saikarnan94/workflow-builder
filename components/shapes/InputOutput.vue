<template>
  <svg class="shape inputoutput" viewBox="0 0 100 100">
    <polygon points="20,0 100,0 80,100 0,100" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'InputOutput'
};
</script>

<style lang="scss" scoped>
$inputoutput-fill: #bce3ff;

.inputoutput {
  min-width: 100px;
  min-height: 100px;
  fill: $inputoutput-fill;
  stroke: black;
  stroke-width: 1;
}
</style>
