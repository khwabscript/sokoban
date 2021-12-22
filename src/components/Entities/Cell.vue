<template>
  <div class="cell">
    <div class="goal" v-if="isGoal">✖</div>
    <div class="player" v-if="hasPlayer">🎅</div>
  </div>
</template>

<script>
export default {
  props: {
    isGoal: Boolean,
    hasPlayer: Boolean
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
    font-size: 2rem;
    font-weight: bold;
    -webkit-text-stroke: 1px brown;
    color: gold;
  }
  .player {
    font-size: 2rem;
  }
</style>