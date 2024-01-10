<template >
<p class= "bg-slate-800 rounded-lg text-yellow-200">
    Hello from Main Menu
</p>
<button @click="$emit('closeMenu')" class="bg-blue-300 p-2 rounded-lg">Close Main Menu</button>
<button @click="$emit('MsgFromRoot')" class="bg-blue-200 p-2 rounded-lg">MSG</button>

<input type="text" v-model="name" placeholder="enter name.." @keyup.enter="$emit('getValue', name)">
<button class="text-white" @click="$emit('change', value = !isMenuOpen)">change</button>

<input
type="checkbox"
id="checkbox"
v-model="value"
@input="$emit('change', value , console.log(value))" />
{{ name }}
</template>
<script>

export default {
  data() {
    return {
      name: '',
      value: this.isMenuOpen,
    };
  },
  emits: ['closeMenu', 'MsgFromRoot', 'getValue', 'change',
  ],
  props: {
    isMenuOpen: Boolean,
  },
  methods: {
    MsgFromRoot() {
      this.$emit('MsgFromRoot');
    },
    closeMenu() {
      this.$emit('closeMenu');
    },

  },
};
</script>
