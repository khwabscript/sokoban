<template>
  <span>Moves: {{ moves }}</span>
</template>

<script>
export default {
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