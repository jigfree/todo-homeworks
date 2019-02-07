<template>
  <div id="app">
    <h2>jigfree's Todo App</h2>
    <todoInput>input</todoInput>
    <todoList>list</todoList>
    <button>RemoveAll</button>
  </div>
</template>

<script>
import todoInput from './components/TodoInput.vue'

var TodoList = {
   props:['propsdata'],
  template:`<div>
    <ul>
      <li>1</li>
      <li>2</li>
      <li>3</li>
    </ul>
  </div>`,
}

export default {
  data(){
    return{
      newTodoItem:'',
    }
  },
  components: {
    'todoInput': todoInput,
    'todoList': TodoList,
  }
}
</script>

<style>
 body {
    text-align: center;
    background-color: #F6F6F8;
  }

  input {
    border-style: none;
    width: 200px;
  }
  
  button {
    border-style: none;
  }
  
 
</style>
