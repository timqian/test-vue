<template>
  <div id="app">
    <h1>{{ msg }}<button v-on:click="auth">auth</button></h1>
  </div>
</template>

<script>
import axios from "axios";

const code = window.location.search.slice(6)
console.log(code, typeof code);
if (code) {
  axios({
    method: 'post',
    url: 'https://github.com/login/oauth/access_token',
    data: {
      'client_id': '317418b2afb5d9d04221',
      'client_secret': 'fa0423f595263172e2a53617d24aa599269875a7',
      'code':code
    }
  }).then((res) => {
    console.log(res);
  }).catch((res) => {
    console.log(res);
  })
} else {

}

export default {
  data () {
    return {
      msg: 'Hello niVue!'
    }
  },

  methods: {
    auth (event) {
      window.location.replace('https://github.com/login/oauth/authorize?client_id=317418b2afb5d9d04221')
    }
  }
}
</script>

<style>
body {
  font-family: Helvetica, sans-serif;
}
</style>
