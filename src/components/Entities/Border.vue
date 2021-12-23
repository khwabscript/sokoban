<template>
  <div class="border" :style="style"></div>
</template>

<script>
export default {
  props: {
    coors: Object
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
  .border {
    background: cadetblue;
    border-color: aliceblue lightblue lightslategrey;
    border: 0.125rem solid;
  }
</style>