<template>
  <div class="inputBox">
    <input type="text" v-model="newTodoItem" placeholder="할일 입력하기" v-on:keyup.enter="addTodo">
    <button class="addBtn" v-on:click="addTodo">+</button>
  </div>
</template>

<script>
export default {
    data(){
        return{
            newTodoItem:'',
        }
    }
};
</script>

<style>
input:focus {
  outline: none;
}
.inputBox {
  text-align: left;
  padding-left: 10px;
  background: white;
  height: 40px;
  line-height: 40px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addBtn {
  float: right;
  height: 40px;
  background:black;
  display: inline-block;
  width: 3rem;
  font-size: 1.4rem;
  border-radius: 0 5px 5px 0;
  color: aliceblue;
}
</style>
