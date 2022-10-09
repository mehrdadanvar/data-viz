<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div class="code-block" v-for="item in block_size" :key="item">
      <codeBlock />
    </div>
  </div>
</template>
<script>
import codeBlock from "../components/codeBlock.vue";
export default {
  components: {
    codeBlock,
  },
  data() {
    return {
      block_size: [1, 1],
    };
  },
};
</script>
<style scoped>
.about {
  background-color: antiquewhite;
}
</style>
