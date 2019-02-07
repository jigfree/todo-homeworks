<template>
    <div class="topArea">
      <h2 class="title">jigfree's Todo App</h2>
      <button class="removeAllBtn" v-on:click="removeAll">Reset</button>
     </div>
</template>

<script>
export default {
    methods:{
      removeAll(){
          this.$emit('removeAll');
      }
    }
}
</script>

<style>

.topArea{
  min-height: 70px;
  width: 100%;
  margin-bottom: 10px ;
}

.topArea .title {
  color: white;
  position: relative;
  height: 30px;
}
 .removeAllBtn {
  float: right;
  height: 30px;
  width: 3.5rem;
  background: rgb(96, 96, 96);
  font-size: 0.9rem;
  border-radius: 0px;
  color: rgb(255, 255, 255);
}
.removeAllBtn:focus {
  outline: none;
}
</style>
