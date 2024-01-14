<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
    <div id="container">
        <RouterLink to="/posts">🏠</RouterLink>
        <RouterLink to="/create-post">➕</RouterLink>
        <RouterLink to="/profile">👤</RouterLink>
    </div>
</template>

<style scoped>
    #container {
        background-color: white;
        height: 2rem;
        width: 100vw;
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        font-size: 1.5rem;    
        }
</style>