<script setup lang="ts">
const route = useRoute()
</script>

<template>
  <div>
    <h1>Single Task {{ route.params?.id }}</h1>
  </div>
  <RouterLink to="/tasks">Back to Tasks</RouterLink>
  <br />
  <RouterLink to="/">Home</RouterLink>
</template>
