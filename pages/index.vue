<template>
  <v-app>
    <v-navigation-drawer class="blue" app>
      Populate Navigation drawer for multiple pages later
    </v-navigation-drawer>

    <v-app-bar class="grey" app>
      <v-avatar class="mr-4" color="blue" size="45"></v-avatar>
      <div v-if="$auth.loggedIn === true">Greetings, {{ $auth.user }}.</div>
      <div v-else>Welcome guest.</div>

      <v-spacer />

      <div v-if="$auth.loggedIn === true">
        <v-btn class="ma-2"> LOGOUT </v-btn>
      </div>

      <div v-else>
        <v-btn nuxt to="/login" class="ma-2"> LOGIN </v-btn>
        <v-btn nuxt to="/registration" class="ma-2"> REGISTER </v-btn>
      </div>
    </v-app-bar>

    <!-- Sizes your content based upon application components -->
    <v-main class="white">
      <v-container fluid>
        THIS PAGE IS FOR EVERYONE ON THE NET
        <br />
        <nuxt-link to="/userOnly"> Go to registered user's section. </nuxt-link>
      </v-container>
    </v-main>

    <v-footer class="grey" app> Vue | Nuxt | Vuetify | Auth </v-footer>
  </v-app>
</template>

<script>
export default {}
</script>

<style></style>
