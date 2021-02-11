<template>
  <div class="home">
    <h1> All Posts </h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <p> {{ post.user }}</p>
     <p> {{ post.title }}</p>
     <p> {{ post.body }}</p>
    </div>
  </div>
</template>

<style>

</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      posts: [],
    };
  },
  created: function() {
    this.indexPosts();
  },
  methods: {
    indexPosts: function() {
      axios.get("/api/posts").then(response => {
        this.posts = response.data;
        console.log("All Blogs", this.posts);
      })
    }
  }
}
</script>