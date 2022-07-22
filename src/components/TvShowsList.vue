<template>
  <div class="card">
    <div class="poster-img">
      <img :src="`${imgPath}/${imgDimension}${posterPath}`" alt="show-poster">
    </div>
    <div class="poster-caption">
      <h4>{{ showTitle }}</h4>
      <p>{{ showOriginalTitle }}</p>
      <div class="lang-img">
        <country-flag :country='showLanguage' size='small'/>
      </div>
      <div class="show-rating" >
        <i class="fa-solid fa-star" v-for="vote in roundedtvShowVote()" :key="vote"></i>
      </div>
    </div>
  </div>
</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {
  components: {
    CountryFlag
  },
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

    &:hover {
      .poster-caption {
        display: block;
      }
    }

    .poster-img {
      height: 100%;

      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
    }

    .poster-caption {
      background-color: rgba(0,0,0,.72);
      position: absolute;
      top: 0;
      left: 0;
      height: 100%;
      width: 100%;
      padding: 1.25rem 1rem;
      color: #fff;
      font-weight: 300;
      cursor: pointer;
      display: none;

      img {
        height: 12px;
      }

      .fa-solid.fa-star {
        display: inline;
        font-size: .75rem;
        margin: 0 .10em;
        color: rgb(255, 247, 0);
      }
    }
  }
</style>