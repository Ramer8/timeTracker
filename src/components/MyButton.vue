<template>
  <button
    :status="status"
    :class="[
      status === 'online' ? 'bg-orange-500' : 'bg-green-500 ',
      'rounded-full font-medium w-32 text-white px-4 py-2 text-sm'
    ]"
  >
    <slot>{{ status === 'online' ? 'Salir' : 'Entrar' }}</slot>
  </button>

  <button></button>
  <!-- <button v-show="status === 'offline' "
       class="bg-orange-600 rounded-full font-medium w-32 text-white px-2 py-1">Salir</button> -->
</template>
<script>
export default {
  props: {
    status: String,
    buttonClass: String,
  },
};
</script>
