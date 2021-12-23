<template>
  <div class="box" :style="style">
    <div class="inner-box"></div>
  </div>
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
  .box {
    box-sizing: border-box;
    background: burlywood;
    border: 0.125rem solid saddlebrown;
  }
  .inner-box {
    box-sizing: border-box;
    width: 80%;
    height: 80%;
    margin: 10%;
    border: 0.125rem solid saddlebrown;
  }
</style>