<template>
  <div class="posts-show">
    <h1>{{ message }}</h1>
    <h1>{{ post.id }}</h1>
    <h1>{{ post.title }}</h1>
    <h1>{{ post.body }}</h1>
    <h1>{{ post.image }}</h1>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios"
export default {
  data: function() {
    return {
      message: "Welcome to Show page.js!",
      post: {}
    };
  },
  created: function() {
    console.log('in created');
    axios.get('/api/posts/' + this.$route.params.id).then(response => {
      console.log(response.data);
      this.post = response.data
    })
  },
  methods: {}
};
</script>
