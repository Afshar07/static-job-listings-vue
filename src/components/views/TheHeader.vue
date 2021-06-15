<template>
  <div class="header"></div>
</template>

<style scoped>
body {
  margin: 0;
  padding: 0;
  width: 100vw !important;
}
@media only screen and (max-width: 500px) {
  .header {
    background: url("../../assets/bg-header-mobile.svg") no-repeat,
      linear-gradient(to right, #5ba4a4 220px, #63baba 70%);
    width: 100%;
    height: 9.5rem;
  }
}
@media only screen and (min-width: 501px) {
  .header {
    background: #5ba4a4 url("../../assets/bg-header-desktop.svg") no-repeat;
    width: 100%;
    height: 9.8rem;
  }
}
</style>
