<template>
  <div>
    <svg class="barchart" :width="width + marginLeft / 2" :height="height + marginTop" />
  </div>
</template>

<script>
import { scaleLinear, scaleBand } from "d3-scale";

export default {
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
  computed: {},
};
</script>

<style lang="scss"></style>
