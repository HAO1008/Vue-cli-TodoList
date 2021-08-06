<template>
  <div class="header-container">
    <a href="javascript:;" v-if="moon" @click="modeTransform"
      ><span><i class="far fa-moon"></i></span
    ></a>
    <a href="javascript:;" v-else @click="modeTransform"
      ><span><i class="far fa-sun"></i></span
    ></a>
    <h2>TodoList</h2>
    <button class="clearbtn" @click="delFinish">刪除勾選</button>
  </div>
</template>

<script>
export default {
  props:{
    todos:Array,
    delFinish:Function,
    changeMode:Function
  },
  name: "Header",
  data(){
    return{
      moon:true,
    }
  },
  methods:{
    modeTransform(){
      this.changeMode(this.moon)
      this.moon = !this.moon
    }
  }
};
</script>

<style>
/* header */
.header-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 1rem;
}
.header-container a span {
  font-size: 1.8rem;
  color: #888;
}
.fa-sun {
  display: block;
}
.fa-moon {
  display: block;
}
.header-container h2 {
  color: #888;
}
.header-container .clearbtn {
  padding: 5px 5px;
  outline: none;
  color: #fff;
  background-color: #888;
  border: 1px solid #888;
  font-size: 0.8rem;
  cursor: pointer;
  font-weight: 700;
}
/* active */
.active .header-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 1rem;
}
.active .header-container a span {
  font-size: 1.8rem;
  color: #ffd180;
}
.active .header-container h2 {
  color: #fff;
}
.active .header-container .clearbtn {
  padding: 5px 5px;
  outline: none;
  color: #222;
  background-color: #ffd180;
  border: 1px solid #ffd180;
  font-size: 0.8rem;
  cursor: pointer;
}
</style>
