<template>
  <h1 class="py-4">Your greeting: {{ msg }}</h1>
</template>

<script setup>
import { defineProps } from 'vue'

defineProps({
  msg: String
})
</script>