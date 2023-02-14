<template>
  <SuspenseWithError>
    <template #default>
      <MyAsyncComponent :timeout="1000" />
    </template>
    <template #fallback>
      <h1>Loading... Please wait 1s.</h1>
    </template>
    <template #error>
      <h1>I failed to load</h1>
    </template>
  </SuspenseWithError>
  <SuspenseWithError>
    <template #default>
      <MyAsyncComponent :timeout="2000" should-fail />
    </template>
    <template #fallback>
      <h1>Loading... Please wait 2s.</h1>
    </template>
    <template #error>
      <h1>I failed to load</h1>
    </template>
  </SuspenseWithError>
  <SuspenseWithError>
    <template #default>
      <MyAsyncComponent :timeout="3000" />
    </template>
    <template #fallback>
      <h1>Loading... Please wait 3s.</h1>
    </template>
    <template #error>
      <h1>I failed to load</h1>
    </template>
  </SuspenseWithError>
</template>
<script setup lang="ts">
import SuspenseWithError from "@/components/SuspenseWithError.vue";
import MyAsyncComponent from "@/components/MyAsyncComponent.vue";
await new Promise<void>((resolve) => {
  setTimeout(() => {
    resolve();
  }, 1000);
});
</script>
