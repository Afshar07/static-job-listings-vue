<template>
  <div class="badge-container">
    <p class="badge-text">{{ filter }}</p>
  </div>
</template>

<script>
export default {
  props: ["filter"],
};
</script>

<style scoped>
.badge-container {
  background-color: rgb(239, 250, 250);
  padding: 0.4rem 0.5rem;
  margin: 0.5rem;
  cursor: pointer;
}
.badge-text {
  color: #5ba4a4;
  font-weight: 700;
  font-size: 0.7rem;
  margin: 0;
}
</style>
