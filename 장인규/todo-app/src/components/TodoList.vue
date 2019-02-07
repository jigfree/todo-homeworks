<template>
  <div>
    <ul>
      <li  v-for="(item, index) in propsdata" :key="item.key" v-on:click="toggleCheck(item.key, index, item.isDone)" :class="{'todoComplete_li':item.isDone === true}">
        <span v-if="item.isDone === true" class="item_txt todoComplete">{{item.value}}</span>
        <span v-else class="item_txt">{{item.value}}</span>
        <!-- <span class="item_txt">{{item.value}}</span> -->
        <button class="removeBtn" v-on:click="removeItems(item.key, index)">-</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    removeItems($todoItem, $idx) {
      event.stopPropagation();
      this.$emit("removeItems", $todoItem, $idx);
    },
    toggleCheck($todoItem, $idx, state) {
      event.stopPropagation();
      event.target.classList.toggle("todoComplete");
      event.target.parentElement.classList.toggle('todoComplete_li')
        this.$emit("toggleCheck", $todoItem, $idx, !state);
    }
  }
};
</script>

<style>
.item_txt {
  width: calc(100% - 3.5rem);
  overflow: hidden;
  padding-left: 0.9rem;
  cursor: pointer;
}



ul {
  list-style-type: none;
  padding: 0px;
  margin-top: 0px;
  text-align: left;
}
li {
  display: flex;
  height: 40px;
  line-height: 40px;
  background: rgb(231, 250, 106);
  margin: 0.6rem 0;
  border-radius: 6px;
}
li:hover{
  margin-left: 7px;
  opacity: 0.8;
}


.removeBtn {
  z-index: 1;
  height: 40px;
  background: rgb(23, 23, 23);
  width: 3.5rem;
  font-size: 1.6rem;
  border-radius: 0 6px 6px 0;
  color: rgb(231, 250, 106);
  font-weight: bold;
  text-shadow: 1px 1px 1px rgb(50, 34, 0);
  cursor: pointer;
}
.removeBtn:hover{
  /* background: rgb(255, 70, 70); */
  background: rgb(176, 0, 82);
  color: white;
}
.removeBtn:focus {
  outline: none;
}

.todoComplete {
  color: gray;
  text-decoration: line-through;
}

.todoComplete_li {
    background:rgb(201, 201, 201)
}
</style>
