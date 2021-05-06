<template>
  <div class="home">
    <!-- <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/> -->
    <headerBar :TodoList="propTodoList" />
    <todoFormCreation @create-task="createTask" />
    <todoListComponent :TodoList="propTodoList" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import UserServiceProvider, { Todo, TodoList } from '@/models/UserServiceProvider'
import HeaderBar from '@/components/HeaderBar.vue'
import TodoFormCreation from '@/components/TodoFormCreation.vue'
import TodoListComponent from '@/components/TodoList.vue'

export default defineComponent({
  name: 'Home',
  components: {
    HeaderBar,
    TodoFormCreation,
    TodoListComponent
  },
  data () {
    return {
      propTodoList: {} as TodoList, // Props & event
      providedUser: new UserServiceProvider('Login Url', 'avatar Url') // Provide & inject
    }
  },
  provide () {
    return {
      user: this.providedUser
    }
  },
  created () {
    this.propTodoList = new TodoList()
    const testTodo = new Todo('test task')
    const testTodo2 = new Todo('test task 2', true)
    this.propTodoList.add(testTodo)
    this.propTodoList.add(testTodo2)
  },
  methods: {
    createTask (payload: Todo) {
      this.propTodoList.add(payload)
    }
  }
})
</script>
