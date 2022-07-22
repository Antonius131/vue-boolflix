<template>
  <div class="card">
    <ul>
      <img :src="`${imgPath}/${imgDimension}${posterPath}`" alt="movie-poster">
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
    'vote': Number,
    'posterPath': String
  },
  data: function() {
    return {
      imgPath: 'https://image.tmdb.org/t/p',
      imgDimension: 'w342'
    }
  },
  methods: {
    roundedMovieVote() {
        const movieVote = this.vote;
        const roundedMovieVote = Math.round(movieVote / 2);
        console.log(roundedMovieVote);
    }
  }
}
</script>

<style lang="scss">
  .lang-img img {
    height: 12px;
  }
</style>