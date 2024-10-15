<script setup>
const msg = ref('to do list')
const editing = ref(false)
const todoItem = ref('')

const characterCount = computed(() => {
  return todoItem.value.length
})

const todoListItems = ref([
  //{id: 1, label: "study Vue.js"},
  //{id: 2, label: "write code"},
])

const todoListItemsReversed = computed(() => {
  return [...todoListItems.value].reverse()
})

const addToList = () => {
  todoListItems.value.push({
    id: todoListItems.value.length + 1,
    label: todoItem.value,
    done: false
  })

  todoItem.value = ''
}

const doEdit = (e) => {
  editing.value = e
}

const markAsDone = (item) => {
  item.done = !item.done
}
</script>

<template>
  <h1>{{ msg.toLocaleUpperCase() }}</h1>
  <div class="flex">
    <Button v-if="editing" @click="doEdit(false)" variant="outline">Nevermind</Button>
    <Button v-else @click="doEdit(true)" variant="destructive">I have something to do! </Button>
  </div>

  <form @submit.prevent="addToList" v-if="editing" class="flex">
    <Input v-model="todoItem" class="w-1/4" />
    <Button><iconify-icon class="pr-2" icon="lucide:plus"></iconify-icon>Add</Button>
  </form>
  <p v-if="editing" class="counter">{{ characterCount }} /200</p>
  <h6>
    Recently added: <span :data-todo="todoItem">{{ todoItem }}</span>
  </h6>

  <ul>
    <li
      v-for="(item, i) in todoListItemsReversed"
      :key="item.id"
      :class="{ 'line-through': item.done }"
      class="static-class"
    >
      <label :for="'check_' + item.id">
        <Checkbox
          :id="'check_' + item.id"
          :checked="item.done"
          @click="markAsDone(item)"
        ></Checkbox>
        {{ item.label }}
      </label>
    </li>
  </ul>

  <p v-if="!todoListItems.length">Nothing on the list</p>
</template>

<style>
input {
  margin-right: 0.5rem;
}
</style>
