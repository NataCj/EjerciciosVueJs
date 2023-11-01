<script setup>
import { ref } from 'vue'

let qty = ref(0)
function addValue() {
  qty.value++
  console.log(qty)
}
function minusValue() {
  if (qty.value > 0) {
    qty.value--
  }
}
</script>

<template>
  <div class="wrapper">
    <div class="profile">
      <div class="ballon" v-show="qty > 0">{{ qty }}</div>
    </div>

    <div class="button-wrapper">
      <div class="button" @click="minusValue">-</div>
      <div class="button" @click="addValue">+</div>
    </div>
    <div class="message">
      <div v-if="qty > 0">Me escribieron! 👀😲</div>
      <div v-else>Nadie me escribe 😢🤔</div>
    </div>
  </div>
</template>

<style scoped>
.message {
  background: rgb(241, 211, 241);
  width: 40%;
  align-items: center;
  justify-content: center;
  margin: auto;
  text-align: center;
  border-radius: 12px;
}
.button {
  background-color: white;
  display: inline-block;
  padding: 4px 0;
  border-radius: 4px;
  width: 32px;
  margin: 0 8px;
  cursor: pointer;
}

.button:hover {
  cursor: pointer;
  background-color: black;
  color: white;
}
.button-wrapper {
  margin-top: 16px;
  text-align: center;
  margin-bottom: 16px;
}
.ballon {
  width: 32px;
  height: 32px;
  background-color: #000;
  border-radius: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  position: absolute;
  top: 0;
  right: 0;
}
.wrapper {
  padding-top: 16px;
  background-color: rgb(132, 71, 189);
  width: 60%;
  border-radius: 12px;
  margin: 0 auto;
  overflow: hidden;
  padding-bottom: 16px;
}

.profile {
  position: relative;
  background-image: url(https://shiftart.com/wp-content/uploads/2017/04/RC-Profile-Square.jpg);
  background-size: cover;
  width: 160px;
  height: 160px;
  margin: auto;
  border-radius: 100%;
}
</style>
