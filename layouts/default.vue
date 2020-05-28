<template>
  <v-app>

    <Navbar />

    <v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>

  </v-app>
</template>

<script>
import Navbar from "./partials/navbar";

export default {
  components: {
    Navbar
  }
}
</script>
