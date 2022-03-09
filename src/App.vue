<template>
  <button @click="count++">{{ count }}</button>
  <div>
    <Blog />
  </div>
</template>

<script setup lang="ts">
import { toRef, reactive, isReactive, isRef } from 'vue';
import Blog from './Blog.vue';

const state = reactive({
  count: 0,
  user: {},
});

const count = toRef(state, 'count');

console.log(isReactive(state));
console.log(isReactive(count));
console.log(isRef(state));
console.log(isRef(count));
</script>

<style scoped lang="scss"></style>
