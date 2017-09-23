
<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>

    <input type="email" name="email" placeholder= "email" v-model="email" /> <br>
    <input type="password" name="password" placeholder= "password" v-model="password" /> <br>
    <button @click="register">Register</button>

  </div>
</template>

<script>
/*eslint-disable*/

import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      msg: 'Register Component',
      email: 'kaka@gmail.com',
      password: 'hihi'
    }
  },

  watch: {
    email(val){
      console.log(`Email ${val} has Change`, val)
    }
  },

  methods: {
    async register() {
      const response = await AuthenticationService.register({
        email: this.email,
        password: this.password
      })

      console.log('Response:', response.data);
    }
  },
  mounted() {
    setTimeout(() => {
      this.email = 'hello World'
    }, 1000);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
