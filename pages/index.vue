<template>
  <v-app class="white">
    <v-app-bar app class="orange">
      SERVER CONTROL BUTTONS ->
      <v-btn class="ma-4"> Reset all data </v-btn>
      <v-btn class="ma-4"> Reload page </v-btn>

      <v-spacer />

      <h4>Logged In -> USERNAME</h4>
    </v-app-bar>

    <v-main class="white">
      <v-container class="blue">
        <div>
          <h1>Query box</h1>
          USER COMMANDS ->
          <v-btn class="ma-4"> Register new user </v-btn>
          <v-btn class="ma-4"> Login </v-btn>
          <v-btn class="ma-4"> Add data </v-btn>
          <v-btn class="ma-4"> See data </v-btn>
          <br />
          ADMIN COMMANDS ->
          <v-btn class="ma-4"> See all registered users </v-btn>
          <v-btn class="ma-4"> See all users' data </v-btn>
        </div>
        <hr />
        <div>
          <h1>Output box</h1>
          <!--<p>{{ output }}</p>-->
        </div>
      </v-container>
    </v-main>

    <v-footer app class="green"> Nuxt-Authentication </v-footer>
  </v-app>
</template>

<script>
export default {
  // data() {
  //   return {
  //     output: '',
  //   }
  // },
  // methods: {
  //   async getAllUsers() {
  //     this.output = await this.$axios.get(
  //       process.env.SERVER_URL + 'dev/auth/all'
  //     )
  //   },
  // },
}
</script>

<style></style>
