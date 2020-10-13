<template>
  <v-app>
    <v-navigation-drawer class="blue" app>
      Navigation drawer for multiple pages
    </v-navigation-drawer>

    <v-app-bar class="grey" app>
      <v-avatar class="mr-4" color="blue" size="45"></v-avatar>
      Greetings, {{ $auth.user }}.
      <v-spacer />
      <v-btn class="ma-2"> LOGOUT </v-btn>
    </v-app-bar>

    <!-- Sizes your content based upon application components -->
    <v-main class="white">
      <v-container fluid>
        THIS PAGE IS FOR LOGGED IN USERS ONLY
        <nuxt-link to="/"> Go back to home. </nuxt-link>
      </v-container>
    </v-main>

    <v-footer class="grey" app>
      Vue | Nuxt | Vuetify | Auth | Nandeesh
    </v-footer>
  </v-app>
</template>

<script>
export default {
  middleware: 'auth',
}
</script>

<style></style>
