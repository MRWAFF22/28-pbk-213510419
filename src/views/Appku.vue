<script setup>
import { ref, computed } from 'vue'

let id = 0

const newTodo = ref('')
const hideCompleted = ref(true)
const todos = ref([
  { id: id++, text: 'Belajar Program JS', done: true },
  { id: id++, text: 'Olahraga', done: true },
  { id: id++, text: 'Belajar Tailwind', done: false }
])

const filteredTodos = computed(() => {
  return hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  todos.value = todos.value.filter((t) => t !== todo)
}
</script>

<template>
  <div class="container mx-auto">
    <div class="text-center">
      <form @submit.prevent="addTodo">
        <div class="mb-6 px-10 md:px-0">
          <label class="block mb-2 text-lg font-medium text-gray-900 dark:text-white">Tambahkan Kegiatan</label>
          <input type="text"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-lime-500 focus:border-lime-500 p-2.5 w-full lg:w-1/2"
            v-model="newTodo">
        </div>
        <button
          class="text-white bg-lime-700 hover:bg-lime-800 focus:outline-none focus:ring-4 focus:ring-lime-300 font-medium rounded-md text-sm px-5 py-2.5 text-center mr-2 mb-2">Tambahkan</button>
      </form>
    </div>
    <ul
      class="w-1/2 mt-4 flex-row mx-auto items-center text-sm font-medium text-gray-900 bg-lime-200 border border-slate-300 rounded-lg">
      <li class="p-2" v-for="todo in filteredTodos" :key="todo.id">
        <div class="items-center flex justify-center">
          <input type="checkbox"
            class="w-4 h-4 text-lime-600 bg-gray-100 border-gray-300 rounded focus:ring-lime-500 mr-2"
            v-model="todo.done">
          <span :class="{ done: todo.done }">{{ todo.text }}</span>
          <button class="ml-2 rounded-lg bg-red-400 hover:bg-red-600" @click="removeTodo(todo)">✖</button>
        </div>
      </li>
    </ul>
    <div class="text-center">
      <button
        class="mt-4 text-white bg-lime-700 hover:bg-lime-800 focus:outline-none focus:ring-4 focus:ring-lime-300 font-medium rounded-md text-sm px-5 py-2.5 mr-2 mb-2"
        @click="hideCompleted = !hideCompleted">
        {{ hideCompleted ? 'Tampilkan Semua' : 'Tampilkan yang belum selesai' }}
      </button>
    </div>
  </div>
</template>

<style>
.done {
  text-decoration: line-through;
}</style>

