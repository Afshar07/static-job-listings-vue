<template>
  <div class="filterbox">
    <div class="badges">
      <filter-badge
        :isRemovable="isFilterRemovable"
        :isFilterBox="isFilterBox"
        v-for="filter in filtered"
        :key="filter.id"
        :filter="filter"
        @remove-filter="removeFilter"
      ></filter-badge>
    </div>
    <button class="clear-btn" @click.prevent="clearFilter">Clear</button>
  </div>
</template>

<script>
import FilterBadge from "../badges/FilterBadge.vue";
export default {
  components: { FilterBadge },
  emits: ["remove-filter", "clear-filter"],
  props: ["filtered"],
  data() {
    return {
      isFilterRemovable: true,
      isFilterBox: true,
    };
  },
  methods: {
    removeFilter(value) {
      this.$emit("remove-filter", value);
    },
    clearFilter() {
      this.$emit("clear-filter");
    },
  },
};
</script>

<style scoped>
@media only screen and (max-width: 500px) {
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
    color: #7b8e8e;
    font-weight: 700;
    font-size: 0.9rem;
  }
}
@media only screen and (min-width: 501px) {
  .filterbox {
    background-color: #fff;
    width: 80%;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    border-radius: 10px;
    margin-top: -1.5rem;
    margin-bottom: 1rem;
    box-shadow: 0px 10px 15px -3px rgba(0, 0, 0, 0.1);
    padding: 0.4rem;
  }
  .badges {
    flex-basis: 70%;
    display: flex;
    flex-wrap: wrap;
  }
  .clear-btn {
    background: none;
    border: none;
    color: #7b8e8e;
    font-weight: 700;
    font-size: 0.9rem;
    cursor: pointer;
  }
  .clear-btn:hover {
    color: #5ba4a4;
    text-decoration: underline;
  }
}
</style>
