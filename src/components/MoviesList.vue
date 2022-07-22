<template>
  <div class="card">
    <div class="poster-img">
      <img :src="`${imgPath}/${imgDimension}${posterPath}`" alt="movie-poster">
    </div>
    <div class="poster-caption">
      <h3>{{ title }}</h3>
      <p>{{ originalTitle }}</p>
      <div class="lang-img">
        <country-flag :country='language' size='small'/>
      </div>
      <div class="movie-rating">
        <i class="fa-solid fa-star" v-for="vote in roundedMovieVote()" :key="vote"></i>
      </div>
    </div>  
  </div>
</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {
  components: {
    CountryFlag
  },
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