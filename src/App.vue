<template>
  <div class="content">
    <img :src="man" alt="">
    <wheelOfFortune />
  </div>
</template>


<script setup>
import wheelOfFortune from './components/wheelOfFortune.vue';
import man from './assets/man.png'
</script>



<style scoped>
.content{
  position: relative;
  margin: 0;
  display: flex;
  place-items: center;
  min-width: 320px;
}
img{
  position: absolute;
  left: -650px;
}
</style>
