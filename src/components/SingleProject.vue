<template>
  <div class="project">
    <div class="flexing">
      <div>
        <h2 @click="showDetail = !showDetail">{{ project.title }}</h2>
      </div>
      <div>
        <i class="fas fa-solid fa-trash pjEditBtn"></i>
        <i class="fas fa-solid fa-edit pjEditBtn"></i>
        <i class="fas fa-solid fa-check pjEditBtn"></i>
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
    };
  },
  props: ["project"],
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
</style>