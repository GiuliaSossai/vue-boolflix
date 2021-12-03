<template>
  <div id="app">

    <Header @takeSearch="performSearch"/>

    <Main :filmsToShow="movie" :seriesToShow="tv"/>

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
      itemToSearch: '',
      movie: [],
      tv: [],
      apiUrl: 'https://api.themoviedb.org/3/search/',
      type: ''
    }
  },

  methods: {
    performSearch(item){
      this.itemToSearch = item;
      console.log('valore di input che ricevo in app', this.itemToSearch);
      this.getApi();
    },

    getApi(){
      //chiamata axios per i film
      this.type = 'movie';

      axios.get(`${this.apiUrl}${this.type}`,{  
        params:{
          api_key : "baf5fb2944f01007fa0cacf4a54c8366",
          query : this.itemToSearch,
          language: "it-IT"
        }
      })
      .then( response => {
        this.movie = response.data.results;
        console.log('array films in chiamata api in main:', this.movie);
      })
      .catch( error => {
        console.log(error);
      });

      // chiamata axios per serie tv
      this.type= "tv";
      axios.get(`https://api.themoviedb.org/3/search/${this.type}`,{  
        params:{
          api_key : "baf5fb2944f01007fa0cacf4a54c8366",
          query : this.itemToSearch,
          language: "it-IT"
        }
      })
      .then( response => {
        this.tv = response.data.results;
        console.log('array serie tv in chiamata api in main:', this.tv);
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
