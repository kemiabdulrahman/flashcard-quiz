<!-- Timer.vue -->
<template>
  <div class="timer">
    <p>Time Remaining: {{ formattedTime }}</p>
  </div>
</template>

<script>
export default {
  props: {
    time: Number
  },
  data() {
    return {
      remainingTime: this.time
    };
  },
  computed: {
    formattedTime() {
      const minutes = Math.floor(this.remainingTime / 60);
      const seconds = this.remainingTime % 60;
      return `${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
    }
  },
  methods: {
    countdown() {
      if (this.remainingTime > 0) {
        this.remainingTime--;
      } else {
        this.$emit('time-up');
      }
    }
  },
  mounted() {
    this.interval = setInterval(this.countdown, 1000);
  },
  beforeDestroy() {
    clearInterval(this.interval);
  }
};
</script>

<style scoped>
.timer {
  margin-bottom: 20px;
  font-size: 18px;
  font-weight: bold;
  color: #e74c3c;
}
</style>
