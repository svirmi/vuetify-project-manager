<template>
  <v-layout>
    <v-flex class="">
      <div class="home">
        <h1 class="subheading grey--text">Dashboard</h1>

        <v-container class="my-5">
          <v-card class="pa-3">
            <v-layout wrap>
              <v-flex xs12 md6>
                <div class="caption grey--tex">Project title</div>
                <div>Create something</div>
              </v-flex>
              <v-flex xs6 sm4 md2>
                <div class="caption grey--tex">Person</div>
                <div>I am the person</div>
              </v-flex>
              <v-flex xs6 sm4 md2>
                <div class="caption grey--tex">Due by</div>
                <div>12-06-2020</div>
              </v-flex>
              <v-flex xs6 sm4 md2>
                <div class="caption grey--tex">Status</div>
                <div>in progress</div>
              </v-flex>
            </v-layout>
          </v-card>
        </v-container>

      </div>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  components: {

  }
}
</script>
