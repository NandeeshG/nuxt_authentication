<template>
  <v-app>
    <v-app-bar app> <h1>SECRET PAGE</h1> </v-app-bar>

    <v-main>
      <v-container>
        <div>
          <h1>THIS PAGE IS ONLY FOR USERS</h1>
        </div>
      </v-container>
    </v-main>

    <v-footer>
      <v-btn @click="$auth.logout()"> Logout </v-btn>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  middleware: 'auth',
}
</script>

<style></style>
