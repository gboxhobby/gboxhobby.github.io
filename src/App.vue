<template>
  <v-app>
    <v-navigation-drawer color="grey-darken-2"></v-navigation-drawer>
    <!-- <v-app-bar color="grey-lighten-2"></v-app-bar> -->
    <v-main>
      <ProductsPage></ProductsPage>
    </v-main>
  </v-app>
</template>

<script>
import { onMounted } from '@vue/runtime-core'
import { useDisplay } from 'vuetify/lib/framework'
import ProductsPage from './components/ProductsPage.vue'
export default {
  name: 'App',
  mounted() {},
  components: {
    ProductsPage,
  },

  data: () => ({
    //
  }),
}
</script>

<style>
a {
  text-decoration: none;
  color: #2196f3;
}
</style>
