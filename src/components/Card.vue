<template>
  <div class="text-center my-3 p-3 flip-card">
     <div class="flip-card-inner">
        <div class="flip-card-front">
           <img 
               :src=" `https://image.tmdb.org/t/p/w342/${picCard.poster_path}` "
               :alt="picCard.name || picCard.title"
            >
        </div>

        <div class="flip-card-back">
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
   width: 380px;
   min-height: 300px;
   perspective: 1000px;
   }

   .flip-card-inner {
   position: relative;
   width: 100%;
   height: 100%;
   text-align: center;
   transition: transform 0.6s;
   transform-style: preserve-3d;
   box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
   overflow: hidden;
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
   }

   .flip-card-front {
   background-color: #bbb;
   color: black;
   }

   .flip-card-back {
   background-color: #2980b9;
   color: white;
   transform: rotateY(180deg);
   }
</style>