<template>
  <button @click.once="display = true">display</button>
  <div v-if="display">
    <LazyBlog />
  </div>
</template>

<script setup lang="ts">
import { ref, defineAsyncComponent } from 'vue';

const LazyBlog = defineAsyncComponent({
  loader: () =>
    new Promise<any>((resolve) => {
      setTimeout(() => {
        import('./Blog.vue').then((c) => resolve(c));
      }, 3000);
    }),
  loadingComponent: Loader,
  delay: 200,
  errorComponent: Error,
  timeout: 2000,
});

const display = ref(false);
</script>

<style scoped lang="scss"></style>
