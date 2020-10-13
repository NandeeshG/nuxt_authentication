<template>
  <v-app>
    <v-app-bar class="grey" app> THIS IS LOGIN PAGE </v-app-bar>
    <v-main class="white">
      <v-container fluid>
        Please login before continuing
        <br />
        <nuxt-link to="/"> Go back to home. </nuxt-link>
        <form @submit="userLogin">
          <div><label>Username</label> <input v-model="login.username" /></div>
          <div><label>Password</label> <input v-model="login.password" /></div>
          <v-btn type="submit" class="ma-2 green"> LOGIN NOW! </v-btn>
        </form>
        <br />
        <v-btn nuxt to="/registration"> REGISTER </v-btn>
      </v-container>
    </v-main>
    <v-footer class="grey" app> Vue | Nuxt | Vuetify | Auth </v-footer>
  </v-app>
</template>

<script>
export default {
  auth: 'guest', // Means only for guests
  data() {
    return {
      login: {
        username: '',
        password: '',
      },
    }
  },
  methods: {
    async userLogin() {
      try {
        const response = await this.$auth.loginWith('local', {
          data: this.login,
        })
        console.log('res', response)
      } catch (err) {
        console.log('err', err)
      }
    },
  },
}
</script>

<style></style>
