<template>
  <nav>

    <!-- Top Bar the one that's fixed -->
    <v-app-bar app class="black">
        <v-app-bar-nav-icon dark class="d-none d-md-flex" @click="drawer = !drawer"></v-app-bar-nav-icon>
        <v-app-bar-title class="text-lowercase white--text">
            <h3>
              <span class="font-weight-light grey--text">github</span>
              <span class="font-weight-dark">Trackr.</span>
            </h3>
        </v-app-bar-title>
        <v-spacer></v-spacer>

      <v-btn icon @click="$emit('toggleMode', {lightMode}); lightMode = !lightMode">
        <v-icon color="white">mdi-theme-light-dark</v-icon>
      </v-btn>
    </v-app-bar>

    <!-- Sidebar the one that toggles -->
    <v-navigation-drawer v-model="drawer" fixed app dark class="black .d-none .d-md-flex" width="225px">
        <v-list rounded>
            <v-list-item v-for="([icon, text, route], i) in links" :key="i" :to="route" link>
                <v-list-item-icon>
                    <v-icon>{{ icon }}</v-icon>
                </v-list-item-icon>
  
                <v-list-item-content>
                    <v-list-item-title class="font-weight-medium">{{ text }}</v-list-item-title>
                </v-list-item-content>

            </v-list-item>
        </v-list>
    </v-navigation-drawer>

  </nav>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      links: [
        [ 'mdi-chart-histogram', 'Profile', '/profile' ],
        [ 'mdi-home', 'Home', '/dashboard' ],
        [ 'mdi-database', 'My Repos', '/user-repos' ],
        [ 'mdi-office-building', 'My Orgs',  '/user-orgs' ],
        [ 'mdi-playlist-star', 'Watchlist', '/watchlist' ],
      ],
      value: 1,
      lightMode: localStorage.getItem('theme') ? (localStorage.getItem('theme') == 'light' ? true : false ) : false
    }
  },
}
</script>

<style>
</style>