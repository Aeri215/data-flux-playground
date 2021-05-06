<template>
  <div>
    <h1>
      Titre
    </h1>
    <p>Nombre de tâche non cloturés : {{ TodoList.items.filter(a => a.isDone !== true).length }}</p>
  </div>
</template>

<script>
import { TodoList } from '@/models/UserServiceProvider'
export default {
  props: {
    TodoList: {
      type: TodoList,
      default: new TodoList()
    }
  }
}
</script>

<style>

</style>
