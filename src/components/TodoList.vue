<template>
  <div>
    <ul>
      <li v-for="(todoItem, index) in propsdata" v-bind:key="index">
        <div> {{todoItem}} </div>
        <button v-on:click="removeTodo(todoItem, index)">delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TodoList",
  props: ['propsdata'],

  methods: {
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index);
    }
  }
}
</script>

<style scoped>
li {
  width: 300px;
  display: flex;
  justify-content: space-between;
}
</style>