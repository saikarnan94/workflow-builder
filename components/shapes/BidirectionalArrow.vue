<template>
  <svg class="shape bidirectional-arrow" viewBox="0 0 100 100">
    <line x1="10" y1="50" x2="90" y2="50" stroke="black" stroke-width="2" />
    <polygon points="90,40 90,60 110,50" fill="black" />
    <polygon points="10,40 10,60 -10,50" fill="black" />
  </svg>
</template>

<script>
import main from '@/assets/main.css';
export default {
  name: 'BidirectionalArrow'
};
</script>

<style scoped>
.bidirectional-arrow {
  min-width: 50px;
  min-height: 50px;
}
</style>
