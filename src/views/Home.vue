<template>
  <div>
    <p>{{msg}}</p>
    <br>
    <button v-on:click="logout">LogOut</button>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      msg: 'Welcome ' + this.$session.get('username')
    }
  },
  beforeCreate(){
    if (!this.$session.exists()) {
      this.$router.push('/')
    }
  },
  methods: {
    logout(){
      this.$session.clear()
      this.$session.destroy()
      this.$router.push('/')
    }
  }
}
</script>
