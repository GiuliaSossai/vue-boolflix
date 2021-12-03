<template>
   <header class="d-flex justify-content-between align-items-center p-4">
      <div class="logo-img">
         <img src="../assets/img/boolflix-logo.png" alt="">
      </div>

      <div class="input-group mb-3">
         <input
            type="text" 
            placeholder="cerca"
            aria-label="cerca"
            class="me-2 form-control"
            aria-describedby="basic-addon2"
            v-model="search"
            @keyup.enter="toApp" 
         >
         <div class="input-group-append">
            <button class="btn btn-outline-danger" type="button" @click="toApp">cerca</button>
         </div>  
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
      .logo-img {
         width: 400px;
         img {
            width: 100%;
         }
      }
      .input-group {
         width: 300px;
      }
   }
</style>