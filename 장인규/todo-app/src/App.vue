<template>
  <div id="app">
    <todoHeader v-on:removeAll="removeAll"></todoHeader>
    <todoInput v-on:addItem="addTodoList"></todoInput>
    <todoList v-bind:propsdata="todoListItems" v-on:removeItems="removeTodoList"></todoList>
  </div>
</template>

<script>
import todoHeader from "./components/TodoHeader.vue";
import todoInput from "./components/TodoInput.vue";
import todoList from "./components/TodoList.vue";

export default {
  data() {
    return {
      todoListItems: []
    };
  },
  methods: {
    addTodoList($item) {
      var newKey = "k"+(new Date().getTime()).toString(); 
      var data = {"key":newKey , "value":$item};
      this.todoListItems.push(data);
      localStorage.setItem(newKey, $item);     
    },
    removeTodoList($todoItem, $idx){
      localStorage.removeItem($todoItem);
      this.todoListItems.splice($idx,1);
    },
    removeAll(){
      localStorage.clear();
      this.todoListItems = [];
    }
  },
  created(){
    if(localStorage.length > 0){
      for(var i=0;i<localStorage.length;i++){
        if(localStorage.key(i) === 'loglevel:webpack-dev-server') continue;        
         var key = localStorage.key(i);
         var value = localStorage[localStorage.key(i)];
         var data = {"key":key , "value":value};
        this.todoListItems.push(data);
      }
    }
  },
  components: {
    todoHeader: todoHeader,
    todoInput: todoInput,
    todoList: todoList
  }
};
</script>

<style>
body {
  text-align: center;
  background-color: rgb(36, 36, 36);
}

</style>
