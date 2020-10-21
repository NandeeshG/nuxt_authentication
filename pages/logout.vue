<template>
  <v-app>
    <v-app-bar app> <h1>LOGGING YOU OUT...</h1> </v-app-bar>
  </v-app>
</template>

<script>
export default {
  middleware: 'auth',
  methods: {
    async logoutUser() {
      try {
        const res = await this.$auth.logout()
        console.log('Logout - ', res)
      } catch (err) {
        console.log('Logout error - ', err.response)
      }
    },
  },
}
</script>

<style></style>
