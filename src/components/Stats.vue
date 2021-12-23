<template>
  <div class="stats">
    <span>Time: {{ seconds }}</span>
    <span>Moves: {{ moves }}</span>
    <span>Pushes: {{ pushes }}</span>
  </div>
  
</template>

<script>
export default {
  props: {
    moves: Number,
    pushes: Number
  },
  data() {
    return {
      seconds: 0
    }
  },
  // mounted() {
  //   setInterval(() => {
  //     this.seconds++
  //   }, 1000)
  // }
}
</script>
<style type="text/css">
  span {
    margin: 5px;
  }
  .stats {
    margin: 10px auto 0;
  }
</style>