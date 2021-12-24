<template>
  <div class="arrow" @click="move">
    <div class="direction" :style="styleObject">
      <svg viewBox="0 0 100 100" version="1.1" xmlns="http://www.w3.org/2000/svg">
        <path d="M0,90 L50,0 L100,90 Z" fill="lightgrey" />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    var angles = {'up': 0, 'right': 90, 'down': 180, 'left': -90}
    return {
      styleObject: {
        transform: 'rotate(' + angles[this.direction] + 'deg)'
      }
    }
  },
  methods: {
    move() {
      this.$emit('move', this.direction)
    }
  },
  props: {
    direction: String
  },
  mounted() {
    window.addEventListener('keydown', event => {
      var keyCodes = {'up': 38, 'right': 39, 'down': 40, 'left': 37}
      if (event.keyCode === keyCodes[this.direction]) { 
        this.move()
      }
    })
  }
}
</script>

<style type="text/css">
  .arrow {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    background: rgba(0, 0, 0, .5);
    border-radius: 0.5rem;
  }
  .direction {
    width: 30%;
    height: 30%;
  }
</style>