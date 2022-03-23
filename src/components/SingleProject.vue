<template>
  <div class="project" @click="showDetail = !showDetail">
    <h2>{{ project.title }}</h2>
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
  cursor: pointer;
}
h2 {
  color: indigo;
}
</style>