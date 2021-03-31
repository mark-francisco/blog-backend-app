<template>
  <div class="posts-new">
    <form v-on:submit.prevent="createPost()">
      <h1>Add a new Post!</h1>
      <!-- Errors go here: -->
      <ul>
        <li class="text-danger" v-for="error in errors" v-bind:key="error">
          {{ error }}
        </li>
      </ul>
      <!-- New Post form goes here -->
      <div class="form-group">
        <label>Title:</label>
        <input type="text" class="form-control" v-model="title" />
      </div>
      <div class="form-group">
        <label>Body:</label>
        <input type="text" class="form-control" v-model="body" />
      </div>
      <div class="form-group">
        <label>Image:</label>
        <input type="text" class="form-control" v-model="image" />
      </div>
      <button type="submit" value="submit">Submit!</button>
    </form>
  </div>
</template>

<style></style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      title: "",
      body: "",
      image: "",
      errors: "",
    };
  },
  methods: {
    createPost: function () {
      let params = {
        title: this.title,
        body: this.body,
        image: this.image,
      };
      axios
        .post("/api/posts", params)
        .then(() => {
          this.$router.push("/posts");
        })
        .catch((err) => {
          console.log(err.response);
          this.errors = err.data;
        });
    },
  },
};
</script>
