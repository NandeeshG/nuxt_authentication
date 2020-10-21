<template>
  <v-app>
    <v-app-bar app> <h1>LOGIN</h1> </v-app-bar>

    <v-main class="grey">
      <v-container>
        <div>
          <div><label>USERNAME</label> <input v-model="username" /></div>
          <div><label>PASSWORD</label> <input v-model="password" /></div>
          <v-btn @click="loginUser"> LOGIN </v-btn>
        </div>
        <div>
          <p>{{ output }}</p>
        </div>
      </v-container>
    </v-main>

    <v-footer>
      <v-btn nuxt to="/"> Home </v-btn>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  auth: 'guest',
  data() {
    return {
      output: '-',
      username: '',
      password: '',
    }
  },
  methods: {
    async loginUser() {
      const loginInfo = { username: this.username, password: this.password }
      try {
        const res = await this.$auth.loginWith('local', {
          data: loginInfo,
        })
        this.output = res
      } catch (err) {
        this.output = err.response
      }
    },
  },
}
</script>

<style></style>
