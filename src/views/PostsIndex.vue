<template>
  <div class="home">
    <h1> All Posts </h1>
    <div v-for="post in posts" v-bind:key="post.id">
      <p> {{ post.user }}</p>
     <p> {{ post.title }}</p>
     <p> {{ post.body }}</p>
     <img v-bind:src="post.image" alt="" />
     <div>
       <a :href="`/posts/${post.id}`">More info</a>
     </div>
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