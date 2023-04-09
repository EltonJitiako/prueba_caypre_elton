<template>
    <v-app>
        <v-card>
            <h1>Felicitaciones!</h1>
            <h2>Compra hecha con suceso.</h2>
        <nuxt-link to="/home_a">Home</nuxt-link>
      </v-card>
    </v-app>
  </template>
  <script>
  import { mapActions } from "vuex";
  export default {
    middleware: ["auth"],
  };
</script>
    
          
