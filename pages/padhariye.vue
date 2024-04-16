<template>
    <div class="background">
      <h1>{{ savedUserName }}</h1>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';

const savedUserName = ref('');

onMounted(() => {
  savedUserName.value = localStorage.getItem('savedUserName');
});
</script>



<style>
.background {
  background-color: #3498db;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>