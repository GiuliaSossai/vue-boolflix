<template>
  <div id="app">

    <Header @takeSearch="performSearch"/>

    <Main :filmsToShow="films"/>

  </div>
</template>

<script>
import axios from 'axios';

import Header from './components/Header.vue';
import Main from './components/Main.vue';

export default {
  name: 'App',
  components: {
    Main,
    Header
  },

  data(){
    return{
      film: '',
      films: [],
      type: 'movie'
    }
  },

  methods: {
    performSearch(item){
      this.film = item;
      console.log('valore di input che ricevo in app', this.film);
      this.getApi();
    },

    getApi(){
       axios.get(`https://api.themoviedb.org/3/search/${this.type}`,{  
        params:{
          api_key : "baf5fb2944f01007fa0cacf4a54c8366",
          query : this.film,
          language: "it-IT"
        }
      })
      //versione estesa:
      // axios.get(`https://api.themoviedb.org/3/search/movie?api_key=baf5fb2944f01007fa0cacf4a54c8366&query=${this.film}&language=it-IT`)
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

  }
  
}
</script>

<style lang="scss">
  @import './assets/style/vars.scss';
  @import './assets/style/generals.scss';
</style>
