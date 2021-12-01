<template>
   <header class="d-flex justify-content-between align-items-center p-4">
      <h1>BOOLFLIX</h1>
      <div>
         <input
            class="me-2"
            type="text" 
            placeholder="cerca"
            v-model="search"
            @keyup.enter="toApp" 
         >
         <button
            @click="toApp"
         >cerca</button>
      </div>
      
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
      toApp(){
         this.$emit('takeSearch', this.search);
         this.search = '';
      }
   }

}
</script>

<style lang="scss">
   @import '../assets/style/vars.scss';
   @import '../assets/style/generals.scss';

   header {
      background-color: #000;
      h1 {
         color: red;
      }
   }
</style>