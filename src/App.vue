<template>
  <v-app>
    <v-app-bar app color="white" light v-if="isHome">
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-spacer></v-spacer>
      <v-btn icon>
        <v-badge color="orange" overlap>
          <template v-slot:badge>
            <span>3</span>
          </template>
          <v-icon>mdi-cart</v-icon>
        </v-badge>
      </v-btn>
    </v-app-bar>
    <v-app-bar color="white" v-else>
      <v-btn icon @click.stop="$router.go(-1)">
        <v-icon>mdi-arrow-left-circle</v-icon>
      </v-btn>
      <v-spacer></v-spacer>
      <v-btn icon to="/about">
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
          <div class="pa-2" v-if="guest">
            <v-btn block color="primary" class="mb-1" to="/login">
              <v-icon left>mdi-lock</v-icon>
              Login
            </v-btn>
            <v-btn block color="success">
              <v-icon left>mdi-account</v-icon>
              Register
            </v-btn>
          </div>
          <v-list-item v-if="!guest">
            <v-list-item-avatar>
              <v-img
                src="https://randomuser.me/api/portraits/men/78.jpg"
              ></v-img>
            </v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-title>Fahriz Dimasqy</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
          <v-divider class="mb-2"></v-divider>
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

        <template v-slot:append v-if="!guest">
          <div class="pa-2">
            <v-btn block color="red" dark>
              <v-icon left>mdi-lock</v-icon>
              Logout
            </v-btn>
          </div>
        </template>
      </v-navigation-drawer></v-card
    >
    <v-main>
      <v-container fluid>
        <v-slide-y-transition mode="out-in">
          <router-view> </router-view>
        </v-slide-y-transition>
      </v-container>
    </v-main>
    <v-bottom-navigation :value="value" color="primary">
      <v-btn to="/">
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
.v-list .v-list-item--active {
  color: blue;
}
</style>
<script>
export default {
  name: "App",
  components: {},
  data: () => ({
    drawer: false,
    menus: [
      { title: "Home", icon: "mdi-home", route: "/" },
      { title: "About", icon: "mdi-account", route: "/about" },
    ],
    guest: true,
    value: 0,
  }),
  computed: {
    isHome() {
      return this.$route.path === "/";
    },
  },
};
</script>
