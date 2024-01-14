<script setup>
  import router from '@/router';
  import { ref } from 'vue'
  import { RouterLink } from 'vue-router'


  let email = ref('')
  let password = ref('')

  function login () {
      const reqBody = {
        "email": email.value,
        "password": password.value
        }
      fetch("http://localhost:3000/login", 
      {
          headers: {"Content-Type": "application/json"},
          body: JSON.stringify(reqBody),
          method: "POST"
      })
      .then(response => {
        return response.json()
      })
      .then(json => {
        //console.log(json)
        document.cookie = json
        router.push('/posts')
        //Do Stuff
      })
      .catch(error => {
        console.log(error)
      })
}
</script>

<template>

    <div class="container">
      <img id="logo" src="https://pngimg.com/d/instagram_PNG12.png">
      <h1>Home</h1>
      <input v-model="email" type="text" placeholder="email"/>
      <input v-model="password" type="text" placeholder="password">
      <button @click="login">Login</button>
      <RouterLink to="/register">Register</RouterLink>
    </div>
</template>

<style scoped>
    .container {
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      gap: 10px;
      height: 100vh;
      background-image: linear-gradient(orange, red, hotpink, darkviolet);
    }
    #logo {
      height: 6rem;
      width: 6rem;
    }

</style>