<template>
  <v-layout>
    <v-flex class="">
      <div class="home">
        <h1 class="subheading grey--text">Dashboard</h1>

        <v-container class="my-5">
          <v-card flat v-for="project in projects" :key="project.title">
            <v-layout wrap :class="`pa-3 project ${project.status.replace(' ','_')}`">
              <v-flex xs12 md6>
                <div class="caption grey--tex">{{ project.title }}</div>
                <div>Create something</div>
              </v-flex>
              <v-flex xs6 sm4 md2>
                <div class="caption grey--tex">Person</div>
                <div>{{ project.person }}</div>
              </v-flex>
              <v-flex xs6 sm4 md2>
                <div class="caption grey--tex">Due by</div>
                <div>{{ project.due }}</div>
              </v-flex>
              <v-flex xs6 sm4 md2>
                <div>
                  <v-chip small :class="`${project.status.replace(' ','_')} white--text caption`">{{ project.status }}</v-chip>
                </div>
              </v-flex>
            </v-layout>
            <v-divider></v-divider>
          </v-card>
        </v-container>

      </div>
    </v-flex>
  </v-layout>
</template>
<script>
export default {
  components: {},
  data() {
    return {
      projects: [
        {title: 'Title 1', person: 'Gummy The Bear', due: '10-10-2020', status: 'in progress', content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Amet aspernatur assumenda beatae consequatur consequuntur delectus distinctio eos, illum in itaque maxime minima nesciunt nostrum nulla repellendus rerum sint, sit voluptate.'},
        {title: 'Title 2', person: 'Sher Lock', due: '02-02-2020', status: 'overdue', content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Amet aspernatur assumenda beatae consequatur consequuntur delectus distinctio eos, illum in itaque maxime minima nesciunt nostrum nulla repellendus rerum sint, sit voluptate.'},
        {title: 'Title 3', person: 'The Beast', due: '04-08-2020', status: 'complete', content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Amet aspernatur assumenda beatae consequatur consequuntur delectus distinctio eos, illum in itaque maxime minima nesciunt nostrum nulla repellendus rerum sint, sit voluptate.'},
        {title: 'Title 4', person: 'Terminator', due: '19-09-2020', status: 'in progress', content: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Amet aspernatur assumenda beatae consequatur consequuntur delectus distinctio eos, illum in itaque maxime minima nesciunt nostrum nulla repellendus rerum sint, sit voluptate.'},
      ]
    }
  }
}
</script>

<style lang="scss">

  $in_progress: orange;
  $complete: #3cd1c2;
  $overdue: tomato;

  .project {
    &.in_progress {
      border-left: 4px solid $in_progress;
    }
    &.complete {
      border-left: 4px solid $complete;
    }
    &.overdue {
      border-left: 4px solid $overdue;
    }
  }

  .v-chip {
    &.in_progress {
      background: $in_progress!important;
    }
    &.complete {
      background: $complete!important;
    }
    &.overdue {
      background: $overdue!important;
    }
  }
</style>
