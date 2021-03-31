<template>
  <div class="home">
    <div v-for="post in posts" v-bind:key="post.id">
      <h1>{{ post.title }}</h1>
      <!-- <h3>
        <em>{{ post.user_id }}</em>
      </h3> -->
      <router-link v-bind:to="`posts/${post.id}`">
        <img v-bind:src="post.image" v-bind:alt="post.title" />
      </router-link>
      <p>{{ post.body }}</p>
      <p>•••</p>
    </div>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      posts: [],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/api/posts").then((response) => {
        this.posts = response.data;
        console.log(response.data);
      });
    },
  },
};
</script>
