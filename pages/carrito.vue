<template>
    <v-app>
        <nuxt-link to="/"> Descripción de la prueba</nuxt-link>
        <v-card>
            <h1 style="color: red;">PruebaShop</h1>
        
        <v-spacer />
        <div v-if="$store.state.token">
        <v-toolbar-title v-if="$store.state.user.name[0]===' '">
          <nuxt-link to="/home" class="mx-4">Home</nuxt-link>
          <span class="mr-4">"Hola, {{ $store.state.user.name }}"</span>
          <nuxt-link to="/logout" class="mx-4">Logout</nuxt-link>
          <nuxt-link to="/carrito" class="mx-4">Carrito</nuxt-link>
        </v-toolbar-title>
        <v-toolbar-title v-else-if="$store.state.user.name[0]==='('">
          <nuxt-link to="/home" class="mx-4">Home</nuxt-link>
          <span class="mr-4">"Hola, {{ $store.state.user.name }}"</span>
          <nuxt-link to="/logout" class="mx-4">Logout</nuxt-link>
          <nuxt-link to="/carrito" class="mx-4">Carrito</nuxt-link>
          <nuxt-link to="/product/create/" class="mr-4">Inserir_Produto</nuxt-link>
          <nuxt-link to="/product/edit/" class="mr-4">Editar_Produto</nuxt-link>
        </v-toolbar-title>
        </div>
        <div v-else>
        <v-toolbar-title>
          <nuxt-link to="/home" class="mx-4">Home</nuxt-link>
          <nuxt-link to="/login" class="mx-4">Login</nuxt-link>
          <nuxt-link to="/signup" class="mx-4">Signup</nuxt-link>
          <nuxt-link to="/carrito" class="mx-4">Carrito</nuxt-link>
        </v-toolbar-title>
        </div>
      </v-card>
      <v-main>
        <v-btn color="green" to="/fel_compra">Finalizar compra</v-btn>
      </v-main>
    </v-app>
  </template>
   <script>
   import { mapActions } from "vuex";
   export default {
     middleware: ["guest"],
   };
 </script>