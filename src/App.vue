<template>
  <the-header></the-header>
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
    ></available-jobs>
  </div>
</template>

<script>
import TheHeader from "./components/views/TheHeader.vue";
import AvailableJobs from "./components/AvailableJobs.vue";
import data from "./data.json";
export default {
  data() {
    return {
      allData: data,
    };
  },
  components: { TheHeader, AvailableJobs },
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
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
