<template>
  <nav class="filter-nav">
    <button @click="filterBy('all')">
      <span :class="{ active: current === 'all' }">All</span>
    </button>
    <button @click="filterBy('complete')">
      <span :class="{ active: current === 'complete' }">Complete</span>
    </button>
    <button @click="filterBy('ongoing')">
      <span :class="{ active: current === 'ongoing' }">Ongoing</span>
    </button>
  </nav>
</template>

<script>
export default {
  props: ["current"],
  methods: {
    filterBy(value) {
      this.$emit("filterValue", value);
    },
  },
};
</script>

<style>
.filter-nav button {
  border: none;
  background-color: rgba(255, 255, 255, 0);
  color: #bbb;
  font-weight: bold;
  text-transform: uppercase;
  cursor: pointer;
}
.active {
  color: #333;
}
</style>