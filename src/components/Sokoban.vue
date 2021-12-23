<template>
  <main class="container">
    <h1>Sokoban</h1>
    <h2>{{ data.name }} - Level {{ data.level }}</h2>
    <div class="field" :style="style">
      <Border v-for="border in data.entities.borders" :coors="{x: border.x, y: border.y}" />
      <Cell v-for="cell in data.entities.cells" :coors="{x: cell.x, y: cell.y}" :is-goal="cell.is_goal" :has-player="cell.has_player" />
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
  computed: {
    style() {
      return {
        'grid-template-columns': 'repeat(' + this.data.width + ', 1fr)',
        'grid-template-rows': 'repeat(' + this.data.height + ', 1fr)'
      }
    }
  },
  data() {
    return {
      data: data,
      moves: 0,
      pushes: 0
    }
  },
  methods: {
    newMove(direction) {
      this.moves++
    }
  }
}
</script>

<style type="text/css">
  #sokoban {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    /*margin-top: 60px;*/
  }
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
