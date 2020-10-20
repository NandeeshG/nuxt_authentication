<template>
  <v-app class="white">
    <v-app-bar app class="orange">
      SUPER CONTROL BUTTONS ->
      <v-btn class="ma-4 red" @click="serverReset"> Reset server data </v-btn>
      <v-btn class="ma-4 red" @click="reloadPage"> Reload this page </v-btn>

      <v-spacer />

      <h4>Logged In -> {{ loggedIn.username }}</h4>
    </v-app-bar>

    <v-main class="white">
      <v-container class="blue">
        <div>
          <h1>Form</h1>
          <div class="ma-4">
            <label>USERNAME</label> <input v-model="username" class="grey" />
          </div>
          <div class="ma-4">
            <label>PASSWORD</label>
            <input v-model="password" class="grey" type="password" />
          </div>
          <div class="ma-4">
            <label>REPEAT PASSWORD</label>
            <input v-model="rpassword" class="grey" type="password" />
            <p>(only required during registration)</p>
          </div>
        </div>
        <div>
          <v-btn class="ma-4 green" @click="registerNewUser">
            Register new user
          </v-btn>
          <v-btn class="ma-4 green" @click="loginUser"> Login </v-btn>
          <v-btn class="ma-4 grey" @click="logoutUser"> Logout </v-btn>
        </div>
        <div>
          <h1>Query box form</h1>

          <div class="ma-4">
            <label>Name</label> <input v-model="name" class="grey" />
          </div>
          <div class="ma-4">
            <label>Age</label> <input v-model="age" class="grey" />
          </div>
          <div class="ma-4">
            <label>Motto</label> <input v-model="motto" class="grey" />
          </div>

          <v-btn class="ma-4 orange" @click="addUserData"> Add data </v-btn>
          <v-btn class="ma-4 orange" @click="seeUserData"> See data </v-btn>
          <br />
          ADMIN COMMANDS ->
          <v-btn class="ma-4 cyan" @click="getAllUsers">
            See all registered users
          </v-btn>
          <v-btn class="ma-4 cyan" @click="getAllData">
            See all users' data
          </v-btn>
        </div>
        <hr />
        <div>
          <h1>Output box</h1>
          <p>{{ output }}</p>
        </div>
      </v-container>
    </v-main>

    <v-footer app class="green"> Nuxt-Axios-Authentication </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      output: 'EMPTY',
      username: '',
      password: '',
      rpassword: '',
      name: '',
      age: '',
      motto: '',
      loggedIn: {
        username: 'guest',
        accessToken: '',
      },
    }
  },
  methods: {
    addUserData() {
      console.log('CS')
    },
    seeUserData() {
      console.log('CS')
    },
    getAllData() {
      console.log('CS')
    },
    async logoutUser() {
      if (
        this.loggedIn.username === 'guest' ||
        this.loggedIn.accessToken === ''
      ) {
        this.output = 'Error: No user loggedin!'
      } else {
        try {
          const authorizationToken = 'Bearer ' + this.loggedIn.accessToken
          const res = await this.$axios.post(
            'api/auth/logout',
            {},
            {
              headers: {
                authorization: authorizationToken,
              },
            }
          )
          console.log(res)
          this.output = res.data
        } catch (err) {
          this.output = err.response
        }
      }
      this.loggedIn.username = 'guest'
      this.loggedIn.accessToken = ''
    },
    async loginUser() {
      if (this.username === '' || this.password === '') {
        this.output = 'Empty data fields!!'
      } else if (
        this.loggedIn.username !== 'guest' ||
        this.loggedIn.accessToken !== ''
      ) {
        this.output = 'Someone is already loggedIn!'
      } else {
        try {
          const res = await this.$axios.post('/api/auth/login', {
            username: this.username,
            password: this.password,
          })
          this.loggedIn.accessToken = res.data.accessToken
          this.loggedIn.username = this.username
          this.output = 'Successgully loggedIn!'
        } catch (err) {
          this.output = err.response.data
        }
      }
      this.username = ''
      this.password = ''
      this.rpassword = ''
    },
    async getAllUsers() {
      try {
        const res = await this.$axios.get('dev/auth/all')
        this.output = res.data
      } catch (err) {
        this.output = err.response.data
      }
    },
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
          this.output = 'Successfully registered!'
          console.log(res.data)
          if (res.data.accessToken !== undefined) {
            this.output += '\n Successfully loggedIn!'
            this.loggedIn.username = this.username
            this.loggedIn.accessToken = res.data.accessToken
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
    async serverReset() {
      try {
        const res = await this.$axios.post('/dev/auth/reset')
        this.output = res.data
      } catch (err) {
        this.output = err.response.data
      }
    },
    reloadPage() {
      window.location.reload()
    },
  },
}
</script>

<style></style>
