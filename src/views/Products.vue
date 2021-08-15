<template>
  <div>
    <v-container class="ma-0 pa-0 mt-2" grid-list-sm>
      <v-text-field
        class="mt-2 mb-4"
        hide-details
        append-icon="mdi-microphone"
        flat
        label="Search"
        prepend-inner-icon="mdi-magnify"
        solo-inverted
        v-model="search"
        @keyup="searchProduct"
      ></v-text-field>
      <v-subheader>
        All Products
      </v-subheader>
      <v-layout wrap>
        <v-flex
          class=" px-1 mb-4"
          v-for="product in products"
          :key="`product - ` + product.id"
          xs6
        >
          <v-card :to="'/products/' + product.id">
            <v-img
              :src="product.image"
              class="white--text align-end"
              gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
              height="200px"
            >
            </v-img>
            <v-card-title
              class="d-inline-block text-truncate"
              v-text="product.title"
              style="max-width: 150px;"
            ></v-card-title>
            <v-card-text v-text="product.price"></v-card-text>
          </v-card>
        </v-flex>
      </v-layout>
      <div class="mb-12"></div>
    </v-container>
  </div>
</template>
<style>
/* .v-application .elevation-8 {
  box-shadow: none !important;
}
.v-item-group.v-bottom-navigation {
  position: fixed !important;
}

.v-carousel {
  height: 150px !important;
  border-radius: 10px;
}
.v-carousel__controls {
  background: none !important;
} */
</style>
<script>
export default {
  name: "products",
  data: () => ({
    products: [],
    search: "",
  }),
  methods: {
    searchProduct() {
      this.axios
        .get("http://localhost:3000/best-products?q=" + this.search)
        .then((response) => {
          let data = response.data;
          this.products = data;
        })
        .catch((error) => {
          let { responses } = error;
          console.log(responses);
        });
    },
  },
  created() {
    console.log("get data products");
    this.axios
      .get("http://localhost:3000/products?page1")
      .then((response) => {
        let data = response.data;
        this.products = data;
        console.log(data);
      })
      .catch((error) => {
        let { responses } = error;
        console.log(responses);
      });
  },
};
</script>
