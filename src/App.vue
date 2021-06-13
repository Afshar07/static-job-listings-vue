<template>
  <the-header></the-header>
  <transition-group tag="div" class="container" name="slide" appear>
    <filter-box
      :filtered="filterArgs"
      @remove-filter="removeFilter"
      @clear-filter="clearFilter"
      v-if="showFilterBox"
    ></filter-box>
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
  </transition-group>
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
    };
  },

  components: { TheHeader, AvailableJobs, FilterBox },

  computed: {
    showFilterBox() {
      // Manage v-if on filterBox
      if (this.filterArgs.length == 0) {
        return false;
      } else {
        return true;
      }
    },
  },

  methods: {
    addFilterDataToArray(value) {
      // Add all fJOB FINDERilters to filerArray if not already exist
      if (!this.filterArgs.includes(value)) {
        this.filterArgs.push(value);
      }
      this.isIncludeFilter();
    },
    isIncludeFilter() {
      // Check the data and see if it includes any of filterArgs
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
      // Remove the filter from filterArgs and check the rest of filters in isIncludeFilter
      const index = this.filterArgs.indexOf(value);
      this.filterArgs.splice(index, 1);
      if (this.filterArgs.length === 0) {
        this.allData = Object.assign(Data);
      } else {
        this.isIncludeFilter();
      }
    },
    clearFilter() {
      this.filterArgs = [];
      this.allData = Data;
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
@media only screen and (max-width: 500px) {
  body {
    display: flex;
    justify-content: center;
    background-color: #effafa;
  }
  .container {
    background-color: #effafa;
    min-height: 80vh;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .slide-enter-from {
    opacity: 0;
    transform: translateX(-500px);
  }
  .slide-enter-to {
    opacity: 1;
    transform: translateX(0);
  }
  .slide-enter-active {
    transition: all 0.5s ease-in-out;
  }
  .slide-leave-from {
    opacity: 1;
    transform: translateX(0) translateX(0);
  }
  .slide-leave-to {
    opacity: 0;
    transform: translateX(500px) translateY(0);
  }
  .slide-leave-active {
    transition: all 0.5s ease-in-out;
    position: absolute;
  }
  .slide-move {
    transition: all 0.5s ease;
  }
}
</style>
