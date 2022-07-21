<template>
   <main>
      <MoviesList v-for="(movie, index) in movies" :key="index"
       :title = 'movie.title'
       :originalTitle = 'movie.original_title'
       :language = 'movie.original_language'
       :vote = 'movie.vote_average'
      />
   </main>
</template>

<script>
import MoviesList from './MoviesList.vue';
export default {
   components: { 
      MoviesList 
   },
   props: {
      'movies': {
         required: true,
         type: Array,
      }
   }
}
</script>

<style>

</style>