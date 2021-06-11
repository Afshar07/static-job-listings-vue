<template>
  <div>
    <ul class="description-container">
      <li class="job-desc" v-for="desc in description" :key="desc">
        {{ desc }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ["description"],
};
</script>

<style scoped>
.description-container {
  color: #7b8e8e;
  display: flex;
  padding: 0;
}
.job-desc {
  font-size: 0.8rem;
  margin-left: 1.5rem;
}
.job-desc:first-of-type {
  margin-left: 0;
  list-style-type: none;
}
</style>
