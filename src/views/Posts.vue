<script setup>
//import Header from '../components/Header.vue'
import Footer from '../components/Footer.vue'
import { ref } from 'vue';

let posts = ref([])

fetch('http://localhost:3000/posts',
{
    headers: { 'Authorization': document.cookie},
})
.then(response => {
    return response.json()
})
.then(json => {
    posts.value.push(...json)
})
.catch(error => {
    console.log(error)
})
</script>

<template>
    <div id="page-container">
        <Header></Header>
        <div v-for="post in posts">
            <div class="post-container">
                <div class="post">
                    <div class="card-header">
                        <p>{{ post.username }}</p>
                    </div>
                    <div class="card-image-container">
                        <img src="https://upload.wikimedia.org/wikipedia/commons/3/3d/Fesoj_-_Papilio_machaon_%28by%29.jpg" alt="butterflies">
                    </div>
                    <div class="card-footer">
                        <div class="likes-container">
                            <p>Likes: {{ post.likes.length }}</p>
                            <p>🤍</p>
                        </div>
                        <div class="caption-container">
                            <p>{{ post.username }}: {{ post.caption }}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <Footer></Footer>
    </div>
</template>


<style scoped>
    #page-container {
        background-color: #D3D3D3;
        margin: 0;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: space-between;

    }

    .post-container {
        background-color: #D3D3D3;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        margin: 1rem;
    }

    .post {
        background-color: white;

    }

    .card-header {
        padding-left: 1rem;
        font-size: 1rem;

    }

    .card-image-container {
        display: flex;
        flex-direction: column;
    }

    .card-footer {
        display: flex;
        flex-direction: column;
        
    }

    .likes-container {
        display: flex;
        justify-content: space-between;
        padding-left: 1rem;
        padding-right: 1rem;

    }

    .caption-container {
        padding-left: 1rem;
    }



</style>