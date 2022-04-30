<template>
  <v-col sm="6" md="4" cols="12">
    <v-card max-width="400" :href="shopeeLink" target="_blank">
      <v-row no-gutters>
        <v-col cols="6">
          <v-img class="ma-2" :src="image"></v-img>
        </v-col>
        <v-col cols="6">
          <v-card-header>{{ name }}</v-card-header>
          <v-card-text class="text-blue text-h6">{{
            price.toLocaleString()
          }}</v-card-text>
          <!-- <v-card-subtitle>{{ id }}</v-card-subtitle> -->
        </v-col>
      </v-row>
    </v-card>
  </v-col>
</template>

<script>
export default {
  props: {
    id: {
      type: Number,
      default: 0,
    },
    name: {
      type: String,
      default: '#',
    },
    price: {
      type: Number,
      default: 0,
    },
    shopeePrice: {
      type: Number,
      default: 0,
    },
    shopeeLink: {
      type: String,
      default: 0,
    },
    image: {
      type: String,
      default: '#',
    },
  },

  data() {
    return {
      dialog: false,
    }
  },
}
</script>
