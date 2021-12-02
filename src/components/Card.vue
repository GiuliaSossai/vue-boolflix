<template>
  <div class="text-center flip-card">
     <div class="flip-card-inner">
        <div class="flip-card-front">
           <img 
               :src=" `https://image.tmdb.org/t/p/w342/${picCard.poster_path}` "
               :alt="picCard.name || picCard.title"
            >
        </div>

        <div class="flip-card-back">
            <!-- titolo -->
            <h3 class="p-3" v-if="picCard.name">{{picCard.name}}</h3>
            <h3 class="p-3" v-else>{{picCard.title}}</h3>

            <!-- titolo originale -->
            <p v-if="picCard.original_name">{{picCard.original_name}}</p>
            <p v-else>{{picCard.original_title}}</p>

            <!-- lingua -->
            <p v-if="picCard.original_language === 'it'"><country-flag country='it' size='normal'/></p>
            <p v-else-if="picCard.original_language === 'en'"><country-flag country='gb' size='normal'/></p>
            <p v-else>{{picCard.original_language}}</p>

            <!-- voto -->
            <h5 v-if="picCard.vote_average !== 0">
               Vote: <i v-for="index in Math.floor(picCard.vote_average / 2)" :key="index" class="fas fa-star"></i>
            </h5>
            <h5 v-else>Vote: N.A.</h5>
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

   // .film-card {
   //    //width: 24%;
   //    width: 380px;
   //    margin: 0 0.5%;
   //    background-color: rgb(252, 219, 249);
   // }
   .flip-card {
   background-color: transparent;
   width: 24%;
   height: 450px;
   perspective: 1000px;
   border: 1px solid #dbdada;
   perspective: 1000px;
   margin: 20px 0.5%;
   color: #fff;
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
   }

   .flip-card-front {
   background-color: rgb(192, 184, 184);
   }

   .flip-card-back {
   background-color: rgb(189, 166, 166);
   transform: rotateY(180deg);
   }
</style>