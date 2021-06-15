<template>
  <div
    class="badge-container"
    :class="{ badgeContainerFilterbox: isFilterBox }"
  >
    <p class="badge-text">{{ filter }}</p>
    <div class="remove" v-if="isRemovable" @click="removeFilter">
      <img :src="removeIcon" alt="remove Icon" class="remove-icon" />
    </div>
  </div>
</template>

<script>
export default {
  props: ["filter", "isRemovable", "isFilterBox"],
  emits: ["remove-filter"],
  data() {
    return {
      removeIcon: require("../../assets/icon-remove.svg"),
    };
  },
  methods: {
    removeFilter() {
      this.$emit("remove-filter", this.filter);
    },
  },
};
</script>

<style scoped>
@media only screen and (max-width: 500px) {
  .badge-container {
    background-color: #effafa;
    margin: 0.5rem;
    display: flex;
    border-radius: 4px;
    min-width: 1rem;
    min-height: 1rem;
  }

  .badge-text {
    color: #5ba4a4;
    font-weight: 700;
    font-size: 0.7rem;
    margin: 0.4rem 0.5rem;
  }
  .remove {
    margin-left: 0.5rem;
    height: auto;
    display: flex;
    align-items: center;
    padding: 0.4rem;
    background-color: #5ba4a4;
    border-top-right-radius: 4px;
    border-bottom-right-radius: 4px;
  }
}
@media only screen and (min-width: 501px) {
  .badge-container {
    background-color: #effafa;
    border-radius: 4px;
    margin: 0.5rem;
    cursor: pointer;
    display: flex;
    align-items: center;
  }
  .badge-container :hover {
    background-color: #5ba4a4;
    color: #fff;
    border-radius: 4px;
  }

  .badgeContainerFilterbox :hover {
    background-color: #effafa !important;
    color: #5ba4a4;
  }

  .badge-text {
    color: #5ba4a4;
    font-weight: 700;
    font-size: 0.7rem;
    padding: 0.35rem 0.5rem;
    margin: 0;
  }
  .remove {
    height: auto;
    display: flex;
    align-items: center;
    padding: 0.4rem;
    background-color: #5ba4a4;
    border-top-right-radius: 4px;
    border-bottom-right-radius: 4px;
  }
  .remove-icon:hover {
    background: none !important;
  }
  .remove:hover {
    border-top-left-radius: 0 !important;
    border-bottom-left-radius: 0 !important;
    background-color: #2c3a3a !important;
  }
}
</style>
