<template>
  <h1>
    Liste Props & events
  </h1>
  <ol>
    <li
      v-for="task in TodoList.items"
      :key="task.title"
      :class="{ done: task.isDone }"
    >
      {{ task.title }}
      <button style="margin-left: 10px;" @click="task.toggle()">
        Done
      </button>
    </li>
  </ol>
  <h1>
    Liste Provide & inject
  </h1>
  <ol>
    <li
      v-for="task in user.todoList.items"
      :key="task.title"
      :class="{ done: task.isDone }"
    >
      {{ task.title }}
      <button style="margin-left: 10px;" @click="task.toggle()">
        Done
      </button>
    </li>
  </ol>
</template>

<script>
import { TodoList } from '@/models/UserServiceProvider'
export default {
  inject: ['user'],
  props: {
    TodoList: {
      type: TodoList,
      default: new TodoList()
    }
  }
}
</script>

<style>
.done {
  font-weight: bold;
  color: green;
}
</style>
