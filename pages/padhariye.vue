<template>
  <div class="background">
    <h1><u>Hey Improwised Family!!</u></h1>
    <br>
    <p>Get ready to break out the party hats and join us in celebrating a monumental moment in our company's journey! Guess what? We're about to hit a major milestone that's making us feel like we're on cloud nine! 
      That's right, we're not just turning 13 - we're hitting the glorious tween years of our corporate existence. And just like any tween, we're ready to celebrate in style!</p>

    <p>So, mark your calendars and save the date for a special lunchtime celebration on this 18th of May! It's going to be a blast from the past with a dash of future-forward flair. Think nostalgic tunes, throwback treats, and maybe even a few surprises that will transport us back to our younger years (but with a lot more wisdom and experience under our belts!).</p>

    <p>We couldn't have reached this amazing milestone without each and every one of you, so let's take this opportunity to toast to our past achievements, embrace the present, and set our sights on an even brighter future ahead.</p>

    <p>Come hungry, come festive, and come ready to party like it's 13 years ago (but better)!  Prepare yourselves for an afternoon packed with tasty treats, laughter, and maybe a few surprises along the way. We'll have delicious food, refreshing beverages, and of course, the company of your fantastic colleagues to make this celebration truly unforgettable.</p>
    
    <p>See you there!</p>
    <p>Warm Regards!</p>

    <audio autoplay loop>
      <source src="background_music.mp3" type="audio/mpeg">
      Your browser does not support the audio element.
    </audio>

    <div>
    <u><a href="https://docs.google.com/forms/d/e/1FAIpQLSfTvu0-ACJsjxROpzrowUqLPcekR5xVoiiyNPJQD29YPEJszw/viewform" style="color: black;"> NEXT -> </a></u>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue';

onMounted(() => {
  // Check if it's the first time loading the page
  if (!localStorage.getItem('loadedBefore')) {
    // Set a flag indicating that the page has been loaded before
    localStorage.setItem('loadedBefore', true);
    // Reload the page
    location.reload();
  }
});
</script>

<style>
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

.background h1 {
  font-size: 36px; /* Adjust font size for headings */
  margin-bottom: 20px; /* Add margin bottom for spacing */
}

.background p {
  font-size: 18px; /* Adjust font size for paragraphs */
  margin-bottom: 15px; /* Add margin bottom for spacing */
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
