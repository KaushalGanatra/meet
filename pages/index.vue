<template>
  <div class="background">
    <div class="modal" v-if="counter === 0">
      <div class="modal-dialog" role="document">
        <div class="modal-content custom-modal">
          <div class="modal-header">
            <h5 class="modal-title">Enter Your Name</h5>
          </div>
          <div class="modal-body">
            <input type="text" class="form-control full-width" placeholder="Bataiye sharmaye nahi" v-model="userName">
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-primary" @click="nameSubmit">Let's Go</button>
          </div>
        </div>
      </div>
    </div>
    <div v-if="counter === 1" class="center-content text-center">
      <h4>Sacchi mea apka naam {{ userName }} hai?</h4>
      <img src="../are-you-sure.png" alt="Photu load nahi hua, Network sudharo" class="img-thumbnail transparent-bg">
      <button type="button" class="btn btn-warning full-width-button" @click="backToName">Batata Hu saccha naam, juth kyu hi bolna</button>
      <button type="button" class="btn btn-success full-width-button" @click="NextFromValidation">Ha Ha Sacchi</button>
    </div>

    <div v-if="counter === 2" class="center-content text-center">
      <div class="welcome-text">
        <h4 class="mb-4">Accha Chalo, We are good people so maan lete hai ki apka naam <strong>{{ userName }}</strong> hai &#128524; !!</h4>
        <h2 class="mb-5">Welcome {{ userName }} &#128513;</h2>
      </div>

      <NuxtLink to="/padhariye"><button type="button" class="btn btn-next">Next -></button></NuxtLink>
      <p class="mt-4">Won't take your much precious time, but abhi jaldi next dabado</p>
    </div>
</div>
</template>

<script setup>
import { ref } from 'vue';

const counter = ref(0);
const userName = ref('');
const savedUserName = ref('');

const nameSubmit = () => {
  if (userName.value === '') {
    alert("Arey naam toa batao");
    return;
  }
  savedUserName.value = userName.value;
  localStorage.setItem('savedUserName', savedUserName.value);
  counter.value++;
};

const backToName = () => {
  userName.value = ""
  counter.value--
}

const NextFromValidation = () => {
  counter.value++
}
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
