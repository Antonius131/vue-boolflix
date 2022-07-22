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
      apiKey: 'e575f76f59f9dd45a7033ae7e19eb74d',
      movieUrl: 'https://api.themoviedb.org/3/search/movie',
      tvShowsUrl: 'https://api.themoviedb.org/3/search/tv',
      moviesList: [],
      tvShowsList: []
    }
  },
  methods: {
    getSearch(value) {
      const queryValue = value;
      axios.get(`${this.movieUrl}?api_key=${this.apiKey}&query=${queryValue}`)
      .then((result) => {
        this.moviesList = result.data.results;
        console.log(this.moviesList);
      });

      axios.get(`${this.tvShowsUrl}?api_key=${this.apiKey}&query=${queryValue}`)
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
