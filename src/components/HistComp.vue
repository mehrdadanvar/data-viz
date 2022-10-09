<template>
  <div class="box">
    <div>
      <svg width="600" height="600">
        <!-- prettier-ignore -->
        <Rect
        class="rect"
        v-for="(rect,index) in rects"
        :key="index"
        :height="rect.freq*5"
        :width="10"
        :x="((11*rect.id)+(11))"
        :y="140"
        :fill="'cyan'"
        :transform="'translate(600,600) rotate(180)'"
         />
        <!-- <Rect
          v-for="(rect, index) in rects"
          :key="index"
          :height="rect.freq * 5"
          :width="10"
          :x="11 * rect.id + 11"
          :y="20"
          :fill="'red'"
          :transform="'translate(600,500) rotate(170)'"
          :fill-opacity="0.3"
        /> -->
        <line x1="0" x2="500" y1="450" y2="450" stroke="blue" stroke-width="1" />
        <line x1="0" x2="0" y1="1" y2="450" stroke="navy" stroke-width="10" />
        <text class="chart-title" x="50" y="15">Normally Distributed Ramdom Numbers</text>
      </svg>
    </div>
    <button @click="generate">generat numbers</button>
    <button @click="binz">get sorted</button>
  </div>
  <div>
    <!-- <h3>this is the arrau of data</h3> -->
    <!-- <ul v-for="rect in rects" v-bind:key="rect">
      <li>{{ rect }}</li>
    </ul> -->
  </div>
</template>
<script>
import Rect from "./RectView.vue";
export default {
  name: "Hist",
  components: {
    Rect,
  },
  data() {
    return {
      rects: "",
      mehrdad: 0.1,
    };
  },
  methods: {
    binz() {
      function cl(a) {
        console.log(a);
      }
      console.log("working");
      function randn(n) {
        let u = 1 - Math.random(); //Converting [0,1) to (0,1)
        let v = Math.random();
        function generate() {
          return (
            Math.sqrt(-2.0 * Math.log(1 - Math.random())) * Math.cos(2.0 * Math.PI * Math.random())
          );
        }
        let rands = [];
        for (let i = 0; i < n; i++) {
          rands.push(generate());
        }
        return rands;
      }
      function hist(data, number_bins) {
        let sorted = data.sort((a, b) => b - a);
        let minimum = Math.min(...sorted);
        let maximum = Math.max(...sorted);
        let range = maximum - minimum;
        let determind_bins = number_bins;
        let len_data = sorted.length;
        let n_bins = Math.round(len_data / determind_bins);
        let dist = range / n_bins;
        cl(minimum, maximum, range, len_data, n_bins, dist);
        let r = {
          minimum: minimum,
          maximum: maximum,
          range: range,
          len: len_data,
          ideal_bins: n_bins,
          dist: dist,
        };
        let quads = [];
        for (let i in [...Array(r.ideal_bins).keys()]) {
          // prettier-ignore
          let lower = r.minimum + (r.dist * i);
          // prettier-ignore
          let upper = lower + r.dist;
          let inter = sorted.filter((x) => {
            let y = x >= lower && x < upper;
            return y;
          });
          let freq = inter.length;
          quads.push({
            lower: parseFloat(lower),
            upper: parseFloat(upper),
            freq: parseFloat(freq),
            id: parseInt(i),
          });
        }
        cl(quads.length);
        return quads;
      }
      let rects = hist(randn(1000), 20);
      console.log(rects);
      this.rects = rects;
    },
  },
};
</script>
<style>
.box {
  width: 500px;
  height: 500px;
  /* border: 3px solid rgb(197, 24, 24); */
  margin-left: 1rem;
}
svg {
  box-shadow: 0 0 10px navy;
  padding: 1rem;
}
.chart-title {
  font-size: 18px;
  text-decoration: underline;
}
.rect {
  opacity: v-bind(mehrdad);
}
</style>
