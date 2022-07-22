<template>
  <div class="card">
    <div class="poster-img">
      <img :src="`${imgPath}/${imgDimension}${posterPath}`" alt="show-poster">
    </div>
    <div class="poster-caption">
      <h4>{{ showTitle }}</h4>
      <p>{{ showOriginalTitle }}</p>
      <div class="lang-img" v-if="showLanguage === 'it'">
        <img src="../assets/img/it-flag.png" :alt="showLanguage">
      </div>
      <div class="lang-img" v-else-if="showLanguage === 'en'">
        <img src="../assets/img/uk-flag.png" :alt="showLanguage">
      </div>
      <div class="lang-img" v-else>
        <img src="" alt="no-flag">
      </div>
      <div class="show-rating" v-for="vote in roundedtvShowVote()" :key="vote">
        <i class="fa-solid fa-star"></i>
      </div>
    </div>
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
        const roundedtvShowVote = Math.round(this.showVote / 2);
        return roundedtvShowVote;
      }
    }
}
</script>

<style lang="scss">
  .card {
    position: relative;
    width: calc((100% / 6) - 0.3rem);
    margin: 0.15rem;
    height: 420px;

    .poster-img {
      height: 100%;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    .poster-caption {
      background-color: rgba(0,0,0,.85);
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      padding: 1.25rem 1rem;
      color: #fff;
      font-weight: 300;
      display: none;


      img {
        height: 12px;
      }
    }
  }
</style>