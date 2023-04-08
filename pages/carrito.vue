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
          <span>User</span>
          <!--<span class="mr-4">{{ $store.state.user.name }}</span>-->
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