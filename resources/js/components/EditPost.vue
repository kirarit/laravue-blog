<style scoped>
.edit-content {
  margin-left: auto;
  margin-right: auto;
  width: 80%;
  background-color: #fffdd0;
}
</style>
<template>
  <div class="edit-content">
    <h3 class="text-center">Edit Post</h3>
    <div class="container">
      <form @submit.prevent="updatePost">
        <div class="form-group">
          <label>Title</label>
          <input type="text" class="form-control" v-model="post.title" />
        </div>
        <br />
        <div class="form-group">
          <label>Description</label>
          <input type="text" class="form-control" v-model="post.description" />
        </div>
        <br />
        <button type="submit" class="btn btn-primary">Update Post</button>
      </form>
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
  created() {
    this.axios
      .get(`http://localhost:8000/api/post/edit/${this.$route.params.id}`)
      .then((response) => {
        this.post = response.data;
        // console.log(response.data);
      });
  },
  methods: {
    updatePost() {
      this.axios
        .post(
          `http://localhost:8000/api/post/update/${this.$route.params.id}`,
          this.post
        )
        .then((response) => {
          this.$router.push({ name: "home" });
          Swal.fire("Successfully updated", " ", "success");
        });
    },
  },
};
</script>