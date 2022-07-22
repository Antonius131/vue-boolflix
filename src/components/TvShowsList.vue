<template>
   <div class="card">
    <ul>
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
      'showVote': Number
   }
}
</script>

<style>

</style>