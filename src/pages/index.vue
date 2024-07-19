<script setup lang="ts"></script>

<template>
  <div>
    <h1>Home Page</h1>
    <RouterLink to="/projects">Projects</RouterLink>
    <br />
    <RouterLink to="/tasks">Tasks</RouterLink>
    <br /><br />
    <RouterLink :to="{ name: '/projects/[id]', params: { id: 1 } }">Got to Project 1</RouterLink>
    <br />
    <RouterLink :to="{ name: '/projects/[id]', params: { id: 2 } }">Got to Project 2</RouterLink>
  </div>
</template>
