<template>
  <div class=" flex gap-2  bg-gray-300 text-gray-900 font-bold rounded-full lg:w-1/2 sm:w-fit text-center p-4">
     <div >
       {{ info.data.workEntryIn.date.slice(11, -6) }} 
     </div>
      <button class=" bg-green-600 rounded-full  font-medium w-32 text-white px-2 py-1">Entar</button>
     | 
     <img class='h-10 mx-auto object-cover rounded-full w-10'
     width='50' height="30" src="/Users/ramirop/Documents/js/timeTracker/public/profilemanpic.jpeg" >
       <div  class="flex w-1/3 bg-gray-300 ">
         {{ info.data.employee.firstName }}
         {{ info.data.employee.lastName }}
       </div>
 </div>
 
</template>
<script>
export default {
  data() {
    return {
      newDate: '',
    };
  },
props: {
  info: Object,
  },
  methods:{
    splitDate(date) {
     newDate =  date.slice(11, -6)
console.log(newDate);
    }
  }
}
</script>
<style></style>
