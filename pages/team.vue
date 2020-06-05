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
                  <v-avatar size="110">
                    <img
                      :src="person.gravatar"
                      :alt="`${person.firstName} ${person.company} avatar`"
                    >
                  </v-avatar>
                </v-responsive>
                <v-card-text>
                  <div class="display-1 text--primary">{{ person.firstName }}</div>
                  <div class="">{{ person.company }}</div>
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
  import Fakerator from "fakerator";

    export default {
      name: "team",
      mounted() {
        this.getData();

      },
      data() {
          return {
            team: []
          }
      },
      methods: {
          getData() {
            const fakerator = Fakerator("nb-NO");
            const teamSize = 8;
            let team = [];

            for (let i = 0; i < teamSize; i++) {
              let user = fakerator.entity.user();
              user.company = fakerator.company.name();
              team.push(user);
            }

            console.log(team);

            this.team = team;
          }
      }
    }
</script>

<style scoped>

</style>
