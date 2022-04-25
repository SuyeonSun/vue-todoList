<template>
  <div class="inputDiv shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" >
    <button type="button" class="btn btn-primary inputBtn" v-on:click="addTodo" >add</button>
  </div>
</template>

<script>
export default {
  name: "TodoInput",
  data() {
    return {
      newTodoItem: ''
    }
  },
  methods: {
    addTodo() {
      let todoItem = this.newTodoItem;
      if (todoItem !== '') {
        this.$emit("addTodo", todoItem);
      }
    }
  }
}
</script>

<style scoped>
/*input:focus {*/
/*  outline: none;*/
/*}*/

/*.inputDiv {*/
/*  background: white;*/
/*  height: 50px;*/
/*  line-height: 50px;*/
/*  border-radius: 5px;*/
/*}*/

/*.inputDiv input {*/
/*  border-style: none;*/
/*  font-size: 0.9rem;*/
/*  height: 90%;*/
/*  padding: 0;*/
/*}*/

/*.inputBtn {*/
/*  color: black;*/
/*  background-color: white;*/
/*  border-style: none;*/
/*}*/
</style>