<template>
  <div class="dialog" v-show="switchBtn">
    <div class="close" @click="bigClose"><i class="fas fa-times"></i></div>
    <input
      type="text"
      placeholder="請輸入想做的事情"
      v-model="title"
      @keyup.enter="addItem"
    />
    <input type="date" v-model="date" @keyup.enter="addItem" />
    <input type="button" value="送出" class="sendbtn" @click="addItem" />
  </div>
</template>

<script>
export default {
  name: "Task",
  props: {
    addTodo: Function,
    closeSwitch:Function,
    switchBtn:Boolean
  },
  data() {
    return {
      title: "",
      date: "",
      close:false
    };
  },
  methods: {
    // 添加數據
    addItem() {
      const title = this.title.trim(); //輸入任務
      const date = this.date; //日期
      console.log(title);
      console.log(date);
      if (!title || !date) {
        alert("請輸入完整資料");
        return;
      }
      let todo = { title, date };
      this.addTodo(todo);
      this.title = "";
      this.date = "";
      this.closeSwitch(this.close)
    },
    bigClose(){
      this.closeSwitch(this.close)
    }
  },
};
</script>

<style>
/* dialog */
.dialog{
  position: fixed;
  top: 0;
  width: 100%;
  height: 100vh;
  background-color: rgba(34, 34, 34, 0.9);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.dialog input {
  width: 250px;
  height: 40px;
  margin: 20px;
  outline: none;
  border: none;
  padding: 10px;
  border-radius: 5px;
}

.sendbtn {
  background-color: rgb(127, 127, 212);
  color: #fff;
  padding: 0;
}
.close{
  position: absolute;
  top: 10%;
  right: 10%;
  color: #fff;
  font-size: 2rem;
  cursor: pointer;
}
/* avtive */
.active input{
  background-color: #222;
  border: 1px solid #fff;
  color: #fff;
}
.active .sendbtn {
  background-color: #ffd180;
  color: #222;
  border: none;
}
.active input[type=date]::-webkit-calendar-picker-indicator{
  background-color: #ffd180;
  border-radius: 50%;
}
.active .close{
  color: #ffd180;
}
</style>
