<template>
  <v-app>
    <v-app-bar app>
      <h1>HOME</h1>
      <v-spacer />
      Hi there! {{ this.$auth.user || 'guest' }}
    </v-app-bar>

    <v-main>
      <v-container>
        <v-btn nuxt to="/login"> Login </v-btn>
        <v-btn nuxt to="/registration"> Register </v-btn>
        <v-btn nuxt to="/secretPage"> secret page </v-btn>
        <div>OUTPUT - {{ this.$auth.user }}</div>
      </v-container>
    </v-main>

    <v-footer> </v-footer>
  </v-app>
</template>

<script>
export default {
  auth: 'false',
}
</script>

<style></style>
