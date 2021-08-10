<template>
  <div class="mt-1">
    <v-container class="ma-0 pa-0 mt-2" grid-list-sm>
      <v-layout wrap>
        <v-flex
          class=" px-1 mb-4"
          v-for="product in products"
          :key="`product - ` + product.id"
          xs6
        >
          <v-card>
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
    </v-container>
    <!-- <v-row dense class="mt-2 mb-15">
      <v-col
        v-for="product in products"
        :key="`product - ` + product.id"
        :cols="product.flex"
      >
        <v-row no-gutters style="flex-wrap: nowrap;">
          <v-col>
            <v-card>
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
          </v-col>
        </v-row>
      </v-col>
    </v-row> -->
  </div>
</template>
<style>
.v-application .elevation-8 {
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
}
</style>
<script>
export default {
  name: "Products",
  data: () => ({
    products: [],
    categories: [],
    model: null,
  }),
  methods: {
    setProduct(data) {
      this.products = data;
    },
  },
  created() {
    console.log("get data products");
    this.axios
      .get("http://localhost:3000/products")
      .then((response) => {
        // let { data } = response.data;
        // this.products = data;
        this.setProduct(response.data);
        console.log(response);
      })
      .catch((error) => {
        let { responses } = error;
        console.log(responses);
      });
  },
};
</script>
