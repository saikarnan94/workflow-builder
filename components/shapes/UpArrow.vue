<template>
  <svg class="shape uparrow" viewBox="0 0 100 100">
    <line x1="50" y1="90" x2="50" y2="30" stroke="black" stroke-width="2" />
    <polygon points="40,30 60,30 50,10" fill="black" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'UpArrow'
};
</script>

<style scoped>
.uparrow {
  min-width: auto;
  min-height: auto;
}
</style>