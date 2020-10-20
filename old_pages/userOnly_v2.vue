<template>
  <v-container>
    <h1>Axios</h1>
    <h3>
      Nobody can access GET 4,5. Other than that Only user id iTh can access iTh
      Get
    </h3>
    <v-row>
      <v-col cols="3">
        <v-btn @click="getClick(0)"> GET 0 </v-btn>
        <v-btn @click="getClick(1)"> GET 1 </v-btn>
        <v-btn @click="getClick(2)"> GET 2 </v-btn>
        <v-btn @click="getClick(3)"> GET 3 </v-btn>
        <v-btn @click="getClick(4)"> GET 4 </v-btn>
        <v-btn @click="getClick(5)"> GET 5 </v-btn>
      </v-col>
    </v-row>
    <h4>DATA-</h4>
    <h3>{{ userinfo }}</h3>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  middleware: 'auth',
  data() {
    return {
      userinfo: '',
    }
  },
  mounted() {
    console.log('Page mounted')
  },
  methods: {
    getClick(idx) {
      axios({
        method: 'get',
        url: `http://127.0.0.1:5000/${idx}`,
      })
        .then((res) => {
          this.userinfo = res.data
        })
        .catch((err) => {
          this.userinfo = 'Internal error. Probably API Down...'
          console.log(err)
        })
    },
    postClick() {
      console.log('Clicked post')
    },
  },
}
</script>

<style>
body {
  background-color: gray;
}
h1 {
  text-align: center;
  font-size: 60px;
  background-color: brown;
  color: white;
}
</style>
