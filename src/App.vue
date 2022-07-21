<template>
  <div id="app">
    <MainHeader @search="getSearch"/>
    <MainContent 
      :movies="moviesList"/>
  </div>
</template>

<script>
import MainHeader from './components/MainHeader.vue';
import MainContent from './components/MainContent.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    MainHeader,
    MainContent
  },
  data: function() {
    return {
      moviesList: [],
      movieUrl: 'https://api.themoviedb.org/3/search/movie?api_key=e575f76f59f9dd45a7033ae7e19eb74d&include_adult=false&query=',
      tvShowsUrl: 'https://api.themoviedb.org/3/search/tv?api_key=e575f76f59f9dd45a7033ae7e19eb74d&linclude_adult=false&query='
    }
  },
  methods: {
    getSearch(value) {
      const queryValue = value;
      let searchedMovies;
      let searchedSeries;

      axios.get(`${this.movieUrl}${queryValue}`)
      .then((result) => {
        searchedMovies = result.data.results;
        console.log(searchedMovies);
      });

      axios.get(`${this.tvShowsUrl}${queryValue}`)
      .then((result) => {
        searchedSeries = result.data.results;
        console.log(searchedSeries);
      });
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
