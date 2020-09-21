<template>
  <div class="home">
    <button @click="changeData">Change Data</button>
    <BarChart
      class="chart"
      :data-set="data"
      :margin-left="40"
      :margin-top="40"
      :tick-count="5"
      :bar-padding="0.5"
    />
  </div>
</template>

<script>
import BarChart from "../components/BarChart.vue";

export default {
  name: "home",
  data() {
    return {
      data: [
        {
          name: "2020-06-04",
          age: 4,
        },
        {
          name: "2020-06-05",
          age: 2,
        },
        {
          name: "2020-06-06",
          age: 2,
        },
        {
          name: "2020-06-07",
          age: 2,
        },
        {
          name: "2020-06-08",
          age: 6,
        },
        {
          name: "2020-06-09",
          age: 6,
        },
        {
          name: "2020-06-10",
          age: 6,
        },
      ],
    };
  },
  components: {
    BarChart,
  },
  methods: {
    changeData() {
      this.data = [
        {
          name: "2020-06-04",
          age: 4,
        },
        {
          name: "2020-06-05",
          age: 2,
        },
        {
          name: "2020-06-06",
          age: 2,
        },
        {
          name: "2020-06-07",
          age: 2,
        },
        {
          name: "2020-06-08",
          age: 6,
        },
        {
          name: "2020-06-09",
          age: 6,
        },
        {
          name: "2020-06-10",
          age: 6,
        },
      ];
    },
  },
};
</script>
