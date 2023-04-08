<!--<template>
    <v-app-bar :clipped-left="clipped" fixed app>
        <nuxt-link to="/" style="color:blue;">Descripción de la prueba</nuxt-link>
        <nuxt-link to="/login" style="color:blue;">Login</nuxt-link>
        <h1 style="color: red;">PruebaShop</h1>
    </v-app-bar>
    
</template>-->

<template>
    <v-app>
        <nuxt-link to="/"> Descripción de la prueba</nuxt-link>
        <v-card>
            <h1 style="color: red;">PruebaShop</h1>
        
        <v-spacer />
        <!--<v-toolbar-title v-if="$store.state.token">-->
        <v-toolbar-title>
          <nuxt-link to="/home" class="mx-4">Home</nuxt-link>
          <nuxt-link to="/product/create/" class="mr-4">Create(admin)</nuxt-link>
          
          <span class="mr-4">{{ $store.state.user.name }}</span>
          <v-btn color="error" @click="logout">Logout</v-btn>
        <!--</v-toolbar-title>-->
        <!--<v-toolbar-title v-else>-->
          <nuxt-link to="/login" class="mx-4">Login</nuxt-link>
          <nuxt-link to="/signup" class="mx-4">Signup</nuxt-link>
          <nuxt-link to="/carrito" class="mx-4">Carrito</nuxt-link>
        </v-toolbar-title>
      </v-card>
      <v-main>
        
      </v-main>
    </v-app>
  </template>
  
  <script>
    
  import { mapActions } from "vuex";
  export default {
    name: "DefaultLayout",
    data() {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        items: [
          {
            icon: "mdi-apps",
            title: "Welcome",
            to: "/",
          },
          {
            icon: "mdi-chart-bubble",
            title: "Inspire",
            to: "/inspire",
          },
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: "Crud App",
      };
    },
  
    methods: {
      ...mapActions(["logoutUser"]),
      ...mapActions(["readUser"]),
      logout() {
        this.logoutUser();
      },
    },
    mounted() {
      this.readUser();
    },
  };
  </script>
  
  <style>
  a {
    text-decoration: none !important;
  }
  </style>