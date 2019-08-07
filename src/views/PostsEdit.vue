<template>
  <div class="posts-show">
    <h1>{{ message }}</h1>
    <form v-on:submit.prevent="updatePost()">
      <p>title: <input type="text" v-model="post.title"></p>
      <p>body: <input type="text" v-model="post.body"></p>
      <p>image: <input type="text" v-model="post.image"></p>
      <input type="submit" value="update your post">
    </form>
  </div>

</template>

<style>
</style>

<script>
import axios from "axios"
export default {
  data: function() {
    return {
      message: "Welcome to Edit page.js!",
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
  methods: {
    updatePost: function() {
      console.log('updating post');
      // take the user data
      this.post
      // send it to the api
      axios.patch('/api/posts/' + this.post.id, this.post).then(response => {
        console.log('updated the post');
        this.$router.push('/posts/' + this.post.id)
        // redirect somewhere
      })
    }
  }
};
</script>
