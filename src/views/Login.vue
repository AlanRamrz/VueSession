<template>
  <div>
    <label>User</label>
    <br>
    <input type="text" v-model="username">
    <br><br>
    <label>Password</label>
    <br>
    <input type="password" v-model="password">
    <br><br>
    <button v-on:click="login">LogIn</button>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      username: '',
      password: ''
    }
  },
  methods: {
    login(){
      if (this.username && this.password) {

        if (this.username === this.password) {
          this.$session.start()
          this.$session.set('username', this.username)
          this.$router.push('/home')
        }
        else {
          console.log('Error')
        }
      }
      else {
        console.log('Error')
      }
    }
  },
  beforeCreate(){
    if (this.$session.exists()) {
      this.$router.push('/home')
    }
  }
}
</script>
