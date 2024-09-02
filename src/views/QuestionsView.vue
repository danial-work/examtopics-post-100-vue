<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/question?qs=1&qe=10">Questions</router-link>
  </nav>
  <div>
    <h1>Questions</h1>
    
    </div>
</template>

<script setup>
import { useRoute } from 'vue-router'

const route = useRoute()
console.log(route.query)
</script>