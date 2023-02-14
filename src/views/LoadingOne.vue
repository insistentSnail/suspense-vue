<template>
  <div class="loadingOneTitle">{{ data }}</div>
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
</template>

<script setup lang="ts">
import { ref } from "vue";
import SuspenseWithError from "@/components/SuspenseWithError.vue";
import MyAsyncComponent from "@/components/MyAsyncComponent.vue";
const data = ref<string>("");
const result = await new Promise((resolve) => {
  setTimeout(() => {
    resolve("刘鑫");
  }, 1000);
});
data.value = result as string;
</script>

<style lang="scss" scoped>
.loadingOneTitle {
  font-size: 30px;
  color: #f00;
}
</style>
