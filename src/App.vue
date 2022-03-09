<template>
  <button @click.once="display = true">display</button>
  <div v-if="display">
    <LazyBlog />
  </div>
</template>

<script setup lang="ts">
import { ref, defineAsyncComponent } from 'vue';
import AppError from './AppError.vue';
import AppLoader from './AppLoader.vue';

const LazyBlog = defineAsyncComponent({
  loader: () =>
    new Promise<any>((resolve) => {
      setTimeout(() => {
        import('./Blog.vue').then((c) => resolve(c));
      }, 3000);
    }),
  loadingComponent: AppLoader,
  delay: 200,
  errorComponent: AppError,
  timeout: 2000,
});

const display = ref(false);
</script>

<style scoped lang="scss"></style>
