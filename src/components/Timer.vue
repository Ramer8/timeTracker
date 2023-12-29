<template>
  <body className="container mx-auto mt-1 my-0">
    <div className="h-auto flex flex-row">
      <div class="text-gray-400 mt-2 flex mr-2">
        <div class="mr-2">/</div>
        {{ formattedTime }}</div>
      <button
        class="bg-gray-400 mx-1 hover:text-gray-800 rounded-full w-32 text-white px-4 py-2"
        @click="start"
      >
        Pausar
      </button>
    </div>
  </body>
</template>

<script>
import MyButton from './MyButton.vue';

export default {
  name: 'Timer',
  props: {
    workedTime: String
  },
  components: {
    MyButton
  },
  data() {
    return {
       counter: 0,
      interval: null,
    };
  },
  computed: {
    formattedTime() {
      const valor = this.counter;
      var hours = Math.floor(valor / 3600);
      var minutes = Math.floor((valor / 60) % 60);
      var seconds = valor % 60;
      return `${this.formatDigit(hours)}:${this.formatDigit(minutes)}:${this.formatDigit(seconds)}`;
    },
    // getTime() {
    //   let time = new Date(this.workedTime);
    //   let timeHours = time.getHours();
    //   let timeMinutes = time.getMinutes();
    //   let timeSeconds = time.getSeconds();
    //   let TotalInSeconds = parseInt(timeHours * 3600) + parseInt(timeMinutes * 60) + timeSeconds;
    //   return TotalInSeconds;
    // }
  },
  methods: {
    formatDigit(value) {
      // Add leading zero if the value is less than 10
      return value < 10 ? `0${value}` : value;
    },

    start() {
      // let time = new Date(this.workedTime);
      // let timeHours = time.getHours();
      // let timeMinutes = time.getMinutes();
      // let timeSeconds = time.getSeconds();
      // let TotalInSeconds = parseInt(timeHours * 3600) + parseInt(timeMinutes * 60) + timeSeconds;
      // this.counter = TotalInSeconds;
     
      if (this.interval) return this.stop();
      this.interval = setInterval(() => {
        this.counter = this.counter + 1;
      }, 1000);
      // if (this.interval) return this.stop();
      // this.interval = setInterval(() => {
      //   this.counter = this.counter + 1;
      // }, 1000);
    },
    stop() {
      if (this.interval) clearInterval(this.interval);
      this.interval = null;
    },
    saveTimer() {
      const elapsedTime = this.counter;
    },

    clear() {
      // reinicia cuenta
      this.stop();
      this.counter = 0;
    }
  }
};
</script>
