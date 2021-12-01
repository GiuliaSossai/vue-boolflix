<template>
  <main>
     <div class="container d-flex flex-wrap">
        <div 
            class="film-card text-center my-3 p-3"
            v-for="(film, index) in films"
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
import axios from 'axios';
export default {
   name: 'Main',
   components: {
      
   },
   data(){
      return {
         films: []
      }
   },
   methods: {
      getApi(){
      axios.get("https://api.themoviedb.org/3/search/movie", {
        params:{
          api_key: "175c5ba4ca5c3e6fc669aa56a7f621e0",
          query : "il signore degli anelli"
        }
      })
        .then( response => {
          this.films = response.data.results;
          console.log('array films in chiamata api in main:', this.films);
        })
        .catch( error => {
          console.log(error);
        });
      }
   },

   mounted(){
      this.getApi();
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