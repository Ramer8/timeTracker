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
      @resetClock="resetClock"
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
<div  v-if="info">
  {{ info?.data.workedSeconds }} from info
</div>
</div>
    <button class="bg-gray-400 hover:bg-blue-300 px-2 py-1 m-2 rounded-full" @click="getData">
      Get Data
    </button>
    <button class="bg-gray-400 hover:bg-blue-300 px-2 py-1 m-2 rounded-full" @click="putData">
      Put data
    </button>

    <div v-if="this.newData.workedSeconds"> {{ newData.workedSeconds}} from newData! </div>
    <div v-if="info"> {{ info.data.workedSeconds }} from varaible 'info'  </div>
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
      newData: '',
      workEntryInDate: '',
      workEntryOutDate: '',
      currentWorkedSeconds: '',
      totalWorkedSeconds: 0,
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
      if (!this.initialTime === 0) {
        this.currentTime = this.initialTime;
      }
      this.workEntryInDate = Date.now();
      // fijo fecha de ingreso
      this.timerInterval = setInterval(() => {
        if (!this.isPaused) {
          console.log('contando..');
          this.currentTime++;
        }
      }, 1000);
    },
    togglePause() {
      this.isPaused = !this.isPaused;
      if (this.isPaused) {
        console.log('pausando..');

        this.workEntryOutDate = Date.now();
        // fijo fecha de egreso
        console.log(new Date(this.workEntryOutDate));

        this.totalWorkedSeconds = this.info.data.workedSeconds + this.currentTime;
      }
    },
    resetClock() {
      this.putData();
      console.log('reseting clock..');
      this.currentTime = 0;
      if (this.isPaused) {
        this.isPaused = !this.isPaused;
      }
    },
    getData() {
      axios.get('http://localhost:3000/data').then((response) => (this.info = response));
      console.log('getting data...');
    },
    putData() {
      this.newData = {
        ...this.info.data,
        workEntryIn: {
          origin: 'string',
          date: new Date(this.workEntryInDate),
          coordinates: {
            latitude: 0,
            longitude: 0,
          },
        },
        workEntryOut: {
          origin: 'string',
          date: new Date(this.workEntryOutDate),
          coordinates: {
            latitude: 0,
            longitude: 0,
          },
        },
        workedSeconds: this.totalWorkedSeconds,
        createdAt: new Date(this.workEntryInDate),
        updatedAt: new Date(Date.now()),
        deletedAt: '2020-01-01T10:00:00+01:00',
      };
      // myDate: new Date(Date.now()),
      axios.put('http://localhost:3000/data', this.newData).then((response) => {
        console.log(response);
        this.getData();
      });
    },
  },
};
</script>
