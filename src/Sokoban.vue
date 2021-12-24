<template>
  <main class="container">
    <h1>Sokoban</h1>
    <h2>{{ data.name }} - Level {{ data.level }}</h2>
    <Field ref="field" :data="data" @moved="moved" @pushed="pushed" />
    <ControlPanel @move="newMove" />
    <Stats :moves="moves" :pushes="pushes" />
  </main>
</template>

<script>
import data from './data.json'
import ControlPanel from './components/ControlPanel.vue'
import Field from './components/Field.vue'
import Stats from './components/Stats.vue'

export default {
  components: {
    ControlPanel,
    Field,
    Stats
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
      this.$refs.field.newMove(direction)
    },
    moved() {
      this.moves++
    },
    pushed() {
      this.pushes++
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
  }
  h2 {
    text-transform: capitalize;
  }
  .container {
    width: 50vh;
    margin: 0 auto;
  }
</style>
