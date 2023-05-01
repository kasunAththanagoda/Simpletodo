<template>
  <v-app >
   
  
    <v-main class="grey lighten-4">
      <NavBar></NavBar>
      <v-content class="mx-4 mb-4">
        <router-view/>
      </v-content>
      
    </v-main>
  </v-app>
</template>

<script>
import NavBar from './components/NavBar.vue';

export default {
  name: 'App',

  data: () => ({
    //
  }),

  components:{
     NavBar
  }
};
</script>
