<template>
  <div class="mt-1">
    <h3>Hello Fahriz Dimasqy</h3>
    <p class="text--disabled">Let's gets something</p>
    <v-sheet class="mx-auto" elevation="8" max-width="800">
      <v-slide-group
        v-model="model"
        class="pa-4"
        active-class="success"
        show-arrows
      >
        <v-slide-item v-for="n in 15" :key="n" v-slot="{ active, toggle }">
          <v-card
            :color="active ? undefined : 'grey lighten-1'"
            class="ma-4"
            height="200"
            width="400"
            @click="toggle"
          >
            <v-row class="fill-height" align="center" justify="center">
              <v-scale-transition>
                <v-icon
                  v-if="active"
                  color="white"
                  size="48"
                  v-text="'mdi-close-circle-outline'"
                ></v-icon>
              </v-scale-transition>
            </v-row>
          </v-card>
        </v-slide-item>
      </v-slide-group>
    </v-sheet>

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

    <v-row dense class="mt-2 mb-15">
      <v-col v-for="card in cards" :key="card.title" :cols="card.flex">
        <v-card>
          <v-img
            :src="card.src"
            class="white--text align-end"
            gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
            height="200px"
          >
          </v-img>
          <v-card-title
            class="d-inline-block text-truncate"
            v-text="card.title"
            style="max-width: 150px;"
          ></v-card-title>
          <v-card-text v-text="card.price"></v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>
<style>
.v-application .elevation-8 {
  box-shadow: none !important;
}
.v-item-group.v-bottom-navigation {
  position: fixed !important;
}
</style>
<script>
export default {
  name: "Home",
  data: () => ({
    cards: [
      {
        title: "Apple Watch",
        price: "Rp. 1.50000",
        src:
          "https://static.nike.com/a/images/t_PDP_1280_v1/f_auto,q_auto:eco/5602db01-a34b-4820-bd24-2d62d14154ba/apple-watch-series-6-gps-with-nike-sport-band-40mm-space-gray-aluminum-case-65dvHn.png",
        flex: 6,
      },
      {
        title: "Adidas Neo Dailyjjj",
        price: "Rp. 300.000",
        src: "https://s0.bukalapak.com/img/53971606541/large/data.png",
        flex: 6,
      },
      {
        title: "Adidas Neo Dailyjjj",
        price: "Rp. 300.000",
        src: "https://s0.bukalapak.com/img/53971606541/large/data.png",
        flex: 6,
      },
      {
        title: "Adidas Neo Dailyjjj",
        price: "Rp. 300.000",
        src: "https://s0.bukalapak.com/img/53971606541/large/data.png",
        flex: 6,
      },
    ],
    model: null,
  }),
};
</script>
