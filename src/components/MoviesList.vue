<template>
  <div class="card">
    <ul>
      <li>{{ title }}</li>
      <li>{{ originalTitle }}</li>
      <li>{{ language }}</li>
      <li>{{ vote }}</li>
    </ul>
  </div>
</template>

<script>


export default {
  props: {
    'title': String,
    'originalTitle': String,
    'language': String,
    'vote': Number
  }
}
</script>

<style>

</style>