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
      var ranKey = "k"+(new Date().getTime()).toString(); 
      var data = {ranKey, $item};
      this.todoListItems.push(data);//[ranKey.toString()] = $item;
      localStorage.setItem(ranKey, $item);
      //this.todoListItems.keys({String(ranKey),$item});
     
    },
    removeTodoList($todoItem, $idx){
      localStorage.removeItem($todoItem);
      this.todoListItems.splice($idx,1);
      //delete this.todoListItems[$todoItem];
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

        this.todoListItems.push(localStorage.key(i));
        // var key = localStorage.key(i);
        // var value = localStorage[localStorage.key(i)];
        // var data = {key, value};

        // console.log(key)
        // console.log(value)
        // this.todoListItems.push(data);

        // console.log(this.todoListItems)
        //this.todoListItems[localStorage.key(i)] = localStorage[localStorage.key(i)];
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
