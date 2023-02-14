<template>
  <nav>
    <RouterLink to="/" class="link">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink>
    <RouterLink to="/LoadingOne"> LoadingOne </RouterLink>
  </nav>

  <router-view v-slot="{ Component }">
    <Suspense timeout="0">
      <template #default>
        <component :is="Component" />
      </template>

      <template #fallback>
        <Loading />
      </template>
    </Suspense>
  </router-view>
</template>

<script setup lang="ts">
import Loading from "@/components/Loading.vue";
</script>

<style lang="scss" scoped>
#app {
  a {
    color: #000;
    margin-right: 20px;
    font-size: 30px;
    &.router-link-exact-active {
      color: #f00;
    }
  }
}
</style>
