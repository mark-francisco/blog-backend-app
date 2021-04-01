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
        <input type="text" class="form-control" v-model="title" maxlength="30" />
        <small class="text-warning">WARNING: Title must catch the reader's attention.</small>
        <br />
        <small class="text-danger" v-if="title.length > 0 && title.length <= 30">
          {{ 30 - title.length }} characters remaining.
        </small>
      </div>
      <div class="form-group">
        <label>Body:</label>
        <input type="text" class="form-control" v-model="body" />
        <small class="text-warning">WARNING: Blog post content must be compelling and stylistically consistent.</small>
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
