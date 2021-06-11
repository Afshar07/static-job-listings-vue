<template>
  <div class="job-container" :class="featuredClass">
    <img :src="imgLinkNew" alt="Company Logo" class="company-logo" />

    <div class="names-badges">
      <h3 class="company-name">{{ company }}</h3>

      <new-badge v-if="isNew"></new-badge>

      <featured-badge v-if="isFeatured"></featured-badge>
    </div>
    <h4 class="position">{{ position }}</h4>

    <job-description :description="jobDescription"></job-description>

    <hr />
    <div class="filter-badges">
      <filter-badge
        v-for="filter in filterBadge"
        :key="filter"
        :filter="filter"
      ></filter-badge>
    </div>
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
    "level",
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
      filterBadge: [this.role, this.level, ...this.languages, ...this.tools],
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
  .job-container {
    width: 80%;
    height: 100%;
    background-color: #fff !important;
    margin: 2.5rem 1rem 1rem 1rem;
    padding: 1rem;
    border-radius: 0.3rem;
    position: relative;
    box-shadow: 0px 10px 15px -3px rgba(0, 0, 0, 0.1);
  }
  .job-container:first-of-type {
    margin-top: 4rem;
  }
  .job-container:last-of-type {
    margin-bottom: 4rem;
  }
  .company-logo {
    position: absolute;
    top: -2.5rem;
    left: 1.5rem;
    transform: scale(0.8);
  }
  .new-border {
    border-left: 3px solid #5ba4a4;
  }
  .names-badges {
    display: flex;
    align-items: center;
    margin-top: 1rem;
  }
  .company-name {
    color: #5ba4a4;
  }
  .position {
    font-size: 1rem;
    color: #2c3a3a;
    margin-top: 0;
  }
  hr {
    border: none;
    width: 97%;
    border-bottom: 2px solid rgba(44, 58, 58, 0.1);
  }
  .filter-badges {
    display: flex;
    flex-wrap: wrap;
  }
}
</style>
