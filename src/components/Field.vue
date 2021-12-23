<template>
  <div class="field" :style="style" @move="newMove">
    <Border v-for="border in data.entities.borders" :coors="{x: border.x, y: border.y}" />
    <Cell v-for="cell in data.entities.cells" :coors="{x: cell.x, y: cell.y}" :is-goal="cell.is_goal" :has-player="hasPlayer(cell.x, cell.y)" />
    <Box v-for="box in data.entities.boxes" :coors="{x: box.x, y: box.y}"/>
  </div>
</template>

<script>
import Border from './Entities/Border.vue'
import Box from './Entities/Box.vue'
import Cell from './Entities/Cell.vue'

export default {
  components: {
    Border,
    Box,
    Cell
  },
  props: {
    data: Object
  },
  data() {
    return {
      player: this.data.entities.player,
    }
  },
  computed: {
    style() {
      return {
        'grid-template-columns': 'repeat(' + this.data.width + ', 1fr)',
        'grid-template-rows': 'repeat(' + this.data.height + ', 1fr)'
      }
    }
  },
  methods: {
    newMove(direction) {
      this.changePlayerCoors(direction)
    },
    hasPlayer(x, y) {
      return this.player.x === x && this.player.y === y
    },
    changePlayerCoors(direction) {
      const directions = {'up': {x: 0, y: -1}, 'right': {x: 1, y: 0}, 'down': {x: 0, y: 1}, 'left': {x: -1, y: 0}}
      this.player.x += directions[direction].x
      this.player.y += directions[direction].y
    }
  }
}
</script>
<style type="text/css">
  .field {
    display: grid;
    width: 100%;
    height: 50vh;
  }
</style>