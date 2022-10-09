<template>
  <div class="code-block">
    <button class="add">+</button>
    <button class="add">*</button>
    <div class="code-input">
      <input type="text" />
    </div>
  </div>
</template>

<script>
export default {
  name: "codeBlock",
  data() {
    return {
      blocks: 1,
    };
  },
  methods: {},
};
</script>

<style>
.code-block {
  width: 1200px;
  height: auto;
  min-height: 100px;
  border: 1px solid grey;
  background-color: white;
}
input {
  width: 1100px;
  height: auto;
  min-height: 100px;
  background-color: white;
}
</style>
