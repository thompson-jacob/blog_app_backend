<template>
  <div class="home">
    <h1> Post</h1>
      <p> {{ post.user }}</p>
     <p> {{ post.title }}</p>
     <p> {{ post.body }}</p>
     <img v-bind:src="post.image" alt="" />
    <a href=" /Posts/Index">Back to all posts</a>

    
  </div>
</template>

<script>

import axios from "axios";

export default {
  data: function() {
    return {
      post: {},

    };
  },
created: function() {
  this.showPost();
},
methods: {
  showPost: function() {
    axios.get("/api/posts/" + this.$route.params.id).then(response => {
      console.log(response.data);
      this.post = response.data;
    });
  },
},
};
</script>