<template>
  <div :style="{ backgroundImage: color }" class="app-container">
    <h1>{{ message }}</h1>
    <button @click="changeColor" class="btn">Click to Change Gradient</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'App',
  setup() {
    const message = 'Click the button to change the background gradient!';
    const color = ref('linear-gradient(45deg, #ff6f61, #6fa3ef)');

    const changeColor = () => {
      
      color.value = `linear-gradient(45deg, ${randomColor()}, ${randomColor()})`;
    };

    
    const randomColor = () => {
      return `#${Math.floor(Math.random() * 16777215).toString(16)}`;
    };

    return {
      message,
      color,
      changeColor
    };
  },
});
</script>

<style scoped>
.app-container {
  text-align: center;
  padding: 2rem;
  background-size: cover;
  background-position: center;
  min-height: 100vh;
  transition: background-image 0.3s ease;
}

h1 {
  color: white;
  font-size: 2rem;
}

button {
  padding: 10px 20px;
  font-size: 1.2rem;
  cursor: pointer;
  border: none;
  border-radius: 5px;
  background-color: #4caf50;
  color: white;
  margin-top: 20px;
}

button:hover {
  background-color: #45a049;
}
</style>
