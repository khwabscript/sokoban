<template>
  <div class="field" :style="style" @move="newMove">
    <Border v-for="border in data.entities.borders" :coors="{x: border.x, y: border.y}" />
    <Cell v-for="cell in data.entities.cells" :coors="{x: cell.x, y: cell.y}" :is-goal="cell.is_goal" :has-box="hasBox(cell.x, cell.y)"
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
      boxes: this.data.entities.boxes,
      cells: this.data.entities.cells,
      player: this.data.entities.player,
      directions: {'up': {x: 0, y: -1}, 'right': {x: 1, y: 0}, 'down': {x: 0, y: 1}, 'left': {x: -1, y: 0}},
      entities: {empty_cell: 'Empty cell', box: 'Box', border: 'Border'},
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
      var dx = this.directions[direction].x
      var dy = this.directions[direction].y
      var entity = this.getCoorsEntity(this.player.x + dx, this.player.y + dy)
      if (entity === this.entities.box) {
        var boxCoors = {x: this.player.x + dx, y: this.player.y + dy}
        if (this.canPush(boxCoors.x + dx, boxCoors.y + dy)) {
          this.pushBox(boxCoors.x, boxCoors.y, dx, dy)
          this.changePlayerCoors(dx, dy)
        }
      }
      if (entity === this.entities.empty_cell) {
        this.changePlayerCoors(dx, dy)
      }
    },
    changePlayerCoors(dx, dy) {
      this.player.x += dx
      this.player.y += dy
      this.$emit('moved')
    },
    pushBox(x, y, dx, dy) {
      this.boxes.forEach(function(box, i, boxes) {
        if (box.x === x && box.y === y) {
          boxes[i].x += dx;
          boxes[i].y += dy;
        }
      });
      this.$emit('pushed')
    },
    canPush(x, y) {
      return this.getCoorsEntity(x, y) === this.entities.empty_cell
    },
    hasBox(x, y) {
      return this.boxes.filter(box => box.x === x && box.y === y).length > 0
    },
    hasPlayer(x, y) {
      return this.player.x === x && this.player.y === y
    },
    getCoorsEntity(x, y) {
      var cells = this.cells.filter(cell => cell.x === x && cell.y === y)
      if (cells.length === 0) {
        return this.entities.border
      }
      if (cells.filter(cell => this.hasBox(cell.x, cell.y)).length > 0) {
        return this.entities.box
      }

      return this.entities.empty_cell
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