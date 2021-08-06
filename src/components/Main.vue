<template>
  <div class="main-container">
    <ul class="content">
        <Item v-for="(todo,index) in todos" :key="index" :todo="todo"></Item>
    </ul>
  </div>
</template>

<script>
import Item from "./Item.vue";
export default {
  name: "Main",
  props:{
    todos:Array
  },
  components:{
    Item
  }
};
</script>

<style>
/* main */
.main-container {
  width: 90%;
  margin: 15% auto;
}
.content {
  display: block;
}
</style>
