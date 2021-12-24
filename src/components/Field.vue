<template>
  <div class="field" :style="style" @move="newMove">
    <Border v-for="border in data.entities.borders" :coors="{x: border.x, y: border.y}" />
    <Cell v-for="cell in data.entities.cells" :coors="{x: cell.x, y: cell.y}" :is-goal="cell.is_goal" :has-box="cell.has_box"
      :has-player="hasPlayer(cell.x, cell.y)" />
  </div>
</template>

<script>
import Border from './Entities/Border.vue'
import Cell from './Entities/Cell.vue'

export default {
  components: {
    Border,
    Cell
  },
  props: {
    data: Object
  },
  data() {
    return {
      cells: this.data.entities.cells,
      entities: {cell: 'Cell'},
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
      return this.changePlayerCoors(direction)
    },
    hasPlayer(x, y) {
      return this.player.x === x && this.player.y === y
    },
    changePlayerCoors(direction) {
      const directions = {'up': {x: 0, y: -1}, 'right': {x: 1, y: 0}, 'down': {x: 0, y: 1}, 'left': {x: -1, y: 0}}
      var dx = directions[direction].x
      var dy = directions[direction].y
      if (this.getCoorsEntity(this.player.x + dx, this.player.y + dy) === this.entities.cell) {
        this.player.x += dx
        this.player.y += dy
        return true
      }
    },
    getCoorsEntity(x, y) {
      if (this.cells.filter(cell => cell.x === x && cell.y === y).length > 0) {
        return this.entities.cell
      }
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