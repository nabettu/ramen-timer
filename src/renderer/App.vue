<template>
  <div id="app">
    <v-app dark>
      
      <v-toolbar fixed app :clipped-left="clipped">
        <v-text>ラーメンタイマー</v-text>
      </v-toolbar>
      <v-content>
        <v-container fluid fill-height>
          <v-slide-y-transition mode="out-in">
            <router-view></router-view>
          </v-slide-y-transition>
        </v-container>
      </v-content>
      <v-navigation-drawer
        temporary
        fixed
        :right="right"
        v-model="rightDrawer"
        app
      >
        <v-list>
          <v-list-tile @click.native="right = !right">
            <v-list-tile-action>
              <v-icon light>compare_arrows</v-icon>
            </v-list-tile-action>
            <v-list-tile-title>Switch drawer (click me)</v-list-tile-title>
          </v-list-tile>
        </v-list>
      </v-navigation-drawer>
      <v-footer :fixed="fixed" app>
        <v-spacer></v-spacer>
        <span>&copy; 2017</span>
      </v-footer>
    </v-app>
  </div>
</template>

<script>
export default {
  name: "vuetron",
  data: () => ({
    clipped: false,
    drawer: true,
    fixed: false,
    items: [
      { icon: "apps", title: "Welcome", to: "/" },
      { icon: "bubble_chart", title: "Inspire", to: "/inspire" }
    ],
    miniVariant: false,
    right: true,
    rightDrawer: false,
    title: "Vuetify.js"
  })
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons");
/* Global CSS */
</style>
