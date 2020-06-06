<template>
  <nav>
    <v-app-bar flat app>
      <v-app-bar-nav-icon class="grey--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>
        <span class="font-weight-light">Todo</span>
        <span>Vuetify</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-btn text>
        <span>Sign Out</span>
        <v-icon right>mdi-exit-to-app</v-icon>
      </v-btn>
    </v-app-bar>

    <v-navigation-drawer
      temporary
      v-model="drawer"
      app>

      <v-list>
        <v-list-item v-for="link in links" :key="`drawer-`+link.text" :to="link.route">
          <v-list-item-icon>
            <v-icon v-text="link.icon"></v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="link.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>

    </v-navigation-drawer>
  </nav>
</template>
<script>
    export default {
        name: "Navbar",
      data() {
          return {
            drawer: false,
            links: [
              {icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/'},
              {icon: 'mdi-folder', text: 'My projects', route: '/projects'},
              {icon: 'mdi-account-multiple', text: 'Team', route: '/team'},
              {icon: 'mdi-format-line-style', text: 'Styling', route: '/styling'},
              {icon: 'mdi-apps', text: 'Form A', route: '/form-a'},
              {icon: 'mdi-apps', text: 'Form B', route: '/form-b'},
            ]
          }
      }
    }
</script>
