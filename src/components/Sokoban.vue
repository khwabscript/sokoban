<template>
  <h1>Sokoban</h1>
  <h2>{{ data.name }} - Level {{ data.level }}</h2>
  <div class="field" v-bind:style="
    { 'grid-template-columns': 'repeat(' + data.width + ', 1fr)', 'grid-template-rows': 'repeat(' + data.height + ', 1fr)' }
    ">
      <Floor v-for="floor in data.entities.floor" v-bind:style="{ 'grid-column': floor.x, 'grid-row': floor.y}"/>
    </div>
</template>

<script>
import data from '../data.json'
import Floor from './Entities/Floor.vue'

export default {
  components: {
    Floor
  },
  data() {
    return {
      data: data
    }
  }
}
</script>
<style type="text/css">
  h2 {
    text-transform: capitalize;
  }
  .field {
    margin: 0 auto;
    display: grid;
    width: 50vh;
    height: 50vh;
  }
</style>
