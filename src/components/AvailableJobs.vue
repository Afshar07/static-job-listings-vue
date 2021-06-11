<template>
  <div class="container" :class="featuredClass">
    <img :src="imgLinkNew" alt="Company Logo" />

    <h2 class="company-name">{{ company }}</h2>

    <new-badge v-if="isNew"></new-badge>

    <featured-badge v-if="isFeatured"></featured-badge>

    <h4 class="position">{{ position }}</h4>

    <job-description
      v-for="description in jobDescription"
      :key="description"
      :desc="description"
    ></job-description>

    <hr />
    <filter-badge
      v-for="filter in filterBadge"
      :key="filter"
      :filter="filter"
    ></filter-badge>
  </div>
</template>

<script>
import NewBadge from "./badges/NewBadge.vue";
import FeaturedBadge from "./badges/FeaturedBadge.vue";
import FilterBadge from "./badges/FilterBadge.vue";
import jobDescription from "./views/JobDescription.vue";
export default {
  components: { NewBadge, FeaturedBadge, FilterBadge, jobDescription },
  props: [
    "logo",
    "company",
    "isNew",
    "isFeatured",
    "position",
    "role",
    "postedTime",
    "contract",
    "location",
    "languages",
    "tools",
  ],
  data() {
    return {
      imgLinkNew: require(`../assets/${this.logo}`),
      filterBadge: [...this.languages, ...this.tools, this.role, this.position],
      jobDescription: [this.postedTime, this.contract, this.location],
    };
  },
  computed: {
    featuredClass() {
      return this.isFeatured ? "new-border" : "";
    },
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
  .position {
    font-size: 1rem;
    color: #2c3a3a;
  }
  hr {
    border: none;
    width: 90%;
    border-bottom: 2px solid rgba(44, 58, 58, 0.1);
  }
}
</style>
