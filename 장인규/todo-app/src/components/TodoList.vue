<template>
    <div>
        <ul>
            <li v-for="(item, index) in propsdata" :key="item.key">
                <span class="item_txt">{{item.value}}</span>
                <button class="removeBtn" v-on:click="removeItems(item.key, index)">-</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    props:['propsdata'],
    methods:{
        removeItems($todoItem, $idx){
            this.$emit('removeItems', $todoItem, $idx);
        }
    }

}
</script>

<style>
.item_txt{
    width: calc(100% - 3.5rem);
    overflow: hidden;
}
ul{
    list-style-type: none;
    padding:0px;
    margin-top: 0px;
    text-align: left;
}
li{
    display: flex;
    height: 40px;
    line-height: 40px;
    background: rgb(211, 211, 211);
    margin: 0.6rem 0;
    padding-left: 0.9rem;
    border-radius: 6px;
}

.removeBtn {
  height: 40px;
  background:rgb(171, 171, 171);
  width: 3.5rem;
  font-size: 1.6rem;
  border-radius: 0 6px 6px 0;
  color: rgb(255, 174, 0);
  font-weight: bold;
  text-shadow: 1px 1px 1px rgb(50, 34, 0);
}
.removeBtn:focus{
  outline: none;
}
</style>
