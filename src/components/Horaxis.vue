<template>
  <line :x1="x1" :y1="y1" :x2="x2" :y2="y2" :stroke="stroke" :stroke-width="strwidth"></line>
</template>

<script>
export default {
  name: "Horaxis",
  props: {
    x1: { type: Number },
    x2: { type: Number },
    y1: { type: Number },
    y2: { type: Number },
    stroke: { type: String },
    strwidth: { type: Number },
  },
};
</script>

<style></style>
