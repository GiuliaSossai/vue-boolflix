<template>
  <main>
     <div class="container d-flex flex-wrap">
        <div 
            class="film-card text-center my-3 p-3"
            v-for="(film, index) in filmsToShow"
            :key="index"
         >
            <p>{{film.title}}</p>
            <p>{{film.original_title}}</p>
            <p>{{film.original_language}}</p>
            <p>{{film.vote_average}}</p>
         </div>
     </div>  
  </main>
</template>

<script>

export default {
   name: 'Main',
   props: {
      filmsToShow: Array
   },

   components: {
      
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

   .film-card {
      width: 24%;
      margin: 0 0.5%;
      background-color: rgb(252, 219, 249);
   }

</style>