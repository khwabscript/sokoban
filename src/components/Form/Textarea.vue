<template>
  <textarea class="textarea" v-model="scheme" :placeholder="placeholder"></textarea>
</template>

<script>
export default {
  data() {
    return {
      scheme: '',
      placeholder: 
`Draw your sokoban

-++++-
++ *++
+ 0 #+
+  P++
+++++-`
    }
  }
}
</script>

<style type="text/css">
  .textarea {
    text-align: center;
    letter-spacing: .5rem;
    font-size: 1rem;
    padding: 6px;
    margin: 1rem 0;
    min-height: 10rem;
    border-radius: .5rem;
  }
  .textarea:focus {
    border: 2px solid black;
  }
</style>