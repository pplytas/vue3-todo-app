<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits<{ addTodo: [newTodo: string] }>()

const newTodo = ref('')
const input = ref<HTMLInputElement>()

const addTodo = () => {
  emit('addTodo', newTodo.value)
  newTodo.value = '' // Reset the input
  input.value?.focus() // Focus the input
}
</script>

<template>
  <form class="space-x-2" @submit.prevent="addTodo">
    <input
      ref="input"
      class="border border-slate-900 h-[40px] px-3 rounded-md shadow"
      type="text"
      v-model="newTodo"
      autofocus
    />
    <button class="bg-slate-900 text-gray-100 rounded-md shadow h-[40px] px-4">Save</button>
  </form>
</template>
