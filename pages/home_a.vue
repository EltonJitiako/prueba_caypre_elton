<template>
    <v-app>
        <nuxt-link to="/"> Descripción de la prueba</nuxt-link>
        <v-card>
            <h1 style="color: red;">PruebaShop</h1>
        
        <v-spacer />
        <!--<v-toolbar-title v-if="$store.state.user.name[0]===' '">
          <nuxt-link to="/home_a" class="mx-4">Home</nuxt-link>
          <span class="mr-4">"Hola, {{ $store.state.user.name }}"</span>
          <nuxt-link to="/logout" class="mx-4">Logout</nuxt-link>
          <nuxt-link to="/carrito_a" class="mx-4">Carrito</nuxt-link>
        </v-toolbar-title>
        <v-toolbar-title v-else-if="$store.state.user.name[0]==='('">-->
        <v-toolbar-title>
          <nuxt-link to="/home_a" class="mx-4">Home</nuxt-link>
          <span class="mr-4">"Hola, {{ $store.state.user.name }}"</span>
          <nuxt-link to="/logout" class="mx-4">Logout</nuxt-link>
          <nuxt-link to="/carrito_a" class="mx-4">Carrito</nuxt-link>
          <nuxt-link to="/product/create/" class="mr-4">Inserir_Produto</nuxt-link>
          <nuxt-link to="/product/edit/" class="mr-4">Editar_Produto</nuxt-link>
        </v-toolbar-title>
      </v-card>
      <v-main>
       <div>
    <v-container>
      <v-simple-table dark>
        <template v-slot:default>
          <thead>
            <tr>
              <th class="text-left">Product Id</th>
              <th class="text-left">Title</th>
              <th class="text-left">User Id</th>
              <th class="text-left">Content</th>
              <th class="text-left">Price</th>
              <th class="text-left">Comprar</th>
            </tr>
          </thead>
          <tbody v-if="$store.state.products.length > 0">
            <tr v-for="product in $store.state.products" :key="product.id">
              <td>{{ product.id }}</td>
              <td>{{ product.title }}</td>
              <td>{{ product.user_id }}</td>
              <td>{{ product.content }}</td>
              <td>{{ product.price }}</td>
              <td>
                <nuxt-link
                  :to="{
                    name: 'product-productid',
                    path: 'product/:productid',
                    params: { productid: product.id },
                  }"
                  ><v-btn style="background-color:green;">Inserir no carrito</v-btn></nuxt-link
                >
              </td>
              <td>
                <!--<v-btn @click="deletePro(product.id)" class="error"
                  >Delete</v-btn
                >-->
              </td>
            </tr>
          </tbody>
          <tbody v-else>
            <h3>Record Not Found</h3>
          </tbody>
        </template>
      </v-simple-table>
    </v-container>
  </div>
             
      </v-main>
    </v-app>
  </template>
  
  <script>
    
  import { mapActions } from "vuex";
  export default {
    
    middleware: ["auth"],
    methods: {
  ...mapActions(["getAllProduct"]),
  ...mapActions(["deleteProduct"]),
  ...mapActions(["readUser"]),
  deletePro(id) {
    const data = {
      id: id,
    };
    this.deleteProduct(data);
    this.getAllProduct();
  },
},
mounted() {
  this.readUser();
  this.getAllProduct();
},
    
//methods: {
      //...mapActions(["logoutUser"]),
      //...mapActions(["readUser"]),
      /*logout() {
        this.logoutUser();
      },*/
    /*},
    mounted() {
      this.readUser();
    },*/

  };
  </script>
  
  <style>
  a {
    text-decoration: none !important;
  }
  </style>