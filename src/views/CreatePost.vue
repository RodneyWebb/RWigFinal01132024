<script setup>
import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import router from '@/router';
import { ref } from 'vue';

let imageURL = ref('')
let caption = ref('')

function createPost() {
    const reqBody = {
        "image": imageURL.value,
        "caption": caption.value
    }
    fetch('http://localhost:3000/posts', 
    {
        headers: {"Content-Type": "application/json", "Authorization": document.cookie},
        body: JSON.stringify(reqBody),
        method: "POST"
    })
    .then(response => {
        if(response.status === 200) {
            alert("Post Successful!")
            router.push('/posts')
        } else {
            alert("Something went wrong. Please try again.")
        }
    })
    .catch(error => {
        console.log(error)
    })
}
</script>

<template>
    <div id="post-container">
        <div>
            <img id="logo" class="image" src="https://pngimg.com/d/instagram_PNG12.png">
        </div>
        <h1>Create a Post! 💻</h1>
        <div>
            <input v-model="imageURL" type="text" placeholder="Image URL" id="image-input">
            <!-- <label for="image-input">Image URL</label> -->
        </div>

        <div>
            <input v-model="caption" type="text" placeholder="Caption" id="caption-input">
            <!-- <label for="caption-input">Caption</label> -->
        </div>

        <button @click="createPost()">Post!</button>

    </div>
    <Footer></Footer>
</template>

<style scoped>
    #post-container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 1rem;
        background-image: linear-gradient(orange, red, hotpink, darkviolet);
        height: 90vh;
        gap: 10px;
    }
    #logo {
      height: 6rem;
      width: 6rem;
    }
</style>