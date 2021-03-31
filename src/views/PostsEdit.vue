<template>
  <div class="posts-edit">
    <ul v-bind="post">
      <hr />
      <h1>Edit this Post:</h1>
      <form v-on:submit.prevent="updatePost(post)">
        <div class="form-group">
          <label>Title:</label>
          <input type="text" class="form-control" v-model="post.title" />
        </div>
        <div class="form-group">
          <label>Body:</label>
          <input type="text" class="form-control" v-model="post.body" />
        </div>
        <button type="submit" value="submit">Submit:</button>
      </form>

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
      errors: [],
    };
  },
  created: function () {
    // on page load, grab the individual Post to EDIT
    axios.get(`/api/posts/${this.$routes.params.id}`).then((res) => {
      console.log(res.data);
      this.post = res.data;
    });
  },
  methods: {
    // on button click, send the patch request to axios to actually UPDATE the Post
    updatePost: function (post) {
      let params = {
        title: post.title,
        body: post.body,
      };
      // End user will provide the "id" param in the browser. we can then use the "$route" global var to grab param and use it in axios request.
      axios.patch(`/api/posts/${this.$route.params.id}`, params).then(() => {
        this.$router.push("/posts/" + post.id);
      });
    },
  },
};
</script>
