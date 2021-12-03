<template>
  <div class="flip-card">
     <div class="flip-card-inner">
        <div class="flip-card-front">
           <img 
               v-if="picCard.poster_path"
               :src=" `https://image.tmdb.org/t/p/w342/${picCard.poster_path}` "
               :alt="picCard.name || picCard.title"
            >
            <div v-else class="placeholder-img">
               <h5 class="p-4 text-center">{{picCard.name|| picCard.title}}</h5>
            </div>
        </div>

        <div class="flip-card-back p-3">
            <!-- titolo -->
            <h3 class="mb-4">{{picCard.name|| picCard.title}}</h3>

            <!-- titolo originale -->
            <h5>Titolo originale: {{picCard.original_name || picCard.original_title}}</h5>
            
            <!-- lingua -->
            <h5 v-if="picCard.original_language === 'it'">Lingua originale: <country-flag country='it' size='normal'/></h5>
            <h5 v-else-if="picCard.original_language === 'en'">Lingua originale: <country-flag country='gb' size='normal'/></h5>
            <h5 v-else>Lingua: {{picCard.original_language}}</h5>

            <!-- voto -->
            <h5 class="my-3" v-if="picCard.vote_average !== 0">Voto: 
               <i 
                  v-for="(item, index) in 5" 
                  :key="index" 
                  class="fa-star fs-4"
                  :class="index < Math.round(picCard.vote_average / 2) ? 'fas' : 'far' "
               >
               </i>
            </h5>
            <h5 class="my-3" v-else>Voto: non disponibile</h5>

            <!-- descrizione -->
            <div class="overview">{{picCard.overview}}</div>
        </div>
     </div>  
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

   .flip-card {
      background-color: transparent;
      width: 24%;
      height: 450px;
      perspective: 1000px;
      //border: 2px solid $myRed;
      perspective: 1000px;
      margin: 20px 0.5%;
      color: rgb(202, 202, 202);
      h3, .fa-star {
         color: rgb(245, 244, 244);
      }
   }

   .flip-card-inner {
      position: relative;
      width: 100%;
      height: 100%;
      transition: transform 0.6s;
      transform-style: preserve-3d;
   }

   .flip-card:hover .flip-card-inner {
      transform: rotateY(180deg);
   }

   .flip-card-front, .flip-card-back {
      position: absolute;
      width: 100%;
      height: 100%;
      -webkit-backface-visibility: hidden;
      backface-visibility: hidden;
         img{
         overflow: hidden;
         object-fit: cover;
         height: 100%;
         width: 100%;
         }
      .placeholder-img {
         height: 100%;
         background-image: url('../assets/img/coverFilm_placeholder.png');
         img {
         width: 100%;
         
         }
      }
   }

   .flip-card-back {
      background-color: #3a3b3d;
      //background-color: darken($myRed , 35%);
      transform: rotateY(180deg);
      overflow: hidden;
      .overview {
         height: 140px;
         overflow: scroll;
         padding-bottom: 8px;
      }
   }
</style>