<template>
  <rect
    :width="width"
    :height="height"
    :x="x"
    :y="y"
    :fill="fill"
    :transform="transform"
    :fill-opcaity="opacity"
  >
  </rect>
</template>

<script>
export default {
  name: "Rect",
  props: {
    width: { type: Number },
    height: { type: Number },
    x: { type: Number },
    y: { type: Number },
    fill: { type: String },
    transform: { type: String },
    opacity: { type: Number },
  },
  data() {
    return {};
  },
};
</script>
<style>
rect {
  border: 1px solid rgb(11, 136, 232);
}
</style>
