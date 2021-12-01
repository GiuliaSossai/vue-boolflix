<template>
   <header>
      <input 
         type="text" 
         placeholder="cerca"
         v-model="search"
         @keyup.enter="getInput"
      >
      <button>cerca</button>
   </header>
</template>

<script>
export default {
   name: 'Header',
   components: {
      
   },
   data(){
      return {
         search: ''
      }
   },
   methods: {
      getInput(){
         console.log(this.search);
      }
   }

}
</script>

<style lang="scss">
   @import '../assets/style/vars.scss';
   @import '../assets/style/generals.scss';

   header {
      font: $main-font;
   }
</style>