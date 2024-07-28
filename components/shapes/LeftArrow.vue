<template>
  <svg class="shape leftarrow" viewBox="0 0 100 100">
    <line x1="30" y1="50" x2="90" y2="50" stroke="black" stroke-width="2" />
    <polygon points="30,40 30,60 10,50" fill="black" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'LeftArrow'
};
</script>

<style scoped>
.leftarrow {
  min-width: auto;
  min-height: auto;
}
</style>