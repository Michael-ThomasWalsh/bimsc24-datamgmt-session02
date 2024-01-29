<!-- the script is where the js code goes -->
<script setup>
import { ref, computed } from "vue";

let name = ref("Michael's Website");

// For the text input
let inputText = ref('');
let displayedText = ref('');

// For changing background color
let containerBackgroundColors = {
  main: '#3b3b3b', // Initial background color for main container
  sidebar: '#5a5a5a' // Initial background color for sidebar container
};

const addText = () => {
  displayedText.value += inputText.value;
};

const resetText = () => {
  displayedText.value = '';
};

const changeBackgroundColor = () => {
  containerBackgroundColors.main = '#ff5733'; // Change to your desired color
};
</script>

<!-- the template is where the html code goes -->
<template>
  <div id="navbar" class="container">
    <div id="title">{{ name }}</div>
  </div>

  <div id="flex">
    <div id="sidebar" class="container">
      <input v-model="inputText" placeholder="Type something...">
      <button @click="addText">Add Text</button>
      <button @click="resetText">Reset Text</button>
      <label for="targetContainer">Container:</label>
      <input v-model="targetContainerId" id="targetContainer" placeholder="Enter container ID">
      <label for="hexValue">Hex Value:</label>
      <input v-model="hexValue" id="hexValue" placeholder="Enter Hex value">
      <button @click="changeBackgroundColor">Change Color</button>
    </div>
    
    <div id="main" class="container" :style="{ backgroundColor: containerBackgroundColors.main }">
      <section>
        <h2>Main</h2>
        <p>{{ displayedText }}</p>
      </section>
    </div>
  </div>
</template>

<!-- style is where the css code goes -->
<style scoped>
html {
  background-color: #3b3b3b;
  color: white;
}

body {
  margin: 0;
  font-family: 'Courier New', Courier, monospace;
}

div {
  /* put the borders in the inside of container */
  box-sizing: border-box;
}

#navbar {
  height: 50px;
  background-color: #5a5a5a;
  font-family: 'Courier New', Courier, monospace;
  color: #ffffff;
}

#flex {
  display: flex;
  height: calc(100vh - 50px);
}

#sidebar {
  width: 30%;
  background-color: #5a5a5a;
  font-family: 'Courier New', Courier, monospace;
  color: #ffffff;
}

#main {
  width: 70%;
  border-color: green;
  font-family: 'Courier New', Courier, monospace;
}

#title {
  width: 100%;
  text-align: center;
  font-size: 24px; /* Adjust the font size as needed */
}

.container {
  border-style: solid;
  border-width: 1px;
}

section {
  padding: 20px;
}

/* Additional styling for labels and inputs */
label {
  display: block;
  margin-top: 10px;
}

input {
  margin-bottom: 10px;
}
</style>
