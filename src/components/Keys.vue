<template>
  <table class="table" cellpadding="5" >
    <caption class="caption">Scheme keys</caption>
    <tbody>
      <tr v-for="(description, key) in keys">
        <th>{{ key.replace(' ', '”&nbsp;”') }}</th>
        <th>{{ '&nbsp;-&nbsp;' }}</th>
        <td style="text-align: left">{{ description }}</td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: {
    keys: Object
  }
}
</script>

<style type="text/css">
  .caption {
    padding: 6px;
    font-weight: bold;
  }
</style>