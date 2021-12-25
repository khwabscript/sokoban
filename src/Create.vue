<template>
  <main class="container">
    <h1>Sokoban</h1>
    <h2>Create Level</h2>
    <!-- <Field ref="field" :data="data" /> -->
    <div class="flex">
      <Keys :keys="schemeKeys" />
      <Textarea  v-model="scheme" />
    </div>
    <PrettyJson :scheme="scheme" />

  </main>
</template>

<script>
import Field from './components/Field.vue'
import Keys from './components/Keys.vue'
import PrettyJson from './components/PrettyJson.vue'
import Textarea from './components/Form/Textarea.vue'
import schemeKeys from './scheme-keys.json'

export default {
  components: {
    Field,
    Keys,
    PrettyJson,
    Textarea,
  },
  data() {
    return {
      scheme: '',
      schemeKeys: schemeKeys,
    }
  }
}
</script>

<style type="text/css">
  #create {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
  .container {
    margin: 0 auto;
  }
  .flex {
    display: flex;
    margin: 0 auto;
    max-width: 500px;
    justify-content: space-around;
    align-items: center;
  }
</style>
