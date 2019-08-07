<template>
  <div class="home">
    <!-- <h1>{{ blog_posts }}</h1> -->
    <div v-for="post in blog_posts">
      <p>{{post.title}}</p>
      <p><router-link v-bind:to="'/posts/' + post.id">See more info</router-link></p>
      <p><router-link v-bind:to="'/posts/' + post.id + '/edit'">Edit the post</router-link></p>
    </div>
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
