<script setup>
import router from '@/router';
import { ref } from 'vue'

const email = ref('')
const username = ref('')
const password = ref('')


function register() {

    const reqBody = {
      "email": email.value,
      "username": username.value,
      "password": password.value
    }

    fetch("http://localhost:3000/users", 
    {
            headers: {"Content-Type": "application/json"},
            body: JSON.stringify(reqBody),
            method: "POST"
    })
    .then(response => {
        if(response.status === 201) {
            alert("Account Created! Please login to continue.")
            router.push("/")
        } else {
            alert("Something went wrong! Please try again.")
        }

    })
    .catch(error => {
        console.log(error)
    })
}
</script>

<template>
    <div class="container">
        <img id="logo" 
            src="https://pngimg.com/d/instagram_PNG12.png">
        <h1>Register</h1>
        <input v-model="email" type="text" placeholder="email" />
        <input v-model="username" type="text" placeholder="username" />
        <input v-model="password" type="text" placeholder="password">
        <button @click="register">Register</button>
        <RouterLink to="/">Cancel</RouterLink>
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