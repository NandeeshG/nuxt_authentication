<template>
  <h1>Hi</h1>
</template>

<script>
const http = require('http')

export default {
  data() {
    return {
      name: 'user',
    }
  },
  mounted() {
    console.log('Before req')
    http.get('http://127.0.0.1:5000/1', (res) => console.log(res))
    console.log('After req')
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
