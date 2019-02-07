<template>
  <div id="app">
    <todoHeader v-on:removeAll="removeAll"></todoHeader>
    <todoInput v-on:addItem="addTodoList"></todoInput>
    <todoList v-bind:propsdata="todoListItems" v-on:removeItems="removeTodoList" v-on:toggleCheck="changeDone"></todoList>
  </div>
</template>

<script>
import todoHeader from "./components/TodoHeader.vue";
import todoInput from "./components/TodoInput.vue";
import todoList from "./components/TodoList.vue";

export default {
  data() {
    return {
      todoListItems: [],
    };
  },
  methods: {
    addTodoList($item) {
      var newKey = "k" + new Date().getTime().toString();
      var data = { key: newKey, value: $item, isDone: false };
      this.todoListItems.push(data);
      localStorage.setItem(newKey, JSON.stringify(data));
    },
    removeTodoList($todoItem, $idx) {
      localStorage.removeItem($todoItem);
      this.todoListItems.splice($idx, 1);
    },
    removeAll() {
      localStorage.clear();
      this.todoListItems = [];
    },
    changeDone($todoItem, $idx, state) {
      this.todoListItems[$idx].isDone = state
      var data = this.todoListItems[$idx];
      console.log(data)
      localStorage.setItem($todoItem, JSON.stringify(data));
    }
  },
  created() {
    if (localStorage.length > 0) {
      for (var i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) === "loglevel:webpack-dev-server") continue;
        var strData = localStorage[localStorage.key(i)];
        var jsonObj = JSON.parse(strData);
        this.todoListItems.push(jsonObj);
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
