<template>
  <div>
    <v-card class="mx-auto" max-width="374">
      <template slot="progress">
        <v-progress-linear
          color="deep-purple"
          height="10"
          indeterminate
        ></v-progress-linear>
      </template>

      <v-img :src="product.image"></v-img>

      <v-card-title>{{ product.title }}</v-card-title>

      <v-card-text>
        <v-row align="center" class="mx-0">
          <v-rating
            :value="4.5"
            color="amber"
            dense
            half-increments
            readonly
            size="14"
          ></v-rating>

          <div class="grey--text ms-4">
            4.5 (413)
          </div>
        </v-row>

        <div class="my-4 text-subtitle-1">Rp. {{ product.price }}</div>

        <div>
          {{ product.description }}
        </div>
      </v-card-text>

      <v-divider class="mx-4"></v-divider>

      <v-card-actions>
        <v-btn depressed block color="primary" @click="buy">
          <v-icon>mdi-cart-plus</v-icon> &nbsp; Buy
        </v-btn>
      </v-card-actions>
    </v-card>
    <div class="mb-15"></div>
  </div>
</template>
<script>
export default {
  name: "DetailProducts",
  data: () => ({
    product: [], // objek book
  }),
  created() {
    this.go();
  },
  methods: {
    go() {
      this.axios
        .get("http://localhost:3000/products/" + this.$route.params.id)
        .then((response) => {
          let data = response.data;
          this.product = data;
          console.log(data);
        })
        .catch((error) => {
          let { responses } = error;
          console.log(responses);
        });
    },
    buy() {
      alert("buy");
    },
  },
};
</script>
