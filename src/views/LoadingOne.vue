<template>
  <div class="loadingOneTitle">{{ data }}</div>
  <Suspense>
    <template #default>
      <A></A>
    </template>
    <template #fallback>
      <div>loading</div>
    </template>
  </Suspense>
</template>

<script setup lang="ts">
import { ref, defineAsyncComponent } from "vue";
const A = defineAsyncComponent(() => import("@/components/Loading1.vue"));
const data = ref<string>("");
const result = await new Promise((resolve) => {
  setTimeout(() => {
    resolve("刘鑫");
  }, 3000);
});
data.value = result as string;
</script>

<style lang="scss" scoped>
.loadingOneTitle {
  font-size: 30px;
  color: #f00;
  &:hover {
    color: #0f0;
  }
}
</style>
