<style scoped>
.add-content {
  margin-left: auto;
  margin-right: auto;
  width: 80%;
  background-color: #fffdd0;
}
</style>

<template>
  <div class="add-content">
    <h3 class="text-center">Add Post</h3>
    <div class="row">
      <div class="col-md-6">
        <form @submit.prevent="addPost">
          <div class="form-group">
            <label>Title</label>
            <input type="text" class="form-control" v-model="post.title" />
          </div>
          <br />
          <div class="form-group">
            <label>Description</label>
            <input
              type="text"
              class="form-control"
              v-model="post.description"
            />
          </div>
          <br />
          <button type="submit" class="btn btn-primary">Add Post</button>
        </form>
      </div>
    </div>
  </div>
</template>
 
<script>
import Swal from "sweetalert2";
export default {
  data() {
    return {
      post: {},
    };
  },
  methods: {
    addPost() {
      this.axios
        .post("http://localhost:8000/api/post/add", this.post)
        .then((response) =>
          this.$router.push({ name: "home" })
          // console.log(response.data)
        );
      Swal.fire("Successfully added", " ", "success")
        .catch((error) => console.log(error))
        .finally(() => (this.loading = false));
    },
  },
};
</script>