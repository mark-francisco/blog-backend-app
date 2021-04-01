<template>
  <div id="app">
    <div id="nav"></div>

    <nav class="navbar navbar-expand-lg navbar-light bg-light" style="background-color: #e3f2fd">
      <a class="navbar-brand" href="/">Blog Vue App</a>
      <button
        class="navbar-toggler"
        type="button"
        data-toggle="collapse"
        data-target="#navbarNavAltMarkup"
        aria-controls="navbarNavAltMarkup"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
        <div class="navbar-nav">
          <router-link class="nav-link" to="/">Home</router-link>
          <router-link class="nav-link" to="/about">About</router-link>
          <router-link class="nav-link" to="/signup">Sign Up</router-link>
          <router-link class="nav-link" to="/login">Log In</router-link>
          <router-link class="nav-link" to="/logout">Log Out</router-link>
          <router-link class="nav-link" to="/posts">View All Posts</router-link>
          <router-link class="nav-link" to="/posts/new">Create a new Post</router-link>
        </div>
      </div>
    </nav>

    <router-view />
  </div>
</template>

<style>
body {
  background-image: url("./assets/papyrus.png");
}

#app {
  font-family: Geneva, Tahoma, Verdana, sans-serif;
}
</style>

<script>
export default {
  data: function () {},
  methods: {
    isLoggedIn: function () {
      return localStorage.getItem.jwt;
    },
  },
};
</script>
