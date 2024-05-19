<script setup lang="ts">
import { onMounted, ref } from 'vue'
import TodoInput from './TodoInput.vue'
import TodoList from './TodoList.vue'

const todos = ref<string[]>([])

onMounted(() => {
  const storedTodos = sessionStorage.getItem('todos')
  if (storedTodos) {
    todos.value = JSON.parse(storedTodos)
  }
})

const addTodo = (newTodo: string) => {
  todos.value.push(newTodo)
  sessionStorage.setItem('todos', JSON.stringify(todos.value))
}

const deleteTodo = (index: number) => {
  todos.value.splice(index, 1)
  sessionStorage.setItem('todos', JSON.stringify(todos.value))
}
</script>

<template>
  <div class="space-y-4 p-8">
    <TodoInput @addTodo="addTodo" />

    <TodoList :todos="todos" @deleteTodo="deleteTodo" />
  </div>
</template>
