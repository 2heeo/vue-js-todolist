<template>
  <v-app>
    <v-container class="grey lighten-4" fluid>
      <v-layout row wrap>
        <v-flex xs12>
          <Home/>
        </v-flex>
      </v-layout>
  </v-container>
  </v-app>
</template>

<script>
import Home from "./components/Home.vue"

export default {
  components: {
    Home
  }
}
</script>
