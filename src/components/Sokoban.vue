<template>
  <h1>Sokoban</h1>
  <h2>{{ data.name }} - Level {{ data.level }}</h2>
  <div class="field" v-bind:style="fieldStyle">
      <Border v-for="border in data.entities.borders" v-bind:style="{ 'grid-column': border.x, 'grid-row': border.y}"/>
      <Cell v-for="cell in data.entities.cells" :is-goal="cell.is_goal ?? false" :has-player="cell.has_player ?? false" 
        v-bind:style="{ 'grid-column': cell.x, 'grid-row': cell.y}"/>
      <Box v-for="box in data.entities.boxes" v-bind:style="{ 'grid-column': box.x, 'grid-row': box.y}"/>
    </div>
</template>

<script>
import data from '../data.json'
import Border from './Entities/Border.vue'
import Box from './Entities/Box.vue'
import Cell from './Entities/Cell.vue'

export default {
  components: {
    Border,
    Box,
    Cell
  },
  computed: {
    fieldStyle() {
      return {
        'grid-template-columns': 'repeat(' + this.data.width + ', 1fr)',
        'grid-template-rows': 'repeat(' + this.data.height + ', 1fr)'
      }
    }
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
