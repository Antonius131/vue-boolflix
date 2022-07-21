<template>
   <main>
      <MoviesList v-for="(movie, index) in movies" :key="index" />
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