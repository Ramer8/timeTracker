<template>
  <div>
    <div className="container mx-auto px-3 mt-3 text-center text-base text-gray-600">
      {{
        `${formatDigit(new Date(info.data.workEntryIn.date).getHours())}:${formatDigit(
          new Date(info.data.workEntryIn.date).getMinutes()
        )}:${formatDigit(new Date(info.data.workEntryIn.date).getSeconds())}`
      }}
    </div>
    <Timer
      v-if="state === 'online'"
      :workedTime="info.data.workEntryIn.date"
    />
    <button
      @click="changeState"
      :class="[
        state === 'online' ? 'bg-orange-500' : 'bg-green-500 ',
        'rounded-full w-auto hover:text-gray-800 text-white px-12 py-1 mt-1'
      ]"
    >
      <slot>{{ state === 'online' ? 'Salir' : 'Entrar' }}</slot>
    </button>
    <div class="container mt-1">
      <img
          class="h-10 object-cover rounded-full w-10 container"
          src="/profilemanpic.jpeg"
        />
          <button
          :class="[
            state === 'online' ? 'bg-green-500' : 'bg-red-400',
            'absolute rounded-full w-3 h-3 -my-6 mx-3 cursor-none'
          ]"
        ></button>
    </div>
    <Dropdowns class="container mx-auto mt-1 text-center"
      >{{ info.data.employee.firstName }}<span></span> {{ info.data.employee.lastName }}</Dropdowns
    >
  </div>
</template>
<script>
import Dropdowns from './Dropdowns.vue';
import MyButton from './MyButton.vue';
import Timer from './Timer.vue';
export default {
  data() {
    return {
      newDate: '',
      state: 'online'
    };
  },
  components: { Dropdowns, MyButton, Timer },
  props: {
    info: Object,
    workedTime: String
  },
  methods: {
    changeState() {
      if (this.state === 'online') {
        this.state = 'offline';
      } else {
        this.state = 'online';
      }
      return console.log(this.state);
    },
    formatDigit(value) {
      // Add leading zero if the value is less than 10
      return value < 10 ? `0${value}` : value;
    }
  }
};
</script>
<style></style>
