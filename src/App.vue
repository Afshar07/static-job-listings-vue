<template>
  <the-header></the-header>
  <filter-box :filtered="filterArgs" @remove-filter="removeFilter"></filter-box>
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
      filterArgs: [],
      searchInThese: [],
    };
  },

  components: { TheHeader, AvailableJobs, FilterBox },

  methods: {
    addFilterDataToArray(value) {
      // Add all fJOB FINDERilters to filerArray if not already exist
      if (!this.filterArgs.includes(value)) {
        this.filterArgs.push(value);
      }
      this.filterArgs.every((each) => {
        this.isIncludeFilter(each);
      });
    },
    isIncludeFilter() {
      const result = Data.filter((job) => {
        let filterableItems = [
          ...job.languages,
          ...job.tools,
          job.level,
          job.role,
        ];
        return this.filterArgs.every((filter) =>
          filterableItems.includes(filter)
        );
      });
      this.allData = result;
    },

    removeFilter(value) {
      const index = this.filterArgs.indexOf(value);
      this.filterArgs.splice(index, 1);
      if (this.filterArgs.length === 0) {
        this.allData = Object.assign(Data);
      } else {
        this.isIncludeFilter();
      }
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
