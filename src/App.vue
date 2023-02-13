<template>
  <nav>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink>
    <RouterLink to="/LoadingOne">LoadingOne</RouterLink>
  </nav>

  <h1 v-if="error">load async component error</h1>

  <!-- <Suspense v-else>
    <template #default>
      <RouterView />
    </template>
    <template #fallback>
      <div>
        <h1>loading</h1>
      </div>
    </template>
  </Suspense> -->

  <RouterView v-slot="{ Component }">
    <template v-if="Component">
      <Suspense>
        <component :is="Component"></component>
        <template #fallback> 正在加载... </template>
      </Suspense>
    </template>
  </RouterView>
</template>

<script setup lang="ts">
import { RouterLink, RouterView } from "vue-router";
import { onErrorCaptured, ref } from "vue";

const error = ref(null);
onErrorCaptured((e) => {
  error.value = e as any;
  return false;
});
</script>

<style scoped>
nav a.router-link-exact-active {
  color: var(--color-text);
}
</style>
