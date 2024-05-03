<template>
  <div class="background">
    <!-- Counter 0 - Select Team -->
    <div class="modal" v-if="counter === 0">
      <div class="modal-dialog" role="document">
        <div class="modal-content custom-modal">
          <div class="modal-header">
            <h5 class="modal-title">Select Your Team</h5>
          </div>
          <div class="modal-body">
            <select class="form-control full-width" v-model="selectedTeam">
              <option value="">Select Team</option>
              <option value="DevEmpire">DevEmpire</option>
              <option value="Mevricks">Mevricks</option>
              <!-- Add more options as needed -->
            </select>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-primary" @click="teamSubmit">Let's Go</button>
          </div>
        </div>
      </div>
    </div>

    <!-- Counter 1 - Enter Password -->
    <div v-if="counter === 1" class="center-content text-center">
      <h4>{{ selectedTeam }} - Enter Password</h4>
      <div class="form-group">
        <input type="password" class="form-control" v-model="password" placeholder="Password">
      </div>
      <button type="button" class="btn btn-primary" @click="validatePassword">Submit</button>
    </div>

    <!-- Counter 2 - Success/Failure -->
    <div v-if="counter === 2" class="center-content text-center">
      <div v-if="!success">
      <h4>Password is incorrect. Please try again.</h4>
      <button type="button" class="btn btn-next" @click="proceed">Try Again</button>
      </div>
    </div>
<!-- Quiz Content -->
<div v-if="success" class="quiz-container">
  <h1><u>Welcome {{ selectedTeam }}</u></h1>
  <h4>Let's Go on a Quiz about our Improvised Family</h4>
  <ol>
    <li>When was our company established?</li>
    <ul>
      <li><input type="radio" id="q1a" name="q1" value="a"> <label for="q1a">2001</label></li>
      <li><input type="radio" id="q1b" name="q1" value="b"> <label for="q1b">2011</label></li>
      <li><input type="radio" id="q1c" name="q1" value="c"> <label for="q1c">2013</label></li>
      <li><input type="radio" id="q1d" name="q1" value="d"> <label for="q1d">2009</label></li>
    </ul>
    <li>Date when the company was established?</li>
    <ul>
      <li><input type="radio" id="q2a" name="q2" value="a"> <label for="q2a">19</label></li>
      <li><input type="radio" id="q2b" name="q2" value="b"> <label for="q2b">18</label></li>
      <li><input type="radio" id="q2c" name="q2" value="c"> <label for="q2c">23</label></li>
      <li><input type="radio" id="q2d" name="q2" value="d"> <label for="q2d">19</label></li>
    </ul>
    <li>In which month?</li>
    <ul>
      <li><input type="radio" id="q3a" name="q3" value="a"> <label for="q3a">Jan</label></li>
      <li><input type="radio" id="q3b" name="q3" value="b"> <label for="q3b">Feb</label></li>
      <li><input type="radio" id="q3c" name="q3" value="c"> <label for="q3c">May</label></li>
      <li><input type="radio" id="q3d" name="q3" value="d"> <label for="q3d">Dec</label></li>
    </ul>
  </ol>

  <div v-if="rightANS">
   <nuxt-link to="padhariye">But Why did you asked that!?</nuxt-link>
  </div>

  <!-- Submit Button -->
  <button type="button" class="btn btn-primary" @click="submitQuiz">Submit</button>
</div>

      
  </div>
</template>

<script setup>
import { ref } from 'vue';

const counter = ref(0);
const selectedTeam = ref('');
const password = ref('');
const success = ref(false);
const rightANS = ref(false);

const teamSubmit = () => {
  if (selectedTeam.value === '') {
    alert("Please select your team");
    return;
  }
  counter.value++;
};

const validatePassword = () => {
  // Static passwords for teams (you can change these as needed)
  const passwords = {
    DevEmpire: 'dev123',
    Mevricks: 'mev456'
    // Add more teams and passwords as needed
  };

  if (password.value === passwords[selectedTeam.value]) {
    success.value = true;
  }
  counter.value++;
};

const proceed = () => {
  if (success.value) {
    // Proceed to the next step
    // You can navigate to another route or perform other actions here
    console.log("Proceeding to the next step");
  } else {
    // Reset counter and fields for retry
    counter.value = 1;
    password.value = '';
  }
};

const submitQuiz = () => {
  // Get the selected answers
  const answer1 = document.querySelector('input[name="q1"]:checked')?.value;
  const answer2 = document.querySelector('input[name="q2"]:checked')?.value;
  const answer3 = document.querySelector('input[name="q3"]:checked')?.value;
  
  // Check if the answers are correct
  if (answer1 === 'b' && answer2 === 'b' && answer3 === 'c') {
    // Correct answers
    alert('CORRECT');
    rightANS.value = true
    // Redirect to 'padhariye.vue' using nuxt-link
    // Example: window.location.href = '/padhariye.vue';
  } else {
    // Incorrect answers
    alert('Wrong answers. Please try again.');
    // Stay on the same page
  }
};

</script>

<style>
.background {
  background-color: #3498db;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.custom-modal {
  background-color: #fff;
  border-radius: 10px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
  max-width: 90%;
  padding: 20px;
}

.full-width {
  width: 100%;
}

.modal-body input {
  border: none;
  border-radius: 0;
  border-bottom: 1px solid #ccc;
  padding: 10px 0;
  box-sizing: border-box;
}

.modal-footer {
  text-align: center;
}

.center-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.transparent-bg {
  background-color: transparent;
  border: none; /* Remove border */
}

.full-width-button {
  width: 100%;
  border: 1px solid #000; /* Add border */
}

.center-content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.welcome-text {
  margin-bottom: 20px;
}

.welcome-text h4 {
  font-size: 20px;
}

.welcome-text h2 {
  font-size: 36px;
  text-align: center;
  color: yellow;
}

.btn-next {
  background-color: #007bff;
  color: #fff;
  border: none;
  border-radius: 25px;
  padding: 10px 20px;
  font-size: 18px;
  transition: all 0.3s ease;
}

.btn-next:hover {
  background-color: #0056b3;
  transform: scale(1.05);
}

@media (max-width: 768px) {
  .welcome-text h4 {
    font-size: 18px;
  }

  .welcome-text h2 {
    font-size: 30px;
  }

  .btn-next {
    font-size: 16px;
    padding: 8px 16px;
  }
}
</style>
