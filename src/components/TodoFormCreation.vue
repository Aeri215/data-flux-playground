<template>
  <div>
    <form>
      <input type="text" v-model="title">
      <button type="submit" @click="addTask">
        Ajouter la tâche Liste Props & events
      </button>
    </form>
    <form>
      <input type="text" v-model="title2">
      <button type="submit" @click="addTask2">
        Ajouter la tâche Liste Provide & inject
      </button>
    </form>
  </div>
</template>

<script>
import { Todo } from '@/models/UserServiceProvider'
export default {
  inject: ['user'],
  data () {
    return {
      title: 'Chose à faire',
      title2: 'Chose à faire'
    }
  },
  methods: {
    addTask () {
      if (this.title.length > 0) {
        this.$emit('createTask', new Todo(this.title))
        this.title = ''
      }
    },
    addTask2 () {
      if (this.title2.length > 0) {
        this.user.todoList.add(new Todo(this.title2))
        this.title2 = ''
      }
    }
  }
}
</script>

<style>

</style>
