<template>
  <div class="box" :style="style">
    <div class="inner-box" :style="style"></div>
  </div>
</template>

<script>
export default {
  props: {
    onTarget: Boolean
  },
  computed: {
    style() {
      return {
        background: this.onTarget ? 'limegreen' : 'burlywood',
        'border-color': this.onTarget ? 'darkgreen' : 'saddlebrown'
      }
    }
  }
}
</script>

<style type="text/css">
  .box {
    position: absolute;
    width: 100%;
    height: 100%;
    box-sizing: border-box;
    border: 0.125rem solid;
  }
  .inner-box {
    box-sizing: border-box;
    width: 80%;
    height: 80%;
    margin: 10%;
    border: 0.125rem solid;
  }
</style>