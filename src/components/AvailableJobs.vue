<template>
  <div class="container">
    <img :src="imgLinkNew" alt="" />
  </div>
</template>

<script>
export default {
  props: ["logo"],
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
  }
}
</style>
