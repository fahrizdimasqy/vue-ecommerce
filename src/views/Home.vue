<template>
  <div>
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

    <v-row dense class="mt-2">
      <v-col v-for="card in cards" :key="card.title" :cols="card.flex">
        <v-card>
          <v-img
            :src="card.src"
            class="white--text align-end"
            gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
            height="200px"
          >
          </v-img>
          <v-card-title v-text="card.title"></v-card-title>
          <v-card-text v-text="card.price"></v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>
<style scoped>
.v-application .elevation-8 {
  box-shadow: none !important;
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
        src: "https://cdn.vuetifyjs.com/images/cards/road.jpg",
        flex: 6,
      },
      {
        title: "Best airlines",
        price: "Rp. 1.50000",
        src: "https://cdn.vuetifyjs.com/images/cards/plane.jpg",
        flex: 6,
      },
    ],
    model: null,
  }),
};
</script>
