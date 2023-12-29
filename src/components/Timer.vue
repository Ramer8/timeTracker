<template>
  <body className="container -ml-2 mt-1 my-0 mx-auto">
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
  },
  methods: {
    formatDigit(value) {
      return value < 10 ? `0${value}` : value;
    },

    start() {     
      if (this.interval) return this.stop();
      this.interval = setInterval(() => {
        this.counter = this.counter + 1;
      }, 1000);;
    },
    stop() {
      if (this.interval) clearInterval(this.interval);
      this.interval = null;
    },
    clear() {
      this.stop();
      this.counter = 0;
    }
  }
};
</script>
