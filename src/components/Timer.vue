<template>
  <body className="container -ml-2 mt-1 my-0 mx-auto">
    <div className="h-auto flex flex-row">
      <div class="text-gray-400 mt-2 flex mr-2">
        <div class="mr-2">/</div>
        {{ formattedTime }}</div>
      <button
      :class="[
        isPaused ? 'bg-green-500' : 'bg-gray-400 text-white',
        'bg-gray-400 mx-1 hover:text-gray-800 rounded-full w-32 px-4 py-2'
      ]"
        @click="$emit('togglePause')"
      >
       {{ isPaused ? 'Resume' : 'Pause' }}
      </button>
    </div>
  </body>
</template>

<script>
// import MyButton from './MyButton.vue';

export default {
  // components: {
  //   MyButton,
  // },
  data() {
    return {
      isPausedTimer: '',
    };
  },
  emits: ['startTimer', 'togglePause'],
  props: {
    initialTime: Number,
    currentTime: Number,
    timerInterval: Number,
    isPaused: Boolean,
  },
  computed: {
    formattedTime() {
      const hours = Math.floor(this.currentTime / 3600);
      const minutes = Math.floor(this.currentTime / 60);
      const seconds = this.currentTime % 60;

      return `${this.formatDigit(hours)}:${this.formatDigit(minutes)}:${this.formatDigit(seconds)}`;
    },
  },
  mounted() {
    this.startTimer();
  },
  methods: {
    startTimer() {
      this.$emit('startTimer');
    },
    togglePause() {
      this.$emit('togglePause');
    },
    // startTimer() {
    //   if (!this.initialTime == 0) {
    //     this.currentTime = this.initialTime;
    //     console.log('es distinto');
    //     console.log(this.currentTime);
    //   }
    //   this.timerInterval = setInterval(() => {
    //     if (!this.isPaused) {
    //       this.currentTime++;
    //     }
    //   }, 1000);
    // },
    // togglePause() {
    //   this.isPaused = !this.isPaused;
    // },
    formatDigit(value) {
      return value < 10 ? `0${value}` : value;
    },
  },
  beforeUnmount() {
    clearInterval(this.timerInterval);
  },
};
</script>
