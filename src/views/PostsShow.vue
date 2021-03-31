<template>
  <div class="posts-show">
    <h1>{{ post.title }}</h1>
    <img v-bind:src="post.image" v-bind:alt="post.title" />

    <p>{{ post.body }}</p>
    <router-link v-bind:to="`/posts/${post.id}/edit`">
      <button>Edit</button>
    </router-link>
    <br />
    <button v-on:click="destroyPost(post)">Delete Post</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      post: {},
    };
  },
  created: function () {
    this.showPost();
  },
  methods: {
    showPost: function () {
      axios.get("/api/posts/" + this.$route.params.id).then((response) => {
        this.post = response.data;
        console.log(response.data);
      });
    },
    destroyPost: function (post) {
      axios.delete("/api/posts/" + post.id).then(() => {
        console.log("post was destroyed");
        this.$router.push("/posts/");
      });
    },
  },
};
</script>
