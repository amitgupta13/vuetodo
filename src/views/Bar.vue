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
        { name: "Bob", age: 32 },
        { name: "Robin", age: 24 },
        { name: "Mark", age: 22 },
        { name: "Joe", age: 29 },
        { name: "Eve", age: 38 },
        { name: "Karen", age: 21 },
        { name: "Kirsty", age: 25 },
        { name: "Chris", age: 30 },
        { name: "Butcher", age: 32 },
      ],
    };
  },
  components: {
    BarChart,
  },
  methods: {
    changeData() {
      this.data = [
        { name: "Bob", age: 42 },
        { name: "Robin", age: 64 },
        { name: "Mark", age: 25 },
        { name: "Joe", age: 19 },
        { name: "Eve", age: 38 },
        { name: "Karen", age: 21 },
        { name: "Kirsty", age: 59 },
        { name: "Chris", age: 43 },
        { name: "Butcher", age: 22 },
      ];
    },
  },
};
</script>
