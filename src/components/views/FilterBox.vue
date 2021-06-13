<template>
  <div class="filterbox">
    <!-- <div class="spacer"></div> -->
    <div class="badges">
      <filter-badge
        :isRemovable="isFilterRemovable"
        v-for="filter in filtered"
        :key="filter.id"
        :filter="filter"
        @remove-filter="removeFilter"
      ></filter-badge>
    </div>
    <button class="clear-btn">Clear</button>
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
  width: 90%;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  border-radius: 10px;
  margin-top: -3rem;
  margin-bottom: 1rem;
}
.badges {
  flex-basis: 70%;
  display: flex;
  flex-wrap: wrap;
}
.clear-btn {
  background: none;
  border: none;
  color: #5ba4a4;
  font-weight: 700;
  font-size: .9rem;
}
</style>
