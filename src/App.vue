<template>
  <v-app>
    <v-app-bar app color="white" light>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-slide-y-transition mode="out-in">
        <v-text-field
          class="mt-2"
          hide-details
          append-icon="mdi-microphone"
          flat
          label="Search"
          prepend-inner-icon="mdi-magnify"
          solo-inverted
          v-show="isSearch"
        ></v-text-field>
      </v-slide-y-transition>
      <v-spacer></v-spacer>
      <v-btn icon @click="isSearch = !isSearch">
        <v-icon>mdi-magnify</v-icon>
      </v-btn>
      <v-btn icon>
        <v-badge color="orange" overlap>
          <template v-slot:badge>
            <span>3</span>
          </template>
          <v-icon>mdi-cart</v-icon>
        </v-badge>
      </v-btn>
    </v-app-bar>
    <v-card>
      <v-navigation-drawer app v-model="drawer">
        <v-list>
          <v-list-item
            v-for="(item, index) in menus"
            :key="`menu-` + index"
            :to="item.route"
          >
            <v-list-item-icon>
              <v-icon left>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer></v-card
    >

    <v-content>
      <v-container fluid>
        <v-slide-y-transition mode="out-in">
          <router-view></router-view>
        </v-slide-y-transition>
      </v-container>
    </v-content>
    <v-bottom-navigation :value="value" color="primary">
      <v-btn>
        <v-icon>mdi-home</v-icon>
      </v-btn>

      <v-btn>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn>
        <v-icon>mdi-cart</v-icon>
      </v-btn>
      <v-btn>
        <v-icon>mdi-account</v-icon>
      </v-btn>
    </v-bottom-navigation>
  </v-app>
</template>
<style scoped>
* {
  font-family: "Nunito";
}
.v-sheet.v-app-bar.v-toolbar:not(.v-sheet--outlined) {
  box-shadow: none;
}
</style>
<script>
export default {
  name: "App",
  data: () => ({
    drawer: false,
    isSearch: false,
    menus: [
      { title: "Home", icon: "mdi-home", route: "/" },
      { title: "About", icon: "mdi-account", route: "/about" },
    ],
  }),
};
</script>
