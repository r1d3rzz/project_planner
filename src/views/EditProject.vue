<template>
  <h1>Edit Project</h1>
  <form @submit.prevent="editProject">
    <div class="inputBox">
      <label for="title" class="projectTitle">Edit Title</label>
      <input type="text" id="title" class="projectInput" v-model="title" />
    </div>

    <div class="inputBox">
      <label for="detail" class="projectTitle">Edit Detail</label>
      <input type="text" id="detail" class="projectInput" v-model="detail" />
    </div>

    <div class="btnBox">
      <button class="editBtn">Edit Project</button>
    </div>
  </form>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      title: "",
      detail: "",
      api: "http://localhost:3000/projects/",
    };
  },
  methods: {
    editProject() {
      fetch(this.api + this.id, {
        method: "PATCH",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          title: this.title,
          detail: this.detail,
        }),
      })
        .then(() => this.$router.push("/"))
        .catch((err) => console.log(err.message));
    },
  },
  mounted() {
    fetch(this.api + this.id)
      .then((resolve) => {
        return resolve.json();
      })
      .then((data) => {
        this.title = data.title;
        this.detail = data.detail;
      })
      .catch((err) => console.log(err.message));
  },
};
</script>

<style>
.editBtn {
  border: none;
  outline: none;
  background-color: green;
  padding: 5px 10px;
  color: white;
  font-size: 18px;
  font-weight: bold;
  border-radius: 5px;
  cursor: pointer;
}
</style>