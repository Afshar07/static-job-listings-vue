<template>
  <div class="filterbox">
    <filter-badge
      :isRemovable="isFilterRemovable"
      v-for="filter in filtered"
      :key="filter.id"
      :filter="filter"
      @remove-filter="removeFilter"
    ></filter-badge>
  </div>
</template>

<script>
import FilterBadge from "../badges/FilterBadge.vue";
export default {
  components: { FilterBadge },
  emits: ["remove-filter"],
  props: ["filtered"],
  data() {
    return {
      isFilterRemovable: true,
    };
  },
  methods: {
    removeFilter(value) {
      this.$emit("remove-filter", value);
    },
  },
};
</script>

<style scoped>
.filterbox {
  background-color: #fff;
  display: flex;
  flex-wrap: wrap;
}
</style>
