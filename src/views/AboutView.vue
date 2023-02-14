<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script lang="ts">
export default {
  async setup() {
    await new Promise((resolve) => {
      setTimeout(() => {
        resolve("success");
      }, 2000);
    });
  },
};
</script>
