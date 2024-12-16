<template>
  <div>
    <button @click="showToast">Show Toast</button>
    <button @click="playSound">Play Sound</button>
    <audio controls>
      <source src="/public/notification.mp3" type="audio/mpeg" />
      Your browser does not support the audio element.
    </audio>
  </div>
</template>

<script>
import { useToast } from "vue-toastification";
export default {
  setup() {
    const toast = useToast();

    // Function to play sound
    const playSound = () => {
      const audio = new Audio("/notification.mp3"); // Correct path without `/public`
      audio.play();
    };

    // Function to show toast and play sound
    const showToast = () => {
      toast.success("This is a success message!");
      if (toast) {
        playSound();
      }
    };

    return {
      showToast,
      playSound,
    };
  },
};
</script>
