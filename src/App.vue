<template>
  <div id="app">
    <MainHeader @search="getSearch"/>
    <MainContent />
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
      searchedList: []
    }
  },
  methods: {
    getSearch(value) {
      const queryValue = value;
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=e575f76f59f9dd45a7033ae7e19eb74d&language=en-US&include_adult=false&query=${queryValue}`)
      .then((result) => {
        console.log(result.data.results);
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
