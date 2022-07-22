<template>
   <div class="card">
    <ul>
      <img :src="`${imgPath}/${imgDimension}${posterPath}`" alt="show-poster">
      <li>{{ showTitle }}</li>
      <li>{{ showOriginalTitle }}</li>
      <div class="lang-img" v-if="showLanguage === 'it'">
        <img src="../assets/img/it-flag.png" :alt="showLanguage">
      </div>
      <div class="lang-img" v-else-if="showLanguage === 'en'">
        <img src="../assets/img/uk-flag.png" :alt="showLanguage">
      </div>
      <div class="lang-img" v-else>
        <img src="" alt="no-flag">
      </div>
      <li>{{ showVote }}</li>
    </ul>
   </div>
</template>

<script>
export default {
    props: {
      'showTitle': String,
      'showOriginalTitle': String,
      'showLanguage': String,
      'showVote': Number,
      'posterPath': String
    },
    data: function() {
      return {
        imgPath: 'https://image.tmdb.org/t/p',
        imgDimension: 'w342'
      }
    },
    methods: {
      roundedtvShowVote() {
        const tvShowVote = this.showVote;
        const roundedtvShowVote = Math.round(tvShowVote / 2);
        console.log(roundedtvShowVote);
      }
    }
}
</script>

<style>

</style>