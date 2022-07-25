<template>
   <main>
      <div id="wrapper">
         <MoviesList v-for="movie in movies" :key="movie.id"
            :title = 'movie.title'
            :originalTitle = 'movie.original_title'
            :language = 'movie.original_language'
            :vote = 'movie.vote_average'
            :posterPath = 'movie.poster_path'
            :id = 'movie.id'
         />
         <TvShowsList v-for="show in tvShows" :key="show.id"
            :showTitle = 'show.name'
            :showOriginalTitle = 'show.original_name'
            :showLanguage = 'show.original_language'
            :showVote = 'show.vote_average'
            :posterPath = 'show.poster_path'
         />
      </div>
   </main>
</template>

<script>
import MoviesList from './MoviesList.vue';
import TvShowsList from './TvShowsList.vue';

export default {
   components: {
      MoviesList,
      TvShowsList
   },
   props: {
      'movies': {
         required: true,
         type: Array,
      },
      'tvShows': {
         required: true,
         type: Array,
      }
   }
}
</script>

<style lang="scss">
   main {
      height: calc(100vh - 60px);
      background-color: rgb(30, 30, 30);
      padding: 3rem 4rem;
      overflow: auto;

      #wrapper {
         display: flex;
         justify-content: flex-start;
         align-items: center;
         flex-wrap: wrap;
      }
   }
</style>