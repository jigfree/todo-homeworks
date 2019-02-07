<template>
  <div class="inputBox">
    <input type="text" v-model="newItem" placeholder="할일을 입력후 추가해 주세요." v-on:keyup.enter="addItem">
    <button class="addBtn" v-on:click="addItem">+</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newItem: ""
    };
  },
  methods: {
    addItem() {
      if (this.newItem !== "") {
        var str = this.newItem;
        this.$emit("addItem", str);
        this.clearText();
      } else {
        alert("할일을 입력해주세요.");
      }
    },
    clearText() {
      this.newItem = "";
    }
  },
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
  width: calc(100% - 4rem);
  border-style: none;
  background: white;
  font-size: 0.9rem;
  color: rgb(137, 11, 179);
}
::placeholder {
  color: rgb(242, 174, 174);
}

.addBtn {
  float: right;
  height: 40px;
  background: rgb(12, 2, 7);
  color: rgb(231, 250, 106);

  width: 3.5rem;
  font-size: 1.6rem;
  border-radius: 0 5px 5px 0;
  font-weight: bold;
  text-shadow: 1px 1px 1px rgb(50, 34, 0);
  cursor: pointer;
}
.addBtn:hover {
  background: rgb(254, 1, 119);
  color: white;
}

.addBtn:focus {
  outline: none;
}
</style>
