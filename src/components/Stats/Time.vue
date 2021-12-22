<template>
  <span>Time: {{ seconds }}</span>
</template>

<script>
export default {
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