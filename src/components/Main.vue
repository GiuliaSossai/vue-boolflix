<template>
  <main>
     <div>
        <!-- film -->
        <h2 class="container m-5">Film Trovati</h2>
        <div class="container d-flex flex-wrap">
            <Card
               :picCard="film"
               v-for="film in filmsToShow"
               :key="film.id"
            />
        </div>

         <!-- TV series -->
         <h2 class="container m-5">Serie TV</h2>
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

   h2 {
      color: #fff;
   }

</style>