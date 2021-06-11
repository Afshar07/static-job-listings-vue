<template>
  <div class="filterbox">
    <filter-badge
      :isRemovable="isFilterRemovable"
      v-for="filter in filtered"
      :key="filter"
      :filter="filter"
    ></filter-badge>
  </div>
</template>

<script>
import FilterBadge from "../badges/FilterBadge.vue";
export default {
  components: { FilterBadge },
  props: ["filtered"],
  data() {
    return {
      isFilterRemovable: true,
    };
  },
};
</script>

<style scoped>
.filterbox {
  background-color: #fff;
  display: flex;
}
</style>
