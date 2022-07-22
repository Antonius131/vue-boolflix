<template>
  <div class="card">
    <ul>
      <li>{{ title }}</li>
      <li>{{ originalTitle }}</li>
      <div class="lang-img" v-if="language === 'it'">
        <img src="../assets/img/it-flag.png" :alt="language">
      </div>
      <div class="lang-img" v-else-if="language === 'en'">
        <img src="../assets/img/uk-flag.png" :alt="language">
      </div>
      <div class="lang-img" v-else>
        <img src="" alt="no-flag">
      </div>
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
  },
  data: function() {
    return {
      imgPath: 'https://image.tmdb.org/t/p/',
      imgDimension: 'w342'
    }
  }
}
</script>

<style lang="scss">
  img {
    height: 12px;
  }
</style>