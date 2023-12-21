<template>
  
    <div class="p-6 bg-color: bg-gray-200 text-white  h-screen">
      <ShowData  v-if="info" :info="info"></ShowData>
      <button class="bg-gray-500 hover:bg-gray-600 px-2 py-1 m-2 rounded-full " 
      @click="getData">Get Data </button>
    </div>
  
</template>
<script>
 import ShowData from './components/ShowData.vue';
 import axios from 'axios';

export default {
  components: {
    ShowData
  },
  data() {
    return {
      info: '',
      newData: ''
    };
  },
  methods: {
    getData() {
        axios
          .get('http://localhost:3000/data')
          .then(response => (this.info = response))
          console.log(this.info.data);
          
    }
  }
};
</script>

<style scoped></style>
