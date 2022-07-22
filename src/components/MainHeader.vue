<template>
   <header>
      <nav>
         <div class="logo-box">
            <h3>Boolflix</h3>
         </div>
         <div class="user-search">
            <input class="search-bar" placeholder="Ricerca" v-model="searchValue" >
            <button class="nav-btn" type="submit" @click="$emit('search', searchValue)">Cerca</button>
         </div>
      </nav>
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

<style lang="scss">
   header {
      background-color: rgb(24, 24, 24);
      height: 60px;
      padding: 1rem 4rem;

      nav {
         display: flex;
         justify-content: space-between;
         align-items: center;

         h3 {
            color: #C00;
            font-weight: 800;
         }

         .search-bar {
            padding: .45rem .75rem;
            margin-right: .5rem;
            border: none;
         }

         .nav-btn {
            padding: .45rem 1rem;
            border: none;
            border-radius: 0px;
            background-color: #C00;
            color: #fff;
            font-weight: 600;

            &:hover {
               cursor: pointer;
               background-color: #D00;
            }
         }
      }
   }

</style>