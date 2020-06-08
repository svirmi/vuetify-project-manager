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
  name: 'Default', // fixes [Vue warn]: Invalid component name: "layouts/default.vue". Component names should error
  components: {
    Navbar
  }
}
</script>
