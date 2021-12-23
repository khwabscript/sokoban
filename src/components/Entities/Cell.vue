<template>
  <div class="cell" :style="style">
    <div class="goal" v-if="isGoal">✖</div>
    <div class="player" v-if="hasPlayer">🎅</div>
  </div>
</template>

<script>
export default {
  props: {
    coors: Object,
    isGoal: Boolean,
    hasPlayer: Boolean
  },
  computed: {
    style() {
      return {
        'grid-column': this.coors.x,
        'grid-row': this.coors.y
      }
    }
  }
}
</script>

<style type="text/css">
  .cell {
    display: flex;
    align-items: center;
    justify-content: center;
    background: lightgrey;
    border: 0 solid grey;
    border-right-width: 0.125rem;
    border-bottom-width: 0.125rem;
  }
  .goal {
    font-size: 1.75rem;
    font-weight: bold;
    -webkit-text-stroke: 1px brown;
    color: gold;
  }
  .player {
    font-size: 2rem;
  }
</style>