<template>
  <div class="posts-show">
    <ul v-bind="post">
      <hr />
      <h1>More Info:</h1>
      <h2>{{ post.id }}: {{ post.title }}</h2>
      <p>{{ post.body }}</p>
      <img v-bind:src="post.image" />
      <br />
      <router-link v-bind:to="`/posts/${post.id}/edit`"><button>Edit this Post:</button></router-link>

      <hr />
    </ul>
  </div>
</template>

<style>
img {
  height: 200px;
}
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      post: [],
    };
  },
  created: function () {
    this.showPost();
  },
  methods: {
    showPost: function () {
      axios.get(`/api/posts/` + this.$route.params.id).then((res) => {
        this.post = res.data;
      });
    },
  },
};
</script>
