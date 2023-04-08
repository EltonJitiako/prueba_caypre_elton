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
        <div>
      <v-container>
        <v-row justify="center" align="center">
          <v-col cols="12" sm="8" md="6">
            <v-card>
              <v-card-title>
                <h1 class="my-4 text-center">Create Product</h1>
                <form action="" id="w-100" @submit.prevent="create">
                  <v-textField
                    label="Enter Your Title"
                    v-model="title"
                    type="text"
                  ></v-textField>
                  <v-textField
                    label="Enter Your Content"
                    type="text"
                    v-model="content"
                  ></v-textField>
                  <v-textField
                    label="Enter Your Price"
                    type="number"
                    v-model="price"
                  ></v-textField>
                  <v-btn color="primary" type="submit">Save</v-btn>
                </form>
              </v-card-title>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </div>
      </v-main>
    </v-app>
    
  </template>
  <script>
  import { mapActions } from "vuex";
  export default {
    middleware: ["auth"],
    data() {
      return {
        title: "",
        content: "",
        price: "",
      };
    },
    methods: {
      ...mapActions(["createProduct"]),
      create() {
        if (!this.title || !this.content || !this.price) {
          alert("Please fill all the field");
        } else {
          const data = {
            title: this.title,
            content: this.content,
            price: this.price,
          };
          this.createProduct(data);
        }
      },
    },
  };
  </script>
  <style>
  #w-100 {
    width: 100%;
  }
  .text-center {
    text-align: center !important;
  }
  </style>