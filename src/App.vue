<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import Sokoban from './components/Sokoban.vue'
import Moves from './components/Stats/Moves.vue'
import Pushes from './components/Stats/Pushes.vue'
import Time from './components/Stats/Time.vue'
</script>

<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Hello Vue 3 + Vite" /> -->
  
  <div style="margin: 10px auto;">
    <Sokoban />
    <!-- <div style="width: 300px;height: 300px;border: 30px solid; border-color: lightgray darkgray black;background: gray;margin: 30px auto;"></div> -->
    <div style="margin: 10px auto 0">
      <Time />
      <Moves :moves="0" />
      <Pushes />  
    </div>
  </div>
</template>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}
</style>
