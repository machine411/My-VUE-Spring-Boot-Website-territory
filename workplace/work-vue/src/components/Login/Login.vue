<template>
  <div>
      USER NAME:<input type="text" v-model="loginForm.username" placeholder="please input user name"/>
      <br><br>
      PASSWORD:<input type="password" v-model="loginForm.password" placeholder="please input password"/>
      <br><br>
      <button v-on:click="login">Login</button>
  </div>
</template>

<script>

  export default {
    name: 'Login',
    data () {
      return {
        loginForm: {
          username: '',
          password: ''
        },
        responseResult: []
      }
    },
    methods: {
      login () {
        this.$axios
          .post('/login', {
            username: this.loginForm.username,
            password: this.loginForm.password
          })
          .then(successResponse => {
            if (successResponse.data.code === 200) {
              this.$router.replace({path: '/index'})
            }
          })
          .catch(failResponse => {
          })
      }
    }
  }
</script>
