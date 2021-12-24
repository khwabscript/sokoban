<template>
  <div class="cell" :style="style">
    <div class="goal centered" v-if="isGoal">✖</div>
    <div class="player centered" v-if="hasPlayer">🎅</div>
    <Box v-if="hasBox" :on-target="isGoal" />
  </div>
</template>

<script>
import Box from './Box.vue'

export default {
  components: {
    Box
  },
  props: {
    coors: Object,
    isGoal: Boolean,
    hasBox: Boolean,
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
    position: relative;
    background: lightgrey;
    border: 0 solid grey;
    border-right-width: 0.125rem;
    border-bottom-width: 0.125rem;
  }
  .centered {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
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