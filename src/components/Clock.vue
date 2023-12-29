<template>
  <div>
    <h1>Time</h1>
    <div>
      {{ formattedTime }}
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      currentTime: new Date()
    };
  },
  computed: {
    formattedTime() {
      const hours = this.currentTime.getHours();
      const minutes = this.currentTime.getMinutes();
      const seconds = this.currentTime.getSeconds();

      return `${this.formatDigit(hours)}:${this.formatDigit(minutes)}:${this.formatDigit(seconds)}`;
    }
  },
  mounted() {
    // Update the current time every second
    setInterval(this.updateTime, 1000);
  },
  props: {
    workedTime: String
  },
  methods: {
    start() {
      console.log(this.inverval);
      if (this.interval) return this.stop();
      this.interval = setInterval(() => {
        this.counter = this.counter + 1;
      }, 1000);
    },
    stop() {
      if (this.interval) clearInterval(this.interval);
      this.interval = null;
    },
    clear() {
      this.stop();
      this.counter = 0;
    },
    updateTime() {
      this.currentTime = new Date();
    },
    formatDigit(value) {
      // Add leading zero if the value is less than 10
      return value < 10 ? `0${value}` : value;
    }
  }
};
</script>

<!-- <template>
    <div class="contenedor">
        <div class="reloj"> / <br> 
            <div class="horas">{{ workedTime.slice(11, -12) }}</div>
            <div class="horas">{{ horas }}</div>
            <div class="divisor">:</div>
            <div class="minutos">{{ minutos }}</div>
            <div class="divisor">:</div>
            <div class="segundos">{{ segundos }}</div>
        </div>
    </div>
</template>

<script>
export default {
    name: "RelojDigital",
    data() {
        return {
            horas: 0,
            minutos: 0,
            segundos: 0
        }
    },
    mounted() {
        setInterval(() => this.setTiempo(), 1000)
    },
    props:{
        workedTime: String
    },
    methods: {
        setTiempo() {
             const date = new Date();
            let horas = date.getHours();
            let minutos = date.getMinutes();
            let segundos = date.getSeconds();
            horas = horas <= 9 ? `${horas}`.padStart(2, 0) : horas;
            minutos = minutos <= 9 ? `${minutos}`.padStart(2, 0) : minutos;
            segundos = segundos <= 9 ? `${segundos}`.padStart(2, 0) : segundos;
            this.horas = horas;
            this.minutos = minutos;
            this.segundos = segundos;
        }
    }
}
</script>

<style scoped>
.reloj {
    display: inline-flex;
    font-size: 16px;
}
</style> -->

<!-- <template>
    <div class="text-black">
        Clock .<strong class="hover:font-thin cursor-pointer" @click="start"> START. </strong><br />
        <span>.{{ timerFormated }} Minutos </span>
        <span class="hover:bg-red-400" @click="clear">. y Segundos: {{ counter }}</span><br />
    </div>

    <div>
{{workedTime}}
<strong>
    {{ this.counter }}
</strong>
    </div>
</template>

<script>
export default {
  name: 'Timer',
  props: {
    workedTime: String
  },
  data() {
    return {
      counter: 0,
      interval: null
    };
  },
  computed: {
    getTime(){
        let time = new Date(workedTime)
       let timeString = time.getHours().toString()
       let pieceHourString = time.getMinutes().toString()
       timeString = timeString.concat(':', pieceHourString)
       pieceHourString = time.getSeconds().toString()
       timeString = timeString.concat(':', pieceHourString)
            },
    timerFormated() {
        console.log(parseInt(this.counter / 60, 10));
    //   return `${('0' + parseInt(this.workedTime / 60, 10)).slice(-2)}:${(
      return `${('0' + parseInt(this.counter / 60, 10)).slice(-2)}:${(
        '0' +
        (this.counter % 60)).slice(-2)}`;
    }
  },
  methods: {
    start() {
      console.log(this.inverval);
      if (this.interval) return this.stop();
      this.interval = setInterval(() => {
        this.counter = this.counter + 1;
      }, 1000);
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
</script>  -->
<!-- 
    
<template>
    <div>
        <h1>Countdown Timer</h1>
        <div>
            {{ formatTime(timer) }}
            {{ timer }}
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            targetDate: new Date("2023-12-31T23:59:59"), // Set your target date and time here
            timer: 0,
        };
    },
    mounted() {
        // Update the timer every second
        setInterval(this.updateTimer, 1000);
    },
    methods: {
        updateTimer() {
            const now = new Date();
            const timeDifference = this.targetDate - now;

            // Check if the target date has passed
            if (timeDifference <= 0) {
                this.timer = 0;
                // You can perform additional actions when the timer reaches zero
                // For example, display a message or trigger another function
                console.log('Timer reached zero!');
            } else {
                // Calculate remaining time and update the timer
                this.timer = timeDifference;
            }
        },
        formatTime(milliseconds) {
            const seconds = Math.floor(milliseconds / 1000) % 60;
            const minutes = Math.floor(milliseconds / (1000 * 60)) % 60;
            const hours = Math.floor(milliseconds / (1000 * 60 * 60)) % 24;
            const days = Math.floor(milliseconds / (1000 * 60 * 60 * 24));

            // return `${days}d ${hours}h ${minutes}m ${seconds}s`;
            return ` ${hours}h ${minutes}m ${seconds}s`;
        },
    },
};
</script>

<style>
/* Add your styles here if needed */
</style> -->
