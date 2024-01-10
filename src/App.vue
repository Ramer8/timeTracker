<template>
  <body class="p-3 dark:bg-gray-800 dark:text-gray-300 h-screen">
    <ShowData
      v-if="info"
      :info="info"
      :newData="newData"
      :initialTime="initialTime"
      :currentTime="currentTime"
      :timerInterval="timerInterval"
      :isPaused="isPaused"
      @startTimer="startTimer"
      @togglePause="togglePause"
      class="flex gap-1 bg-gray-300 text-gray-900 font-semibold rounded-full w-fit text-center p-2"
    ></ShowData>

<div>
  <!-- <button class="bg-yellow-500 p-1 rounded-md text-teal-800"
  @click="isMenuOpen = true"> Open Menu</button> -->

<!-- <MainMenu v-if="isMenuOpen"
@closeMenu="isMenuOpen = false"
@MsgFromRoot="MsgFromRoot"
@getValue="getValue"
@change="change">
</MainMenu> -->

</div>
    <button class="bg-gray-400 hover:bg-blue-300 px-2 py-1 m-2 rounded-full" @click="getData">
      Get Data
    </button>
  </body>
</template>
<script>
import axios from 'axios';
// import MainMenu from './components/MainMenu.vue';
import ShowData from './components/ShowData.vue';

export default {
  components: {
    ShowData,
  },
  data() {
    return {
      // name: '',
      // isMenuOpen: false,
      info: '',
      newData: {},
      initialTime: 0, // Initial time in seconds
      currentTime: 0,
      isPaused: false,
      timerInterval: null,
    };
  },
  methods: {
    // change(value) {
    //   // console.log(value);
    //   this.isMenuOpen = value;
    // // console.log(this.isMenuOpen);
    // },
    // getValue(value) {
    //   this.name = value;
    //   // console.log(this.name);
    // },
    // MsgFromRoot() {
    //   console.log('Msg by console from root');
    // },
    startTimer() {
      if (!this.initialTime == 0) {
        this.currentTime = this.initialTime;
      }
      this.timerInterval = setInterval(() => {
        if (!this.isPaused) {
          console.log('contando..');
          this.currentTime++;
        }
      }, 1000);
    },
    togglePause() {
      this.isPaused = !this.isPaused;
    },
    getData() {
      axios.get('http://localhost:3000/data').then((response) => (this.info = response));
    },
    putData() {
      axios.put('http://localhost:3000/data', this.NewData).then((response) => {
        console.log(response);
      });
    },
  },
};
</script>
