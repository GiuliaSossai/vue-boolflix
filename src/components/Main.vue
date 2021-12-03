<template>
  <main>
     <div class="text-center" v-if="filmsToShow.length <= 0 && seriesToShow.length <= 0">
        <h2>Cosa vuoi vedere?</h2>
     </div>

     <!-- <div class="text-center" v-else-if="filmsToShow = [] && seriesToShow.length = 0 ">
        <h2>Nessun risultato! Cerca di nuovo!</h2>
     </div> -->

     <div v-else>
        <!-- film -->
        <h2 class="container text-center p-5">Film Trovati</h2>
        <div class="container d-flex flex-wrap">
            <Card
               :picCard="film"
               v-for="film in filmsToShow"
               :key="film.id"
            />
        </div>

         <!-- TV series -->
         <h2 class="container text-center p-5">Serie TV</h2>
         <div class="container d-flex flex-wrap">
            <Card
               :picCard="serie"
               v-for="serie in seriesToShow"
               :key="serie.id"
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
   },
   data(){
      return {
         
      }
   },
   methods: {
      
   },

   mounted(){
      
   }
}
</script>

<style lang="scss">
   @import '../assets/style/vars.scss';
   @import '../assets/style/generals.scss';

   main {
      height: 100%;
      background-image: linear-gradient(to bottom, #000, #fff);
      h2 {
      color: #fff;
      }
   }

</style>