<template>
  <TodoHeader></TodoHeader>
  <TodoInput v-on:addTodo="addTodo"></TodoInput>
  <TodoList v-bind:propsdata="todoItems" v-on:removeTodo="removeTodo"></TodoList>
</template>

<script>
import TodoHeader from "@/components/TodoHeader";
import TodoInput from "@/components/TodoInput";
import TodoList from "@/components/TodoList";

export default {
  name: 'App',
  props: ["propsdata"],
  components: {
    TodoList,
    TodoHeader,
    TodoInput,
  },
  data() {
    return {
      todoItems:[]
    }
  },
  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1)
    }
  },
  created() {
    if (localStorage.length > 0) {
      for (let i=0; i<localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
      }
    }
  }
}
</script>

<style>
body {
  text-align: center;
  background-color: paleturquoise;
  vertical-align: middle;
}

input {
  border-style: groove;
  width: 200px;
}
</style>
