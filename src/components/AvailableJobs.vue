<template>
  <div class="container" :class="{ 'new-border': isFeatured }">
    <img :src="imgLinkNew" alt="Company Logo" />

    <h2 class="company-name">{{ company }}</h2>

    <new-badge v-if="isNew"></new-badge>

    <featured-badge v-if="isFeatured"></featured-badge>

    <h2 class="position">{{ position }}</h2>
  </div>
</template>

<script>
import NewBadge from "./badges/NewBadge.vue";
import FeaturedBadge from "./badges/FeaturedBadge.vue";
export default {
  components: { NewBadge, FeaturedBadge },
  props: ["logo", "company", "isNew", "isFeatured", "position"],
  data() {
    return {
      imgLinkNew: require(`../assets/${this.logo}`),
    };
  },
};
</script>

<style scoped>
@media only screen and (max-width: 500px) {
  .container {
    width: 80%;
    height: 100%;
    background-color: #fff;
    margin: 1rem;
    padding: 1rem;
    border-radius: 0.3rem;
  }
  .new-border {
    border-left: 3px solid #5ba4a4;
  }
  .company-name {
    color: #5ba4a4;
  }
}
</style>
