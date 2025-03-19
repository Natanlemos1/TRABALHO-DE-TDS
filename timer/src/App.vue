<template>
  <div class="timer-container">
    <h1 class="timer-display">Timer: {{ formattedTime }}</h1>
    <AddTime @add-minute="addMinute" />
    <Encerrar @reset-timer="resetTimer" />
  </div>
</template>

<script>
import AddTime from "./components/AddTime.vue";
import Encerrar from "./components/Encerrar.vue";

export default {
  components: {
    AddTime,
    Encerrar,
  },
  data() {
    return {
      timeLeft: 0, // Tempo em segundos
      timer: null,
    };
  },
  computed: {
    formattedTime() {
      const minutes = Math.floor(this.timeLeft / 60);
      const seconds = this.timeLeft % 60;
      return `${String(minutes).padStart(2, '0')}:${String(seconds).padStart(2, '0')}`;
    },
  },
  methods: {
    addMinute() {
      this.timeLeft += 60;
      if (!this.timer) {
        this.startTimer();
      }
    },
    resetTimer() {
      this.timeLeft = 0;
      if (this.timer) {
        clearInterval(this.timer);
        this.timer = null;
      }
    },
    startTimer() {
      this.timer = setInterval(() => {
        if (this.timeLeft > 0) {
          this.timeLeft--;
        } else {
          clearInterval(this.timer);
          this.timer = null;
        }
      }, 1000);
    },
  },
  beforeUnmount() {
    if (this.timer) {
      clearInterval(this.timer);
    }
  },
};
</script>

<style scoped>
.timer-container {
  text-align: center;
  font-family: Arial, sans-serif;
  background-color: black;
  color: white;
  padding: 20px;
  border-radius: 10px;
  width: 300px;
  margin: auto;
}

.timer-display {
  font-size: 2em;
  font-weight: bold;
}
</style>
