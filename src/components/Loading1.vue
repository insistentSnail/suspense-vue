<template>
  <div class="loadingOneTitle">{{ result }}</div>
</template>

<script setup lang="ts">
const result = await new Promise((resolve) => {
  setTimeout(() => {
    resolve("哈哈哈哈");
  }, 3000);
});
</script>
