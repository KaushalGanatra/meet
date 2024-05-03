<template>
  <div class="container background">
    <iframe src="https://docs.google.com/forms/d/e/1FAIpQLSfTvu0-ACJsjxROpzrowUqLPcekR5xVoiiyNPJQD29YPEJszw/viewform?embedded=true" width="640" height="625" frameborder="0" marginheight="0" marginwidth="0">Loading…</iframe>
    <!-- <h1>Join the Celebration</h1>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label for="name">Your Name:</label>
        <input type="text" id="name" v-model="name" required>
      </div>
      <div class="form-group">
        <label>Are you going to join?</label>
        <div>
          <button type="button" @click="setJoin(true)" :class="{ active: join }">Yes</button>
          <button type="button" @click="setJoin(false)" :class="{ active: !join }">No</button>
        </div>
      </div>
      <button type="submit" @click="submitForm">Submit</button>
    </form>-->
  </div> 
</template>

<script setup>
import { ref } from 'vue';

const name = ref('');
const join = ref(true); // Default to "Yes" for joining

const setJoin = (status) => {
  join.value = status;
};

const submitForm = () => {
  // Send the data to Google Sheets
  const formData = {
    name: name.value,
    join: join.value ? 'Yes' : 'No',
  };
  console.log(formData); // Replace with your logic to send data to Google Sheets
};
</script>

<style scoped>
.background {
  background-color: #3498db;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center; /* Center text horizontally */
  font-family: 'Arial', sans-serif; /* Choose a suitable font */
  animation: fadeIn 2s ease; /* Animation for fade in effect */
  padding: 20px; /* Add padding for better spacing */
  line-height: 1.6; /* Increase line height for better readability */
  width: 100%; /* Make the background fill the entire width */
  position: fixed; /* Fix the background */
  top: 0; /* Align to the top */
  left: 0; /* Align to the left */
  overflow-y: auto; /* Enable vertical scrolling */
}

.container {
  max-width: 600px;
  margin: 0 auto;
}

.form-group {
  margin-bottom: 20px;
}

label {
  display: block;
  margin-bottom: 5px;
}

input[type="text"] {
  width: 100%;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button.active {
  background-color: #007bff;
  color: #fff;
}
</style>
