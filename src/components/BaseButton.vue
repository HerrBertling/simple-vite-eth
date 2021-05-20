<template>
  <button
    class="py-4 px-6 text-white rounded-md bg-blue-500 hover:bg-blue-600" 
    @click="$emit('click')"
  >
    <slot />
  </button>
</template>
<script>
  export default {
    name: 'BaseButton',
    emits: ['click']
  }
</script>