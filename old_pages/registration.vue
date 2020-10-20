<template>
  <v-app>
    <v-app-bar class="grey" app> THIS IS REGISTRATION PAGE </v-app-bar>
    <v-main class="cyan">
      <v-container fluid>
        <nuxt-link to="/"> Go back to home. </nuxt-link>
        <br />
        Please enter your details
        <form @submit="userRegister">
          <br />
          <div>
            <label>Username</label>
            <input v-model="login.username" class="grey" />
          </div>
          <br />
          <div>
            <label>Password</label>
            <input v-model="login.password" class="grey" />
          </div>
          <v-btn type="submit" class="ma-2 green"> REGISTER NOW! </v-btn>
        </form>
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
