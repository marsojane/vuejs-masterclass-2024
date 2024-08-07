<script setup lang="ts">
import { useRoute } from 'vue-router'

const route = useRoute()
</script>

<template>
  <div>
    <h1>Single Project {{ route.params?.slug }}</h1>
  </div>
  <RouterLink to="/projects">Back to Projects</RouterLink>
  <br />
  <RouterLink to="/">Home</RouterLink>
</template>
