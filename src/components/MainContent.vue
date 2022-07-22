<template>
   <main>
      <MoviesList v-for="movie in movies" :key="movie.id"
         :title = 'movie.title'
         :originalTitle = 'movie.original_title'
         :language = 'movie.original_language'
         :vote = 'movie.vote_average'
         :posterPath = 'movie.poster_path'
      />
      <TvShowsList v-for="show in tvShows" :key="show.id"
         :showTitle = 'show.name'
         :showOriginalTitle = 'show.original_name'
         :showLanguage = 'show.original_language'
         :showVote = 'show.vote_average'
         :posterPath = 'show.poster_path'
      />
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

<style>

</style>