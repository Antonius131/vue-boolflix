<template>
  <div id="app">
    <MainHeader @search="getSearch"/>
    <MainContent 
      :movies="moviesList"
      :tvShows="tvShowsList"/>
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
      tvShowsList: [],
      movieUrl: 'https://api.themoviedb.org/3/search/movie?api_key=e575f76f59f9dd45a7033ae7e19eb74d&include_adult=false&query=',
      tvShowsUrl: 'https://api.themoviedb.org/3/search/tv?api_key=e575f76f59f9dd45a7033ae7e19eb74d&linclude_adult=false&query='
    }
  },
  methods: {
    getSearch(value) {
      const queryValue = value;
      axios.get(`${this.movieUrl}${queryValue}`)
      .then((result) => {
        this.moviesList = result.data.results;
        console.log(this.moviesList);
      });

      axios.get(`${this.tvShowsUrl}${queryValue}`)
      .then((result) => {
        this.tvShowsList = result.data.results;
        console.log(this.tvShowsList);
      })
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
