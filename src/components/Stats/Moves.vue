<template>
  <span>Moves: {{ moves }}</span>
</template>

<script>
export default {
  // data() {
  //   return {
  //     moves: 0
  //   }
  // }
  props: {
    moves: Number
  }
}
</script>
<style type="text/css">
  span {
    margin: 5px;
  }
</style>