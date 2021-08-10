<template>
  <div class="mt-1">
    <h3>Hello Fahriz Dimasqy</h3>
    <p class="text--disabled">Let's gets something</p>
    <v-text-field
      class="mt-2 mb-4"
      hide-details
      append-icon="mdi-microphone"
      flat
      label="Search"
      prepend-inner-icon="mdi-magnify"
      solo-inverted
    ></v-text-field>
    <div class="text-right mt-5 mb-2">
      <v-btn small text to="/categories" class="black--text">
        All Categories <v-icon>mdi-chevron-right</v-icon>
      </v-btn>
    </div>
    <v-sheet class="" max-width="700">
      <v-slide-group multiple show-arrows>
        <v-slide-item v-for="n in 25" :key="n" v-slot="{ active, toggle }">
          <v-btn
            class=""
            :input-value="active"
            active-class="purple white--text"
            depressed
            rounded
            @click="toggle"
          >
            Options {{ n }}
          </v-btn>
        </v-slide-item>
      </v-slide-group>
    </v-sheet>
    <v-container class="ma-0 pa-0 mt-2" grid-list-sm>
      <div class="text-right mt-5">
        <v-btn small text to="/products" class="blue--black">
          All Product <v-icon>mdi-chevron-right</v-icon>
        </v-btn>
      </div>
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
      <div class="mb-12"></div>
    </v-container>
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
// import VueSlickCarousel from "vue-slick-carousel";

export default {
  name: "Home",
  // components: { VueSlickCarousel },
  data: () => ({
    settings: [
      {
        dots: true,
        infinite: false,
        speed: 500,
        slidesToShow: 4,
        slidesToScroll: 4,
        initialSlide: 0,
        responsive: [
          {
            breakpoint: 1024,
            settings: {
              slidesToShow: 3,
              slidesToScroll: 3,
              infinite: true,
              dots: true,
            },
          },
          {
            breakpoint: 600,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 2,
              initialSlide: 2,
            },
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1,
            },
          },
        ],
      },
    ],
    items: [
      {
        src: "https://cdn.vuetifyjs.com/images/carousel/squirrel.jpg",
      },
      {
        src: "https://cdn.vuetifyjs.com/images/carousel/sky.jpg",
      },
      {
        src: "https://cdn.vuetifyjs.com/images/carousel/bird.jpg",
      },
      {
        src: "https://cdn.vuetifyjs.com/images/carousel/planet.jpg",
      },
    ],
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
      .get("http://localhost:3000/best-products")
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
