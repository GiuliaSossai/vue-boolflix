<template>
  <div id="app">

    <Header @takeSearch="performSearch"/>

    <Main/>

  </div>
</template>

<script>


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
      film: ''
    }
  },

  methods: {
    performSearch(itemToSearch){
      this.film = itemToSearch;
      console.log('valore di input che ricevo in app', this.film);
    },

  },

  mounted(){
      
  }
  
}
</script>

<style lang="scss">
  @import './assets/style/vars.scss';
  @import './assets/style/generals.scss';
</style>
