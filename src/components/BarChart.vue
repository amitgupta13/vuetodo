<template>
  <div>
    <svg
      class="barchart"
      :width="width + marginLeft / 2"
      :height="height + marginTop"
    >
      <g :transform="`translate(${marginLeft / 2}, ${marginTop / 2})`">
        <g
          class="x-axis"
          fill="none"
          :transform="`translate(0, ${height})`"
          style="color: #888"
        >
          <path
            class="domain"
            stroke="currentColor"
            :d="`M0.5,6V0.5H${width}.5V6`"
          />
          <g
            class="tick"
            opacity="1"
            font-size="10"
            font-family="sans-serif"
            text-anchor="middle"
            v-for="(bar, index) in bars"
            :key="index"
            :transform="`translate(${bar.x + bar.width / 2}, 0)`"
          >
            <line stroke="currentColor" y2="6" />
            <text fill="currentColor" y="9" dy="0.71em">{{ bar.xLabel }}</text>
          </g>
        </g>
        <g
          class="y-axis"
          fill="none"
          :transform="`translate(0, 0)`"
          style="color: #888"
        >
          <path
            class="domain"
            stroke="currentColor"
            :d="`M0.5,${height}.5H0.5V0.5H-6`"
          />
          <g
            class="tick"
            opacity="1"
            font-size="10"
            font-family="sans-serif"
            text-anchor="end"
            v-for="(tick, index) in yTicks"
            :key="index"
            :transform="`translate(0, ${y(tick) + 0.5})`"
          >
            <line stroke="currentColor" x2="-6" />
            <text fill="currentColor" x="-9" dy="0.32em">{{ tick }}</text>
          </g>
        </g>
        <g class="bars" fill="none">
          <rect
            v-for="(bar, index) in bars"
            fill="#2196f3"
            :key="index"
            :height="bar.height"
            :width="bar.width"
            :x="bar.x"
            :y="bar.y"
          />
          <text
            v-for="(bar, index) in bars"
            :key="index + bar.xLabel"
            fill="currentColor"
            :x="bar.x + 3"
            :y="bar.y - 3"
          >
            {{ bar.age }}
          </text>
        </g>
      </g>
    </svg>
  </div>
</template>

<script>
import { scaleLinear, scaleBand } from "d3-scale";
import moment from "moment";

export default {
  data() {
    return {
      moment,
    };
  },
  name: "BarChart",
  props: {
    height: { default: 200 },
    width: { default: 500 },
    dataSet: { default: [] },
    marginLeft: { default: 40 },
    marginTop: { default: 40 },
    marginBottom: { default: 40 },
    marginRight: { default: 40 },
    tickCount: { default: 5 },
    barPadding: { default: 0.3 },
  },
  computed: {
    yTicks() {
      return this.y.ticks(this.tickCount);
    },
    x() {
      return scaleBand()
        .range([0, this.width])
        .padding(this.barPadding)
        .domain(this.dataSet.map((e) => e.name));
    },
    y() {
      let values = this.dataSet.map((e) => e.age);
      return scaleLinear()
        .range([this.height, 0])
        .domain([0, Math.max(...this.dataSet.map((item) => item.age))]);
    },
    bars() {
      let bars = this.dataSet.map((d) => {
        return {
          xLabel: this.moment(new Date(d.name)).format("LL"),
          age: d.age,
          x: this.x(d.name),
          y: this.y(d.age),
          width: this.x.bandwidth(),
          height: this.height - this.y(d.age),
        };
      });

      return bars;
    },
    // xTicks() {},
  },
};
</script>

<style lang="scss"></style>
