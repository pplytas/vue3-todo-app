<script setup lang="ts">
import { XIcon } from 'lucide-vue-next'

defineProps<{ todos: string[] }>()
defineEmits<{ deleteTodo: [index: number] }>()
</script>

<template>
  <ul class="space-y-2 list-disc list-inside">
    <li v-for="(todo, index) in todos" v-bind:key="todo" class="space-x-2">
      <span>{{ todo }}</span>
      <button
        class="rounded-full p-1 bg-red-100 hover:bg-red-200"
        @click="$emit('deleteTodo', index)"
      >
        <XIcon aria-label="trash" class="w-4 h-4 text-red-400" />
      </button>
    </li>
  </ul>
</template>
