<template>
  <div class="content">
    <img class="image" :src="money" alt="">
    <wheelOfFortune />
  </div>
</template>


<script setup>
import wheelOfFortune from './components/wheelOfFortune.vue';
import money from './assets/money.png'
</script>



<style scoped>
.content{
  margin: 0;
  display: flex;
  place-items: center;
  min-width: 320px;
  min-height: 100vh;
}
.image{
  position: absolute;
  left: 0;
  max-height: 100vh;
}
</style>
