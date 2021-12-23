<template>
  <div class="control-panel">
    <Arrow direction="up" v-bind:style="cellStyle(2, 1)" @move="newMove"/>
    <Arrow direction="right" v-bind:style="cellStyle(3, 2)" @move="newMove"/>
    <Arrow direction="left" v-bind:style="cellStyle(1, 2)" @move="newMove"/>
    <Arrow direction="down" v-bind:style="cellStyle(2, 3)" @move="newMove"/>
  </div>
</template>

<script>
import Arrow from './Entities/Arrow.vue'
export default {
  components: {
    Arrow
  },
  methods: {
    cellStyle(x, y) {
      return {
        'grid-column': x,
        'grid-row': y
      }
    },
    newMove(direction) {
      this.$emit('move', direction)
    }
  }
}
</script>

<style type="text/css">
  .control-panel {
    margin: 2rem auto;
    width: 15vh;
    height: 15vh;
    display: grid;
    grid-template-columns: 3;
    grid-template-rows: 3;
  }
</style>