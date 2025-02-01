<script setup lang="ts">
import { ref } from 'vue';
import SingleTodo from '@/components/SingleTodo.vue';

const todos = ref<string[]>([]);

const todoName = ref('');

function addTodo() {
  todos.value.push(todoName.value);
}
</script>

<template>
  <main>
    <div class="my-8">
      <template v-if="todos.length > 0">
        <div v-for="(todo, index) in todos" :key="index">
          <SingleTodo :todo-text="todo" />
        </div>
      </template> 
      <p v-else>You are done with all tasks</p>
    </div>
    <input type="text" v-model="todoName" @keyup.enter="addTodo" />
    <button @click="addTodo">add a todo</button>
  </main>
</template>
