<template>
  <div class="scene-selector">
    <button
    v-for="(scene, index) in scenes"
      :key="index"
      class="scene-button"
      @click="selectScene(scene)"
      :style="{backgroundColor: selectedScene === scene ? '#4CAF50' : '#ddd',
                color: selectedScene === scene ? 'white' : 'black'}"></button>
    
  </div>
</template>

<script>
export default {
  props: {
    scenes: {
      type: Array,
      required: true
    },
    selectedScene: {
      type: String,
      required: true
    }
  },
  emits: ['scene-selected'],  // Define the event we'll emit
  methods: {
    selectScene(scene) {
      this.$emit('scene-selected', scene);  // Emit the event when a button is clicked
    }
  }
};
</script>

<style scoped>
.scene-selector {
  position: absolute;
  top: 10px;
  right: 3%;
  display: flex; /* Arrange buttons in a row */
  gap: 10px; /* Add space between buttons */
  z-index: 10; /* Ensure it's on top of the video */
}

.scene-button {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  border: none;
  cursor: pointer;
  opacity: 0.6;
}

.scene-button:hover {
  opacity: 1;
}
</style>