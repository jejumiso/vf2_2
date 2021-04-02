<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>타이틀</v-toolbar-title>
      <v-spacer />
      <v-btn icon to="/about">s </v-btn>
    </v-app-bar>

    <v-content>
      <router-view />
    </v-content>
  </v-app>
</template>

<script>
export default {
  name: "App",

  mounted() {
    console.log(this.$firebase);
  },
};
</script>
