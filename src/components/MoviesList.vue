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
      <div class="cast-info">
        <button @click="getCast()">show cast</button>
        <ul>
          <li>
            actor name
          </li>
        </ul>
      </div>
    </div>  
  </div>
</template>

<script>
import CountryFlag from 'vue-country-flag';
import axios from 'axios';

export default {
  components: {
    CountryFlag
  },
  props: {
    'title': String,
    'originalTitle': String,
    'language': String,
    'vote': Number,
    'posterPath': String,
    'id': Number
  },
  data: function() {
    return {
      imgPath: 'https://image.tmdb.org/t/p',
      imgDimension: 'w342',
      apiKey: 'e575f76f59f9dd45a7033ae7e19eb74d',
      apiUrl: 'https://api.themoviedb.org/3/movie/',
      movieCast: []
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