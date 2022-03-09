<template>
  <button @click.once="display = true">display</button>
  <div v-if="display">
    <Blog />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import Blog from './Blog.vue';

const display = ref(false);
</script>

<style scoped lang="scss"></style>
