<template>
  <div class="p-3 bg-color: bg-gray-800 text-gray-700 h-screen">
    <ShowData
      v-if="info"
      :info="info"
      :newData="newData"
      class="flex gap-1 bg-gray-300 text-gray-900 font-semibold rounded-full w-fit text-center p-2"
    ></ShowData>

    <button class="bg-gray-400 hover:bg-blue-300 px-2 py-1 m-2 rounded-full" @click="getData">
      Get Data
    </button>
  </div>
</template>
<script>
import ShowData from './components/ShowData.vue';
import axios from 'axios';

export default {
  components: {
    ShowData,
  },
  data() {
    return {
      info: '',
      newData: {}
    };
  },
  methods: {
    getData() {
      axios.get('http://localhost:3000/data').then((response) => (this.info = response));
    },
    putData() {
      axios.put('http://localhost:3000/data', this.NewData).then((response) => {
        console.log(response);
      });
    }
  }
};
</script>
