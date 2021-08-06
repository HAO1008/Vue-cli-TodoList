<template>
  <div :class="isActive?'active':''">
    <!-- header -->
    <Header :todos="todos" :del-finish="delFinish" :change-mode="changeMode"></Header>
    <!-- main -->
    <Main :todos="todos"></Main>
    <!-- nav -->
    <Footer @click="openSwitch"></Footer>
    <!-- task -->
    <Task :add-todo="addTodo" :close-switch="closeSwitch" :switch-btn="switchBtn"></Task>
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Main from "./components/Main.vue";
  import Footer from "./components/Footer.vue";
  import Task from "./components/Task.vue";


  export default {
    name:'app',
    data(){
      return{
        todos:[
          {title:'到104投履歷',date:'2021-07-26',finished:false},
          {title:'到貴公司面試',date:'2021-07-28',finished:false},
          {title:'到貴單位報到',date:'2021-08-02',finished:false},
        ],
        switchBtn:false,
        isActive:false
      }
    },
    methods:{
      addTodo(todo){
        this.todos.unshift(todo)
      },
      delFinish(){
        this.todos = this.todos.filter((todo)=>{
          return !todo.finished
        })
      },
      openSwitch(){
        this.switchBtn = true
        console.log(this.switchBtn);
      },
      closeSwitch(close){
        this.switchBtn = close
      },
      changeMode(mode){
        this.isActive = mode
      }
    },
    components:{
      Header,
      Main,
      Footer,
      Task
    }
  }
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  font-family: Arial, Helvetica, sans-serif;
}
ul {
  list-style: none;
}
a {
  text-decoration: none;
}
.active{
  background-color: #222;
  position: absolute;
  width: 100%;
  height: 100vh;
}
/* media */
@media (min-width: 768px) {
  /* header */
  .header-container {
    justify-content: space-around;
    margin: 1.8rem;
  }
  .header-container a i {
    font-size: 2rem;
  }
  .header-container h2 {
    font-size: 2rem;
  }
  .header-container .clearbtn {
    padding: 8px 16px;
    font-size: 1rem;
  }
  /* main */
  .main-container {
    margin: 10% auto;
  }
  .content {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
  }
  .content li {
    margin: 10px 10px;
    padding: 12%;
  }
  /* dialog */
  dialog div input {
    width: 350px;
    height: 50px;
    margin: 20px;
    font-size: 1.2rem;
  }
}
@media (min-width: 1024px) {
  /* header */
  .header-container {
    margin: 2rem;
  }
  .header-container a i {
    font-size: 2.5rem;
  }
  .header-container h2 {
    font-size: 2.5rem;
  }
  .header-container .clearbtn {
    padding: 10px 20px;
    font-size: 1.2rem;
  }
  /* main */
  .content {
    grid-template-columns: repeat(4, 1fr);
  }
  .content li {
    padding: 15%;
  }
  /* dialog */
  dialog div input {
    width: 500px;
    height: 60px;
    margin: 25px;
    font-size: 1.5rem;
  }
}
</style>
