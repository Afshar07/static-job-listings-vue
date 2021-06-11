<template>
  <div class="badge-container">
    <p class="badge-text">{{ filter }}</p>
    <div class="remove" v-if="isRemovable">
      <img :src="removeIcon" alt="remove Icon" class="remove-icon" />
    </div>
  </div>
</template>

<script>
export default {
  props: ["filter", "isRemovable"],
  emits: ["filtered"],
  data() {
    return {
      removeIcon: require("../../assets/icon-remove.svg"),
    };
  },
};
</script>

<style scoped>
.badge-container {
  background-color: rgb(239, 250, 250);
  margin: 0.5rem;
  display: flex;
  border-radius: 4px;
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
</style>
