<template>
  <v-app>
    <v-app-bar app> <h1>REGISTRATION</h1> </v-app-bar>

    <v-main class="grey">
      <v-container>
        <div>
          <div><label>USERNAME</label> <input v-model="username" /></div>
          <div><label>PASSWORD</label> <input v-model="password" /></div>
          <div>
            <label>REPEAT PASSWORD</label> <input v-model="rpassword" />
          </div>
          <v-btn @click="registerNewUser"> REGISTER </v-btn>
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
      rpassword: '',
    }
  },
  methods: {
    async registerNewUser() {
      if (this.username === '' || this.password === '') {
        this.output = 'Empty data fields!!'
      } else if (this.password !== this.rpassword) {
        this.output = 'Passwords don;t match!'
      } else if (this.username === 'guest') {
        this.output = 'Username not allowed.'
      } else {
        try {
          const res = await this.$axios.post('api/auth/register', {
            username: this.username,
            password: this.password,
          })
          this.output = 'Successfully registered! \n'
          console.log(res.data)
          const loginInfo = { username: this.username, password: this.password }
          try {
            const res = await this.$auth.loginWith('local', {
              data: loginInfo,
            })
            this.output += res
          } catch (err) {
            this.output += err.response
          }
        } catch (err) {
          this.output = err.response.data
          console.log(err)
        }
      }
      this.username = ''
      this.password = ''
      this.rpassword = ''
    },
  },
}
</script>

<style></style>
