<script setup lang="ts">
import { supabase } from '@/lib/supabaseClient'
import { ref } from 'vue'
import type { Tables } from 'database/types'

const tasks = ref<Tables<'tasks'>[] | null>(null)

const getTasks = async () => {
  const { data, error } = await supabase.from('tasks').select()

  if (error) console.log(error)

  tasks.value = data
}

;(async () => {
  //anonymous function (gets invoked directly = IIF = Immediately Invoked Function Expression)
  getTasks()
})()
</script>

<template>
  <div>
    <h1>Tasks Page</h1>
    <RouterLink to="/">Home</RouterLink>

    <div id="projects">
      <li v-for="task in tasks" :key="task.id">
        {{ task.name }}
      </li>
    </div>
  </div>
</template>
