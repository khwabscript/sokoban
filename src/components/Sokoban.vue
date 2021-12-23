<template>
  <main class="container">
    <h1>Sokoban</h1>
    <h2>{{ data.name }} - Level {{ data.level }}</h2>
    <div class="field" v-bind:style="styleObject">
      <Border v-for="border in data.entities.borders" v-bind:style="cellStyle(border.x, border.y)"/>
      <Cell v-for="cell in data.entities.cells" :is-goal="cell.is_goal ?? false" :has-player="cell.has_player ?? false" 
        v-bind:style="cellStyle(cell.x, cell.y)"/>
      <Box v-for="box in data.entities.boxes" :coors="{x: box.x, y: box.y}"/>
    </div>
    <ControlPanel @move="newMove" />
    <div class="footer">
      <Time />
      <Moves :moves="moves" />
      <Pushes :pushes="pushes" />
    </div>
  </main>
</template>

<script>
import data from '../data.json'
import Border from './Entities/Border.vue'
import Box from './Entities/Box.vue'
import Cell from './Entities/Cell.vue'
import ControlPanel from './ControlPanel.vue'
import Moves from './Stats/Moves.vue'
import Pushes from './Stats/Pushes.vue'
import Time from './Stats/Time.vue'

export default {
  components: {
    Border,
    Box,
    Cell,
    ControlPanel,
    Moves,
    Pushes,
    Time
  },
  data() {
    return {
      data: data,
      moves: 0,
      pushes: 0,
      styleObject : {
        'grid-template-columns': 'repeat(' + data.width + ', 1fr)',
        'grid-template-rows': 'repeat(' + data.height + ', 1fr)'
      }
    }
  },
  methods: {
    cellStyle(x, y) {
      return {
        'grid-column': x,
        'grid-row': y
      }
    },
    newMove(direction) {
      this.moves++
    }
  }
}
</script>

<style type="text/css">
  h2 {
    text-transform: capitalize;
  }
  .container {
    width: 50vh;
    margin: 0 auto;
  }
  .field {
    display: grid;
    width: 100%;
    height: 50vh;
  }
  .footer {
    margin: 10px auto 0;
  }
</style>
