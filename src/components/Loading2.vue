<template>
  <div class="loadingOneTitle">{{ result }}</div>
</template>

<script setup lang="ts">
const result = await new Promise((resolve) => {
  setTimeout(() => {
    resolve("啦啦啦啦");
  }, 3000);
});
</script>
