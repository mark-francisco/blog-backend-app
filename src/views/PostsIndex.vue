<template>
  <div class="posts-index">
    <div class="card" style="width: 18rem">
      <ul v-for="post in posts" v-bind:key="post.id">
        <router-link v-bind:to="`/posts/${post.id}`">
          <img v-bind:src="post.image" class="card-img-top" alt="..." />
        </router-link>
        <div class="card-body">
          <p class="card-text">{{ post.id }}: {{ post.title }}</p>
        </div>
      </ul>
    </div>

    <!-- <ul v-for="post in posts" v-bind:key="post.id">
      <hr />
      <h2>{{ post.id }}</h2>
      <h2>{{ post.title }}</h2>
      pre-pending your routes with "/" ensures that you start at the root route -->
    <!-- <router-link v-bind:to="`/posts/${post.id}`">
        <img v-bind:src="post.image" />
      </router-link>
      <hr />
    </ul> -->
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
      posts: [],
    };
  },
  created: function () {
    this.indexPosts();
  },
  methods: {
    indexPosts: function () {
      axios.get("/api/posts").then((res) => {
        this.posts = res.data;
        console.log("INDEX OF POSTS:", this.posts);
      });
    },
  },
};
</script>
