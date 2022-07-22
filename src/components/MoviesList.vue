<template>
  <div class="card">
    <div class="poster-img">
      <img :src="`${imgPath}/${imgDimension}${posterPath}`" alt="movie-poster">
    </div>
    <div class="poster-caption">
      <h3>{{ title }}</h3>
      <p>{{ originalTitle }}</p>
      <div class="lang-img" v-if="language === 'it'">
        <img src="../assets/img/it-flag.png" :alt="language">
      </div>
      <div class="lang-img" v-else-if="language === 'en'">
        <img src="../assets/img/uk-flag.png" :alt="language">
      </div>
      <div class="lang-img" v-else>
        <img src="" alt="no-flag">
      </div>
      <div class="movie-rating" v-for="vote in roundedMovieVote()" :key="vote">
        <i class="fa-solid fa-star"></i>
      </div>
    </div>  
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

        return roundedMovieVote;
    }
  }
}
</script>

<style lang="scss">
</style>