<template>
  <div class="border" :style="style"></div>
</template>

<script>
export default {
  computed: {
    style() {
      return {
        'grid-column': this.coors.x,
        'grid-row': this.coors.y
      }
    }
  },
  props: {
    coors: Object
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