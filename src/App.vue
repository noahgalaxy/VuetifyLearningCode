<template>
  <v-app class="grey lighten-4">
    <nav-bar></nav-bar>
    <v-main class="mx-4 mb-4">
      <router-view></router-view>
    </v-main>


  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import NavBar from "./components/NavBar";

export default {
  name: 'App',

  components: {
    NavBar,
  },

  data: () => ({
    //
  }),
};
</script>
