<template>
  <v-app>
    <Sidebar @drag-start="handleDragStart" />
    <v-main>
      <Canvas ref="canvas" />
    </v-main>
  </v-app>
</template>

<script>
import Sidebar from '@/components/Sidebar.vue';
import Canvas from '@/components/Canvas.vue';

export default {
  components: {
    Sidebar,
    Canvas,
  },
  methods: {
    handleDragStart(component) {
      this.$refs.canvas.$el.ondragstart = (event) => {
        event.dataTransfer.setData('component', JSON.stringify(component));
      };
    },
  },
};
</script>
