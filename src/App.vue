<template>
  <the-header></the-header>
  <div class="container">
    <available-jobs
      v-for="data in allData"
      :key="data.id"
      :id="data.id"
      :company="data.company"
      :logo="data.logo"
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
html,
body {
  margin: 0;
  padding: 0;
}
.container {
  background-color: #effafa;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
