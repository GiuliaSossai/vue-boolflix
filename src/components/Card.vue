<template>
  <div class="film-card text-center my-3 p-3">
      <!-- titolo -->
      <h3 v-if="picCard.name">{{picCard.name}}</h3>
      <h3 v-else>{{picCard.title}}</h3>

      <!-- titolo originale -->
      <p v-if="picCard.original_name">{{picCard.original_name}}</p>
      <p v-else>{{picCard.original_title}}</p>

      <!-- language -->
      <p v-if="picCard.original_language === 'it'"><country-flag country='it' size='normal'/></p>
      <p v-else-if="picCard.original_language === 'en'"><country-flag country='gb' size='normal'/></p>
      <p v-else>{{picCard.original_language}}</p>

      <h5>{{picCard.vote_average}}</h5>
  </div>
</template>

<script>
import CountryFlag from 'vue-country-flag';

export default {
   name: 'Card',
   props: {
      picCard: Object
   },
   components: {
     CountryFlag 
   }
}
</script>

<style lang="scss">
   @import '../assets/style/vars.scss';
   @import '../assets/style/generals.scss';

   .film-card {
      width: 24%;
      margin: 0 0.5%;
      background-color: rgb(252, 219, 249);
   }
</style>