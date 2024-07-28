<template>
  <svg class="shape downarrow" viewBox="0 0 100 100">
    <line x1="50" y1="10" x2="50" y2="70" stroke="black" stroke-width="2" />
    <polygon points="40,70 60,70 50,90" fill="black" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'DownArrow'
};
</script>

<style scoped>
.downarrow {
  min-width: auto;
  min-height: auto;
}
</style>