<template>
  <div class="project" :class="{ complete: project.complete }">
    <div class="flexing">
      <div>
        <h2 @click="showDetail = !showDetail">{{ project.title }}</h2>
      </div>
      <div>
        <i class="fas fa-solid fa-trash pjEditBtn" @click="deleteProject"></i>
        <router-link :to="{ name: 'editProject', params: { id: project.id } }">
          <i class="fas fa-solid fa-edit pjEditBtn"></i>
        </router-link>
        <i class="fas fa-solid fa-check pjEditBtn" @click="completeProject"></i>
      </div>
    </div>
    <p v-if="showDetail">{{ project.detail }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      showDetail: false,
      api: "http://localhost:3000/projects/",
    };
  },
  props: ["project"],
  methods: {
    deleteProject() {
      let deleteRoute = this.api + this.project.id;
      fetch(deleteRoute, { method: "DELETE" })
        .then(() => {
          this.$emit("delete", this.project.id);
        })
        .catch((err) => console.log(err.message));
    },
    completeProject() {
      let completeRoute = this.api + this.project.id;
      /*
        Update => 3 
        1.method : "PATCH"
        2.headers : "Content-Type" : "application/json"
        3.body : JSON.stringify({
          //repair data
        }) 
      */
      fetch(completeRoute, {
        method: "PATCH",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify({
          complete: !this.project.complete,
        }),
      })
        .then(() => {
          this.$emit("complete", this.project.id);
        })
        .catch((err) => {
          console.log(err.message);
        });
    },
  },
};
</script>

<style>
.project {
  background-color: #f2f2f2;
  padding: 10px 15px;
  margin: 10px;
  border-left: 6px solid red;
  border-radius: 10px;
}
h2 {
  color: indigo;
  cursor: pointer;
  user-select: none;
}
h2:hover {
  color: blue;
}
.flexing {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.pjEditBtn {
  font-size: 20px;
  margin-left: 15px;
  user-select: none;
}
.pjEditBtn:hover {
  color: #777;
  cursor: pointer;
}
.complete {
  border-left-color: yellow;
}
</style>