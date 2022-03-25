<template>
  <h1>Add Project</h1>
  <form>
    <div class="inputBox">
      <label for="title" class="projectTitle">Project Title</label>
      <input type="text" id="title" class="projectInput" />
    </div>

    <div class="inputBox">
      <label for="detail" class="projectTitle">Project Detail</label>
      <input type="text" id="detail" class="projectInput" />
    </div>

    <div class="btnBox">
      <button class="addBtn">Add Project</button>
    </div>
  </form>
</template>

<script>
export default {};
</script>

<style>
h1 {
  text-align: center;
}
.inputBox {
  margin: 50px 0;
}
.projectTitle {
  display: block;
  font-size: 25px;
  font-weight: bold;
  color: rgb(20, 161, 107);
}
.projectInput {
  border: none;
  border-bottom: 1px solid #aaa;
  width: 80%;
  font-size: 22px;
  padding: 6px 0;
  outline: none;
}
.addBtn {
  border: none;
  outline: none;
  background-color: blue;
  padding: 5px 10px;
  color: white;
  font-size: 18px;
  font-weight: bold;
  border-radius: 5px;
  cursor: pointer;
}
.btnBox {
  text-align: center;
}
</style>