<template>
  <div>
    <li @click="dealShow()">
      {{todo.title}}
      <span class="date">{{todo.date}}</span>
      <span class="font" v-show="this.todo.finished"><i class="fas fa-check-circle"></i></span>
    </li>
  </div>
</template>

<script lang="ts">
export default {
  name: "Item",
  props:{
    todo:Object
  },
  data(){
    return{

    }
  },
  methods:{
    dealShow(){
      this.todo.finished = !this.todo.finished
    }
  }
};
</script>

<style>
.content li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 5% 3%;
  box-shadow: 1.2px 1.5px 5px 0.1px #999;
  border-radius: 10px;
  margin-bottom: 8%;
  cursor: pointer;
}
.content li .font {
  color: rgb(127, 127, 212);
  font-size: 1.5rem;
}
.date {
  color: #888;
}
/* active */
.active .content li {
  box-shadow: 1.2px 1.5px 5px 0.1px #444;
  color: #fff;
}
.active .content li .font {
  color: #ffd180;
}
.active .date {
  color: #ffd180;
}
</style>
