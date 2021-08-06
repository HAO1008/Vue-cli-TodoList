<template>
  <div>
    <button class="addbtn" @click="changeSwitch">
      <span></span>
      <span></span>
    </button>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props:{
    openSwitch:Function
  },
};
</script>

<style>
/* nav */
.addbtn {
  position: fixed;
  bottom: 5%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: rgb(127, 127, 212);
  width: 80px;
  height: 80px;
  border: none;
  border-radius: 50%;
  box-shadow: 1px 1px 3px 0.1px #222;
}
.addbtn span {
  background-color: #fff;
  width: 30px;
  height: 2px;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
.addbtn span:nth-child(2) {
  transform: rotate(90deg);
  left: 32.5%;
}
/* active */
.active .addbtn {
  position: fixed;
  bottom: 5%;
  left: 50%;
  transform: translate(-50%, -50%);
  background-color: #ffd180;
  width: 80px;
  height: 80px;
  border: none;
  border-radius: 50%;
  box-shadow: 1px 1px 3px 0.1px #666;
}
.active .addbtn span {
  background-color: #222;
}
</style>
