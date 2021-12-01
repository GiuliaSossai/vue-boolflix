<template>
   <header class="p-4">
      <input 
         type="text" 
         placeholder="cerca"
         v-model="search"
         @keyup.enter="$emit('takeSearch', search)"
         
      >
      <button
         @click="$emit('takeSearch', search)"
      >cerca</button>
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
      
   }

}
</script>

<style lang="scss">
   @import '../assets/style/vars.scss';
   @import '../assets/style/generals.scss';

   header {
      background-color: #000;
   }
</style>