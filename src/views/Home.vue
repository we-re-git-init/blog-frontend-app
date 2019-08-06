<template>
  <div class="home">
    <h1>{{ blog_posts }}</h1>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios"
export default {
  data: function() {
    return {
      message: "Welcome to Vue.js!",
      blog_posts: []
    };
  },
  created: function() {
    axios.get('/api/posts').then(response => {
      this.blog_posts = response.data;
    })
  },
  methods: {}
};
</script>
