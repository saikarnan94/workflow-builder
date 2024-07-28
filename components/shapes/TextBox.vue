<template>
  <div>
    <v-text-field
      v-model="text"
      placeholder="Enter text"
    ></v-text-field>
  </div>
</template>

<script>
export default {
  name: 'TextBox',
  props: {
    initialText: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      text: this.initialText,
    };
  },
  watch: {
    text(newText) {
      this.$emit('update:text', newText);
    }
  }
};
</script>