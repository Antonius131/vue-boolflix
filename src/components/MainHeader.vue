<template>
   <header>
      <div class="user-search">
         <input class="search-bar" placeholder="Ricerca" v-model="searchValue" >
         <button class="btn" type="submit">Cerca</button>
      </div>
   </header>
</template>

<script>
export default {
   data: function() {
      return {
         searchValue: ''
      }
   }
}
</script>

<style>

</style>