<script setup>

import {useTodoListStore} from "@/stores/todoList";
import {storeToRefs} from "pinia";

const store = useTodoListStore()

const {todoList} = storeToRefs(store)
// helper method - bring in properties from the store by creating ref for the properties

const {toggleCompleted} = store
const {deleteTodo} = store

</script>

<template>
  <div v-for="todo in todoList" :key="todo.id" class="item">
    <div class="content">
      <span :class="{completed: todo.completed}">{{ todo.item}}</span>
      <span @click.stop="toggleCompleted(todo.id)">&#10004;</span>
      <span @click.stop="deleteTodo(todo.id)">&#10006;</span>

    </div>
  </div>
</template>

<style scoped>
.completed {
  text-decoration: line-through;
}
</style>