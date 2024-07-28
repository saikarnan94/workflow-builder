<template>
  <svg class="shape rightarrow" viewBox="0 0 100 100">
    <line x1="10" y1="50" x2="70" y2="50" stroke="black" stroke-width="2" />
    <polygon points="70,40 70,60 90,50" fill="black" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'RightArrow'
};
</script>

<style scoped>
.rightarrow {
  min-width: auto;
  min-height: auto;
}
</style>