<template>
  <div class="container">
    <div class="top-bar">
      <h2 class="text-warning">Laravel Vue CRUD</h2>
      <nav class="navbar float-right">
        <div class="collapse navbar-collapse">
          <div class="navbar-nav">
            <router-link to="/" tag="button">Home</router-link>
            <router-link to="/add" tag="button">Add Post</router-link>
          </div>
        </div>
      </nav>
    </div>
    <br />
    <router-view></router-view>
  </div>
</template>
 
<script>
export default {};
</script>