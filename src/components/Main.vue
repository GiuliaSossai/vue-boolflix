<template>
  <main>
     <div class="text-center" v-if="filmsToShow.length <= 0 && seriesToShow.length <= 0">
        <h2 class="p-5">Cosa vuoi vedere?</h2>
     </div>

      <!-- film -->
      <div v-if="filmsToShow.length > 0">
        <h2 class="container text-center p-5">FILM</h2>
        <div class="container d-flex flex-wrap">
            <Card
               :picCard="item"
               v-for="item in filmsToShow"
               :key="item.id"
            />
        </div>
      </div>

      <!-- TV series -->
      <div v-if="seriesToShow.length > 0">
         <h2 class="container text-center p-5">SERIE TV</h2>
         <div class="container d-flex flex-wrap">
            <Card
               :picCard="item"
               v-for="item in seriesToShow"
               :key="item.id"
            />
         </div>
      </div>         
      
  </main>
</template>

<script>
import Card from './Card.vue'
export default {
   name: 'Main',

   props: {
      filmsToShow: Array,
      seriesToShow: Array
   },

   components: {
     Card 
   }
}
</script>

<style lang="scss">
   @import '../assets/style/vars.scss';
   @import '../assets/style/generals.scss';

   main {
      background-image: linear-gradient(to bottom, #000, #5D5D5D 50%, #fff);
      h2 {
         color: #fff;
         font-size: 50px;
      }  
   }

</style>