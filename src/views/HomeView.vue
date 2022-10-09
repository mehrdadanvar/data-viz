<template>
  <div class="home">
    <h1>Home view</h1>
    <section class="section">
      <!-- <div class="container left">
        <input type="range" min="20" max="150" />
        <input type="range" min="20" max="150" />
        <button @click="increase">increase height</button>
        <button @click="deacrease">deacrease height</button>
        <p>value of the slider is {{ value }}</p>
      </div> -->
      <div class="container right">
        <Hist />
      </div>
    </section>
    <!-- <section class="hist">
      <Hist />
    </section> -->
  </div>
</template>

<script>
// @ is an alias to /src
import Hist from "../components/HistComp.vue";
export default {
  name: "HomeView",
  components: {
    Hist,
  },
  methods: {
    increase() {
      console.log("change");
      this.height++;
    },
    deacrease() {
      console.log("change");
      this.height--;
    },
  },
};
</script>
<style>
.section {
  width: 1200px;
  height: 700px;
  display: flex;
}

.container {
  border: 3px solid rgb(171, 26, 26);
  border-radius: 1rem;
  width: 700px;
  height: 700px;
  margin-left: 5rem;
}
.home {
}
</style>
