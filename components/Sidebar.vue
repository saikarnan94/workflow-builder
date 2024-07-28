<template>
  <v-navigation-drawer app class="sidebar">
    
    <div class="sidebar-logo">
      <img src="..\assets\logo-workflow.jpg" class="flowchart-logo" alt="logo" />
    </div>
    <v-toolbar flat>
      <v-toolbar-title>Component Palette</v-toolbar-title>
    </v-toolbar>
    <v-list>
      <v-subheader>Nodes</v-subheader>
      <v-list-item
        v-for="(shape, index) in nodeShapes"
        :key="shape.type"
        draggable="true"
        @dragstart="dragStart(shape, $event)"
      >
        <v-list-item-avatar>
          <v-icon>{{ shape.icon }}</v-icon>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title>{{ shape.name }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-subheader>Connections</v-subheader>
      <v-list-item
        v-for="(shape, index) in connectionShapes"
        :key="shape.type"
        draggable="true"
        @dragstart="dragStart(shape, $event)"
      >
        <v-list-item-avatar>
          <v-icon>{{ shape.icon }}</v-icon>
        </v-list-item-avatar>
        <v-list-item-content>
          <v-list-item-title>{{ shape.name }}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
  </v-navigation-drawer>
</template>

<script>
export default {
  data() {
    return {
      nodeShapes: [
        { name: 'Terminal', icon: 'mdi-circle-outline' },
        { name: 'Process', icon: 'mdi-rectangle-outline' },
        { name: 'Step', icon: 'mdi-square-outline' },
        { name: 'InputOutput', icon: 'mdi-parallelogram-outline' },
        { name: 'Decision', icon: 'mdi-cards-diamond-outline' },
        { name: 'TextBox', icon: 'mdi-format-text' },
      ],
      connectionShapes: [
        { name: 'RightArrow', icon: 'mdi-arrow-right' },
        { name: 'LeftArrow', icon: 'mdi-arrow-left' },
        { name: 'UpArrow', icon: 'mdi-arrow-up' },
        { name: 'DownArrow', icon: 'mdi-arrow-down' },
        { name: 'BidirectionalArrow', icon: 'mdi-arrow-left-right' },
      ],
    };
  },
  methods: {
    dragStart(shape, event) {
      event.dataTransfer.setData('application/json', JSON.stringify(shape));
      event.dataTransfer.effectAllowed = 'move';
    },
  },
};
</script>

<style lang="scss">

$border-radius: 7px;
$box-shadow: 3px 2px 3px 2px #ccc;

$cursor-grab: grab;

.sidebar {
    border-radius: $border-radius !important;
    box-shadow: $box-shadow !important;
}

.theme--light.v-list-item:not(.v-list-item--active):not(.v-list-item--disabled) {
    cursor: $cursor-grab;
}

.sidebar-logo {
  width: 100%; 
  height: 100px;
  text-align: center;
}

.flowchart-logo {
  width: 100px;
  height: 100px; 
  margin: 0 auto;
}

.v-list-item:hover {
  background-color: #f0f0f0; // Change this color as per your design
  cursor: pointer;
}

.v-list-item-title {
  transition: color 0.3s ease;
}

.v-list-item:hover .v-list-item-title {
  color: #007BFF; // Change this color as per your design
}

</style>