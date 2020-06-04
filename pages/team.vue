<template>
  <v-layout>
    <v-flex class="">
      <div class="team">
        <h1 class="grey--text">Team Page</h1>

        <v-container class="my-5">
          <v-layout wrap :class="`pa-3 project`">
            <v-flex xs12 sm6 md4 lg3 v-for="person in team" :key="person.name">
              <v-card class="text-center ma-3">
                <v-responsive class="pt-4">
                  image goes here
                </v-responsive>
                <v-card-text>
                  <div class="display-1 text--primary">{{ person.name }}</div>
                  <div class="">{{ person.role }}</div>
                </v-card-text>
                <v-card-actions>
                  <v-btn text>
                    <v-icon right>mdi-message</v-icon>
                    <span>Message</span>
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-flex>
          </v-layout>
        </v-container>

      </div>
    </v-flex>
  </v-layout>
</template>

<script>
    export default {
        name: "team",
      data() {
          return {
            team: [
              { name: 'Gummy The Bear', role: 'Web developer' },
              { name: 'Sher Lock', role: 'Software engineer'},
              { name: 'The Beast', role: 'Front-end developer'},
              { name: 'Terminator', role: 'Back-end developer'},
              { name: 'Denis', role: 'SEO guru'}
            ]
          }
      }
    }
</script>

<style scoped>

</style>
