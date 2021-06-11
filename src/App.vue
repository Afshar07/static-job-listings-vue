<template>
  <the-header></the-header>
  <filter-box :filtered="filterArray"></filter-box>
  <div class="container">
    <available-jobs
      v-for="data in allData"
      :key="data.id"
      :id="data.id"
      :company="data.company"
      :logo="data.logo"
      :isNew="data.new"
      :isFeatured="data.featured"
      :position="data.position"
      :level="data.level"
      :role="data.role"
      :postedTime="data.postedAt"
      :contract="data.contract"
      :location="data.location"
      :languages="data.languages"
      :tools="data.tools"
      @filterItems="addFilterDataToArray"
    ></available-jobs>
  </div>
</template>

<script>
import TheHeader from "./components/views/TheHeader.vue";
import AvailableJobs from "./components/AvailableJobs.vue";
import FilterBox from "./components/views/FilterBox.vue";
import Data from "./data.json";
export default {
  data() {
    return {
      allData: Object.assign(Data),
      filterArray: [],
    };
  },
  components: { TheHeader, AvailableJobs, FilterBox },
  methods: {
    addFilterDataToArray(value) {
      // Add all filters to filerArray
      if (!this.filterArray.includes(value)) {
        this.filterArray.push(value);
        this.newFilteredData(value);
      }
      console.log(this.filterArray);
    },

    newFilteredData(value) {
      let filtered = this.allData.filter((jobs) => {
        const filterableItems = [
          ...jobs.languages,
          ...jobs.tools,
          jobs.level,
          jobs.role,
        ];

        return filterableItems.includes(value);
      });
      this.allData = filtered;
    },
  },
};
</script>
<style>
@import url("https://fonts.googleapis.com/css2?family=Spartan:wght@500;700&display=swap");
html,
body {
  margin: 0;
  padding: 0;
  font-family: "Spartan", sans-serif !important;
}
</style>
<style scoped>
.container {
  background-color: #effafa;
  min-height: 100vh;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
