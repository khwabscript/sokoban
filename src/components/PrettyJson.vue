<template>
  <div class="json-pretty">
    <vue-json-pretty :path="'res'" :data="data"> </vue-json-pretty>
  </div>
</template>

<script>
import VueJsonPretty from 'vue-json-pretty';
import 'vue-json-pretty/lib/styles.css';

export default {
  components: {
    VueJsonPretty,
  },
  props: {
    scheme: String
  },
  computed: {
    data() {
      return {
        cells: Array.from(this.scheme.split('\n'), el => el.split(''))
      }
    }
  },
  methods: {

  }
};
</script>

<style type="text/css">
  .json-pretty {
    max-width: 500px;
    margin: 0 auto;
  }
</style>