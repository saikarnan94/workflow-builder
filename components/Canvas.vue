<template>
  <div>
    <v-app-bar app>
      <v-toolbar-title><h2>Workflow Builder</h2></v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn @click="clearCanvas" class="clear-btn toolbar-btn">Clear</v-btn>
      <v-btn @click="saveCanvas" class="save-btn toolbar-btn">Save</v-btn>
      <v-btn @click="loadCanvas" class="load-btn toolbar-btn">Load</v-btn>
    </v-app-bar>
    <div
      ref="canvas"
      class="canvas"
      @drop="drop"
      @dragover="handleDragEvent"
      @dragenter="handleDragEvent"
      @dragleave="handleDragEvent"
    >
      <vue-draggable-resizable
        v-for="(component, index) in droppedComponents"
        :key="index"
        :x="component.x"
        :y="component.y"
        :w="component.width"
        :h="component.height"
        @dragging="updatePosition($event, index)"
        @resizing="updateSize($event, index)"
        @mousedown="startDragging(component, $event)"
        :class="'no-border'"
        :resizable="true"
      >
        <component :is="component.type" 
                   :initialText="component.text"
                   @update:text="updateText(index, $event)" />
        <v-icon
          medium
          color="red"
          class="delete-btn"
          @click.stop="deleteComponent(index)"
        >
          mdi-delete-circle
        </v-icon>
      </vue-draggable-resizable>
      <div v-if="showNote" class="banner-note">
        <v-icon class="close-btn" @click="showNote = false">mdi-close</v-icon>
        <p>{{ noteText }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import VueDraggableResizable from 'vue-draggable-resizable';
import 'vue-draggable-resizable/dist/VueDraggableResizable.css';
import * as shapes from './shapes';

export default {
  components: {
    VueDraggableResizable,
    ...shapes
  },
  data() {
    return {
      droppedComponents: [],
      showNote: true, 
      noteText: 'Welcome to Workflow Builder! You can now drag and drop components from the palette on to the canvas to build your workflows!',
    };
  },
  methods: {
    drop(event) {
      event.preventDefault();
      const shape = JSON.parse(event.dataTransfer.getData('application/json'));
      const rect = this.$refs.canvas.getBoundingClientRect();
      const x = event.clientX - rect.left;
      const y = event.clientY - rect.top;
      console.log(shape, x, y);
      const componentType = shapes[shape.name];
      this.droppedComponents.push({
        type: componentType,
        shape,
        x,
        y,
        text: shape.name === 'TextBox' ? 'Enter text' : ''
      });
    },
    handleDragEvent(event) {
      event.preventDefault();
    },
    startDragging(component, event) {
      console.log('dragging starts');
      this.currentDragComponent = component;
      const rect = event.target.getBoundingClientRect();
      this.offsetX = event.clientX - rect.left;
      this.offsetY = event.clientY - rect.top;
      document.addEventListener('mousemove', this.dragging);
      document.addEventListener('mouseup', this.stopDragging);
    },
    dragging(event) {
      if (this.currentDragComponent) {
        const rect = this.$refs.canvas.getBoundingClientRect();
        this.currentDragComponent.x = event.clientX - rect.left - this.offsetX;
        this.currentDragComponent.y = event.clientY - rect.top - this.offsetY;
      }
    },
    stopDragging() {
      this.currentDragComponent = null;
      document.removeEventListener('mousemove', this.dragging);
      document.removeEventListener('mouseup', this.stopDragging);
    },
    updatePosition(event, index) {
      this.$set(this.droppedComponents, index, {
        ...this.droppedComponents[index],
        x: event.left,
        y: event.top,
      });
    },
    updateSize(event, index) {
      console.log('Resizing');
      this.$set(this.droppedComponents, index, {
        ...this.droppedComponents[index],
        width: event.width,
        height: event.height,
      });
    },  
    updateText(index, newText) {
      this.$set(this.droppedComponents, index, {
        ...this.droppedComponents[index],
        text: newText,
      });
    },
    deleteComponent(index) {
      this.droppedComponents.splice(index, 1);
    },
    saveCanvas() {
      const savedState = JSON.stringify(this.droppedComponents);
      console.log(savedState);
      localStorage.setItem('canvasState', savedState);
      alert('Canvas state saved!');
    },
    loadCanvas() {
      const savedState = localStorage.getItem('canvasState');
      if (savedState) {
        const components = JSON.parse(savedState);
        this.droppedComponents = components.map(component => ({
          ...component,
          type: shapes[component.shape.name],
        }));
        alert('Canvas state loaded!');
      } else {
        alert('No saved canvas state found.');
      }
    },
    clearCanvas() {
      this.droppedComponents = [];
    },
  },
};
</script>

<style lang="scss" scoped>

$save-btn-fill: #6cd970;
$clear-btn-fill: #ff7b7b;
$load-btn-fill: #f5f5f5;

$toolbar-btn-spacing: 10px;

.canvas {
  width: 100%;
  height: 100vh;
  border: 1px solid #ccc;
  position: relative;
  background-image: url("../assets/canvas-bg.PNG"); 
  background-repeat: repeat;
}

.save-btn {
  background-color: $save-btn-fill !important;
}

.load-btn { 
  background-color: $load-btn-fill !important;
}

.clear-btn {
  background-color: $clear-btn-fill !important;
}

.toolbar-btn {
  margin: $toolbar-btn-spacing;
}

.vue-draggable-resizable {
  border: none !important;
  outline: none !important;
}

.vue-draggable-resizable .shape {
  border: none !important;
  outline: none !important;
}

.no-border {
  border: none !important;
  outline: none !important;
}

.banner-note {
  background-color: #fff8c4;
  border: 1px solid #ccc;
  padding: 10px;
  position: absolute;
  top: 0;  // Change to 'bottom: 0;' if you want it at the bottom
  width: 100%;
  box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.1);
  text-align: center;
}

.close-btn {
  position: absolute;
  top: 5px;
  right: 5px;
  cursor: pointer;
}

</style>
